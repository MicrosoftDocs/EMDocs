---
# required metadata

title: Enterprise Mobility + Security for US Government Service Description 
description: EMS GCC High plans are monthly subscriptions and are licensed on a per user basis.
keywords:
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 08/30/2019
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.suite: ems


---
# Enterprise Mobility + Security for US Government Service Description
In response to the unique and evolving requirements of the United States public sector, Microsoft has created Enterprise Mobility + Security (EMS) plans for our United States government community customers. This document provides an overview of features that are specific to these EMS plans.

## How to use this Service Description
The EMS for US Government Service Description is designed to serve as an overview of our applicable offerings and will cover: (1) which services and features are included in different offerings, (2) how the US Government offerings differ from our commercial offerings, and (3) our current compliance authorizations.

## EMS offers for US Government and Office 365 Interoperability

|EMS US Government Offers|Location of Hosted Services|Interoperable Office 365 Government Community Cloud (GCC) Offer(s)|
|-----------|-----------|-----------|
|EMS for GCC</br>*Available in both E3 and E5**|Azure Commercial Cloud|Office 365 GCC|
|EMS for GCC High and DOD</br>*Available in E3 and E5**|Azure Government Cloud|Office 365 GCC High</br>Office 365 DOD|

> [!Note]
> *E5 offerings are limited to Azure AD Premium 2 and Azure Information Protection P2 at this time (in addition to Microsoft Intune). Microsoft Cloud App Security and Azure Advanced Threat Protection (ATP) are not currently included in offerings for Office 365 GCC, GCC High, or DOD customers. However, GCC customers can choose to add-on commercial offerings of Microsoft Cloud App Security and Azure ATP with the purchase of an EMS E5 SKU.  

## EMS for US Office 365 GCC Customers
Azure Active Directory P1/P2, Microsoft Intune, and Azure Information Protection P1/P2 are hosted in the Azure commercial environment and are interoperable with the Office 365 GCC platform.  These services are certified FedRAMP-High and meet all the [GCC compliance](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc#us-government-community-compliance) attributes.

GCC customers can choose to add-on commercial offerings of Microsoft Cloud App Security and Azure ATP with the purchase of an EMS E5 SKU.  As described above, Microsoft Cloud App Security and Azure ATP are commercial offerings covered by the Azure Commercial FedRAMP High Authorization to Operate (ATO), but may not meet other [GCC compliance](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc#us-government-community-compliance) attributes, such as CJIS background screening, IRS 1075, and access to customer content by US government screened personnel.  A list of compliance offerings for Microsoft products and services can be found on the [Microsoft Trust Center](https://www.microsoft.com/en-us/trustcenter/compliance/complianceofferings).  

## EMS for US Office 365 GCC High and DOD Customers
The EMS offering for US GCC High and DOD customers is built on the Microsoft [Azure Government](https://docs.microsoft.com/azure/azure-government/documentation-government-welcome) Cloud and is designed to interoperate with the Office 365 GCC High and DOD environment. Azure Active Directory P1/P2, Microsoft Intune, and Azure Information Protection P1/P2 are certified FedRAMP-High for this offering. (We are targeting to add Microsoft Cloud App Security and Azure Advanced Threat Protection to this offer in calendar year 2019, pending FedRAMP-High authorization.)

GCC High customers can use a separate set of endpoints for Intune based on different requirements and management needs. Below is a list of EMS management portals available to US GCC High customers:

- Office 365 Portal: https://portal.office365.us (for user, group, and license management])
- Azure / Intune Admin Portal: https://portal.azure.us
- Intune Web Company Portal: https://portal.manage.microsoft.us

### Parity with Commercial 
While our goal is to deliver all commercial features and functionality to government customers with our US Government offerings, there are some capabilities not yet available in the Azure Government environment that we’d like to highlight.  These are the known existing gaps between EMS in Azure Government (available to GCC High and DOD customers) and our commercial offerings as of June 2019:
- Microsoft Intune:
  - Only supports standalone deployments. It does not support hybrid setup with System Center Configuration Manager.
  - Does not support legacy PC management (with the Intune software agent). Management of Windows 10 is supported via the modern MDM channel.
  - Will not support on-premise Exchange Connector.
  - Co-management support is not available at this time.
  - Windows Autopilot and Business Store features are not available to government customers at this time.
- Azure Information Protection:
  - Visit the [Azure Information Protection Premium](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-aip-premium-govt-service-description) page within the Azure Government documentation site for a list of features that are currently not available in Azure Government.
- Azure Active Directory:
  - Visit the [Azure Active Directory Premium](https://docs.microsoft.com/azure/azure-government/documentation-government-services-securityandidentity#azure-active-directory-premium-p1-and-p2) page of the Azure Government Documentation site for a list of features that are currently not available in Azure Government.

## Customer Eligibility
US Government offers are available to (1) US federal, state, local, and tribal government entities, and (2) other entities that handle data that is subject to government regulations and requirements and where use of services is appropriate to meet these requirements, subject to validation of eligibility. Validation of eligibility by Microsoft will include confirmation of handling government-regulated or controlled data. EMS plans for GCC, GCC High, and DOD customers are monthly subscriptions and are licensed on a per user basis. Entities with questions about eligibility should consult their account team.

## Location of Customer Data
EMS services for US Government customers (GCC, GCC High, and DOD) are provided from data centers physically located in the United States. Your organization’s customer data is stored at rest within the United States. More information can be found on the [Microsoft Trust Center](https://products.office.com/en-us/where-is-your-data-located?ms.officeurl=datamaps&geo=All#office-ContentAreaHeadingTemplate-bkjgypc) page. For information on where Microsoft stores customer data at rest in connection with Microsoft Cloud App Security, a commercial service, please review the [Online Services Terms](https://www.microsoft.com/licensing/product-licensing/products). For information on where Microsoft stores customer data at rest in connection with Azure ATP, also a commercial service, review the [product documentation](https://docs.microsoft.com/azure-advanced-threat-protection/atp-technical-faq#do-i-have-the-flexibility-to-select-where-to-store-my-data) for Azure ATP.

Various EMS services provide the ability to work seamlessly with certain third-party applications and services. These third-party applications and services might involve storing, transmitting, and processing your organization’s data or content on third-party systems that are outside of the EMS infrastructure and therefore are not covered by our compliance and data protection commitments. It is recommended that you review the privacy and compliance statements provided by these third parties when assessing the appropriate use of third-party apps and services for your organization.
