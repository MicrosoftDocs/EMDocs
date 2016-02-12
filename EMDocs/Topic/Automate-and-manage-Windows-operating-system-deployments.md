---
title: Automate and manage Windows operating system deployments
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 87b2210a-fb5b-4aff-a70b-ddbb44ee5d0e
author: Jeffgilb
---
# Automate and manage Windows operating system deployments
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>
      <embeddedLabel>
        <?Comment JJG: This is being tracked in TFS throughAnswer 4668:Automate and manage enterprise client operating system deployments 2014-10-07T12:21:00Z  Id='0?>How can this guide help you?<?CommentEnd Id='0'
    ?></embeddedLabel> As a <?Comment JJG: http://sharepoint/sites/samstudios/Research/IT-User-Model/Pages/Computer%20and%20Mobile%20Device%20Administrators.aspx#commonpainpoints 2014-10-07T12:21:00Z  Id='1?>computer and mobile device administrator <?CommentEnd Id='1'
    ?>and enterprise IT Professional, you can use this solution guide to understand the Microsoft recommended processes for creating and deploying Windows operating systems. </para>
    <para>
      <embeddedLabel>In this solution guide:</embeddedLabel>
    </para>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="#BKMK_Scenario">Scenario, problem statement, and goals.</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="#BKMK_RecommendedDesign">What is the recommended design for this solution?</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="#BKMK_WhyThisDesign">Why we are recommending this design.</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="#BKMK_ImplementationSteps">What are the steps to implement this solution?</link>
        </para>
      </listItem>
    </list>
    <para>The following diagram illustrates the problem that this solution guide is addressing.</para>
    <para>Common problems facing desktop administrators when deploying enterprise operating systems:</para>
    <mediaLink>
      <?Comment JJG: (from Aaron)I think it would be good to also add something about software updates. It could be its own row with icons, or just extend the last one to also include software updates, as that one is basically saying the same thing for apps – don’t reinvent the wheel. If you’re already managing apps and/or updates for operational systems, integrate that into the same OS build and deployment process. 2014-10-07T12:21:00Z  Id='2?>
      <image xlink:href="b1c4dee7-3356-489f-8fca-55f6823505a4"/>
      <?CommentEnd Id='2'
    ?>
    </mediaLink>
    <para/>
  </introduction>
  <section address="BKMK_Scenario">
    <title>Scenario, problem statement, and goals</title>
    <content>
      <para>This section describes the current problem and goals that you might have. Review the solution and then check whether it meets your needs or whether you need to adjust it for your business environment.</para>
    </content>
    <sections>
      <sectionSimple>
        <para>
          <embeddedLabel>
            <?Comment JJG: More like a problem statement than a scenario.What is the current environment, what software are they using to doosd, AD, how manymachine’ish. Software expertise and skill set needed to complete this stuff (already know CM and have experience with some OSD deployment tools) and some other things as well.If you are new to the problem space or a new thing you’re just thrown into you are stuck.These kinds of people with these kinds of skills with this software and these types of skills already in place. What has to be in place, deployed and working correctly to even get to this. 2014-10-07T12:21:00Z  Id='3?>Scenario<?CommentEnd Id='3'
    ?></embeddedLabel>
        </para>
        <para>The computing infrastructure for many large enterprise organizations is built around Microsoft technologies including Windows Server and the network services necessary to support daily operations such as AD DS, DHCP, and WDS. In addition, many enterprise IT Professionals are already familiar with System Center Configuration Manager and use it to support computer and device management requirements. However, in many cases, those administrators are not familiar with Microsoft best practices recommendations or the operating system deployment tools and capabilities available to them. Instead, they typically use manual methods that include combinations of answer files, scripts, the Windows Automated Installation Kit (Windows AIK), and so on to perform operating system deployments. Because of this, operating system deployment projects can be extremely challenging and costly to implement.</para>
        <para/>
      </sectionSimple>
      <sectionSimple>
        <para>
          <embeddedLabel>Problem statement</embeddedLabel>
        </para>
        <para>The overall problem to solve is:</para>
        <para>
          <embeddedLabel>Enterprise Windows operating system deployments are complicated, costly, and it is difficult to ensure consistent results. </embeddedLabel> </para>
        <para>Without following Microsoft best practices and using the recommended tools and technologies, operating system deployment projects do not scale well, and are inefficient and expensive. Even if great care is taken to manually document the steps necessary for each step in the deployment, things can and will eventually go wrong when deploying operating systems in this manner. Without automating operating system image creation and deployment testing, computer and mobile device  administrators face the following challenges: </para>
        <list class="bullet">
          <listItem>
            <para>Downloading and maintaining operating system, drivers, and application files necessary to perform operating system deployments on all enterprise hardware.</para>
          </listItem>
          <listItem>
            <para>Creating bootable images and painstakingly installing standard, desktop applications one at a time after operating system deployment has completed.</para>
          </listItem>
          <listItem>
            <para>Manually deploying operating systems in production environments with very little testing.</para>
          </listItem>
          <listItem>
            <para>Manually supporting ongoing configuration changes and other changing operating system deployment requirements. </para>
          </listItem>
          <listItem>
            <para>Consistently performing operating system deployments using repeatable and reliable processes.</para>
          </listItem>
          <listItem>
            <para>Accurately reporting on operating system deployment progress and issues.</para>
          </listItem>
        </list>
      </sectionSimple>
      <sectionSimple>
        <para>
          <embeddedLabel>
            <?Comment JJG: Make sure that each goal has a 1:1 or 1:many relationship between the problem and the goal. 2014-10-07T12:21:00Z  Id='4?>Organizational g<?Comment JJG: These should address the problem statement issues. 2014-10-07T12:21:00Z  Id='5?>oals<?CommentEnd Id='5'
    ?><?CommentEnd Id='4'
    ?></embeddedLabel>
        </para>
        <para>Based on the scenario and problem statement, a solution for automating and managing Windows operating system deployment that meets the following goals is needed:</para>
        <list class="bullet">
          <listItem>
            <para>Manage operating system, driver, and application files in a centralized file system.</para>
          </listItem>
          <listItem>
            <para>Easily create or update Windows operating system images and then properly test them before beginning production deployments.</para>
          </listItem>
          <listItem>
            <para>Rapidly deploy operating systems, desktop software, and Windows updates to new hardware using reliable and consistent processes.</para>
          </listItem>
          <listItem>
            <para>Utilize enterprise-level operating system deployment management and reporting software.</para>
          </listItem>
        </list>
      </sectionSimple>
    </sections>
  </section>
  <section address="BKMK_RecommendedDesign">
    <title>What is the recommended design for this solution?</title>
    <content address="d846090a-9cf5-4915-b255-799c0b038f60">
      <para>
        <?Comment JJG: Need to find a good definition of LTI and ZTI to link these to. 2014-10-07T12:21:00Z  Id='6?>The following diagram illustrates how you Use Microsoft Deployment Toolkit (MDT) lite touch installation (LTI) to automate operating system image creation and testing and then use Configuration Manager zero touch installation (ZTI) to manage and report on enterprise client operating system deployments. Following this recommended approach, you can meet the previously stated goals and solve this business problem in your environment. <?CommentEnd Id='6'
    ?></para>
      <alert class="note">
        <para>Although the principles and recommendations  in this solution can be applied to previous versions, unless otherwise stated MDT refers to MDT 2013 and Configuration Manager refers to Microsoft System Center 2012 Configuration Manager R2.</para>
      </alert>
      <para>Automate and manage enterprise client operating system deployments solution design:</para>
      <mediaLink>
        <image xlink:href="d846090a-9cf5-4915-b255-799c0b038f60"/>
      </mediaLink>
      <para/>
      <para>The following table lists the elements that are part of this solution design and describes why they’re included in the design:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD colspan="2">
              <para/>
              <para>
                <embeddedLabel>Solution element</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>
                <embeddedLabel>Why is it included in this solution design?</embeddedLabel>
              </para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <embeddedLabel>1.</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>
                <embeddedLabel>Operating system and applicable files</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>Operating system installation files, including applicable operating system drivers and updates, must be available to deploy to new, bare metal computer hardware. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>2.</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>
                <embeddedLabel>MDT automation</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>
                <?Comment JJG: Based on feedback from Aaron about showing how much easier MDT is to use and maintain than CM. 2014-10-07T12:21:00Z  Id='7?>MDT provides a lightweight working infrastructure for automating and deploying operating system images without the need, costs, or overhead of setting up and maintaining a completely separate Configuration Manager infrastructure solely for operating system image creation. <?CommentEnd Id='7'
    ?></para>
              <para>MDT is used to create and validate deployment images in a clean, test environment to reduce deployment time, increase security, and improve ongoing configuration management.  </para>
              <para/>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>3.</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>
                <embeddedLabel>MDT deployment share</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>The MDT deployment share is the repository for operating system images, language packs, applications, device drivers, and other software that will be deployed to target computers.</para>
              <alert class="note">
                <para>Target computers need to connect to the deployment share to perform operating system deployments so a high-speed, persistent connection from them to the deployment share is recommended.</para>
              </alert>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>4.</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>
                <embeddedLabel>Operating system boot image</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>Operating system boot images are used for starting target computers using a customized version of Windows PE created when you update the MDT deployment share. The following boot images are created by the deployment workbench and stored in the <embeddedLabel><placeholder>deployment_share</placeholder>\Boot</embeddedLabel> folder (where <placeholder>deployment_share</placeholder> is the network shared folder used as the deployment to start computers over the network):</para>
              <list class="bullet">
                <listItem>
                  <para>LiteTouchPE_x64.iso and LiteTouchPE_x64.wim files (for 64-bit target computers)</para>
                </listItem>
                <listItem>
                  <para>LiteTouchPE_x86.iso and LiteTouchPE_x86.wim files (for 32-bit target computers)</para>
                </listItem>
              </list>
              <alert class="note">
                <para>When deploying to legacy BIOS computers, you can use a 32-bit boot image to deploy both 32-bit and 64-bit operating systems; however, a 64-bit boot image can only be used to deploy 64-bit operating systems. In contrast, UEFI systems require the architecture to match so a 64-bit system to which you’re deploying a 64-bit operating system would require a 64-bit boot image.</para>
                <para/>
              </alert>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>5.</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>
                <embeddedLabel>WDS deployment server</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>
                <?Comment JJG: Based on feedback from Aaron. 2014-10-07T12:21:00Z  Id='8?> <externalLink><linkText>Windows Deployment Services</linkText><linkUri>http://technet.microsoft.com/library/jj648426.aspx</linkUri></externalLink>, and PXE-based operating system deployment methods, is useful in the test environment because it is relatively easy to set up and it also enables faster, more iterative testing without the need to mount and dismount ISOs or create operating system CDs. <?CommentEnd Id='8'
    ?></para>
              <para>You must add the MDT boot image WIM files from the boot folder of the deployment share to Windows Deployment Services for custom, network-based operating system deployments.  </para>
              <alert class="tip">
                <para>You will only need to add the MDT boot images to Windows Deployment Services. You do not need to add operating system images from the Deployment Workbench.</para>
              </alert>
              <para/>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>6.</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>
                <embeddedLabel>Test virtual machine installation</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>This test virtual machine, or reference computer, is used to validate the installation of operating system images created by MDT in a test environment.</para>
              <alert class="tip">
                <para>The reference computer is the template for deploying new operating system images to target computers in production so be sure to configure this computer exactly as you want the production computers to be configured.</para>
              </alert>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>7.</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>
                <embeddedLabel>Captured operating system image</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>The operating system image (WIM file) that is captured from the reference computer will be deployed to your target computers.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>8.</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>
                <embeddedLabel>Captured operating system image and device drivers</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>These files are necessary to run Windows on new device hardware in your environment including the drivers necessary for network and storage communication. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>9.</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>
                <embeddedLabel>Configuration Manager primary site server</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>A Configuration Manager primary site server with <externalLink><linkText>necessary operating system deployment features</linkText><linkUri>http://technet.microsoft.com/library/gg682187.aspx</linkUri></externalLink> installed is used to deploy captured operating system images in the production environment. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>10.</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>
                <embeddedLabel>PXE-enabled distribution point</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>In this method of deployment, the operating system image and a Windows PE boot image are sent to a distribution point that is <externalLink><linkText>configured to accept PXE boot requests</linkText><linkUri>http://technet.microsoft.com/library/hh397405.aspx</linkUri></externalLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>11.</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>
                <embeddedLabel>Operating system deployment</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>PXE-initiated operating system deployments let computers request an operating system deployment over the network.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>12.</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>
                <embeddedLabel>Windows devices with standard software installed</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>The end result of this solution—Windows devices with driver files and standard desktop applications necessary for users to be successful.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para/>
    </content>
    <sections>
      <section address="BKMK_WhyThisDesign">
        <title>Why are we recommending this design?</title>
        <content>
          <para>There are many ways to install operating systems to a new computer, or bare metal system, such as MDT standalone, Configuration Manager build and capture, or MDT integrated into Configuration Manager. These methods assume that there is no user data or profile to preserve and can be used for everything from using MDT to create a “thin” Windows operating system image with basic updates and applications to integrating MDT with Configuration Manager to create and deploy ”thick” images containing many applications and post-installation configurations and management. </para>
          <para>The following table provides an overview of possible methods and Microsoft recommendations for when each should be used for optimal performance and scalability.</para>
          <alert class="note">
            <para>Operating system deployment methods are often interchangeable. Use the recommendations provided below as guidelines to select the method most applicable to your individual needs.</para>
          </alert>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>Operating system deployment method</embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>
                    <embeddedLabel>Recommended when</embeddedLabel>
                  </para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>Microsoft Deployment Toolkit (MDT) standalone</embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>MDT is a <externalLink><linkText>freely downloadable toolkit</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=40796</linkUri></externalLink> that helps automate the deployment of Windows operating systems and applications to desktop, laptop, and server computers. At a high level, MDT automates the deployment process by configuring the unattended Setup files for Windows and packaging the necessary files into a consolidated image file that you then deploy to reference and target computers.</para>
                  <alert class="tip">
                    <para>In very small, or disconnected, environments MDT standalone might be all that you need to use for operating system deployment. In those cases, the test environment steps detailed in this solution would satisfy the operating system deployment process requirements for those environments.</para>
                  </alert>
                  <para>MDT performs deployments by using the Lite Touch Installation (LTI) method. While you can create reference images for operating system deployment using Configuration Manager, in general we recommend creating them in MDT LTI for the following reasons:</para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <?Comment JJG: Based on feedback from Aaron. 2014-10-07T12:21:00Z  Id='9?>MDT Lite Touch does not require any infrastructure and can be quickly set up.<?CommentEnd Id='9'
    ?></para>
                    </listItem>
                    <listItem>
                      <para>
                        <?Comment JJG: Based on feedback from Aaron. 2014-10-07T12:21:00Z  Id='10?>Due to its simplicity and low footprint, MDT is typically the fastest way to create a reference image.<?CommentEnd Id='10'
    ?></para>
                    </listItem>
                    <listItem>
                      <para>You can use the same image for every type of operating system deployment—Microsoft Virtual Desktop Infrastructure (VDI), Microsoft System Center 2012 R2 Virtual Machine Manager (SCVMM), MDT, Configuration Manager, Windows Deployment Services (WDS), and more.</para>
                    </listItem>
                    <listItem>
                      <?Comment JJG: Moved based on Aaron’s feedback. 2014-10-07T12:21:00Z  Id='11?>
                      <para>With MDT, you can follow your deployments in real time, and if you have access to Microsoft Diagnostics and Recovery Toolkit (DaRT), you can even remote into Windows Preinstallation Environment (Windows PE) during deployment. The real-time monitoring data can be viewed from within the MDT Deployment Workbench, via a web browser, Windows PowerShell, the Event Viewer, or Microsoft Excel 2013. In fact, any script or app that can read an Open Data (OData) feed can read the information.<?CommentEnd Id='11'
    ?></para>
                    </listItem>
                    <listItem>
                      <para>Configuration Manager performs deployments in the LocalSystem account context. This means that you cannot configure the Administrator account with all of the settings that you would like to be included in the image. MDT runs in the context of the Local Administrator, which means you can configure the look and feel of the configuration and then use the CopyProfile functionality to copy these changes to the default user during deployment.</para>
                    </listItem>
                    <listItem>
                      <para>MDT LTI supports a Suspend action that allows for reboots, which is useful when you need to perform a manual installation or check the reference image before it’s automatically captured.</para>
                    </listItem>
                  </list>
                  <alert class="tip">
                    <para>It is best to use MDT to create “<placeholder>thin</placeholder>” images that contain necessary software updates, runtimes, and few standard desktop applications. </para>
                  </alert>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>MDT and Configuration Manager</embeddedLabel>
                  </para>
                  <alert class="important">
                    <para>This is the recommended operating system deployment method described in this solution.</para>
                  </alert>
                </TD>
                <TD>
                  <para>This option is recommended for large, enterprise businesses with thousands of computers and applications to support and maintain. It is our recommendation for this solution based on the following Microsoft best practices:</para>
                  <list class="bullet">
                    <listItem>
                      <para>You should use MDT for building and testing operating system images.</para>
                    </listItem>
                    <listItem>
                      <para>You should use MDT standalone for small-scale testing before deploying to production environments.</para>
                    </listItem>
                    <listItem>
                      <para>You should use MDT with WDS to enable PXE deployment integration for small pilots or small-scale production operating system deployments with LTI.</para>
                    </listItem>
                    <listItem>
                      <para>You should use MDT operating system images with Configuration Manager for large-scale operating system deployments to take advantage of enterprise-level management features such as: replication, multicast DPs, bandwidth management, reporting, poor network connections to remote sites, and stronger security through encryption and password protection.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>Configuration Manager standalone</embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>
                    <externalLink>
                      <linkText>Configuration Manager operating system deployment</linkText>
                      <linkUri>http://technet.microsoft.com/library/gg682018.aspx</linkUri>
                    </externalLink> provides administrative users with a tool for creating operating system images that they can deploy to computers. The operating system image, in a Windows Imaging Format (WIM) format file, contains the required version of a Windows operating system and any line-of-business applications that have to be installed on the computer.</para>
                  <alert class="tip">
                    <para>It is best to use Configuration Manager (or MDT integrated with Configuration Manager) to create “<placeholder>thick</placeholder>” images that contain many line of business (LOB) applications that must be installed during operating system deployment rather than duplicating the applications in MDT.</para>
                  </alert>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>MDT integrated with Configuration Manager</embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>While only MDT is used in LTI deployments, ZTI and User Driven Installation (UDI) deployments are performed using MDT integrated with Configuration Manager.</para>
                  <para>
                    <externalLink>
                      <linkText>Integrating MDT with Configuration Manager</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn744295.aspx</linkUri>
                    </externalLink> enhances the Configuration Manager operating system deployment feature by making additional MDT commands available to Configuration Manager task sequences. </para>
                  <para>For example, <embeddedLabel>MDT 2013 simplifies the creation and operation of dynamic deployments</embeddedLabel>. When MDT is integrated with Configuration Manager, the task sequence takes additional instructions from the MDT rules. In its most simple form, these settings are stored in a text file, the CustomSettings.ini file, but you can store the settings in Microsoft SQL Server databases, or have Microsoft Visual Basic Scripting Edition (VBScripts) or web services provide the settings used.</para>
                  <para>
                    <embeddedLabel>MDT 2013 also adds an optional deployment wizard</embeddedLabel>. For some deployment scenarios, you may need to prompt the user for information during deployment such as the computer name, the correct organizational unit (OU) for the computer, or which applications should be installed by the task sequence. With MDT integration, you can enable the User-Driven Installation (UDI) wizard to gather the required information, and customize the wizard using the UDI Wizard Designer.</para>
                  <para>To take advantage of these, and other, enhancements after integrating MDT with Configuration manager, simply <?Comment JJG: Verified in console 2014-10-07T12:21:00Z  Id='12?>click Create MDT task sequence in the Task Sequences group on the Home tab on the Operating Systems node in the Software Library workspace of the Configuration Manager console<?CommentEnd Id='12'
    ?>.</para>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_ImplementationSteps">
    <title>What are the steps to implement this solution?</title>
    <content>
      <para>Use the steps in this section to implement the solution. Make sure to verify the success of each step before proceeding to the next step. These steps are divided into two sections, the test environment using MDT standalone and production environment using Configuration Manager.</para>
      <alert class="note">
        <para>If you want to print or export a customized set of solution topics, see <externalLink><linkText>Print/Export Multiple Topics – Help</linkText><linkUri>http://technet.microsoft.com/library/export/help/?returnUrl=%2fen-US%2flibrary%2fff630950.aspx</linkUri></externalLink>.</para>
      </alert>
    </content>
    <sections>
      <section>
        <title>Test environment steps</title>
        <content>
          <para>In the test environment you will use MDT to deploy Windows to a reference computer, capture an image of the reference computer, and then deploy the captured image to a target computer to validate the deployment image before moving it into production.</para>
          <para>Follow these implementation steps to create and test operating system images using MDT LTI.</para>
          <list class="ordered">
            <listItem>
              <para>
                <embeddedLabel>Prepare the environment and workbench computer for MDT installation</embeddedLabel>  to ensure the required infrastructure and supporting files are configured and installed correctly. Before starting MDT setup, be sure you have considered the following: </para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <tbody>
                  <tr>
                    <TD>
                      <para>
                        <externalLink>
                          <linkText>Review the hardware and software requirements</linkText>
                          <linkUri>http://technet.microsoft.com/library/dn781086.aspx</linkUri>
                        </externalLink> for the version of MDT that you are installing to ensure the workbench computer operating system is supported.</para>
                    </TD>
                    <TD>
                      <alert class="tip">
                        <para>The MDT 2013 workbench is designed to work with the Windows 8.1 operating system. However, if you are not using Windows 8.1 for your workbench computer, you will need to install the <externalLink><linkText>.NET Framework 3.5</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=21</linkUri></externalLink> and <externalLink><linkText>Windows PowerShell 2.0</linkText><linkUri>http://support.microsoft.com/kb/968930</linkUri></externalLink>.</para>
                      </alert>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Download the appropriate version of the Microsoft Deployment Toolkit (MDT) required for the version of Windows you want to deploy.</para>
                    </TD>
                    <TD>
                      <alert class="tip">
                        <para>
                          <externalLink>
                            <linkText>MDT 2013</linkText>
                            <linkUri>http://www.microsoft.com/download/details.aspx?id=40796</linkUri>
                          </externalLink> supports deployment of Windows 8.1, Windows 8, Windows 7, Windows Server 2012 R2, Windows Server 2012, and Windows Server 2008 R2. </para>
                      </alert>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Download the Windows Assessment and Deployment Kit (Windows ADK) required for the version of MDT you are using. </para>
                    </TD>
                    <TD>
                      <alert class="tip">
                        <para>The <externalLink><linkText>Windows Assessment and Deployment Kit (Windows ADK) for Windows 8.1</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=39982</linkUri></externalLink> is required for MDT 2013.</para>
                      </alert>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Check that Windows Deployment Services (WDS) is running on the network to enable PXE-boot installations and that both the deployment server and transport server role services are installed. </para>
                      <para>
                        <?Comment JJG: Need something aboutcolocation of PXE and DHCP which involves different settings (or vice versa, I don’t recall off the top of my head….) 2014-10-07T12:21:00Z  Id='13?>WDS requires AD DS, DHCP, DNS, and an NTFS file system partition to store images. Configure WDS to respond to client requests and create the deployment share directory, but it is not necessary to add boot or operating system images at this step. On the WDS Server Advanced properties tab, ensure that you enable the “Authorize this Windows Deployment Services server in DCHP”.<?CommentEnd Id='13'
    ?></para>
                      <para>If DHCP will be the running on the same server as WDS, you will need to <externalLink><linkText>configure DHCP option 60 to use value of PXEClient</linkText><linkUri>http://technet.microsoft.com/library/cc732351(WS.10).aspx</linkUri></externalLink>. </para>
                      <alert class="important">
                        <para>In this solution we are recommending WDS with DHCP option integration for ease of use in the test environment because that is suitable for small scale testing without using routers for network traffic management. However, this is not recommended for large scale production deployments on routed networks because that method is not as reliable as configuring routers. In production environments, you should implement DHCP relay agents, sometimes referred to as IP helpers, to enable network boot requests to reach designated servers from computers across a router from a DHCP server on a remote subnet.</para>
                      </alert>
                    </TD>
                    <TD>
                      <alert class="tip">
                        <?Comment JJG: Fromhttp://technet.microsoft.com/library/bb680753.aspx 2014-10-07T12:21:00Z  Id='14?>
                        <para>Whether you plan to co-host WDS and DHCP on the same server or use two different servers you must configure WDS to listen on a specific port. DHCP and WDS both require port number 67. If you have co-hosted WDS and DHCP you can move DHCP or the PXE site role to a separate server or use the procedure below to configure the WDS server to listen on a different port.</para>
                        <para>Modify the following registry key:</para>
                        <para>
                          <embeddedLabel>HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WDSServer\Providers\WDSPXE</embeddedLabel>
                        </para>
                        <para>Set the registry value to:</para>
                        <para>
                          <embeddedLabel>UseDHCPPorts = 0</embeddedLabel>
                        </para>
                        <para>For the new configuration to take effect run the following command on the co-located DHCP and WDS server:</para>
                        <para>WDSUTIL /Set-Server /UseDHCPPorts:No /DHCPOption60:Yes<?CommentEnd Id='14'
    ?></para>
                      </alert>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> </para>
              <list class="bullet">
                <listItem>
                  <para>Ensure you are planning to install the MDT workbench on a supported operating system, and have installed the .NET Framework 3.5 and PowerShell 2.0 if you are not using Windows 8.1. </para>
                </listItem>
                <listItem>
                  <para>You have identified the Windows Assessment and Deployment Kit (Windows ADK) required for the version of MDT you are using.</para>
                </listItem>
                <listItem>
                  <para>WDS and required network services are present and properly configured in the test environment.</para>
                </listItem>
              </list>
              <para/>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Install MDT and the Windows ADK</embeddedLabel> by <externalLink><linkText>Downloading the MDT software</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=40796</linkUri></externalLink> and installing it on a supported operating system in the test environment accepting the default values. </para>
              <alert class="important">
                <para>When you first open the MDT workbench after installation, you might be prompted to check for updated components. In MDT 2013, you should not do this because it will download an older list of components. Specifically, it will download an older version of bddmanifest.cab, reverting the component manifest (ComponentList.xml) to an older version. To learn more about this issue and other known issues with MDT 2013, you can review the <externalLink><linkText>MDT 2013 release notes</linkText><linkUri>http://technet.microsoft.com/library/dn781277.aspx</linkUri></externalLink>.</para>
              </alert>
              <para>After MDT is installed, you need to install the appropriate <externalLink><linkText>Windows ADK</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=39982</linkUri></externalLink> to support the version of MDT you are using. When installing the Windows ADK, only the deployment tools and the Windows Preinstallation Environment (Windows PE) are required to interact with deployment shares.</para>
              <alert class="tip">
                <para>After installing Windows ADK, log off, and then log on again to the computer so that the PATH environment variable is updated to include the %Program Files%\Windows Imaging folder.</para>
              </alert>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> Check that the MDT and the appropriate version of the Windows ADK are installed on the MDT workbench computer before continuing. If you do not install the Windows ADK, you will be prompted to install it when trying to access the deployment shares node of the workbench console.</para>
              <para/>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Create an MDT deployment share</embeddedLabel> that will be the repository for the operating system images, language packs, applications, device drivers, and other software that will be deployed to target computers. <externalLink><linkText>Start the New Deployment Share Wizard</linkText><linkUri>http://technet.microsoft.com/library/dn781086.aspx</linkUri></externalLink> from the action pane in the deployment shares node of the MDT workbench to create a new MDT deployment share and take note of the location of the deployment share created. </para>
              <para>For this solution, MDT deployment share properties should be configured with defaults when you run the New Deployment Share Wizard. </para>
              <alert class="tip">
                <para>The deployment share settings are stored in the CustomSettings.ini file in the deployment share’s Control folder and can be changed later.</para>
              </alert>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> You should now see the deployment share name displayed in the details pane. By default, the MDT will create a deployment share folder named C:\DeploymentShare and a hidden shared folder called \\<placeholder>&lt;computerName&gt;</placeholder>\deploymentshare$. If you go to the location of the deployment share using file explorer, you should see that a folder structure has been created for you. </para>
              <para/>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Import operating system files</embeddedLabel> into the Operating Systems node in the Deployment Workbench using the <externalLink><linkText>Import Operating System Wizard</linkText><linkUri>http://technet.microsoft.com/library/dn781086.aspx</linkUri></externalLink>. If you will have many operating systems, you should create sub-folders in the Operating Systems node to store your files before importing them. </para>
              <alert class="note">
                <para>
                  <?Comment JJG: Needs to be beefed up and also talk about WSUS. 2014-10-07T12:21:00Z  Id='15?>You can also create applications in MDT to install desktop software, but because this solution involves using Configuration Manager for desktop application installation, none will be created as part of this solution.<?CommentEnd Id='15'
    ?></para>
              </alert>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> If the Import Operating System Wizard was successful, the message “The process completed successfully” should be displayed. The name and description of the operating systems you import should be displayed in the MDT workbench console and the operating system installation files should have been copied into the operating system folder in the MDT deployment share folder structure.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Add out-of-box drivers</embeddedLabel> that are required for the reference computer and the target computer in your test environment by using the <externalLink><linkText>New Driver Wizard</linkText><linkUri>http://technet.microsoft.com/library/dn781086.aspx</linkUri></externalLink>. These device drivers will be added to Windows PE and deployed with the operating system. Add the device drivers in the Out-of-box Drivers node in the Deployment Workbench. </para>
              <para>If you will support many operating systems or device types in your test environment, you should make sub-folders for each operating system and make and model you plan to deploy to.</para>
              <alert class="tip">
                <para>If the device drivers for the reference computer and the target computer are included with operating system you are deploying, you can skip this step.</para>
              </alert>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> Verify that the New Driver Wizard copies the device driver files to the deployment share in the appropriate Out-of-Box Drivers\<placeholder>&lt;driver name&gt;</placeholder> directories.</para>
              <para/>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Create a standard client task sequence for the reference computer</embeddedLabel> using the <externalLink><linkText>New Task Sequence Wizard</linkText><linkUri>http://technet.microsoft.com/library/dn781086.aspx#CreateTaskSequence</linkUri></externalLink> in the Task Sequences node of the Deployment Workbench that will be used to deploy and capture a reference computer image using the operating system files you previously imported into the workbench.</para>
              <alert class="tip">
                <para>This task sequence should both install and capture the reference computer image. This is preferable to using two task sequences (one to install and one to capture) because if there is any lapse in time between when the system is built and when it’s captured, then it is possible that other configurations can be unexpectedly introduced.</para>
              </alert>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel>  If the New Task Sequence Wizard was successful, the message “The process completed successfully” should be displayed. The name and description of the task sequence you created should also now be displayed in the MDT workbench console.</para>
              <para/>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Enable deployment process monitoring </embeddedLabel>in the MDT deployment share properties.  This will provide you <externalLink><linkText>basic monitoring of the task sequence as it processes the steps you have configured</linkText><linkUri>http://technet.microsoft.com/library/dn781086.aspx</linkUri></externalLink> from within the MDT workbench. This will also add a line to the customsettings.ini file that is displayed on the Rules tab of the deployment share properties similar to EventService=http:// <placeholder>&lt;computername&gt;</placeholder>:9800.</para>
              <para>Additionally, more detailed logging can be enabled by manually modifying the customsettings.ini file contents on the Rules tab of the deployment share properties to create detailed log files for each computer when a task sequence is run; you can also enable dynamic logging to capture all active task sequence actions. You will first need to first create a network share to store log files and set the proper share permissions. If you want to enable dynamic logging, you should create a folder within the previously created network share to host that dynamic log file. </para>
              <list class="bullet">
                <listItem>
                  <para>To configure per-computer logging, update your customsettings.ini rule file with the following line: SLSHARE=\\<placeholder>YourMDTServerName</placeholder>\<placeholder>YourMDTLogsShareName</placeholder>\%ComputerName%.</para>
                </listItem>
                <listItem>
                  <para>To configure dynamic logging to capture all task sequence activities in real time, update your customsettings.ini rule file with the following line: SLShareDynamicLogging=\\<placeholder>YourMDTServerName</placeholder>\<placeholder>YourMDTLogsShare</placeholder>\<placeholder> YourDymanicMDTLogsShare</placeholder> </para>
                </listItem>
              </list>
              <alert class="tip">
                <para>While you are modifying the customsettings.ini rule file, you can also customize the organization name displayed in the MDT wizard by adding the following line above the logging entries: _SMSTSOrgName=<placeholder>OrganizationNameYouWantDisplayed</placeholder>. You can also </para>
              </alert>
              <para>Together, those lines would look like this in the <externalLink><linkText>customsettings.ini rules file</linkText><linkUri>http://technet.microsoft.com/library/dn759415.aspx</linkUri></externalLink>: </para>
              <code>[Settings]
