---
title: Envisioning the BYOD Infrastructure Solution
ms.custom: na
ms.reviewer: na
ms.service: multiple
ms.suite: na
ms.technology: na 
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0000
author: YuriDio
---
#Envisioning the BYOD infrastructure solution

After clearly defining the BYOD problem you are trying to solve, you can begin to define a solution to the problem and define detailed requirements for the solution.

## Solution definition

To solve the problems previously identified and assist organizations to encourage users to bring their own devices to work and access corporate data with their devices, a company must switch from a device-centric IT approach to a people-centric IT approach. The design considerations in this document can be used when defining your own BYOD infrastructure solution to: 

- Provide users the flexibility to use their own devices to access corporate apps and data.
- Manage devices that are accessing corporate resources when on-premises and from the cloud.
- Enable an IT department to protect corporate data stored on devices by using encryption and rights management to safeguard against unauthorized local access, and remotely wiping corporate data over the Internet when a device is lost or retired, or during an employee’s termination process.
- Provide users a common identity when they are accessing resources when on-premises and from the cloud.
- Enable IT to manage multiple identities and keep information in sync across different environments.
- Enable enterprise authentication services such as multi-factor authentication and single sign-on.
- Provide for information security and compliance activities such as attestation of compliance.

## Solution requirements

Before enabling users to bring their own devices and have access to a company’s resources, the existing infrastructure’s technical capabilities must be revised. The goal of this revision is to understand if the solution requirements for this new model are already in place or if new technologies must be introduced to resolve the problem. You must first define a number of requirements for doing so, as well as the constraints for the environment. Some of the requirements and constraints are defined by the consumers of the capabilities; others are defined by your existing environment, in terms of existing technical capabilities, services, policies, and processes.

Determining the requirements, constraints, and design to allow users to have access to company resources from their managed devices is a key process. Initial requirements, coupled with the constraints of your environment, may drive an initial design that cannot meet all of the initial requirements, necessitating changes to the initial requirements and subsequent design. Multiple iterations through the definition of requirements and the solution design are necessary before finalizing the requirements and the design. Therefore, do not expect that your first run through this document will be your last. You might find that decisions you make early in the process exclude more preferred options made available to you later in the process.

Your answers to the questions in the next sections build a comprehensive list of requirements for enabling users to access company resources from their devices, which can be managed by IT while keeping the data protected. These questions are not vendor specific and can be applied to any BYOD infrastructure solution.

The considerations regarding the BYOD problem domain presented in this guide will be divided into subdomains. Each subdomain will have a collection of components. For each subdomains presented in this guide you have a set of requirements:

- Users and devices requirements
- Data access and protection requirements
- Management requirements
- Apps requirements

