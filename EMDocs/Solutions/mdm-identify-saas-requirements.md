---
# required metadata

title: Identify SaaS requirements
description:
keywords:
author: andredm7
manager: swadhwa
ms.date: 10/3/2016
ms.topic: solution
ms.prod:
ms.service: 
ms.technology:
ms.assetid: 5380e56c-9c48-459e-aea5-95ad90dbb7d1

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: microsoft-intune

---

# Identify SaaS requirements

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

Each SaaS solution will have different requirements, mobile device management features, and levels of integration with on-premises networks and platforms. Many SaaS solutions offer trial tenants or services for you to evaluate their features and functionality, which is an important part of determining which solution actually meets your needs. However, many SaaS solutions may have subtle differences in features and functionality, depending on the platform type.

The majority of SaaS solutions are based on three cloud types:

- Multi-tenant
- Private (dedicated)
- Hybrid

Before making decisions on how you’ll use a SaaS solution to manage your mobile devices, you’ll also need to examine the differences between these types of cloud platform architectures and choose the one that best fits the overall needs of your organization. Individual SaaS solutions have differing levels of support for areas such as customization, feature configuration, integration, and collaborative functionality.

## Cloud types

*Multi-tenant* SaaS solutions are what are typically called “public” cloud infrastructures. This is when the software architecture of the service is in a single instance, but serves multiple tenants or organizations. The solution is designed to provide every tenant a reserved share of its services, such as user or device management, configuration, and data support. The tenant accounts and services are separated virtually, with each tenant accessing the platform infrastructure in separate instances. Multi-tenant SaaS solutions also typically offer cost-savings earned from sharing the infrastructure and distributing the overhead costs amongst multiple tenants. Most mobile device management platforms are offered in a multi-tenant SaaS platform infrastructure.
                
*Private*, or dedicated cloud services are instances of SaaS solutions that are operated for a single organization or tenant. These can either be private cloud services hosted by the organization or private cloud services hosted by a 3rd party provider. Private cloud solutions also typically offer greater opportunities for customization, both in the areas of services and security. Some dedicated SaaS solutions offer mobile device management services as a part of larger private cloud tenant options.

*Hybrid* SaaS solutions can offer a combination of either multi-tenant and private cloud infrastructures, or a combination of hosted (either multi-tenant or private) and on-premises cloud infrastructures. A hybrid infrastructure may also include leveraging an external cloud SaaS solution for delivering certain types of services (such as applications), but leveraging internal resources for other types of services. Most SaaS solutions offer the ability to support a hybrid cloud configuration, but may vary significantly on the depth and completeness of integration with on-premises or other hosted cloud platforms.

### Cloud questions

As part of SaaS management lifecycle planning, you’ll want to answer the following planning questions about cloud types:

- What level of security do I need for mobile device data stored in my SaaS solution?
- How does the SaaS solution address intrusion detection and data loss prevention for mobile devices?
- Does your organization have to comply with any regulatory, certification, or compliance requirements for mobile devices or data stored on mobile devices? If so, do these require a specific level of security, customization, scalability, or resiliency? How is compliance audited and reported?
- Does the SaaS solution need connectivity with other cloud services or platforms that will manage mobile devices? If so, is this connectivity:
 - Pre-configured or standardized?
 - Customizable?
 - Supported by the platforms you need to connect to?
- Do you need to connect your SaaS solution with an existing on-premises device management infrastructure? If so, is this connectivity:
 - Supported by your on-premises device management platform?
 - Supported by the SaaS solution?
 - Supported without the need for additional on-premises physical resources?
- Will your cloud-based services, applications, and processes for mobile devices require different levels of security, customization, scalability, and resiliency?

## Scalability

Ease of scalability is one of the primary reasons for considering or deploying a SaaS solution for managing mobile devices in your organization. By definition, public SaaS solutions typically offer a virtually limitless ability to support any amount of users or mobile devices. Private and hybrid SaaS solutions may be subject to scaling limits, based of available organization resources. Scaling increases or decreases to support greater or lesser number of users or devices usually depends on a specific licensing model or per user/device pricing package for public clouds.

