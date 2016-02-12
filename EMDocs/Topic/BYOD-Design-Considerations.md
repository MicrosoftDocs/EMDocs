---
title: BYOD Design Considerations
ms.custom: na
ms.reviewer: na
ms.service: multiple
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a6319952-e9cd-4308-b9b9-b2e6005e6506
author: YuriDio
---
# BYOD Design Considerations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>With an understanding of the requirements detailed in <link xlink:href="ecb6271f-8f38-42bd-aae7-10ba5e17a5f1">3 Envisioning the BYOD Infrastructure Solution</link> in this document, you can select appropriate products and technologies to implement the requirements for your BYOD infrastructure design. The following table lists Microsoft products, technologies, and services that can be used to implement a BYOD infrastructure solution.</para>
  </introduction>
  <section>
    <title>In this topic</title>
    <content>
      <list class="bullet">
        <listItem>
          <para>
            <link xlink:href="dcccd316-d550-4db8-bc7e-0b8e66a275a8" />
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="d1653116-3922-40d3-bc4f-3d845b6aaecb" />
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="181eb917-119d-4e56-8ead-1182b1dc5cab" />
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="bf0d4210-5edc-4ad7-bcb5-372099049630" />
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="4b871c74-fec8-45e2-8b45-6ef0e62f7cc6" />
          </para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <content />
    <sections>
      <section>
        <content />
        <sections>
          <section>
            <title>Table 5 Microsoft products, technologies, and services for a BYOD infrastructure solution</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <tbody>
                  <tr>
                    <TD>
                      <para>
                        <legacyBold>Subdomains</legacyBold>
                      </para>
                    </TD>
                    <TD>
                      <para>
                        <legacyBold>Products/technologies/external services</legacyBold>
                      </para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Users and devices</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Windows Server 2012 R2</para>
                        </listItem>
                        <listItem>
                          <para>Windows 8.1</para>
                        </listItem>
                        <listItem>
                          <para>Workplace Join</para>
                        </listItem>
                        <listItem>
                          <para>Device Registration Service</para>
                        </listItem>
                        <listItem>
                          <para>Device Enrollment</para>
                        </listItem>
                        <listItem>
                          <para>Wi-Fi profile</para>
                        </listItem>
                        <listItem>
                          <para>Company Portal</para>
                        </listItem>
                        <listItem>
                          <para>HTTPS protocol</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Data access and protection</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Windows Server 2012 R2</para>
                        </listItem>
                        <listItem>
                          <para>Active Directory Domain Services (AD DS) </para>
                        </listItem>
                        <listItem>
                          <para>Windows Azure Active Directory (Windows Azure AD) </para>
                        </listItem>
                        <listItem>
                          <para>Windows Azure Multi-Factor Authentication</para>
                        </listItem>
                        <listItem>
                          <para>Active Directory Federation Services (AD FS)</para>
                        </listItem>
                        <listItem>
                          <para>Dynamic Access Control</para>
                        </listItem>
                        <listItem>
                          <para>Microsoft Rights Management service</para>
                        </listItem>
                        <listItem>
                          <para>SMB Encryption</para>
                        </listItem>
                        <listItem>
                          <para>Single sign-on</para>
                        </listItem>
                        <listItem>
                          <para>Work Folders</para>
                        </listItem>
                        <listItem>
                          <para>Web Application Proxy </para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Management</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Windows Intune</para>
                        </listItem>
                        <listItem>
                          <para>Device Management Policies</para>
                        </listItem>
                        <listItem>
                          <para>Unified Management Infrastructure</para>
                        </listItem>
                        <listItem>
                          <para>Selective Wipe</para>
                        </listItem>
                        <listItem>
                          <para>Software Distribution</para>
                        </listItem>
                        <listItem>
                          <para>Distribution Point Usage Reports and Management</para>
                        </listItem>
                        <listItem>
                          <para>System Center 2012 R2 Configuration Manager</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Apps</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Web Application Proxy</para>
                        </listItem>
                        <listItem>
                          <para>Automatic Trigger VPN</para>
                        </listItem>
                        <listItem>
                          <para>RemoteApp</para>
                        </listItem>
                        <listItem>
                          <para>Session Shadow</para>
                        </listItem>
                        <listItem>
                          <para>Quick Reconnect</para>
                        </listItem>
                        <listItem>
                          <para>Deduplication Storage</para>
                        </listItem>
                        <listItem>
                          <para>Security Development Lifecycle (SDL)</para>
                        </listItem>
                        <listItem>
                          <para>Active Directory Federations Services (AD FS)</para>
                        </listItem>
                        <listItem>
                          <para>HTTPS protocol</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para>The sections that follow outline the design process, but as mentioned in <link xlink:href="ecb6271f-8f38-42bd-aae7-10ba5e17a5f1">3 Envisioning the BYOD Infrastructure Solution</link> in this document, the design and requirements definition process is iterative until it has been completed.</para>
              <para>The remainder of the document addresses design considerations and the products, technologies, and services listed in the preceding table. When multiple Microsoft products, technologies, and services can be used to address different design considerations, the tradeoffs among them are discussed.</para>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <section>
    <title>See also</title>
    <content>
      <list class="bullet">
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