---
# required metadata

title: Enterprise Mobility + Security for US Government Service Description 
description: EMS GCC High plans are monthly subscriptions and are licensed on a per user basis.
keywords:
author: shsagir
ms.author: shsagir
manager: dougeby
ms.date: 01/12/2020
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.suite: ems


---
# Enterprise Mobility + Security for US Government service description
In response to the unique and evolving requirements of the United States public sector, Microsoft has created Enterprise Mobility + Security (EMS) plans for our United States government community customers. This document provides an overview of features that are specific to these EMS plans.

## How to use this service description
The EMS for US Government Service Description is designed to serve as an overview of our applicable offerings and will cover: (1) which services and features are included in different offerings, (2) how the US Government offerings differ from our commercial offerings, and (3) our current compliance authorizations.

## Customer eligibility
US Government offers are available to (1) US federal, state, local, and tribal government entities, and (2) other entities that handle data that is subject to government regulations and requirements and where use of services is appropriate to meet these requirements, subject to validation of eligibility. Validation of eligibility by Microsoft will include confirmation of handling government-regulated or controlled data. EMS plans for GCC, GCC High, and DOD customers are monthly subscriptions and are licensed on a per user basis. Entities with questions about eligibility should consult their account team. 

## EMS offers for US Government and Office 365 interoperability

