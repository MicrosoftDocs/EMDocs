---
# required metadata

title: Enterprise Mobility + Security for US Government Service Description 
description: EMS GCC High plans are monthly subscriptions and are licensed on a per user basis.
keywords:
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 09/19/2018
ms.topic: article
ms.prod:
ms.service: ems

ms.suite: ems


---
# Enterprise Mobility + Security for US Government Service Description 
In response to the unique and evolving requirements of the United States public sector, Microsoft has created Enterprise Mobility + Security plans for our United States Government customers. This document provides an overview of features that are specific to EMS plans.  

## How to use this Service Description 
The EMS for US Government Service Description is designed to serve as an overview of our offering and will cover (1) which services and features are included in this offer, (2) how the Government offers differ from our existing commercial offers, and (3) our current compliance commitments. This document defines the unique commitments and differences compared to EMS commercial offerings.  

## EMS offers for US Government and Office 365 Interoperability 
Office 365 is currently available in both the GCC and GCC High environments. To learn more about these offers, please reference the Office 365 Government Service Description. The EMS commercial offering is fully interoperable with Office 365 GCC, and we’re currently targeting FedRAMP-Moderate certification for this offer. 

The EMS GCC High offering is built on the Microsoft Azure Government Cloud, and is designed to interoperate with the Office 365 GCC High and Office 365 DoD offers. We are targeting FedRAMP-High certification for the EMS GCC High offer. (Microsoft Cloud App Security and Azure ATP are not currently in scope for this offer.)

|EMS offer|Corresponding Office 365 Government Offer|Compliance Commitment|
|-----------|-----------|-----------|
|EMS (commercial)</br>Available in both E3 and E5|Office 365 GCC|FedRAMP-Moderate*|
|EMS GCC High</br>Available in both E3 and E5|Office 365 GCC High|FedRAMP-High| 

> [!Note]    
> Target date for FedRAMP compliance is Calendar Year 2018.
> \* This does not include certification for Microsoft Cloud App Security or Azure Information Protection.

## About EMS for US Government 
EMS GCC High plans are monthly subscriptions and are licensed on a per user basis. Organizations that use EMS GCC High benefits from the following unique features:  

- Your organization’s content is physically segregated from content in Microsoft's commercial EMS services. 

- Your organization’s content is stored within the United States. 

- Access to Microsoft systems containing your content is restricted to screened Microsoft personnel. 

- EMS GCC High complies with common certifications and accreditations that are required for US Public Sector customers. 

## Customer Eligibility 
EMS Government offers are available to (1) US federal, state, local, and tribal government entities, and (2) other entities that handle data that is subject to government regulations and requirements and where use of EMS  is appropriate to meet these requirements, subject to validation of eligibility. Validation of eligibility by Microsoft will include confirmation of handling government-regulated or controlled data. This offer is limited to customers that have at least 500 seats. Entities with questions about eligibility for EMS should consult their account team.  

## Location of Customer Data 
EMS GCC High services are provided from datacenters physically located in the United States. All content is stored at rest in datacenters physically located only in the United States.  

## EMS GCC High and Third-Party Services 
Various EMS services provide the ability to work seamlessly with third-party applications and services. These third-party applications and services might involve storing, transmitting, and processing your organization’s customer content on third-party systems that are outside of the EMS infrastructure and therefore are not covered by our compliance and data protection commitments. It is recommended that you review the privacy and compliance statements provided by the third parties when assessing the appropriate use of these services for your organization.  

## Parity with EMS Commercial Offerings 
While our goal is to deliver all commercial features and functionality to government customers with our EMS GCC High offer, there are some capabilities not yet available that we’d like to highlight.  
    
These are the known existing gaps between EMS GCC High and our commercial offer as of September 2018:  

- Azure Active Directory:

  - B2B

  - Azure Active Directory Gallery with pre-configured apps will not be available. 

  - MFA FedRAMP Audit is separate from Azure AD FedRAMP Audit and is delayed. At launch, MFA will not have FedRAMP certification in place and customers must opt in to this service. 

- Microsoft Intune:

  - Only supports standalone deployments. It does not support hybrid setup with SCCM.

  - Does not support legacy PC management (with the Intune agent). Management of Windows 10 is supported via the modern MDM channel.

  - Does not support on-premise Exchange Connector.

  - Windows Autopilot and Business Store features are not available to government customers at this time, though planning is underway.

  - Co-Management support is not available at this time, but this feature will be available to our government customers at a later date.


- Azure Information Protection:

  - Document tracking and revocation will not be available.

  - The classification and labelling add-in will be supported only for Office 365 Pro Plus (version 9126.1001 or higher). Office 2010, Office 2013, and other Office 2016 versions are not supported.

  - Information Rights Management (IRM) will be supported only for Office 365 Pro Plus (version 9126.1001 or higher). Office 2010, Office 2013, and other Office 2016 versions are not supported.

  - Migration from Active Directory Rights Management Services (AD RMS) to Azure Information Protection is not supported.

  - The Azure Information Protection viewer app on iOS and Android are not supported.

  - Sharing of protected documents and emails to users in the commercial cloud is not supported. This includes Office 365 users in the commercial cloud, non-Office 365 users in the commercial cloud, and users with an RMS for Individuals license.

  - Information Rights Management will not be supported with SharePoint Online. IRM-protected sites and libraries will not be available. 

- Group Based Licensing. This is currently in preview in the commercial cloud. Once this feature is generally available in commercial cloud, we will work to bring this functionality to Azure Active Directory Premium GCC High.

- Microsoft Cloud App Security and Azure Advanced Threat Protection are not included in the EMS E5 offering for GCC High at this time.
