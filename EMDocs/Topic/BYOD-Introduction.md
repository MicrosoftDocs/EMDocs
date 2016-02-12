---
title: BYOD Introduction
ms.custom: na
ms.reviewer: na
ms.service: multiple
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0da8559b-8371-40c6-aa10-0439aa24e130
author: YuriDio
---
# BYOD Introduction
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>With the proliferation of devices used by employees, most enterprises are facing a big dilemma: how do they allow their users to use their own devices, while protecting corporate data that resides on those devices? Enterprises are moving away from the traditional model, in which they own and provide devices to their employees, to a model in which employees use their personal devices for some of their work tasks. This model is often referred to as <externalLink><linkText>Bring Your Own Device (BYOD)</linkText><linkUri>http://www.microsoft.com/en-gb/business/community/hints-and-tips/byod-can-everyone-bring-toys-to-the-office</linkUri></externalLink>. In this model, employees are allowed to use their personal devices for some work tasks, but only if the employees allow the company to manage some aspects of their devices to ensure the security of corporate data. Often, this means that users allow the company to apply custom policies, perform hardening of the devices, or standardize the operating system established by company policy. Executives and decision makers that read the <externalLink><linkText>CIO considerations for workstyle transformation</linkText><linkUri>http://download.microsoft.com/download/5/3/A/53A96632-02E3-416C-B209-D8725AA80AFE/CIO%20Considerations%20for%20Workstyle%20Transformation2.pdf</linkUri></externalLink> paper from Microsoft can also identify the benefits of embracing a model in which people are empowered to use their devices to be productive at work.</para>
    <para>Though data access and protection is one of the main challenges of BYOD, other challenges require addressing the problem with a broader approach:</para>
    <list class="bullet">
      <listItem>
        <para>Users and their devices: how can users be enabled to use their own devices and remain compliant with company policies?</para>
      </listItem>
      <listItem>
        <para>Management: how will noncorporate devices be managed by IT?</para>
      </listItem>
      <listItem>
        <para>Apps: how will line-of-business (LOB) apps be accessed from users’ devices?</para>
      </listItem>
    </list>
    <para>This discussion will be driven by requirements, capabilities, and design considerations for a device management infrastructure. Microsoft technologies are mentioned within the context of the requirements and capabilities—not vice versa. It is our expectation that this approach will resonate better with architects and designers who are interested in the problems that must be solved and the approaches that are available for solving these problems. Only then is the technology discussion relevant.</para>
  </introduction>
  <section>
    <title>1.1 Document audience</title>
    <content>
      <para>The primary audience for this document is the system architect or system designer who is interested in understanding the issues that need to be considered before implementing a BYOD infrastructure. Others who might be interested in this document include IT implementers, enterprise security specialists, and device management specialists.</para>
    </content>
  </section>
  <section>
    <title>1.2 Document purpose</title>
    <content>
      <para>The purpose of this document is twofold: </para>
      <list class="ordered">
        <listItem>
          <para>To provide the system architect or system designer a collection of issues and questions to be answered. The answers to these questions can serve as the requirements for a BYOD infrastructure design. </para>
        </listItem>
        <listItem>
          <para>To provide the system architect or system designer a collection of design options that can be evaluated and chosen based on identified requirements. </para>
        </listItem>
      </list>
      <para>Though the questions can be used with any vendor, examples of available options will focus on capabilities within Windows Server 2012 R2, System Center 2012 R2, and Windows Intune.</para>
      <para>In addition, this document includes:</para>
      <list class="bullet">
        <listItem>
          <para>Vendor-agnostic design considerations to adapt an infrastructure to enable the BYOD model. </para>
        </listItem>
        <listItem>
          <para>Design considerations for users, devices, management platforms, apps, and data access and protection. </para>
        </listItem>
      </list>
      <para>Before embarking on a BYOD model in a production environment, security, availability, performance, and scalability issues need to be considered in the areas of networking, storage, compute, and identity. There is a tendency to want to embrace BYOD before there is a concrete analysis of the current environment and what needs to be done to securely enable users to work from any device anywhere.</para>
      <para>It is <legacyItalic>not</legacyItalic> the purpose of this document to:</para>
      <list class="bullet">
        <listItem>
          <para>Provide a performance baseline for the infrastructure components of a BYOD model. </para>
        </listItem>
        <listItem>
          <para>Provide performance tuning and best practices for the infrastructure components of BYOD.</para>
        </listItem>
        <listItem>
          <para>Provide app development guidance for mobile devices.</para>
        </listItem>
        <listItem>
          <para>Provide app development best practices for mobile devices.</para>
        </listItem>
        <listItem>
          <para>Provide guidance and best practices for third-party components.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>See also</title>
    <content>
      <list class="bullet">
        <listItem>
          <para>
            <link xlink:href="bc4d8a1d-9b5b-4a26-8620-d5917871e34c" />
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="ecb6271f-8f38-42bd-aae7-10ba5e17a5f1" />
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="a6319952-e9cd-4308-b9b9-b2e6005e6506" />
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="423c1de5-db20-4327-8c3b-a39b830cb58b" />
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="ed940ba8-866c-477f-a59b-beb620300a79" />
          </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>