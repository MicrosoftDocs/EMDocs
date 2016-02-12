---
title: BYOD management considerations
ms.custom: na
ms.reviewer: na
ms.service: multiple
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bf0d4210-5edc-4ad7-bcb5-372099049630
author: YuriDio
---
# BYOD management considerations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A management domain is mandatory in an infrastructure that supports a BYOD model. In order to fully support BYOD demands, the management domain must be able to enable IT to monitor resources, provide reporting capabilities, manage compute and storage resources, enable device configuration and automation, and manage apps deployment and provisioning.</para>
  </introduction>
  <section>
    <title>4.4.1 Monitoring</title>
    <content>
      <para>One of the roles of the management domain is to monitor compliance settings, not only for corporate assets but also for mobile devices owned by users. Considerations regarding compliance should be evaluated according to the company line of business. Some companies might allow corporate data to reside on users’ devices only if it is encrypted. Security settings must be controlled by IT in order to enforce those policies.</para>
      <para>The level of management in users’ devices will vary according to company policy and the BYOD infrastructure that the company will adopt. If the company establishes that it is necessary to provide full-wipe capability in order to have access to company resources, IT must enforce this setting on all monitored devices. IT also needs the ability to reset devices to the manufacturer’s defaults, wiping all personal settings and data if necessary.</para>
      <para>Use the following table to determine the monitoring options that will be required for your BYOD infrastructure.</para>
    </content>
    <sections>
      <section>
        <content />
        <sections>
          <section>
            <title>Table 15 Monitoring options—advantages and disadvantages</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Monitoring options</para>
                    </TD>
                    <TD>
                      <para>Advantages</para>
                    </TD>
                    <TD>
                      <para>Disadvantages</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Management agent installed on users’ devices.</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>More control over users’ devices.</para>
                        </listItem>
                        <listItem>
                          <para>Remote wipe capability.</para>
                        </listItem>
                        <listItem>
                          <para>Selective wipe capability.</para>
                        </listItem>
                        <listItem>
                          <para>Faster app deployment and life cycle management.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Need to install a management agent in users’ devices.</para>
                        </listItem>
                        <listItem>
                          <para>More intrusive from users’ perspective.</para>
                        </listItem>
                        <listItem>
                          <para>Requires a back-end management infrastructure to support the agent.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Management agent not installed.</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>No management agent is installed on users’ devices.</para>
                        </listItem>
                        <listItem>
                          <para>Policy enforcement available only from the app perspective (for example, ActiveSync).</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Limited options available for IT to manage devices.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para>As you can see in the preceding table, when designing the BYOD infrastructure solution, you will need an agent installed on users’ devices if you want to enforce company policy.</para>
              <para>If the company chooses to support different types of devices, you need to understand the devices’ capabilities, such as storage encryption, VPN connectivity options, and supported programming languages. Evaluate what can be implemented to be in compliance with company policies. Monitoring devices in order to meet compliance can be done by enforcing policies. Consider enabling device encryption while data is at rest in users’ devices; this can assist you in your data leakage strategy. Enforcing policies such as password unlock, password history, and strong passwords can lend similar security across on-premises and mobile devices.</para>
              <para>Compliance settings in Configuration Manager allow IT to manage the configuration and compliance of servers, laptops, desktop computers, and mobile devices in the enterprise. Consider using the default compliance settings built into Configuration Manager for mobile devices as a baseline, and from there, customize according to your company’s needs. For more information about compliance settings in Configuration Manager, see <externalLink><linkText>Introduction to Compliance Settings in Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/gg682139.aspx</linkUri></externalLink>.</para>
              <para>By using Windows Selective Wipe, IT can secure the enterprise’s corporate data that is dispersed to corporate or personal devices. Developers can create apps to use a Windows Selective Wipe policy on data and protect it on an Internet domain that is owned by the enterprise. For more information about Windows Selective Wipe, see <externalLink><linkText>Windows Selective Wipe for Device Data Management</linkText><linkUri>http://technet.microsoft.com/library/dn486874.aspx</linkUri></externalLink>.</para>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <section>
    <title>4.4.2 Reporting</title>
    <content>
      <para>Reporting device capabilities or simply understanding how these devices are behaving is fundamental to IT keeping control of known devices. Reports can be used to better understand the current environment. Here are some questions that will arise when you are trying to understand not only the environment, but also the capabilities of some mobile devices:</para>
      <list class="bullet">
        <listItem>
          <para>How many iOS devices are in use in your organization?</para>
        </listItem>
        <listItem>
          <para>Which iOS versions are those devices running?</para>
        </listItem>
        <listItem>
          <para>Which corporate apps are installed on the devices?</para>
        </listItem>
        <listItem>
          <para>Are any devices in your organization jailbroken?</para>
        </listItem>
      </list>
      <para>Consider using a management solution that can provide device inventory and customizable reports. By choosing this option, you will enable a more flexible approach for IT when they need to discover more information about users’ devices. IT must be able to have reports about all devices that were registered on-premises and in the cloud. Reporting capability for the management system can be located on-premises or in the cloud—or it can be a mix of both, which is called a hybrid solution. Use the following table to determine which reporting option is appropriate for your company.</para>
    </content>
    <sections>
      <section>
        <content />
        <sections>
          <section>
            <title>Table 16 Reporting options—advantages and disadvantages</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Reporting options</para>
                    </TD>
                    <TD>
                      <para>Advantages</para>
                    </TD>
                    <TD>
                      <para>Disadvantages</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>On-premises</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Centralized report.</para>
                        </listItem>
                        <listItem>
                          <para>Full controlled by IT.</para>
                        </listItem>
                        <listItem>
                          <para>Customizable.</para>
                        </listItem>
                        <listItem>
                          <para>Security controls managed on-premises.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Unable to natively enumerate devices that are located off-premises.</para>
                        </listItem>
                        <listItem>
                          <para>Higher administrative overhead, when compared to cloud-based solutions.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Cloud based </para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Capability to report devices that are joined to the cloud service.</para>
                        </listItem>
                        <listItem>
                          <para>Cost effective.</para>
                        </listItem>
                        <listItem>
                          <para>Reporting availability (create and view reports from anywhere).</para>
                        </listItem>
                        <listItem>
                          <para>Lower administrative cost, when compared to an on-premises solution.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Unable to natively enumerate devices that are located on-premises.</para>
                        </listItem>
                        <listItem>
                          <para>Usually requires monthly subscription to the service.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Hybrid</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Capability to report devices that are joined to the cloud service.</para>
                        </listItem>
                        <listItem>
                          <para>Cost effective.</para>
                        </listItem>
                        <listItem>
                          <para>Reporting availability (create and view reports from anywhere).</para>
                        </listItem>
                        <listItem>
                          <para>Integration with on-premises management solution.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Usually requires monthly subscription to the service.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para>By combining Windows Intune with System Center 2012 R2, you can have reporting from on-premises and cloud-based devices. Configuration Manager includes many ready-to-use, built-in reports for UDM, including reports for apps, hardware inventory, and settings management. You do not need to create custom reports or separate reports for PC and mobile-device management; these functions can be integrated.</para>
              <para>For more information about Configuration Manager reporting capabilities, see <externalLink><linkText>Introduction to Reporting in Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/gg682105.aspx</linkUri></externalLink>.</para>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <section>
    <title>4.4.3 Compute and storage</title>
    <content>
      <para>After new apps are developed and accessed remotely by users using their own devices, app performance might suffer if the solution has not been well planned. Though this design considerations guide does not intend to offer you a deeper look into performance considerations, questions about the management infrastructure must be answered:</para>
      <list class="bullet">
        <listItem>
          <para>Is the current management solution that your company uses able to manage storage and compute resources for the platform that supports the apps accessed from users’ devices?</para>
        </listItem>
        <listItem>
          <para>Does the current management solution that your company uses have the capability to increase compute and storage resources for the platform that supports app access from users’ devices according to a set of preestablished rules?</para>
        </listItem>
      </list>
      <para>If the management solution that is currently in place is not capable of addressing those two requirements, consider using a management solution that can manage compute and storage by addressing the two core requirements shown in the following table.</para>
    </content>
    <sections>
      <section>
        <content />
        <sections>
          <section>
            <title>Table 17 Compute and storage management capabilities—advantages and disadvantages</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Compute and storage management capabilities</para>
                    </TD>
                    <TD>
                      <para>Advantages</para>
                    </TD>
                    <TD>
                      <para>Disadvantages</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Resource pooling</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Able to allocate compute and storage pooling resources from different locations.</para>
                        </listItem>
                        <listItem>
                          <para>High level of availability.</para>
                        </listItem>
                        <listItem>
                          <para>More robust than solutions that are not able to leverage resource pooling.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Few management solutions are able to take advantage of resource pooling.</para>
                        </listItem>
                        <listItem>
                          <para>Initial overhead to implement could be higher if the company is not yet using cloud computing principles in its datacenter.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Elasticity</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Able to dynamically allocate compute and storage pooling resources based on demand.</para>
                        </listItem>
                        <listItem>
                          <para>High level of availability.</para>
                        </listItem>
                        <listItem>
                          <para>Easier to manage after it is implemented.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Few management solutions are able to take advantage of elasticity capability.</para>
                        </listItem>
                        <listItem>
                          <para>Initial overhead to implement could be higher if the company is not yet using cloud computing principles in its datacenter.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para>System Center 2012 R2 has the capability to use resource pooling and the elasticity to manage storage and compute. System Center 2012 R2 also integrates storage with optimization of differencing disks to reduce storage requirements by allowing a large percentage of disk data to be shared among multiple virtual disks, which optimizes storage costs. Servers that are virtualized using System Center 2012 R2 and will be consumed by apps used by remote users can take advantage of this technology.</para>
              <para>For more information about System Center 2012 R2 storage capabilities, see <externalLink><linkText>What's New in VMM in System Center 2012 R2</linkText><linkUri>http://technet.microsoft.com/library/dn246490.aspx</linkUri></externalLink>.</para>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <section>
    <title>4.4.4 Automation</title>
    <content>
      <para>Automation can be employed to remediate noncompliant devices, and IT can assign different levels of noncompliance severity. You should consider the use of automation in different areas of BYOD; for example, how should you automate the deployment of new services that will be consumed by mobile devices? And how should you automate the authorization process for mobile devices?</para>
      <para>Although you will see that all BYOD subdomains presented can take advantage of automation, the responsibility to automate resources is owned by the management subdomain. Automation can be built into the operating system; however, the management solution that the company will adopt is responsible for extending these capabilities and providing ways to alleviate daily IT tasks while monitoring and reporting results from the automation.</para>
      <para>The most powerful automation option in System Center 2012 R2 is Windows PowerShell. For more information about System Center 2012 R2 automation, see <externalLink><linkText>System Center Automation with Windows PowerShell</linkText><linkUri>http://technet.microsoft.com/library/dn507037(v=sc.20).aspx</linkUri></externalLink>. However, another option is available that provides a simpler but not very robust form of automating tasks: task sequence. Use the following table to evaluate the advantages and disadvantages of each option.</para>
    </content>
    <sections>
      <section>
        <content />
        <sections>
          <section>
            <title>Table 18 Automation options—advantages and disadvantages</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Automation options</para>
                    </TD>
                    <TD>
                      <para>Advantages</para>
                    </TD>
                    <TD>
                      <para>Disadvantages</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Windows PowerShell</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Integrated with the operating system.</para>
                        </listItem>
                        <listItem>
                          <para>More robust than task sequence.</para>
                        </listItem>
                        <listItem>
                          <para>Can be scripted.</para>
                        </listItem>
                        <listItem>
                          <para>Can use programming principles such as procedures, loops, and arrays.</para>
                        </listItem>
                        <listItem>
                          <para>Provides capabilities beyond the management platform.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Requires more technical skills in order to use it.</para>
                        </listItem>
                        <listItem>
                          <para>Depending on the task at hand, developing the initial automation script might require more time.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Task sequence</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Easy to use.</para>
                        </listItem>
                        <listItem>
                          <para>Native capability available in System Center.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Limited functionality.</para>
                        </listItem>
                        <listItem>
                          <para>Not scriptable.</para>
                        </listItem>
                        <listItem>
                          <para>Capabilities are limited to some tasks within System Center itself.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <section>
    <title>4.4.5 Deployment and provisioning</title>
    <content>
      <para>The next step is to understand the considerations for deploying and provisioning apps to remote devices. Two key questions should be answered:</para>
      <list class="bullet">
        <listItem>
          <para>How will users access apps from their own devices?</para>
        </listItem>
        <listItem>
          <para>How will IT provision these apps to users in a friendly and effective manner?</para>
        </listItem>
      </list>
      <para>The management solution that will be adopted by the company is also responsible for addressing software distribution and provisioning, regardless of the platform that the user is using. Users should be able to securely access a centralized location from their devices and install the apps that they are authorized to use to perform their work.</para>
      <para>One challenge in this area is to be able to manage different platforms and preserve a centralized management interface that allows IT to quickly identify devices that are connected on-premises and in the cloud. You must consider the adoption of a management platform that can consolidate both (on-premises and cloud), and also a management platform that is capable of managing Windows and non-Windows systems.</para>
      <para>For centralized management on-premises, you can use Configuration Manager. By using this option, IT can leverage the Enterprise Enrollment capability to enroll devices with the company’s Configuration Manager Server. For more information about how to manage devices using Configuration Manager, see <externalLink><linkText>How to Manage Mobile Devices by Using Configuration Manager and Windows Intune</linkText><linkUri>http://technet.microsoft.com/library/jj884158.aspx</linkUri></externalLink>.</para>
      <para>To manage other platforms that are not Windows-based devices, you can leverage the Windows Intune cloud service. The Windows Intune Company Portal can be used to enroll, manage, and install licensed apps. Users can have easy access to apps and install them on their devices. For more information about Windows Intune, see <externalLink><linkText>Windows Intune Direct Management</linkText><linkUri>http://technet.microsoft.com/library/jj733620.aspx</linkUri></externalLink>. For more information about the Windows Intune Company Portal, see <externalLink><linkText>The Windows Intune Company Portal</linkText><linkUri>http://technet.microsoft.com/library/jj676642.aspx</linkUri></externalLink>.</para>
      <para>Though these are two distinct options, you can integrate both in order to provide app deployment and provisioning from a single location. Use the following table to identify which option fits your BYOD design.</para>
    </content>
    <sections>
      <section>
        <content />
        <sections>
          <section>
            <title>Table 19 Design requirements and associated deployment and provisioning options</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Design requirements</para>
                    </TD>
                    <TD>
                      <para>Deployment and provisioning options</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Deploy and provision apps to devices located on-premises only.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <para>Microsoft System Center 2012</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Deploy and provision apps to devices located outside the company.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <para>Windows Intune</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Deploy and provision apps to non-Windows devices.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <para>Windows Intune</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Deploy and provision apps to devices located on-premises only.</para>
                        </listItem>
                        <listItem>
                          <para>Deploy and provision apps to devices located outside the company.</para>
                        </listItem>
                        <listItem>
                          <para>Deploy and provision apps to non-Windows devices.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <para>Windows Intune integrated with Configuration Manager</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para>For more information about the integration between Configuration Manager and Windows Intune, see <externalLink><linkText>How to Manage Mobile Devices by Using Configuration Manager and Windows Intune</linkText><linkUri>http://technet.microsoft.com/library/jj884158.aspx</linkUri></externalLink>.</para>
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
            <link xlink:href="a6319952-e9cd-4308-b9b9-b2e6005e6506" />
          </para>
        </listItem>
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
            <link xlink:href="4b871c74-fec8-45e2-8b45-6ef0e62f7cc6" />
          </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>