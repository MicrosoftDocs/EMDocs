---
# required metadata

title: Azure Information Protection Premium Government Service Description
description: Azure Information Protection Premium Government Service Description is designed to serve as an overview of our offering
keywords:
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 07/23/2020
ms.topic: article
ms.prod:
ms.service: rights-management
ms-suite: ems

---

# Azure Information Protection Premium Government Service Description 

## How to use this Service Description 

The Azure Information Protection Premium Government Service Description is designed to serve as an overview of our offering in the GCC High, and DoD environments and will cover feature variations compared to Azure Information Protection Premium commercial offerings. To learn more about Azure Information Protection for GCC and GCC High customers, see the description of [EMS offers for US Government and Office 365 interoperability](ems-govt-service-description.md#ems-offers-for-us-government-and-office-365-interoperability).

## Azure Information Protection Premium Government and Third-Party Services 

Some Azure Information Protection Premium services provide the ability to work seamlessly with third-party applications and services. These third-party applications and services may involve storing, transmitting, and processing your organization's customer content on third-party systems that are outside of the Azure Information Protection Premium infrastructure, and therefore not covered by our compliance and data protection commitments. Make sure you review the privacy and compliance statements provided by the third parties when assessing the appropriate use of these services for your organization. 

## Parity with Azure Information Protection Premium Commercial Offerings 

We aim to deliver all commercial features and functionality to government Azure Information Protection Premium GCC High and DoD customers, be aware of the following list of missing functionality.  

Known existing gaps between Azure Information Protection Premium GCC High/DoD and the commercial offering, as of July 2020 are:

* Document tracking and revocation are currently not available. 

* The classification and labeling add-in is only supported for Microsoft 365 Apps (version 9126.1001 or higher). Office 2010, Office 2013, and other Office 2016 versions are not supported. 

* Information Rights Management (IRM) is supported only for Microsoft 365 Apps (version 9126.1001 or higher). Office 2010, Office 2013, and other Office 2016 versions are not supported. 

* Sharing of protected documents and emails to users in the commercial cloud is not currently available. Includes Microsoft 365 Apps users in the commercial cloud, non-Microsoft 365 Apps users in the commercial cloud, and users with an RMS for Individuals license. 

* Information Rights Management with SharePoint Online (IRM-protected sites and libraries) is currently not available. 

* The Rights Management Connector is currently not available.

* The Mobile Device Extension for AD RMS is currently not available.


## Configuring Azure Information Protection unified labeling solution for GCC High and DoD customers

The configuration details provided in this section are relevant only for the Azure Information Protection unified labeling solution for GCC High and DoD customers. For all other configuration details, see [standard configuration information for GCC High and DoD customers](#configuring-azure-information-protection-for-gcc-high-and-dod-customers) 

### AIP apps configuration (unified labeling only)

For the unified labeling solution, AIP apps on Windows need a special registry key to point them to the correct sovereign cloud. Make sure to use the correct values for your setup.  

| Registry Node | HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIP |
| --- | --- |
| Name | CloudEnvType |
| Value | 0/1/2/3/4/5/6/7  |
| Type | REG_DWORD |
 

| Values  | details  |
|---------|---------|
|Commercial  |  0  (default)     |
|GCC   |     1    |
|GCC High    |    2     |
|GCC DOD   |  3       |
|USNat/EX    |    4     |
|USSec/RX    |    5     |
|AAD China (Mooncake/Gallatin)    |   6      |
|AAD Germany    |   7      |

 
- Default value of the registry key is 0 (zero). 
- If the key is empty or incorrect, the expected behavior is a print error into the log, and it will behave like the default (0-commercial). 
- If the key doesn’t exist, it will behave as default (0-commercial).
- Make sure not to delete the registry key after an uninstall. 

## Configuring Azure Information Protection for GCC High and DoD customers

The following configuration details are relevant for all Azure Information Protection solutions for GCC High and DoD customers, including unified labeling solutions. 

### Enable Rights Management for the tenant

For the encryption to work correctly, the Rights Management Service must be enabled for the tenant.

* Check if the Rights Management service is enabled
  * Launch PowerShell as an Administrator
  * Run `Install-Module aadrm` if the AADRM module is not installed 
  * Connect to service using `Connect-aadrmservice -environmentname azureusgovernment`
  * Run `(Get-AadrmConfiguration).FunctionalState` and check if the state is  `Enabled`
* If the functional state is `Disabled`, run `Enable-Aadrm`

### DNS configuration for encryption (Windows)
For encryption to work correctly, Office client applications must connect to the GCC, GCC High/DoD instance of the service and bootstrap from there. To redirect clients applications to the right service instance, the tenant admin must configure a DNS SRV record with information about the Azure RMS URL. Without the DNS SRV record, the client application will attempt connect to the public cloud instance by default, will fail.

Also, the assumption is that users will log in with the username based off the tenant-owned-domain (for example: joe@contoso.us), and not the onmicrosoft username (for example: joe@contoso.onmicrosoft.us). The domain name from the username is used for DNS redirection to the right service instance.

* Get the Rights Management Service ID 
  * Launch PowerShell as an Administrator 
  * If the AADRM module is not installed, run `Install-Module aadrm`  
  * Connect to service using `Connect-aadrmservice -environmentname azureusgovernment`
  * Run `(Get-aadrmconfiguration).RightsManagementServiceId` to get the Rights Management Service ID
* Sign in to your DNS provider, and navigate to the DNS settings for the domain to add a new SRV record
  * Service = `_rmsredir` 
  * Protocol = `_http` 
  * Name = `_tcp` 
  * Target = `[GUID].rms.aadrm.us`  (where GUID is the Rights Management Service ID) 
  * Port = `80` 
  * Priority, Weight, Seconds, TTL = default values 
* Associate the custom domain with the tenant in the [Azure portal](https://portal.azure.us/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Domains). Associating the custom domain will add an entry in DNS, which may take a few minutes to verify after adding the value.   
* Sign in to the Office Admin Center with the corresponding global admin credentials and add the domain (example: contoso.us) for user creation. In the verification process, some more DNS changes might be required. Once verification is done, users can be created.

### DNS configuration for encryption (Mac, iOS, Android)
* Sign in to your DNS provider, and navigate to the DNS settings for the domain to add a new SRV record
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


## Firewalls and network infrastructure

If you have a firewall or similar intervening network devices that are configured to allow specific connections, use these settings to ensure smooth communication for Azure Information Protection.

- To enable the Azure Information Protection Classic client to download labels and label policies: Allow the URL **api.informationprotection.azure.us** over HTTPS.

- Do not terminate the TLS client-to-service connection to the **rms.aadrm.us** URL (for example, to perform packet-level inspection). 

You can use the following PowerShell commands to help you determine whether your client connection is terminated before it reaches the Azure Rights Management service:
 
    $request = [System.Net.HttpWebRequest]::Create("https://admin.aadrm.us/admin/admin.svc")
    $request.GetResponse()
    $request.ServicePoint.Certificate.Issuer


The result should show that the issuing CA is from a Microsoft CA, for example: `CN=Microsoft Secure Server CA 2011, O=Microsoft Corporation, L=Redmond, S=Washington, C=US`. If you see an issuing CA name that is not from Microsoft, it is likely that your secure client-to-service connection is being terminated and needs to be reconfigured on your firewall.

## Service Tags

Make sure to allow access to all ports for the following **Service Tags**:
*    AzureInformationProtection
*    AzureActiveDirectory
*    AzureFrontDoor.FrontEnd