Priority=Default
Properties=MyCustomProperty

[Default]
OSInstall=Y
SkipCapture=NO
SkipAdminPassword=YES
SkipProductKey=YES
SkipComputerBackup=NO
SkipBitLocker=NO

Copy Logs if en error occurs or when deployment is successfully completed
SLShare=\\<placeholder>&lt;YourMDTServerName&gt;</placeholder>\<placeholder>&lt;YourMDTLogsShare&gt;</placeholder>

; Enable Dynamig Logging
SLSHAREDynamicLogging=\\<placeholder>&lt;YourMDTServerName&gt;</placeholder>\<placeholder>&lt;YourMDTLogsShare&gt;</placeholder>\<placeholder>&lt;YourDymanicMDTLogsShare&gt;</placeholder>

_SMSTSOrgName=<placeholder>&lt;OrganizationNameYouWantDisplayed&gt;</placeholder></code>
              
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel>
              </para>
              <list class="bullet">
                <listItem>
                  <para>If monitoring is enabled, you should not receive the message “No monitoring data is available because monitoring is ne enabled for this deployment share.” when the monitoring node of the deployment workbench is selected. </para>
                </listItem>
                <listItem>
                  <para>A line similar to the following has been added to the customsettings.ini file contents displayed on the Rules tab of the deployment share properties: EventService=http:// <placeholder>&lt;computername&gt;</placeholder>:9800</para>
                </listItem>
                <listItem>
                  <para>If you have added a custom organization name to be displayed by the task sequence, a line similar to the following has been added to the customsettings.ini file contents displayed on the Rules tab of the deployment share properties: _SMSTSOrgName=<placeholder>&lt;OrganizationNameYouWantDisplayed&gt;</placeholder></para>
                </listItem>
                <listItem>
                  <para>If you have enabled detailed logging by adding custom log file share locations to the customsettings.ini file contents displayed on the Rules tab of the deployment share properties, then verify that you can access the network shares for both the per-computer logging directory and the dynamic logging directly that will contain a single BDD.log log file that is dynamically updated when a task sequence runs. </para>
                </listItem>
              </list>
              <para/>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Update the deployment share</embeddedLabel> with the latest information after you have completed configuring it by using the <externalLink><linkText>Update Deployment Share action</linkText><linkUri>http://technet.microsoft.com/library/dn781086.aspx</linkUri></externalLink> in the action pane of the MDT workbench. Updating the deployment share updates all the MDT configuration files and generates a customized version of Windows PE that is used to start the reference computer and initiate LTI deployment.</para>
              <para>When the deployment share is updated, MDT will generate ISO images and WIM image files that are used to initiate operating system deployment according to the settings you have configured in the deployment share properties.  </para>
              <para/>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> When the deployment workbench is updated, MDT should have created the LiteTouchPE_x64.iso and LiteTouchPE_x64.wim files (for 64-bit target computers) and LiteTouchPE_x86.iso and LiteTouchPE_x86.wim files (for 32-bit target computers) in the \\<placeholder>&lt;computerName&gt;</placeholder>\deploymentshare$\Boot folder.</para>
              <para/>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Load boot image into the WDS console</embeddedLabel> to <externalLink><linkText>enable target computers to start using the customized Windows PE images</linkText><linkUri>http://technet.microsoft.com/library/dn759415.aspx#AddLTIBootImagestoWindowsDeploymentServices</linkUri></externalLink> over the network. </para>
              <para>All that you need to add is the boot image created by MDT to the Boot Images node in the WDS console (right-click Boot Images, and browse to the location of the boot image created by MDT in the last step (%InstallDir%\DeploymentShare\Boot\LiteTouchPE_x64.wim). There is no need to add any install images to WDS.  </para>
              <para/>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> If the Add Image Wizard was successful, the message “The operation is complete. The selected images were successfully added to the server.” should be displayed. Additionally, when you start a computer configured to boot from the network, select the option to boot from PXE, the custom boot image should be available from the list of options.</para>
              <para/>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Use PXE to install and capture your image over the network</embeddedLabel>. Start the reference computer and select the option to PXE network boot from network using WDS and then select the boot image that was previously uploaded into WDS to start the customized Windows PE environment. </para>
              <para>When the Windows Deployment Wizard starts, select and run the standard client task sequence that you previously created to install and capture the operating system on the reference computer. There is no need to worry about the majority of settings that are displayed by the Windows Deployment Wizard, but be sure to select the option to capture an image of the reference computer on the Capture Image wizard page. Otherwise, simply accept the defaults, including the path to store the captured image, and begin the operating system installation and image capture process.</para>
              <alert class="tip">
                <para>By default, you’ll need to provide network access credentials to access the deployment share from WinPE each time the computer starts from the boot image. If you will be doing a lot of testing using this method, you can add network share access credentials by editing the Bootstrap.ini file contents found on the Rules tab of the deployment share properties similar to the following example. After doing so, be sure to update the deployment share and replace the boot image stored on the PXE server. </para>
              </alert>
              <code>
[Settings]
Priority=Default

DeployRoot=<placeholder>&lt;DeployRootPath&gt;</placeholder>
UserDomain=<placeholder>&lt;FQDNofTestDomain</placeholder>&gt;
UserID=<placeholder>&lt;TestDomainUser&gt;</placeholder>
UserPassword=<placeholder>&lt;TestDomainUserPassword&gt;</placeholder>
</code>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> The reference computer should go through the steps necessary to install the operating system defined in the task sequence. Afterwards, it should immediately run the sysprep and capture steps to save an image of the reference computer in the network share specified when running the task sequence. By default, the captured image should be present in the <embeddedLabel>%InstallDir%\DeploymentShare\Captures</embeddedLabel> directory.</para>
              <para/>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Add the captured reference image to the deployment workbench</embeddedLabel>. Before you can deploy the capture image, it must be added to the list of operating systems in the Operating Systems node in the Deployment Workbench from the %InstallDir%\DeploymentShare\Captures directory using the Import Operating System Wizard.</para>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> When the Import Operating System Wizard finishes, the captured image of the reference computer should be added to the list of operating systems in the details pane of the Operating Systems node in the deployment workbench and the captured WIM file should be copied to the operating systems directory. </para>
              <para/>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Create a second standard client task sequence</embeddedLabel> using the <externalLink><linkText>New Task Sequence Wizard</linkText><linkUri>http://technet.microsoft.com/library/dn781086.aspx</linkUri></externalLink>. This task sequence will be used to deploy the captured image to a target, test computer.  You should do this to ensure the basic deployment is functional as desired before moving into production environment.  </para>
              <alert class="tip">
                <para>Be sure to select the captured image from the operating system options in the deployment workbench during task sequence creation.</para>
              </alert>
              <para/>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> If the New Task Sequence Wizard was successful, the message “The process completed successfully” should be displayed. The name and description of the task sequence you created should also now be displayed in the MDT workbench console.</para>
              <para/>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Use PXE to deploy and test your captured image over the network</embeddedLabel>. Start the target computer and select the option to PXE network boot from network using WDS and then select the boot image that was previously uploaded into WDS to start the customized Windows PE environment.</para>
              <para>When the Windows Deployment Wizard starts, select and run the standard client task sequence that you previously created to install the captured operating system on the target computer. You should not select the option to capture an image of this computer on the Capture Image wizard page. Simply accept the defaults and click Next to begin the operating system installation process.</para>
              <para/>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> The target computer should automatically go through the steps necessary to successfully install the reference computer image . When complete, the Deployment Summary dialog box should appear with no errors and no warnings reported.</para>
              <para/>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Copy the reference computer image</embeddedLabel> to a portable storage device or removable media in order to transport it to the production computing environment. Before beginning the production environment steps, you need to copy the reference computer image to a valid network share in the production environment so that it can be imported into the Configuration Manager console. </para>
              <para/>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> The captured and tested operating system image from the reference computer is now present on a portable storage device or removable media that can be taken to the production environment. </para>
              <para/>
            </listItem>
          </list>
        </content>
      </section>
      <section>
        <title>Production environment steps</title>
        <content>
          <para>In the production environment you will use Configuration Manager to deploy the Windows operating system image (WIM file) that you captured in the test environment using MDT.</para>
          <para>Use the following implementation steps to deploy and manage enterprise operating system images in your production environment using Configuration Manager ZTI.</para>
          <list class="ordered">
            <listItem>
              <para>
                <embeddedLabel>Ensure the production network environment will support PXE boot requests</embeddedLabel> from Configuration Manager clients. </para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <tbody>
                  <tr>
                    <TD>
                      <para>Be sure that AD DS, DHCP, and DNS are available to computers starting from the network.</para>
                    </TD>
                    <TD>
                      <alert class="note">
                        <para>It is not necessary to install WDS during this step as the required WDS components will be installed on PXE-enabled Configuration Manager distribution points in the next step.</para>
                      </alert>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>You should also determine an appropriate range of IP addresses that DHCP will provide on the network to use as a Configuration Manager site boundary to support network book requests. </para>
                      <para/>
                    </TD>
                    <TD>
                      <para/>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para/>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> You have ensured the network environment will support PXE boot requests from computers starting from the network and determined a suitable DHCP-based IP address range to use for a Configuration Manager site boundary.</para>
              <para/>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Prepare the Configuration Manager environment</embeddedLabel> for deploying operating systems over the network. </para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <tbody>
                  <tr>
                    <TD>
                      <para>
                        <externalLink>
                          <linkText>Enable Configuration Manager Distribution points to respond to PXE requests from the network</linkText>
                          <linkUri>http://technet.microsoft.com/library/gg712266.aspx</linkUri>
                        </externalLink>. You will need to be sure that PXE support for clients is enabled on the PXE tab of distribution point properties (which will install WDS if required) and also allow the distribution point to respond to incoming PXE requests to enable the distribution point to accept PXE boot requests from computers on the network. </para>
                    </TD>
                    <TD>
                      <alert class="tip">
                        <para>For additional security, you should also require a password for computers to use the PXE-enabled distribution point when starting from the network.</para>
                      </alert>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>The Configuration Manager client needs an account to provide credentials when accessing the Configuration Manager distribution points over the network. This account is necessary because Configuration Manager client computers use the Local System account to perform most operations on the computer, but LocalSystem cannot access network resources during network-based operating system deployments. </para>
                      <para>To enable unknown computers to access Configuration Manager network resources, you will need to <externalLink><linkText>create and configure a Configuration Manager network access account</linkText><linkUri>http://technet.microsoft.com/library/bb680398.aspx</linkUri></externalLink>. </para>
                    </TD>
                    <TD>
                      <?Comment JJG: Is this in the core docs anywhere? 2014-10-07T12:21:00Z  Id='16?>
                      <alert class="tip">
                        <para>You can create and configure the network access account in the Administration node of the Configuration Manager console. To do so, just right-click on your site name, select <embeddedLabel>Configure Site Components</embeddedLabel> and then <embeddedLabel>Software Distribution</embeddedLabel>. From there, select the <embeddedLabel>Network Access Account</embeddedLabel> tab to configure the account properties.<?CommentEnd Id='16'
    ?></para>
                      </alert>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>
                        <externalLink>
                          <linkText>Create an IP range based boundary</linkText>
                          <linkUri>http://technet.microsoft.com/library/hh427326.aspx</linkUri>
                        </externalLink> based on the DHCP-based IP address range you determined in the previous step. You need to do this because unknown computers booting from the network will not be in AD DS yet and unless site boundaries are specified, the client assumes that the computer running Configuration Manager is in a remote site. After adding a site boundary based on the DHCP supported IP subnet, add the site boundary to a site boundary group.</para>
                    </TD>
                    <TD>
                      <para/>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> </para>
              <list class="bullet">
                <listItem>
                  <para>Distribution points have been properly <externalLink><linkText>configured to respond to PXE boot requests over the network</linkText><linkUri>http://technet.microsoft.com/library/gg712266.aspx</linkUri></externalLink>. </para>
                </listItem>
                <listItem>
                  <para>A <externalLink><linkText>network access account has been created and configured</linkText><linkUri>http://technet.microsoft.com/library/bb680398.aspx</linkUri></externalLink> to support network resource access for unknown computers. </para>
                </listItem>
                <listItem>
                  <para>An IP address range based <externalLink><linkText>site boundary has been created</linkText><linkUri>http://technet.microsoft.com/library/hh427326.aspx</linkUri></externalLink> that corresponds to an IP address range provided by DHCP on the network.</para>
                </listItem>
              </list>
              <para/>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Enable the default boot images to support PXE</embeddedLabel> in the Configuration Manager console. In the original release of Configuration Manager 2012, you need to manually <externalLink><linkText>configure the default boot images to support PXE</linkText><linkUri>http://technet.microsoft.com/library/gg712266.aspx</linkUri></externalLink> boot requests. In later versions, this support is enabled by default.</para>
              <para/>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> Verify that the default boot images are PXE-enabled by ensuring the <embeddedLabel>Deploy this boot image from the PXE service point</embeddedLabel> option is enabled on the <embeddedLabel>Data Source</embeddedLabel> tab of the boot image properties in the Configuration Manager console.</para>
              <alert class="note">
                <para>After verifying that the default boot images are PXE-enabled, you should also check the content status to ensure the PXE-enabled boot images have been successfully distributed to the site distribution points supporting PXE boot requests. </para>
              </alert>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Import the captured reference image</embeddedLabel> that you created using MDT into Configuration Manager console, operating systems images node. To do that, use the <?Comment JJG: Nothing in the docs about this wizard? 2014-10-07T12:21:00Z  Id='17?>Add operating system image wizard<?CommentEnd Id='17'
    ?> to browse to the network share that you saved the captured reference computer image.</para>
              <para/>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> The Add operating system image wizard completed successfully and imported the captured reference computer image into the Configuration Manager console.</para>
              <para/>
            </listItem>
            <listItem>
              <para>Before you can use PXE to deploy the captured operating system image, you must <embeddedLabel>distribute the operating system image content</embeddedLabel> to PXE-enabled distribution points in the site using the <externalLink><linkText>Distribute Content Wizard</linkText><linkUri>http://technet.microsoft.com/library/988b456a-efa8-45d1-89a6-894585dfca38</linkUri></externalLink>.</para>
              <para>After the captured operating system image is successfully added, you should also enable the option to <embeddedLabel>Copy the content in this package to a package share on distribution points</embeddedLabel> to allow clients to install the content from the network. </para>
              <para/>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> The distribute content wizard should complete successfully and the content status for the captured image distribution should complete successfully after a few moments.</para>
              <alert class="tip">
                <para>Now is a good time to ensure that both of the boot images (x86 and x64) are distributed as well as the operating system image you just imported.</para>
              </alert>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Create a task sequence</embeddedLabel> to <externalLink><linkText>deploy the captured operating system image package</linkText><linkUri>http://technet.microsoft.com/library/hh273490.aspx</linkUri></externalLink> from the Task Sequences node of the Configuration Manager console that will be used to deploy the image and join the new computer to the production domain.</para>
              <alert class="note">
                <para>For this solution, you do not need to install updates or applications during deployment, but after you are comfortable with the overall process, you should use those options to create more complete task sequences for future deployments.</para>
              </alert>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> The new deployment task sequence should now be displayed in the results pane of the Task Sequences node in the Configuration Manager console.</para>
              <para/>
            </listItem>
            <listItem>
              <para>Deploy the task sequence as <embeddedLabel>Available</embeddedLabel> to the <embeddedLabel>All Unknown Computers</embeddedLabel> collection that contains default resource records (one record for 64-bit computers and another for 32-bit computers) for systems that are not currently members of the Configuration Manager database. </para>
              <para>You should make this task sequence deployment <embeddedLabel>Available</embeddedLabel> instead of <embeddedLabel>Required</embeddedLabel> to safeguard against the task sequence running accidentally on computers with network boot options set higher than local hard drives in the system BIOS. Also note that this can happen regardless of the availability or expiration times set for the task sequence deployment.</para>
              <alert class="tip">
                <para>For additional security, you should require a password for computers to use PXE-enabled distribution points when starting from the network as described in step 2 of the production environment implementation steps.</para>
              </alert>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> The deploy software wizard should complete successfully.</para>
              <para/>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Install the captured operating system image</embeddedLabel> on a bare metal test computer in the production environment using PXE boot.  </para>
              <para>When the computer starts and boots from the network, it will acquire an IP address from the DHCP server, connect to the Configuration Manager site server to run the task sequence you previously deployed to the All Unknown Computers collection. After a dialog box opens to notify you that the task sequence is about to run, the task sequence should run and display an installation progress dialog box to show the tasks being run on the computer as it completes the operating system deployment process.</para>
              <para/>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> Ensure the PXE-boot is successful and the bare metal computer starts using the boot image over the network. After providing the password (if required) to start the imaging process, the actions defined in the task sequence are completed.  </para>
              <para/>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Monitor OS deployment</embeddedLabel> in the Monitoring workspace of the Configuration Manager console by expanding Deployments and selecting the task sequence deployment that you previously deployed. Right-click the task sequence name in the Results pane and click <embeddedLabel>Run Summarization</embeddedLabel> and then refresh the results pane information to view the most current monitoring information.</para>
              <alert class="tip">
                <para>If you have the Reporting Services Point site system role installed, you can also <externalLink><linkText>review the operating system deployment reports</linkText><linkUri>http://technet.microsoft.com/library/gg712299.aspx</linkUri></externalLink> available to you for reporting on task sequence process success. </para>
              </alert>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> Task sequence progress and deployment status progresses through in progress to success.</para>
              <para/>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Validate the test production computer installation</embeddedLabel> of the captured reference system image. Log into the production test computer and verify that the task sequence has successfully completed with the expected operating system installed with the expected configurations.</para>
              <para>You should also now be able to see the new computer name represented as an assigned computer resource client for the Configuration Manager site in the <embeddedLabel>All Systems</embeddedLabel> Collection in the Configuration Manager console.</para>
              <para/>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> The task sequence should have completed successfully to install the captured reference operating system image, join the production domain, and installed and initiated the Configuration Manager client.  The new computer client resource record should also now be present in the All Systems collection of the Configuration Manager console.</para>
              <para/>
            </listItem>
          </list>
        </content>
      </section>
      <sectionSimple>
        <para/>
        <para>
          <embeddedLabel>Implementation complete</embeddedLabel>. </para>
      </sectionSimple>
    </sections>
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
              <para>Planning and design documentation on TechNet</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>Using the Microsoft Deployment Toolkit</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn759415.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Deploy Windows 8.1 with the Microsoft Deployment Toolkit</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn744280.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Operating System Deployment in Configuration Manager</linkText>
                  <linkUri>http://technet.microsoft.com/library/gg682018.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Deploy Windows 8.1 with System Center 2012 R2 Configuration Manager</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn744284.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Quick Start Guide for Lite Touch Installation</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn781086.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Quick Start Guide for MDT 2013 and System Center 2012 R2 Configuration Manager</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn688992.aspx</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Microsoft Virtual Academy training</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>Windows 8.1 Deployment Jump Start</linkText>
                  <linkUri>http://www.microsoftvirtualacademy.com/training-courses/windows-8-1-deployment-jump-start</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>TechNet virtual labs</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>Creating a Windows 8.1 reference image</linkText>
                  <linkUri>https://vlabs.holsystems.com/vlabs/technet?&amp;labid=11968</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Deploying Windows 8.1 with MDT 2013</linkText>
                  <linkUri>https://vlabs.holsystems.com/vlabs/technet?&amp;labid=11970</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Deploying Windows 8.1 with ConfigMgr 2012 R2 and MDT 2013</linkText>
                  <linkUri>https://vlabs.holsystems.com/vlabs/technet?&amp;labid=11969</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Community resources</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>System Center Configuration Manager Team Blog</linkText>
                  <linkUri>http://blogs.technet.com/b/configmgrteam/</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Configuration Manager 2012 Operating System Deployment Forum</linkText>
                  <linkUri>http://social.technet.microsoft.com/Forums/home?forum=configmanagerosd</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>MDT Team Blog</linkText>
                  <linkUri>http://blogs.technet.com/b/msdeployment/</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>MDT Forum</linkText>
                  <linkUri>http://social.technet.microsoft.com/Forums/home?forum=mdt</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics/>
</developerConceptualDocument>
