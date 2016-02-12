---
title: Introduction
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.assetid: 5e577177-3157-420e-885d-16a8b8f05afd
---
# Introduction
<?xml version="1.0" encoding="UTF-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd" xmlns:xlink="http://www.w3.org/1999/xlink">
    <introduction>
        <para>With all of the different design and configuration options for mobile device management (MDM), it’s difficult to determine which combination will best meet the needs of your organization. This design considerations guide will help you to understand mobile device management design requirements and will detail a series of steps and tasks that you can follow to design a solution that best fits the business and technology needs for your organization. Throughout the steps and tasks, this guide will present the relevant technologies and feature options available to organizations to meet functional and service quality (such as availability, scalability, performance, manageability, and security) level requirements. </para><para>Specifically, the goal of this guide is to help you answer the following questions: </para><list class="bullet"><listItem><para>What questions do I need to answer to drive a MDM-specific design for a technology or problem domain that best meets my requirements?</para></listItem><listItem><para>What is the sequence of activities I should complete to design a MDM solution for the technology or problem domain?</para></listItem><listItem><para>What MDM technology and configuration options are available to help me meet my requirements, and what are the trade-offs between those options so that I can select the best option for my MDM requirements?</para></listItem></list><para><legacyBold>Who is this guide intended for? </legacyBold>Information technology architects and professionals responsible for designing a mobile device management solution for medium or large organizations.
</para><para><legacyBold>How can this guide help you? </legacyBold>You can use this guide to understand how to design a mobile device management solution that is able to manage company-owned devices as well as user-owned devices in different form factors.
</para><para><mediaLinkInline>
<image xlink:href="738eb850-3a70-4c19-979b-970152f88f9f"/>
</mediaLinkInline></para><para><legacyBold>Figure 1 - Example of a hybrid <token>Intune</token> and <token>System Center 2012</token> MDM solution
</legacyBold></para><para>Figure 1 is an example of a hybrid solution, where it’s leveraging cloud services to integrate with on-premises capabilities in order to manage all types of devices, regardless of their location. Although this is a very common scenario, every organization’s MDM design might be different than the example due to each organization’s unique management requirements. 
This guide details a series of steps and tasks that you should follow to assist you in designing a customized MDM solution that meets your organization’s unique requirements. Throughout the following steps and tasks, this guide covers the relevant technologies and feature options available to you to meet the functional and service quality level requirements for MDM.
Though this guide can help you design a MDM solution, it does not discuss specific implementation or operations options for the management solutions. You can find detailed deployment and configuration steps for <externalLink target="_blank"><linkText>Microsoft Intune</linkText><linkUri> https://technet.microsoft.com/library/jj676587.aspx</linkUri></externalLink>, <externalLink target="_blank"><linkText>Mobile Device Management for Office 365</linkText><linkUri>https://technet.microsoft.com/library/ms.o365.cc.devicepolicy.aspx</linkUri></externalLink>, and <externalLink target="_blank"><linkText>Microsoft System Center</linkText><linkUri>https://technet.microsoft.com/library/cc507089.aspx</linkUri></externalLink> in the TechNet Library using the links available in the <link xlink:href="eb38d461-bfb0-407c-a5e6-94fa728a86d6">Next steps and additional resources</link> section located at the end of this guide.
</para><para><legacyBold>Assumptions</legacyBold>: You have some experience with <token>Microsoft Intune</token>, <token>System Center 2012 R2 Configuration Manager</token>, <token>Windows Server 2012 R2</token>, and mobile devices running Android, iOS, and <token>Windows Phone</token>. You may have even deployed one of these solutions in an initial MDM test or limited production environment. In this guide, we assume you are looking for how these solutions can best meet your business needs on their own or in an integrated solution.
</para>
    </introduction>
    <section>
        <title>Design Consideration Overview</title>
        <content>
            <para>This guide covers a set of steps and tasks that you can follow to design a solution that best meets your requirements. The steps are presented in an ordered sequence. However, design considerations you learn in later steps may prompt you to change decisions you made in earlier steps as your design matures or due to conflicting design choices. We’ll alert you to potential design conflicts throughout this guide.
</para><para>You will develop a mobile device management design that best meets your requirements only after iterating through the steps as many times as necessary to incorporate all of the considerations within this guide. 
</para><para><link xlink:href="32ef7e4e-41b6-4e40-b9d9-6d2bfb464a99">Identify your mobile device management requirements</link></para><para><link xlink:href="3cdc1318-50a2-4280-b051-1e009620816e">Plan for mobile device management</link></para><para><link xlink:href="5dffb570-dd1a-4beb-aa1e-7c0b51393704">Plan for securing mobile devices</link></para><para><link xlink:href="ab50bf43-0014-4d55-a52d-12e0428adc12">Plan for Software as a Service mobile device management</link></para>
        </content>
        
    </section>

    <relatedTopics/>
</developerConceptualDocument>