### Scalability questions

As part of SaaS management lifecycle planning, you’ll want to answer the following planning questions about cloud scalability:

- What type of short and long-term plans does your organization have for growth or contraction in mobile device and application support infrastructure?
- How rapidly will your organization need to scale mobile device management support services upward or downward?
- What are the initial number of mobile devices and/or users that need support in the SaaS solution? How likely is this number to change in the next year? The next 3 years? The next 5 years?
- Does the number of mobile devices needing SaaS solution support change on a regular pattern (such as seasonally)? Does it change according to the number of active or inactive organization projects?
- Does SaaS solution performance change depending on the scale of supported mobile device and users? If so, in what areas? (nodes, data, processing, etc.) How is the scaling performance measured, reported, and audited?

## Accessibility

Easy access to the SaaS solution is another key component of the SaaS architecture. Because the SaaS solution is hosted on a cloud-based infrastructure, it’s accessible by administrators, users, and devices from any location that has access to the Internet. Administration of mobile devices is done via a browser. Because many SaaS solution providers operate geographically diverse datacenters, users and devices can access the platform “locally”, often avoiding latency and delays that can be associated with connecting to geographically distant endpoints. Accessibility can also typically be expanded by integrating the SaaS solution with on-premises device management platforms.

### Accessibility questions

As part of SaaS management lifecycle planning, you’ll want to answer the following planning questions about cloud accessibility:

- Are there specific mobile device browser requirements in your organization? If so, does the SaaS solution support the required browser(s)?
- Do mobile device users need any special accessibility requirements for applications or services?
- Does your organization need to access the SaaS infrastructure located in the same geographic as the user devices or your on-premises infrastructure? Are there legal ramifications if mobile device data is stored or moved across international borders?

## Resiliency

Since the SaaS infrastructure is cloud-based and hosted across multiple datacenters, resiliency is typically subject to less instability or outages than traditional on-premises hosted services. Multi-location service hosts offer protection against geographic-based outages and service interruptions by using fail-over infrastructure and processes to replicate data across multiple datacenter nodes. Depending on the SaaS solution, access to the service may or may not remain in the original geographic area during a fail-over.

### Resiliency questions
 
As part of SaaS management lifecycle planning, you’ll want to answer the following planning questions about cloud resiliency:

- In the event of primary SaaS solution fail-over, how will mobile device management services be impacted?
- How will mobile device data stored on the SaaS solution be shared in the cloud-based infrastructure?
- If the primary mobile device SaaS datacenter isn’t available, are the fail-over datacenters in the same geographic region as the primary datacenter? Is it OK for fail-over datacenters to be located outside the international borders from which the mobile devices are operating?
- Does the SaaS solution have a defined service level agreement (SLA) outlining support for mobile device management?


## Up-to-date services

SaaS solutions also are able to keep the applications and services up-to-date with the latest application version, features, security updates, and bug fixes. Often these updates are published very quickly, sometimes even on a daily basis. Depending on the SaaS solution, updates may be instantly available to all customers or released in a phased approach to smaller groups of customers. One of the biggest benefits is that when a bug is fixed for one customer, the fix can be easily applied to all customers using the service.

### Services questions

As part of SaaS management lifecycle planning, you’ll want to answer the following planning questions about cloud services:

- How often are mobile device management features and functionality updated in the SaaS service?
- What impact will feature and functionality updates have on your mission-critical mobile device applications and services?
- Are SaaS solution feature and functionality updates deployed to customers on an ad hoc or planned schedule?
- Does the SaaS solution support exemptions from service-wide updates for individual organizations?
- Does the SaaS solution have different service update schedules for mobile device application and mobile device management features and functionality?

>[!TIP]
>Make sure to take notes of each answer and understand the rationale behind the answer. Later tasks will go over the options available and advantages/disadvantages of each option.  Answering these questions will help you select the option that best suits your business needs.
