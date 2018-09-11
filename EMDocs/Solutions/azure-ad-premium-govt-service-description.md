---
# required metadata

title: Azure Active Directory Premium Government Service Description
description: Azure Active Directory Premium Government plans are monthly subscriptions and are licensed on a per user basis. 
keywords: identity
author: arob98
ms.author: mtillman
manager: mtillman
ms.date: 12/21/2017
ms.topic: get-started-article
ms.prod:
ms.service: active-directory
ms.assetid: 112289b0-0336-4cc0-b471-42fc2c015c64

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: 
#ms.tgt_pltfrm:
ms.custom: 

---

# Azure Active Directory Premium Government Service Description

In response to the unique and evolving requirements of the United States public sector, Microsoft has created Azure Active Directory Premium Government plans (or "Azure Active Directory Premium Government"). This document provides an overview of features that are specific to Azure Active Directory Premium Government. 

## How to use this Service Description

The Azure Active Directory Premium Government Service Description is designed to serve as an overview of our offering and will cover (1) which services and features are included in this offer, (2) how the Government offers differ from our existing commercial offers, and (3) our current compliance commitments. This document defines the unique commitments and differences compared to Azure Active Directory Premium commercial offerings.

## About Azure Active Directory Premium Government Environments

Azure Active Directory Premium Government plans are monthly subscriptions and are licensed on a per user basis. Organizations that use Azure Active Directory Premium Government benefit from the following unique features:

* Your organization’s content is logically segregated from content in Microsoft's commercial Azure Active Directory Premium services.
* Your organization’s content is stored within the United States.
* Access to Microsoft systems containing your content is restricted to screened Microsoft personnel.
* Azure Active Directory Premium Government complies with common certifications and accreditations that are required for US Public Sector customers.

## Customer Eligibility 

Azure Active Directory Premium Government is available to (1) US federal, state, local, tribal, and territorial government entities, and (2) other entities that handle data that is subject to government regulations and requirements and where use of Azure Active Directory Premium Government is appropriate to meet these requirements, subject to validation of eligibility. Validation of eligibility by Microsoft will include confirmation of handling government-regulated or controlled data. Validation may require proof of registration with the U.S. Department of State or sponsorship by a government entity with specific requirements for the handling of data. This offer is limited to customers that have at least 500 seats. Upon renewal of a customer’s contract for Azure Active Directory Premium Government, re-validation of eligibility is required. Entities with questions about eligibility for Azure Active Directory Premium Government should consult their account team.

## Location of Customer Data

Azure Active Directory Premium Government services are provided from datacenters physically located in the United States. All content is stored at rest in datacenters physically located only in the United States.

## Azure Active Directory Premium Government and Third-Party Services

Various Azure Active Directory Premium services provide the ability to work seamlessly with third-party applications and services. These third-party applications and services might involve storing, transmitting, and processing your organization’s customer content on third-party systems that are outside of the Azure Active Directory Premium infrastructure and therefore are not covered by our compliance and data protection commitments. It is recommended that you review the privacy and compliance statements provided by the third parties when assessing the appropriate use of these services for your organization.

## Azure Active Directory Premium Government Offers and Office 365 Interoperability

Office 365 is currently available in both the GCC and GCC High environments. To learn more about these offers, please reference the Office 365 Government [Service Description](https://technet.microsoft.com/library/mt774581.aspx). The Azure Active Directory Premium commercial offering is fully interoperable with Office 365 GCC, and we’re currently targeting FedRAMP-Moderate certification for this offer. The Azure Active Directory Premium GCC High offering is built on the [Microsoft Azure Government Cloud](https://docs.microsoft.com/azure/azure-government/documentation-government-welcome), and is designed to interoperate with the Office 365 GCC High and Office 365 DoD offers. We are targeting FedRAMP-High certification for the Azure Active Directory Premium GCC High offer.

|Azure Active Directory Premium Government Offer|Corresponding Office 365 Government Offer|Compliance Commitment|
|-----------|-----------|-----------|
|Azure Active Directory Premium P1/P2 (commercial)|Office 365 <br/> GCC|FedRAMP-Moderate|
|Azure Active Directory Premium P1/P2 GCC High|Office 365 <br/> GCC High|FedRAMP-High|

> [!NOTE]
> Target date for FedRAMP compliance is Calendar Year 2018

## Parity with Azure Active Directory Premium Commercial Offerings

While our goal is to deliver all commercial features and functionality to government customers with our Azure Active Directory Premium GCC High offer, there is some missing functionality that we’d like to highlight. 

These are the known existing gaps between Azure Active Directory Premium GCC High and our commercial offer as of December 2017: 
* Azure Active Directory B2B.
* Azure Active Directory Gallery with pre-configured apps will not be available.
* MFA FedRAMP Audit is separate from Azure AD FedRAMP Audit and is delayed. At launch, MFA will not have FedRAMP certification in place and customers must opt-in to this service.
* Group Based Licensing. This is currently in preview in the commercial cloud. Once this feature is generally available in commercial cloud, we will work to bring this functionality to Azure Active Directory Premium GCC High.

