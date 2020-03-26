---
# required metadata

title: Azure Information Protection Premium Government Service Description
description: Azure Information Protection Premium Government Service Description is designed to serve as an overview of our offering
keywords:
author: mlottner
ms.author: mlottner
manager: dougeby
ms.date: 03/26/2020
ms.topic: article
ms.prod:
ms.service: rights-management
ms-suite: ems

---

# Azure Information Protection Premium Government Service Description 

## How to use this Service Description 

The Azure Information Protection Premium Government Service Description is designed to serve as an overview of our offering in the GCC High and DoD environments and will cover feature variations compared to Azure Information Protection Premium commercial offerings. To learn more about Azure Information Protection for GCC customers, see the description of [EMS offers for US Government and Office 365 interoperability](ems-govt-service-description.md#ems-offers-for-us-government-and-office-365-interoperability).

## Azure Information Protection Premium Government and Third-Party Services 

Various Azure Information Protection Premium services provide the ability to work seamlessly with third-party applications and services. These third-party applications and services might involve storing, transmitting, and processing your organization's customer content on third-party systems that are outside of the Azure Information Protection Premium infrastructure and therefore are not covered by our compliance and data protection commitments. It is recommended that you review the privacy and compliance statements provided by the third parties when assessing the appropriate use of these services for your organization. 

## Parity with Azure Information Protection Premium Commercial Offerings 

While our goal is to deliver all commercial features and functionality to government customers with our Azure Information Protection Premium GCC High and DoD offers, there is some missing functionality that we'd like to highlight. 

These are the known existing gaps between Azure Information Protection Premium GCC High/DoD and our commercial offer as of May 2019: 

* Document tracking and revocation is currently not available. 

* The classification and labelling add-in will be supported only for Office 365 ProPlus (version 9126.1001 or higher). Office 2010, Office 2013, and other Office 2016 versions will not be supported. 

* Information Rights Management (IRM) will be supported only for Office 365 ProPlus (version 9126.1001 or higher). Office 2010, Office 2013, and other Office 2016 versions will not be supported. 

* Migration from Active Directory Rights Management Services (AD RMS) to Azure Information Protection is currently not available. 

* Sharing of protected documents and emails to users in the commercial cloud is currently not available. This includes Office 365 users in the commercial cloud, non-Office 365 users in the commercial cloud, and users with an RMS for Individuals license. 

* Information Rights Management with SharePoint Online (IRM-protected sites and libraries) is currently not available. 

* The Rights Management Connector is currently not available.

* The Mobile Device Extension for AD RMS is currently not available.


## Configuring Azure Information Protection for GCC High and DoD customers

### Enable Rights Management for the tenant
For the encryption to work correctly, the Rights Management Service must be enabled for the tenant.

* Check if the Rights Management service is enabled
  * Launch PowerShell as an Administrator
  * Run `Install-Module aadrm` if the AADRM module is not installed 
  * Connect to service using `Connect-aadrmservice -environmentname azureusgovernment`
  * Run `(Get-AadrmConfiguration).FunctionalState` and check if the state is  `Enabled`
* If the functional state is `Disabled`, run `Enable-Aadrm`

### DNS configuration for encryption (Windows)
For encryption to work correctly, Office client applications must connect to the GCC High/DoD instance of the service and bootstrap from there. To redirect clients applications to the right service instance, the tenant admin must configure a DNS SRV record with information about the Azure RMS URL. Without the DNS SRV record, the client application will attempt connect to the public cloud instance by default, will fail.

Also, the assumption is that users will log in with the username based off the tenant-owned-domain (e.g.: joe@contoso.us), and not the onmicrosoft username (e.g.: joe@contoso.onmicrosoft.us). The domain name from the username is used for DNS redirection to the right service instance.

* Get the Rights Management Service ID 
  * Launch PowerShell as an Administrator 
  * Run `Install-Module aadrm` if the AADRM module is not installed 
  * Connect to service using `Connect-aadrmservice -environmentname azureusgovernment`
  * Run `(Get-aadrmconfiguration).RightsManagementServiceId` to get the Rights Management Service ID
* Log in to your DNS provider, and navigate to the DNS settings for the domain to add a new SRV record
  * Service = `_rmsredir` 
  * Protocol = `_http` 
  * Name = `_tcp` 
  * Target = `[GUID].rms.aadrm.us`  (where GUID is the Rights Management Service ID) 
  * Port = `80` 
  * Priority, Weight, Seconds, TTL = default values 
* Associate the custom domain with the tenant in the [Azure portal](https://portal.azure.us/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Domains). This will add an entry in DNS which might take some minutes to get verified after you add the value in the DNS settings.  
* Login to the Office Admin Center with the corresponding global admin credentials and add the domain (example: contoso.us) for user creation. In the verification process, some more DNS changes might be required. Once verification is done, users can be created.

### DNS configuration for encryption (Mac, iOS, Android)
* Log in to your DNS provider, and navigate to the DNS settings for the domain to add a new SRV record
  * Service = `_rmsdisco` 
  * Protocol = `_http` 
  * Name = `_tcp` 
  * Target = `api.aadrm.us` 
  * Port = `80` 
  * Priority, Weight, Seconds, TTL = default values 


### AIP apps configuration

The AIP apps on Windows need a special registry key to point them to the right service instance for GCC High/DoD.  

| Registry Node | HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIP |
| --- | --- |
| Name | WebServiceUrl |
| Value | https://api.informationprotection.azure.us |
| Type | REG_SZ (String) |

## Service Tags

Make sure to allow access to all ports for the following **Service Tags**:
*    AzureInformationProtection
*    AzureActiveDirectory
*    AzureFrontDoor.FrontEnd
