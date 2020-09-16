---
# required metadata

title: Microsoft Cloud App Security Government Service Description
description: Microsoft Cloud App Security Government Service Description is designed to serve as an overview of our offering
keywords:
author: shsagir
ms.author: shsagir
manager: rkarlin
ms.date: 09/14/2020
ms.topic: article
ms.prod:
ms.service: cloud-app-security
ms.suite: ems


---
# Microsoft Cloud App Security Government service description

## How to use this service description

The Microsoft Cloud App Security US Government service description is designed to serve as an overview of the service offering in the GCC High environment and will cover feature variations from the commercial offering.

To learn more about Microsoft Cloud App Security for GCC customers, see [EMS for US Microsoft 365 GCC customers](./ems-govt-service-description.md#ems-for-us-office-365-gcc-customers).

## Getting started with Microsoft Cloud App Security for US Government GCC High

The Microsoft Cloud App Security GCC High offering is built on the Microsoft Azure Government Cloud and is designed to inter-operate with Microsoft 365 GCC High. Full details on the service and how to use it can be found in the [Microsoft Cloud App Security public documentation](/cloud-app-security/). The public documentation should be used as a starting point for deploying and operating the service and the following Service Description details and changes from functionality or features in the GCC High environment.

To get started, utilize the [Basic Setup](/cloud-app-security/general-setup) page for access to the Microsoft Cloud App Security GCC High portal, and ensure your [Network requirements](/cloud-app-security/network-requirements) are configured. Follow the additional steps in the How-to guides for other detailed instructions.

## Feature variations in Microsoft Cloud App Security GCC High

Unless otherwise specified, new feature releases, including preview features, documented in [What's new with Microsoft Cloud App Security](/cloud-app-security/release-notes), will be available in GCC High within three months of release in the Microsoft Cloud App Security commercial environment, unless otherwise noted.

## API connector

API connectors for AWS GovCloud and other API connected applications that may also offer separate government cloud instances are not supported at this time. API connectors for commercial cloud instances of third-party applications are supported.

The Azure connector and Microsoft 365 connector are for the US Government instances of each service.

## Data Loss Prevention (DLP) features

Content inspection via the Microsoft Cloud App Security built-in DLP engine is available and supports inspection of sensitive data such as credit card, or social security numbers, amongst many other sensitive data types. Learn more about [built-in content inspection](/cloud-app-security/content-inspection-built-in) in Cloud App Security.

**The following DLP integrations are not supported:**

- Microsoft Information Protection labels, which provide unified labeling across Microsoft 365 and Azure Information Protection.

## Conditional Access app control

Microsoft Cloud App Security Conditional Access App Control, which enables organizations to monitor and control user sessions in real time, using the Microsoft Cloud App Security reverse proxy capabilities, is not available.
Activity, file, and anomaly detection policies are still supported for API-connected applications. Learn more about [controlling cloud apps with policies in Microsoft Cloud App Security](/cloud-app-security/control-cloud-apps-with-policies) for additional information.

## Notifications and automation

Admin email notifications for alerts, as well as notifications sent to users when a breach is detected, are not supported at this time.

## Azure Sentinel integration

The integration between Microsoft Cloud App Security and Azure Sentinel is not supported at this time.

## Other integrations

The following integrations are not available:

- Microsoft Defender Advanced Threat Protection
- Surfacing Microsoft Cloud App Security controls in Microsoft Secure Score

## Next steps

To learn more about Cloud App Security and explore how to get started see, [Cloud App Security public documentation](/cloud-app-security/).