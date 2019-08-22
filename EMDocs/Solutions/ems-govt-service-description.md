---
# required metadata

title: Enterprise Mobility + Security for US Government Service Description 
description: EMS GCC High plans are monthly subscriptions and are licensed on a per user basis.
keywords:
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 08/22/2019
ms.topic: article
ms.prod:
ms.service: ems
ms.suite: ems


---
# Enterprise Mobility + Security for US Government Service Description 
In response to the unique and evolving requirements of the United States public sector, Microsoft has created Enterprise Mobility + Security (EMS) plans for our United States Government customers. This document provides an overview of features that are specific to EMS plans.  

## How to use this Service Description 
The EMS for US Government Service Description is designed to serve as an overview of our offering and will cover (1) which services and features are included in this offer, (2) how the Government offers differ from our commercial offers, and (3) our current compliance commitments. This document defines the unique commitments and differences compared to EMS commercial offerings.  

## EMS offers for US Government and Office 365 Interoperability 

|EMS US Government Offer|Location of Hosted Service |Corresponding Office 365 Government Offer|Compliance Commitment|
|-----------|-----------|-----------|
|EMS for GCC</br>Available in both E3 and E5*|Azure Commercial Cloud|Office 365 GCC|FedRAMP-Moderate|
|EMS for GCC High</br>Available in E3 and E5*|Azure Government Cloud|Office 365 GCC High|FedRAMP-High| 

> [!Note]    
> E5 is limited to Azure AD P2 and Azure Information Protection P2 at this time.  Microsoft Cloud App Security and Azure Advanced Threat Protection are not currently included in the GCC or GCC High offerings.  However, GCC customers can choose to add-on commercial offerings of Microsoft Cloud App Security and Azure ATP offerings (which do not meet the same compliance standards) with the purchase of an EMS E5 SKU.

Office 365 is currently available in both the GCC, GCC High, and DOD environments. To learn more about these offers, please reference the [Office 365 Government Service Description](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government). 

## EMS for GCC

The EMS commercial offering is fully interoperable with Office 365 GCC.  Azure Active Directory P1/P2, Intune, and Azure Information Protection P1/P2 are certified FedRAMP-Moderate for this offer and meet the [GCC criteria](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc).

## EMS for GCC High

The EMS for GCC High offering is built on the Microsoft Azure Government Cloud and is designed to interoperate with the Office 365 GCC High offers. Azure Active Directory P1/P2, Intune, and Azure Information Protection P1/P2 are certified FedRAMP-High for this offer. (We are targeting to add Microsoft Cloud App Security and Azure Advanced Threat Protection to this offer in calendar year 2019, pending FedRAMP-High authorization.)

GCC High customers can use a separate set of endpoints for Intune based on different requirements and management needs.  Below is a list of management portals available to EMS customers:
* Office 365 Portal: [https://portal.office365.us](https://portal.office365.us) (for user, group, and license management])
* Azure / Intune Admin Portal: [https://portal.azure.us](https://portal.azure.us)
* Intune Web Company Portal: [https://portal.manage.microsoft.us](https://portal.manage.microsoft.us)

Organizations that use EMS for GCC High benefit from the following unique features:
* Your organization’s content is physically segregated from content in Microsoft's commercial EMS services.
* Your organization’s content is stored within the United States.
* Access to Microsoft systems containing your content is restricted to screened Microsoft personnel.
* EMS GCC High complies with common certifications and accreditations that are required for US Public Sector customers.

## Customer Eligibility 
EMS Government offers are available to (1) US federal, state, local, and tribal government entities, and (2) other entities that handle data that is subject to government regulations and requirements and where use of EMS  is appropriate to meet these requirements, subject to validation of eligibility. Validation of eligibility by Microsoft will include confirmation of handling government-regulated or controlled data. EMS plans for GCC and GCC High are monthly subscriptions and are licensed on a per user basis. Entities with questions about eligibility for EMS should consult their account team.  

## Location of Customer Data 
EMS for US Government services are provided from datacenters physically located in the United States. All content is stored at rest in datacenters physically located only in the United States.  

Various EMS services provide the ability to work seamlessly with certain third-party applications and services. These third-party applications and services might involve storing, transmitting, and processing your organization’s customer content on third-party systems that are outside of the EMS infrastructure and therefore are not covered by our compliance and data protection commitments. It is recommended that you review the privacy and compliance statements provided by these third parties when assessing the appropriate use of third-party apps and services for your organization.

## Parity with EMS Commercial Offerings 
While our goal is to deliver all commercial features and functionality to government customers with our EMS for US government offers, there are some capabilities not yet available that we’d like to highlight.  
    
These are the known existing gaps between EMS GCC High and our commercial offer as of February 2019:  

- Microsoft Intune:

  - Only supports standalone deployments. It does not support hybrid setup with System Center Configuration Manager.

  - Does not support legacy PC management (with the Intune agent). Management of Windows 10 is supported via the modern MDM channel.

  - Does not support on-premise Exchange Connector.

  - Co-management support is available with Configuration Manager version 1906 and later.

  - Windows Autopilot and Business Store features are not available to government customers at this time, though planning is underway.

  - Some Office 365 mobile apps are not available to government customers.  Details can be found on the [Microsoft 365 roadmap](https://www.microsoft.com/microsoft-365/roadmap).

  - Mobile Threat Detection and Telecom Expense Management partner solutions are not available to government customers at this time.

- Azure Information Protection:

  - Please visit the [Azure Information Protection Premium page](ems-aip-premium-govt-service-description.md) within the Azure Government documentation site for a list of features that are currently not available.

- Azure Active Directory:

  - Please visit the [Azure Active Directory Premium page](/azure/azure-government/documentation-government-services-securityandidentity#azure-active-directory-premium-p1-and-p2) of the Azure Government Documentation site for a list of features that are currently not available in Azure Government.
