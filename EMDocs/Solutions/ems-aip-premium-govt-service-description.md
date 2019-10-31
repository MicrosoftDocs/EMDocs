---
# required metadata

title: Azure Information Protection Premium Government Service Description
description: Azure Information Protection Premium Government Service Description is designed to serve as an overview of our offering
keywords:
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 05/29/2019
ms.topic: article
ms.prod:
ms.service: ems

---

# Azure Information Protection Premium Government Service Description 

## How to use this Service Description 

The Azure Information Protection Premium Government Service Description is designed to serve as an overview of our offering and will cover: (1) which services and features are included in this offer, (2) how the Government offers differ from our existing commercial offers, and (3) our current compliance commitments. This document defines the unique commitments and differences compared to Azure Information Protection Premium commercial offerings. 

## About Azure Information Protection Premium Government Environments 

Azure Information Protection Premium Government plans are monthly subscriptions and are licensed on a per user basis. Organizations that use Azure Information Protection Premium Government benefit from the following unique features: 

* Your organization's content is physically segregated from content in Microsoft's commercial Azure Information Protection Premium services. 

* Your organization's content is stored within the United States. 

* Access to Microsoft systems containing your content is restricted to screened Microsoft personnel. 

* Azure Information Protection Premium Government complies with common certifications and accreditations that are required for US Public Sector customers. 

## Customer Eligibility 

Azure Information Protection Premium Government is available to (1) US federal, state, local, and tribal government entities, and (2) other entities that handle data that is subject to government regulations and requirements and where use of Azure Information Protection Premium Government is appropriate to meet these requirements, subject to validation of eligibility. Validation of eligibility by Microsoft will include confirmation of handling government-regulated or controlled data. This offer is limited to customers that have at least 500 seats. Entities with questions about eligibility for Azure Information Protection Premium Government should consult their account team. 

## Location of Customer Data 

Azure Information Protection Premium Government services are provided from datacenters physically located in the United States. All content is stored at rest in datacenters physically located only in the United States. 

## Azure Information Protection Premium Government and Third-Party Services 

Various Azure Information Protection Premium services provide the ability to work seamlessly with third-party applications and services. These third-party applications and services might involve storing, transmitting, and processing your organization's customer content on third-party systems that are outside of the Azure Information Protection Premium infrastructure and therefore are not covered by our compliance and data protection commitments. It is recommended that you review the privacy and compliance statements provided by the third parties when assessing the appropriate use of these services for your organization. 

## Azure Information Protection Premium Government Offers and Office 365 Interoperability 

Office 365 is currently available in both the GCC and GCC High environments, and in the DoD environment in late July, 2019. To learn more about these offers, please reference the Office 365 Government [Service Description](https://technet.microsoft.com/library/mt774581.aspx). 
The Azure Information Protection Premium commercial offering is fully interoperable with Office 365 GCC, and we are FedRAMP-Moderate certified for this offer. 
The Azure Information Protection Premium is currently available in the GCC High environment, and in the DoD environment by July, 2019. It is built on the [Microsoft Azure Government Cloud](https://docs.microsoft.com/azure/azure-government/documentation-government-welcome) and is designed to interoperate with the Office 365 GCC High and Office 365 DoD offers respectively. The Azure Information Protection Premium GCC High and DoD offers are currently certified FedRAMP-High. 

| Azure Information Protection Premium Government Offer | Corresponding Office 365 Government Offer | Compliance Commitment 
|---|---|
Azure Information Protection Premium P1/P2 (commercial) | Office 365, GCC | FedRAMP-Moderate
Azure Information Protection Premium P1/P2 GCC High | Office 365, GCC High | FedRAMP-High 
Azure Information Protection Premium P1/P2 DoD | Office 365, DoD | FedRAMP-High
 

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
