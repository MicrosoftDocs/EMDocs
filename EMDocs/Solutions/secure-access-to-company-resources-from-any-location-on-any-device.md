---
# required metadata

title: Secure access to company resources from any location on any device
description:
keywords:
author: 
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: de3293c6-8ee1-45dc-9686-6210d37a5bd3

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Secure access to company resources from any location on any device
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <title>How can this guide help <?Comment KC: At some point we should probably move some of this text down to the Scenario, problem statement, and goals section to have this part more lightweight. 2014-06-30T11:50:00Z  Id='0?>you<?CommentEnd Id='0'
    ?>?</title>
    <content />
    <sections>
      <section>
        <title>Who is this guide intended for?</title>
        <content>
          <para>This guide is intended for  traditional IT enterprises that have infrastructure architects, enterprise security specialists, and device management specialists who want to understand which solutions are available for consumerization of IT and Bring Your Own Device (BYOD). The end-to-end solution discussed in this guide is part of the Microsoft Enterprise Mobility vision.</para>
          <para />
        </content>
      </section>
      <section>
        <title />
        <content>
          <para>The current trend of the explosion of devices—company-owned devices, personal devices, and consumers using their devices to access corporate resources on-premises or in the cloud—makes it imperative for IT to help increase user productivity and satisfaction with regard to the usage and identity of devices, and the experience of connecting to corporate resources and applications. At the same time, it brings numerous management and security challenges to IT organizations, which must ensure that enterprise infrastructure and corporate data are protected from malicious intent. These corporations must also make sure that resources can be accessed in compliance with corporate policies, regardless of device type or location.</para>
          <para>Your current infrastructure can be extended by implementing and configuring different technologies from Windows Server 2012 R2 to set up an end-to-end solution to deal with these challenges.</para>
          <para>The following diagram illustrates the problem that this solution guide addresses. It shows users using their personal and corporate devices to access applications and data both from the cloud and on-premises. These applications and resources can be inside or outside the firewall.</para>
          <mediaLink>
            <image xlink:href="22f74ac4-1b6e-4f72-9989-1205eab93acd" />
          </mediaLink>
          <para>
            <br />
          </para>
          <para>
            <legacyBold>In this solution guide:</legacyBold>
          </para>
          <list class="bullet">
            <listItem>
              <para>
                <link xlink:href="de3293c6-8ee1-45dc-9686-6210d37a5bd3#ScenarioBKMK1">Scenario, problem statement, and goals</link>
              </para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="de3293c6-8ee1-45dc-9686-6210d37a5bd3#DesignApproachBKMK2">Recommended design for this solution</link>
              </para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="de3293c6-8ee1-45dc-9686-6210d37a5bd3#ImplementationStepsBKMK3">High-level steps to implement this solution</link>
              </para>
            </listItem>
          </list>
        </content>
      </section>
      <section address="ScenarioBKMK1">
        <title>
          <?Comment CL: Still need an “Organization goals” subsection in this section. 2014-07-03T09:54:00Z  Id='50?>Scenario, problem statement, and goals<?CommentEnd Id='50'
    ?></title>
        <content>
          <para>This section describes the scenario, problem statement, and goals for an example organization.</para>
          <para>
            <embeddedLabel>Scenario</embeddedLabel>
          </para>
          <para>Your organization is a medium-sized banking firm. It employs more than 5,000 people who bring their personal devices (Windows RT and iOS-based devices) to work. Currently, they have no way to access company resources from these devices.</para>
          <para>Your current infrastructure includes an Active Directory forest that has a domain controller with Windows Server 2012 installed. It also includes a Remote Access server and a System Center Configuration Manager through System Center.</para>
          <para>
            <embeddedLabel>Problem <?Comment KC: You’re missing the next section after “Problem statement” called “Organization goals” – later, you can create that section. Maybe some of the text at the top would work there… 2014-01-14T22:45:00Z  Id='77?>statement<?CommentEnd Id='77'
    ?></embeddedLabel>
          </para>
          <para>A recent report issued to your company’s management team by the IT team shows that more users are starting to bring their personal devices to work and need access to company data. The management team understands this trend in the market that leads to more users bringing their own devices and wants to ensure that the company implements a solution that securely embraces this demand. To summarize, your company’s IT team needs to: </para>
          <list class="bullet">
            <listItem>
              <para>Let employees use personal devices as well as company devices to access corporate applications and data. These devices include PCs and mobile devices. </para>
            </listItem>
            <listItem>
              <para>Provide secure access to resources according to each user’s needs and company policies for these devices. The user experience across devices must be seamless.</para>
            </listItem>
            <listItem>
              <para>Identify and manage the devices.</para>
            </listItem>
          </list>
          <para>
            <embeddedLabel>Organization Goals</embeddedLabel>
          </para>
          <para> This guide weaves together a solution for extending your company’s infrastructure to achieve the following: </para>
          <list class="bullet">
            <listItem>
              <para>Simplified registration of personal and corporate devices.</para>
            </listItem>
            <listItem>
              <para>Seamless connection to internal resources when needed.</para>
            </listItem>
            <listItem>
              <para>Consistent access to company resources across devices.</para>
            </listItem>
          </list>
        </content>
      </section>
    </sections>
  </section>
  <section address="DesignApproachBKMK2">
    <title> Recommended design for this solution</title>
    <content>
      <para>To solve its business problem and meet all the previously mentioned goals, your organization needs to implement multiple subscenarios. Each of these subscenarios is represented collectively in the following illustration.</para>
      <?Comment CL: Note that the numbered list that follows this graphic does not mention “users can work from anywhere,” Workplace Join, “can enroll devices for access to the company portal,” desktop virtualization, or “web application proxy.” If these things are covered in the numbered items, shouldn’t they at least be referred to in the numbered items’ headings? 2014-07-03T09:56:00Z  Id='108?>
      <mediaLink>
        <image xlink:href="7917cff1-d96c-40e8-bc59-1f063fd4c1cc" />
        <?CommentEnd Id='108'
    ?>
      </mediaLink>
      <?Comment CL: This list needs an introductory sentence that isn’t the sentence above the graphic and isn’t the graphic itself. 2014-07-03T09:56:00Z  Id='109?>
      <list class="ordered">
        <listItem>
          <para>
            <link xlink:href="de3293c6-8ee1-45dc-9686-6210d37a5bd3#EnableUsersBKMK4">Enable users to register their devices and have a single sign-on experience</link>
          </para>
        </listItem>
        <listItem>
          <para> <link xlink:href="de3293c6-8ee1-45dc-9686-6210d37a5bd3#EnableWorkFromAnywhereBKMK5">Set up seamless access to corporate resources</link> </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="de3293c6-8ee1-45dc-9686-6210d37a5bd3#EnhanceRiskManagementBKM6">Enhance Access Control Risk Management </link> </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="de3293c6-8ee1-45dc-9686-6210d37a5bd3#UDM_BKMK9">Unified Device Management</link>
          </para>
        </listItem>
        <?CommentEnd Id='109'
    ?>
      </list>
    </content>
    <sections>
      <section address="EnableUsersBKMK4">
        <title>Enable users to register their devices and have a single sign-on experience</title>
        <content>
          <para>This part of the solution involves the following important <?Comment CL: This is the only place in this topic we use the word “phases.” In what way are these “phases”? 2014-07-03T09:57:00Z  Id='110?>phases<?CommentEnd Id='110'
    ?>.</para>
          <list class="bullet">
            <listItem>
              <para>IT administrators can set up device registration, which allows the device to be associated with the company’s Active Directory and use this association as a seamless second-factor authentication. Workplace Join is a new feature of Active Directory that allows users to securely register their devices with your company directory. This registration provisions the device with a certificate that can be used to authenticate the device when the user is accessing company resources. By using this association, IT pros can configure custom access policies to require that users are both authenticated and using their Workplace Joined device when accessing company resources.</para>
            </listItem>
            <listItem>
              <para>IT administrators can set up single sign-on (SSO) from devices that are associated with the company’s Active Directory. SSO is the ability for an end user to sign in once when accessing an application provided by their company and not be reprompted for their sign-in information when accessing additional company applications. In Windows Server 2012 R2, the SSO capability is extended to Workplace Joined devices. This will improve the end user experience, while avoiding the risk of having each application store user credentials. This has the additional benefit of limiting the opportunities for password harvesting on personal or company-owned devices.</para>
            </listItem>
          </list>
          <para>The following diagram provides a high-level snapshot of Workplace Join.</para>
          <?Comment CL: Need a space between “Registration” and “Service” at the top of this graphic. 2014-07-03T09:58:00Z  Id='113?>
          <mediaLink>
            <image xlink:href="801357e8-8bf0-45ae-9487-ee49938cd039" />
            <?CommentEnd Id='113'
    ?>
          </mediaLink>
          <para>
            <br />
            <br />Each of these capabilities is detailed in the following table.</para>
          <para />
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Solution Design Element</para>
                </TD>
                <TD>
                  <para>Why is it included in this solution?</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>Workplace Join</para>
                </TD>
                <TD>
                  <para>Workplace Join allows users to securely register their devices with your company directory. This registration provisions the device with a certificate that can be used to authenticate the device when the user is accessing company resources. For more information, see <externalLink><linkText> HYPERLINK "http://technet.microsoft.com/library/dn280945.aspx" Join to Workplace from Any Device for SSO and Seamless Second Factor Authentication Across Company Applications</linkText><linkUri>http://technet.microsoft.com/library/dn280945.aspx</linkUri></externalLink>.</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>
            <br />The server roles and technologies that need to be configured for this capability are listed in the following table.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Solution Design Element</para>
                </TD>
                <TD>
                  <para>Why is it included in this solution?</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>Domain Controller with Windows Server 2012 R2 schema update </embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>The Active Directory Domain Services (AD DS) instance provides an identity directory to authenticate users and devices, and for the enforcement of access policies and centralized configuration policies. For more information about setting up your directory services infrastructure for this solution, see <externalLink><linkText>Upgrade Domain Controllers to Windows Server 2012 R2 and Windows Server 2012</linkText><linkUri>http://technet.microsoft.com/library/hh994618.aspx</linkUri></externalLink>.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>AD FS with Device Registration Service</embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>Active Directory Federation Services (AD FS) lets administrators configure the Device Registration Service (DRS) and implements the Workplace Join protocol for a device to Workplace Join with Active Directory. In addition, AD FS has been enhanced with OAuth authentication protocol as well as device authentication and conditional access control policies that include user, device, and location criteria. For more information about planning your AD FS design infrastructure, see <externalLink><linkText>AD FS Design Guide in Windows Server 2012 R2</linkText><linkUri>http://technet.microsoft.com/library/dn554245.aspx</linkUri></externalLink>.</para>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
      </section>
      <section>
        <title>Design considerations for setting up your domain controller</title>
        <content>
          <para>You do not need a domain controller running Windows Server 2012 R2 for this solution. All you need is a schema update from your current AD DS installation. For more information about extending the schema, see <externalLink><linkText>Install Active Directory Domain Services</linkText><linkUri>http://technet.microsoft.com/library/hh472162.aspx</linkUri></externalLink>. You can update the schema on existing domain controllers without installing a domain controller that runs Windows Server 2012 R2 by <externalLink><linkText>Running Adprep.exe</linkText><linkUri>http://technet.microsoft.com/library/dd464018(v=WS.10).aspx</linkUri></externalLink>.</para>
          <para>For a detailed list of new features, system requirements, and prerequisites that must be met before you begin the installation, see <externalLink><linkText>AD DS installation prerequisite validation</linkText><linkUri>http://technet.microsoft.com/library/hh472161.aspx#BKMK_PrereqCheck</linkUri></externalLink> and <externalLink><linkText>System requirements</linkText><linkUri>http://technet.microsoft.com/library/hh472161.aspx#BKMK_SystemReqs</linkUri></externalLink>.</para>
        </content>
      </section>
      <section>
        <title>Design considerations for AD FS</title>
        <content>
          <para>To plan the AD FS environment, see <externalLink><linkText>Identifying Your AD FS Deployment Goals</linkText><linkUri>http://technet.microsoft.com/library/dd807053.aspx</linkUri></externalLink>.</para>
        </content>
      </section>
      <section address="EnableWorkFromAnywhereBKMK5">
        <title>Set up seamless access to corporate resources</title>
        <content>
          <para>Today's employees are mobile and expect to be able to access the applications they need to get work done wherever they happen to be. Companies have adopted multiple strategies to enable this using VPN, Direct Access, and Remote Desktop Gateways. </para>
          <para>However, in a world of Bring Your Own Device, these approaches don't offer the level of security isolation many customers need. To help meet this need, the Web Application Proxy role service is included in the Windows Server RRAS (Routing and Remote Access Service) role. This role service allows you to selectively publish your enterprise Line-of-Business web apps for access from outside the corporate network.</para>
          <para>Work Folders is a new file sync solution that allows users to sync their files from a corporate file server to their devices. The protocol for this sync is HTTPS based. This makes it easy to publish via the Web Application Proxy. This means that users can now sync from both the intranet and the Internet. It also means the same AD FS–based authentication and authorization controls described previously can be applied to syncing corporate files. The files are then stored in an encrypted location on the device. These files can then be selectively removed when the device is unenrolled for management.</para>
          <para>DirectAccess and Routing and Remote Access Service (RRAS) VPN are combined into a single Remote Access role in Windows Server 2012 R2. This new Remote Access server role allows for centralized administration, configuration, and monitoring of both DirectAccess and VPN-based remote access services.</para>
          <para>Windows Server 2012 R2 provides a Virtual Desktop Infrastructure (VDI) that gives your organization’s IT the freedom to choose personal and pooled virtual (VM)–based desktops, as well as session-based desktops. It also offers IT several storage options, based on their requirements.</para>
          <para>The following diagram illustrates the technologies you can implement to ensure seamless access to corporate resources. </para>
          <mediaLink>
            <image xlink:href="88827db0-e949-4c8e-9384-319e9a9be4b1" />
          </mediaLink>
        </content>
        <sections>
          <section>
            <title>Planning access to corporate resources</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Solution Design Element</para>
                    </TD>
                    <TD>
                      <para>Why is it included in this solution?</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>
                        <embeddedLabel>Web Application Proxy</embeddedLabel>
                      </para>
                    </TD>
                    <TD>
                      <para>Allows the publishing of corporate resources, including Multi-Factor Authentication and the enforcement of conditional access polices when users connect to resources. For more information, see <externalLink><linkText>Web Application Proxy Deployment Guide</linkText><linkUri>http://technet.microsoft.com/library/dn280944.aspx</linkUri></externalLink>. </para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>
                        <embeddedLabel>Work Folders (File Server)</embeddedLabel> </para>
                    </TD>
                    <TD>
                      <para>A centralized location on a file server in the corporate environment that is configured to allow the synchronization of files to user devices. Work Folders can be published directly through a reverse proxy or via the Web Application Proxy for conditional access policy enforcement. For more information, see <externalLink><linkText>Work Folders Overview</linkText><linkUri>http://technet.microsoft.com/library/dn265974.aspx</linkUri></externalLink>.</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>
                        <embeddedLabel>Remote Access</embeddedLabel>
                      </para>
                    </TD>
                    <TD>
                      <para>This new Remote Access server role allows for centralized administration, configuration, and monitoring of both DirectAccess and VPN-based remote access services. Additionally, Windows Server 2012 DirectAccess provides multiple updates and improvements to address deployment blockers and provide simplified management. For more information, see <externalLink><linkText>802.1X Authenticated Wireless Access Overview</linkText><linkUri>http://technet.microsoft.com/library/hh994700.aspx</linkUri></externalLink>.</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>
                        <embeddedLabel>VDI</embeddedLabel>
                      </para>
                    </TD>
                    <TD>
                      <para>VDI enables your organization to deliver a corporate desktop and applications to employees that they can access from their personal and corporate devices, from both internal and external locations with the infrastructure (the Remote Desktop Connection Broker, Remote Desktop Session Host, and Remote Desktop Web Access role services) running within the corporate datacenter. For more information, see <externalLink><linkText>Virtual Desktop Infrastructure</linkText><linkUri>http://www.microsoft.com/server-cloud/products/virtual-desktop-infrastructure/default.aspx</linkUri></externalLink>.</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
            </content>
            <sections>
              <section>
                <title>Design considerations for deploying Web Application Proxy</title>
                <content>
                  <para>This section provides an introduction to the planning steps required to deploy Web Application Proxy and to publish applications through it. This scenario describes the available preauthentication methods, including using AD FS for authentication and authorization, which allows you to benefit from AD FS features, including Workplace Join, Multi-Factor Authentication (MFA), and multi-factor access control. These planning steps are explained in detail in <externalLink><linkText>Plan to Publish Applications through Web Application Proxy</linkText><linkUri>http://technet.microsoft.com/library/dn383660.aspx</linkUri></externalLink>.</para>
                </content>
              </section>
              <section>
                <title>Design considerations for deploying Work Folders</title>
                <content>
                  <para>This section explains the design process for a Work Folders implementation and provides information about the software requirements, deployment scenarios, a design checklist, and additional design considerations. Follow the steps in <externalLink><linkText>Designing a Work Folders Implementation</linkText><linkUri>http://technet.microsoft.com/library/dn479242.aspx</linkUri></externalLink> to create a basic checklist. </para>
                </content>
              </section>
              <section>
                <title>Design considerations for deploying Remote Access Infrastructure</title>
                <content>
                  <para>This section describes general considerations that must be taken during planning to deploy a single Windows Server 2012 Remote Access server with basic features:</para>
                  <list class="ordered">
                    <listItem>
                      <para>
                        <externalLink>
                          <linkText>Plan the DirectAccess Infrastructure</linkText>
                          <linkUri>http://technet.microsoft.com/library/jj574098.aspx</linkUri>
                        </externalLink>: Plan network and server topology, firewall settings, certificate requirements, DNS, and Active Directory.</para>
                    </listItem>
                    <listItem>
                      <para>
                        <externalLink>
                          <linkText>Plan the DirectAccess Deployment</linkText>
                          <linkUri>http://technet.microsoft.com/library/jj574097.aspx</linkUri>
                        </externalLink>: Plan client and server deployment.</para>
                    </listItem>
                  </list>
                </content>
              </section>
            </sections>
          </section>
        </sections>
      </section>
      <section DoNotNumber="false" address="EnhanceRiskManagementBKM6">
        <title>Enhance Access Control Risk Management </title>
        <content>
          <para>With Windows Server 2012 R2, your organization can set up control to access company resources based on the identity of the user, the identity of the registered device, and the user’s network location (whether the user is within the corporate boundary or not). Using multi-factor authentication integrated into the Web Application Proxy, IT can take advantage of additional layers of authentication as users and devices connect to the corporate environment.</para>
          <para>To easily limit the risks associated with compromised user accounts, in Windows Server 2012 R2, it is much simpler to implement multiple factors of authentication using Active Directory. A plug-in model lets you configure different risk management solutions directly into AD FS.</para>
          <para>There are numerous access control risk management enhancements in AD FS in Windows Server 2012 R2, including the following: </para>
          <list class="bullet">
            <listItem>
              <para>Flexible controls based on network location to govern how a user authenticates to access an AD FS–secured application.</para>
            </listItem>
            <listItem>
              <para>Flexible policies to determine if a user needs to perform Multi-Factor Authentication based on the user’s data, device data, and network location.</para>
            </listItem>
            <listItem>
              <para>Per-application controls to ignore SSO and force the user to provide credentials every time they access a sensitive application. </para>
            </listItem>
            <listItem>
              <para>Flexible per-application access policies based on user data, device data, or network location. AD FS Extranet Lockout enables administrators to protect Active Directory accounts from brute-force attacks from the Internet.</para>
            </listItem>
            <listItem>
              <para>Access revocation for any Workplace Joined device that is disabled or deleted in Active Directory.</para>
            </listItem>
          </list>
          <para>The following diagram illustrates the Active Directory enhancements for improving access control risk mitigation.</para>
          <?Comment CL: Should “Office Forms Bases Access” be “Office Forms Based Access”? 2014-07-03T10:04:00Z  Id='148?>
          <mediaLink>
            <image xlink:href="ddfff88e-5143-40f3-99c7-6978afaa6880" />
            <?CommentEnd Id='148'
    ?>
          </mediaLink>
        </content>
        <sections>
          <section DoNotNumber="false">
            <title>Design considerations for implementing risk mitigation and access governance for user, device, and applications</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Solution design element</para>
                    </TD>
                    <TD>
                      <para>Why is it included in this solution?</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Workplace Join (enabled by Device Registration Service [DRS])</para>
                    </TD>
                    <TD>
                      <para>Your organization can implement IT governance with device authentication and second-factor authentication with SSO. Workplace Joined devices provide IT administrators greater levels of control for personal devices and corporate devices. For more information about DRS, see <externalLink><linkText>Join to Workplace from Any Device for SSO and Seamless Second Factor Authentication Across Company Applications</linkText><linkUri>http://technet.microsoft.com/library/dn280945.aspx</linkUri></externalLink>.</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Multi-Factor Authentication</para>
                    </TD>
                    <TD>
                      <para>Through Azure Multi-Factor Authentication, IT can apply additional layers of authentication and verification of users and devices. For more information, see <externalLink><linkText>What is Azure Multi-Factor Authentication?</linkText><linkUri>http://azure.microsoft.com/documentation/articles/multi-factor-authentication/</linkUri></externalLink></para>
                    </TD>
                  </tr>
                </tbody>
              </table>
            </content>
          </section>
        </sections>
      </section>
      <section address="UDM_BKMK9" DoNotNumber="false">
        <title>Unified Device Management</title>
        <content>
          <para>In addition to security and access, IT also needs to have a good strategy in place to manage PCs and personal devices from a single administrator console. Managing devices includes setting security and compliance settings, gathering software and hardware inventory, or deploying software.  IT also must have a solution in place to protect the company by wiping corporate data stored on the mobile device when the device is lost, stolen, or retired from use.</para>
          <para>The solution, <externalLink><linkText>Manage mobile devices and PCs by migrating to Configuration Manager with Windows Intune</linkText><linkUri>http://technet.microsoft.com/library/dn582037.aspx</linkUri></externalLink>, explains in detail the <?Comment CL: Note that the landing page doesn’t mention even once “Unified Device Management.” 2014-07-03T10:05:00Z  Id='158?>Unified Device Management <?CommentEnd Id='158'
    ?>solution. </para>
        </content>
        <sections>
          <section>
            <title>Design considerations for unified device management</title>
            <content>
              <para>It is critical that you address important design questions before designing a Bring Your Own Device (BYOD) and Unified Device Management infrastructure that enables employees to use their own devices and protects the company’s data.</para>
              <para>The infrastructure design to support BYOD is discussed in <externalLink><linkText>BYOD user and device considerations</linkText><linkUri>http://technet.microsoft.com/library/dn656901.aspx</linkUri></externalLink>. The design that is discussed in this document uses Microsoft-based technology. However, the design options and considerations can be applied to any infrastructure used to embrace the BYOD model.</para>
              <para>For a handy checklist that lists the steps required to support mobile device management, see <externalLink><linkText>Checklist for Mobile Device Management</linkText><linkUri>http://technet.microsoft.com/en-us/library/bb694052.aspx</linkUri></externalLink>.</para>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <section address="ImplementationStepsBKMK3">
    <title>What are the steps to implement this <?Comment KC: I have some ideas for continuing to streamline the Design/Plan section and this Implementing one. We can talk about later. 2014-01-14T22:57:00Z  Id='160?>solution<?CommentEnd Id='160'
    ?>?</title>
    <content />
    <sections>
      <section>
        <title>Set up the core infrastructure to enable device registration</title>
        <content>
          <para>The following steps take you through the step-by-step process of setting up the domain controller (AD DS), AD FS, and Device Registration Service.</para>
          <list class="ordered">
            <listItem>
              <para>
                <embeddedLabel>Set up your domain controller</embeddedLabel>
              </para>
              <para>Install the AD DS role service and promote your computer to be a domain controller in Windows Server 2012 R2. This will upgrade your AD DS schema as part of the domain controller installation. For more information and step-by-step instructions, see <externalLink><linkText>Install Active Directory Domain Services</linkText><linkUri>http://technet.microsoft.com/library/hh472162.aspx</linkUri></externalLink>. </para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Install and configure the <?Comment CL: Correct casing perhttp://winedit/html/96d404aa-5594-44b9-bde3-2a2b12cfed9b.htm. 2014-01-15T15:49:00Z  Id='167?>federation server<?CommentEnd Id='167'
    ?></embeddedLabel>
              </para>
              <para>You can use Active Directory Federation Services (AD FS) with Windows Server 2012 R2 to build a federated identity management solution that extends distributed identification, authentication, and authorization services to web-based applications across organization and platform boundaries. By deploying AD FS, you can extend your organization’s existing identity management capabilities to the Internet. For more information and step-by-step instructions, see <externalLink><linkText>Windows Server 2012 R2 AD FS Deployment Guide</linkText><linkUri>http://technet.microsoft.com/library/dn486820.aspx</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Configure Domain Registration Service</embeddedLabel>
              </para>
              <para>You can enable DRS on your federation server after you install AD FS. Configuring DRS involves preparing your Active Directory forest to support devices and then enabling DRS. For detailed instructions, see <externalLink><linkText>Configure a federation server with Device Registration Service</linkText><linkUri>http://technet.microsoft.com/library/dn486831.aspx</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Set up a web server and a sample claims–based application to verify and test the AD FS and Device Registration configuration</embeddedLabel>
              </para>
              <para>You need to set up a web server and a sample claims application, and then follow certain procedures to verify the above steps. Perform the steps in the following order: </para>
              <list class="ordered">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Install the Web Server role and the Windows Identity Foundation</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn280939.aspx#BKMK_15</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Install the Windows Identity Foundation SDK</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn280939.aspx#BKMK_13</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Configure the simple claims app in IIS</linkText>
                      <linkUri>http://technet.microsoft.com/en-us/library/dn280939.aspx#BKMK_9</linkUri>
                    </externalLink> </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Create a relying party trust on your federation server</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn280939.aspx#BKMK_11</linkUri>
                    </externalLink>
                  </para>
                </listItem>
              </list>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Configure and verify Workplace Join on Windows and iOS devices</embeddedLabel>
              </para>
              <para>This section provides instructions for setting up Workplace Join on a Windows device, an iOS device, and experience SSO to a company resource.</para>
              <list class="ordered">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Workplace Join with a Windows Device</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn280938.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Workplace Join with an iOS Device</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn280933.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
              </list>
            </listItem>
          </list>
        </content>
      </section>
      <section>
        <title>Configure access to corporate resources</title>
        <content>
          <para>You need to configure File Services Work folders, Remote Desktop Services Virtualization, and Remote Access. </para>
          <list class="ordered">
            <listItem>
              <para>
                <embeddedLabel>Configure Web Application Proxy</embeddedLabel>
              </para>
              <para>This section provides an introduction to the configuration steps required in order to deploy Web Application Proxy and publish applications through it.</para>
              <list class="ordered">
                <listItem>
                  <para> <externalLink><linkText>Configure the Web Application Proxy Infrastructure</linkText><linkUri>http://technet.microsoft.com/library/dn383644.aspx</linkUri></externalLink>: Describes how to configure the infrastructure required to deploy Web Application Proxy.</para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Install and Configure the Web Application Proxy Server</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn383662.aspx</linkUri>
                    </externalLink>: Describes how to configure Web Application Proxy servers, including configuring any required certificates, installing the Web Application Proxy role service, and joining Web Application Proxy servers to a domain.</para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Publish Applications using AD FS Preauthentication</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn383640.aspx</linkUri>
                    </externalLink>: Describes how to publish applications through Web Application Proxy using AD FS preauthentication.</para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Publish Applications using Pass-through Preauthentication</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn383639.aspx</linkUri>
                    </externalLink>: Describes how to publish applications using pass-through preauthentication.</para>
                </listItem>
              </list>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Configure Work Folders</embeddedLabel>
              </para>
              <para>The simplest Work Folders deployment is a single file server (often called a sync server) without support for syncing over the Internet, which can be a useful deployment for a test lab or as a sync solution for domain-joined client computers. To create a simple deployment, these are the minimum steps to follow:</para>
              <list class="ordered">
                <listItem>
                  <para> <externalLink><linkText>Install Work Folders on file servers</linkText><linkUri>http://technet.microsoft.com/library/dn528861.aspx#step3</linkUri></externalLink></para>
                </listItem>
                <listItem>
                  <para> <externalLink><linkText>Create security groups for Work Folders</linkText><linkUri>http://technet.microsoft.com/library/dn528861.aspx#step5</linkUri></externalLink></para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Create sync shares for user data</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn528861.aspx#step6</linkUri>
                    </externalLink>
                  </para>
                </listItem>
              </list>
              <para>For additional detailed instructions about how to deploy work folders, see <externalLink><linkText>Deploying Work Folders</linkText><linkUri>http://technet.microsoft.com/library/dn528861.aspx</linkUri></externalLink>. </para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Configure and verify Remote Desktop Services Session Virtualization</embeddedLabel>
              </para>
              <para>A VDI standard deployment enables you to install the appropriate role services on separate computers. A standard deployment provides more precise control of virtual desktops and virtual desktop collections by not creating them automatically. </para>
              <para>This test lab walks you through the process of creating a Session Virtualization standard deployment by doing the following:</para>
              <list class="bullet">
                <listItem>
                  <para>Installing the RD Connection Broker, RD Session Host, and RD Web Access role services on separate computers.</para>
                </listItem>
                <listItem>
                  <para>Creating a session collection.</para>
                </listItem>
                <listItem>
                  <para>Publishing a session-based desktop for each RD Session Host server in the collection.</para>
                </listItem>
                <listItem>
                  <para>Publishing applications as RemoteApp programs.</para>
                </listItem>
              </list>
              <para>For detailed steps to configure and verify a VDI deployment, see <externalLink><linkText>Remote Desktop Services Session Virtualization Standard Deployment</linkText><linkUri>http://technet.microsoft.com/en-us/library/hh831610.aspx</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Configure Remote Access</embeddedLabel>
              </para>
              <para>Windows Server 2012 combines DirectAccess and Routing and Remote Access Service (RRAS) VPN into a single Remote Access role. The following are the configuration steps required to deploy a single Windows Server 2012 Remote Access server with basic settings.</para>
              <list class="ordered">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Configure the DirectAccess Infrastructure</linkText>
                      <linkUri>http://technet.microsoft.com/library/hh831743.aspx</linkUri>
                    </externalLink>: This step includes configuring network and server settings, DNS settings, and Active Directory settings.</para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Configure the DirectAccess Server</linkText>
                      <linkUri>http://technet.microsoft.com/library/hh831633.aspx</linkUri>
                    </externalLink>: This step includes configuring DirectAccess client computers and server settings.</para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Verify the Deployment</linkText>
                      <linkUri>http://technet.microsoft.com/library/hh831735.aspx</linkUri>
                    </externalLink>: This step includes steps for verifying the deployment.</para>
                </listItem>
              </list>
            </listItem>
          </list>
        </content>
      </section>
      <section>
        <title>Configure risk management by setting up Multifactor Access Control and Multi-Factor Authentication</title>
        <content>
          <para>Set up flexible and expressive per-application authorization policies, whereby you can permit or deny access based on user, device, network location, and authentication state by configuring Multifactor Access Control. Set up additional risk management in your environment with Multi-Factor Authentication. </para>
          <list class="ordered">
            <listItem>
              <para>
                <embeddedLabel>Configure and verify Multifactor Access Control</embeddedLabel>
              </para>
              <para>This involves the following three steps:</para>
              <list class="ordered">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Verify the default AD FS access control mechanism</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn280936.aspx#BKMK_2</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Configure multi-factor access control policy based on user data</linkText>
                      <linkUri>http://technet.microsoft.com/en-us/library/dn280936.aspx#BKMK_3</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Verify multi-factor access control mechanism</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn280936.aspx#BKMK_4</linkUri>
                    </externalLink>
                  </para>
                </listItem>
              </list>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Configure and verify Multi-Factor Authentication</embeddedLabel>
              </para>
              <para>This involves the following three steps:</para>
              <list class="ordered">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Verify the default AD FS authentication mechanism</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn280946.aspx#BKMK_2</linkUri>
                    </externalLink> </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Configure MFA on your federation server</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn280946.aspx#BKMK_3</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Verify MFA mechanism</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn280946.aspx#BKMK_4</linkUri>
                    </externalLink>
                  </para>
                </listItem>
              </list>
            </listItem>
          </list>
        </content>
      </section>
    </sections>
  </section>
  <section DoNotNumber="false">
    <title>Implement unified device management</title>
    <content>
      <para>Follow the following steps in order to set up device management in your enterprise. </para>
      <list class="ordered">
        <listItem>
          <para>
            <embeddedLabel>Install the System Center 2012 R2 Configuration Manager console</embeddedLabel>: By default, when you install a primary site, the Configuration Manager console also is installed on the primary site server computer. After the site installs, you can install additional System Center 2012 R2 Configuration Manager consoles on additional computers to manage the site. Installing a console from both Configuration Manager 2007 and System Center 2012 R2 Configuration Manager on the same computer is supported. This side-by-side installation allows you to use a single computer to manage both your existing Configuration Manager 2007 infrastructure and the mobile devices you manage using Windows Intune with System Center 2012 R2 Configuration Manager. However, you cannot use the management console from System Center 2012 R2 Configuration Manager to manage your Configuration Manager 2007 site, and vice versa. For more information, see <externalLink><linkText>Install a Configuration Manager Console</linkText><linkUri>http://technet.microsoft.com/library/b22fa03d-ad29-4a72-99d9-4c31bfa53f0f#BKMK_InstallConsole</linkUri></externalLink>.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Enroll mobile devices</embeddedLabel>: Enrollment establishes a relationship between the user, the device, and the Windows Intune service. Users enroll their own mobile devices.  For information about how to enroll mobile devices, see <externalLink><linkText>Mobile Device Enrollment</linkText><linkUri>http://technet.microsoft.com/library/2c6bd0e5-d436-41c8-bf38-30152d76be10#bkmk_enroll</linkUri></externalLink>.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Manage mobile devices</embeddedLabel>: After you install and make the basic configurations for your stand-alone primary site, you can begin to configure management of mobile devices. The following are typical actions you might configure: </para>
          <list class="ordered">
            <listItem>
              <para>To apply compliance setting to mobile devices, see <externalLink><linkText>Compliance Settings for Mobile Devices in Configuration Manager<?Comment CL: This link label does not match the landing page’s title at all. Do we have the wrong URL? 2014-07-03T10:09:00Z  Id='219?></linkText><linkUri>http://technet.microsoft.com/library/dn376523.aspx</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>To create and deploy applications to mobile devices, see <externalLink><linkText>How to Create and Deploy Applications for Mobile Devices in Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/dn469410.aspx</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>To configure hardware inventory, see <externalLink><linkText>How to Configure Hardware Inventory for Mobile Devices Enrolled by Windows Intune and Configuration Manager</linkText><linkUri>http://technet.microsoft.com/en-us/library/dn469411.aspx</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>To configure software inventory, see <externalLink><linkText>Introduction to Software Inventory in Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/gg682049.aspx</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>To wipe content from mobile devices, see <externalLink><linkText>How to Manage Mobile Devices by Using Configuration Manager and Windows Intune<?Comment CL: This link label doesn’t match the landing page’s title whatsoever. Is this link pointing to the wrong place? 2014-07-03T10:10:00Z  Id='230?></linkText><linkUri>http://technet.microsoft.com/library/2c6bd0e5-d436-41c8-bf38-30152d76be10</linkUri></externalLink>.</para>
            </listItem>
          </list>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>See Also</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Content type</para>
            </TD>
            <TD>
              <para>References</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Product evaluation/Getting started</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Join to Workplace from Any Device for SSO and Seamless Second Factor Authentication Across Company Applications</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn280945.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>TechNet Virtual Lab: Windows Server 2012 R2: Implementing Workplace Join</linkText>
                      <linkUri>https://vlabs.holsystems.com/vlabs/technet?eng=VLabs&amp;auth=none&amp;src=microsoft.holsystems.com&amp;altadd=true&amp;labid=10874</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Work Folders Overview</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn265974.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Web Application Proxy Deployment Guide</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn280944.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>802.1X Authenticated Wireless Access Overview</linkText>
                      <linkUri>http://technet.microsoft.com/library/hh994700.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Virtual Desktop Infrastructure</linkText>
                      <linkUri>http://www.microsoft.com/server-cloud/products/virtual-desktop-infrastructure/default.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Planning and design</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Plan to Publish Applications through Web Application Proxy</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn383660.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Designing a Work Folders Implementation</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn479242.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Plan the DirectAccess Infrastructure</linkText>
                      <linkUri>http://technet.microsoft.com/library/jj574098.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Community resources</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Active Directory Team Blog</linkText>
                      <linkUri>http://blogs.technet.com/b/ad/archive/2013/07/10/extending-device-support-in-active-directory.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Active Directory IT controls to manage risk when users access company resources from a wide variety of devices</linkText>
                      <linkUri>http://blogs.technet.com/b/ad/archive/2013/07/25/active-directory-it-controls-to-manage-risk-when-users-access-company-resources-from-a-wide-variety-of-devices.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Introducing Work Folders on Windows Server 2012 R2 - File Cabinet Blog</linkText>
                      <linkUri>http://blogs.technet.com/b/filecab/archive/2013/07/09/introducing-work-folders-on-windows-server-2012-r2.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Related solutions</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Manage mobile devices and PCs by migration to Configuration Manager with Windows Intune</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn582037.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <link xlink:href="a480f7a7-0904-4212-a09a-1381db57ef94">Manage identities for hybrid environments using DirSync with Password Sync</link>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <link xlink:href="d71ba67e-3862-48c1-b522-7667416dae1c">Manage identities for hybrid environments using DirSync with Federation (Single Sign-On)</link>
                  </para>
                </listItem>
              </list>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>