For more information on each of the products and their plans found in Enterprise Mobility + Security, visit the [documentation resources](https://docs.microsoft.com/enterprise-mobility-security/) and [compare plans and pricing](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/compare-plans-and-pricing).

|EMS US Government Offerings|Location of Hosted Services|Interoperable Office 365 Government Community Cloud (GCC) Offer(s)|
|-----------|-----------|-----------|
|EMS for GCC</br>*Available in both E3 and E5**|Azure Commercial Cloud|Office 365 GCC|
|EMS for GCC High</br>*Available in E3 and E5**|Azure Government Cloud|Office 365 GCC High</br>Office 365 DOD|
|EMS for DOD</br>*Available in both E3 and E5**|Azure Government Cloud|Office 365 DOD|

> [!Note]
> *E5 offerings are limited to Azure AD Premium 2 and Azure Information Protection P2 at this time (in addition to Microsoft Intune) for GCC and DOD customers. Microsoft Cloud App Security and Azure Advanced Threat Protection (Azure ATP) are not currently included in offerings for Office 365 GCC or DoD customers.  However, GCC customers can choose to add-on commercial offerings of Microsoft Cloud App Security and Azure ATP with the purchase of an EMS E5 license.

## EMS for US GCC customers
Azure Active Directory P1/P2, Microsoft Intune, and Azure Information Protection P1/P2 are hosted in the Azure commercial environment and are interoperable with the Office 365 GCC platform.  These services are certified FedRAMP-High and meet all the [GCC compliance](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc#us-government-community-compliance) attributes.

GCC customers can choose to add-on commercial offerings of Microsoft Cloud App Security and Azure ATP with the purchase of an EMS E5 SKU. Microsoft Cloud App Security and Azure ATP are commercial offerings covered by the Azure Commercial FedRAMP High Authorization to Operate (ATO), but may not meet other [GCC compliance](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc#us-government-community-compliance) attributes, such as CJIS background screening, IRS 1075, and access to customer content by US government screened personnel.  A list of compliance offerings for Microsoft products and services can be found on the [Microsoft Trust Center](https://www.microsoft.com/en-us/trustcenter/compliance/complianceofferings).  

## EMS for US GCC High and DoD customers
The EMS offerings for US GCC High and DOD customers are built on the Microsoft [Azure Government](https://docs.microsoft.com/azure/azure-government/documentation-government-welcome) cloud and are designed to inter-operate with the Office 365 GCC High and DOD environments. The EMS E5 suite is available for both GCC High and DoD customers, however Microsoft Cloud App Security and Azure Advanced Threat Protection are available only to GCC High customers. Azure Active Directory P1/P2, Microsoft Intune, Azure Information Protection P1/P2, Microsoft Cloud App Security, and Azure ATP are certified FedRAMP-High.

GCC High and DOD customers can use a separate set of endpoints for Intune based on different requirements and management needs. Below is a list of EMS management portals available to US GCC High and DOD customers. depending on service availability:

- Office 365 Portal: https://portal.office365.us (for user, group, and license management])
- Azure / Intune Admin Portal: https://portal.azure.us
- Intune Web Company Portal: https://portal.manage.microsoft.us
- Microsoft Cloud App Security Portal: https://portal.cloudappsecurity.us  
- Azure Advanced Threat Protection (Azure ATP) Portal: https://portal.atp.azure.us  

### Parity with commercial 
While our goal is to deliver all commercial features and functionality to government customers with our US Government offerings, there are some capabilities not yet available in the Azure Government environment. Known existing gaps between our commercial offerings and EMS offerings available to GCC High and DOD customers as of November 019 are found on the following product pages: 
- Azure Active Directory: 
  - Visit the [Azure Active Directory Premium](https://docs.microsoft.com/azure/azure-government/documentation-government-services-securityandidentity#azure-active-directory-premium-p1-and-p2) page of the Azure Government Documentation site for a list of features that are currently not available in Azure Government. 
- Azure Information Protection: 
  - Visit the [Azure Information Protection Premium](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-aip-premium-govt-service-description) page for a list of features that are currently not available in Azure Government. 
- Microsoft Intune: 
  - Visit the [Microsoft Intune] page (https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-intune-govt-service-description) for a list of features that are currently not available in Azure Government. 
- Azure Advanced Threat Protection:
  - Visit the [Azure ATP](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-azure-atp-govt-service-description) page for a list of features that are currently not available in Azure Government.
- Microsoft Cloud App Security:
  - Visit the [Microsoft Cloud App Security](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-cloud-app-security-govt-service-description) page for a list of features that are currently not available in Azure Government.

## Location of customer data

### US Government GCC customers
EMS services currently available for US Government customers (Azure AD P1/P2, Intune and Azure Information Protection P1/2) are provided from data centers physically located in the United States. Your organization’s customer data is stored at rest within the United States. GCC customers can also choose to add-on commercial offerings of Microsoft Cloud App Security and Azure ATP with the purchase of an EMS E5 license. (These are not US GCC services and do not adhere to all GCC attributes.) For information on where Microsoft stores customer data at rest in connection with Microsoft Cloud App Security, a commercial service, review the [Online Services Terms](https://www.microsoft.com/licensing/product-licensing/products). For information on where Microsoft stores customer data at rest in connection with Azure ATP, also a commercial service, review the [product documentation](https://docs.microsoft.com/azure-advanced-threat-protection/atp-technical-faq#do-i-have-the-flexibility-to-select-where-to-store-my-data) for Azure ATP.

### US Government GCC High and DoD customers
Organizations that use EMS for US Government GCC High and DOD offerings benefit from the following features: 
- Your organization's customer content is physically segregated from customer content in Microsoft's commercial services. 
- Your organization's customer content is stored within the United States. 
- Access to your organization's customer content is restricted to screened Microsoft personnel. 
- Compliance with certifications and accreditations that are required for US Public Sector customers, including Department of Defense Security - 
Requirements Guidelines, Defense Federal Acquisition Regulations Supplement (DFARS), and International Traffic in Arms Regulations (ITAR) 

More information can be found on the [Microsoft Trust Center](https://products.office.com/en-us/where-is-your-data-located?ms.officeurl=datamaps&geo=All#office-ContentAreaHeadingTemplate-bkjgypc) page. 

### Third-party apps and services

Various EMS services provide the ability to work seamlessly with certain third-party applications and services. These third-party applications and services might involve storing, transmitting, and processing your organization’s data or content on third-party systems that are outside of the EMS infrastructure and therefore are not covered by our compliance and data protection commitments. It is recommended that you review the privacy and compliance statements provided by these third parties when assessing the appropriate use of third-party apps and services for your organization.

For more information, see [Microsoft 365 Government](https://docs.microsoft.com/enterprise-mobility-security/). 
