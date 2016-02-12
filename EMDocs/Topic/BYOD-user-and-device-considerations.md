---
title: BYOD user and device considerations
ms.custom: na
ms.reviewer: na
ms.service: multiple
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d1653116-3922-40d3-bc4f-3d845b6aaecb
author: YuriDio
---
# BYOD user and device considerations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The first user and device issue you need to address is how the technologies in place will affect the user experience when securely accessing company resources. Addressing the user experience across different devices can be challenging, not only from a security point of view, but also from the perspective of app development. The communication channel between the device and company resources must be considered for the proper level of network security required to avoid data leakage while data is in transit.</para>
    <para>The sections that follow are based on components for the Users and Devices subdomain shown in Figure 1 in <link xlink:href="bc4d8a1d-9b5b-4a26-8620-d5917871e34c">BYOD Problem Definition</link>, which is the conceptual diagram for the BYOD problem domain.</para>
  </introduction>
  <section>
    <title>4.2.1 Profiles</title>
    <content>
      <para>Understanding users’ needs and requirements to perform their jobs from the devices of their choice is essential when designing your BYOD infrastructure solution. Not all users will have the same requirements; some users will always access data on-premises, and policy enforcement for them can be different. Remote workers will be accessing company data from a variety of locations and circumstances. You must consider the options available to address these needs. Determine each user’s profile according to their needs:</para>
      <list class="bullet">
        <listItem>
          <para>Do they need to access apps only?</para>
        </listItem>
        <listItem>
          <para>Do they need to access folders located on a file server?</para>
        </listItem>
      </list>
      <para>Though the following table suggests a set of requirements for each user’s profile, you can customize this table by adding or removing requirements based on your company’s needs. The rationale of each profile category compared to what it should contain is based on the resources it consumes. For example, the light profile means low utilization of resources on the device and low network requirements. Ensure that you understand each user’s profile footprint; this will allow you to make more appropriate choices throughout the rest of the design process.</para>
      <para>Use the following table to determine the user profile type and common capabilities that should be available.</para>
    </content>
    <sections>
      <section>
        <content/>
        <sections>
          <section>
            <title>Table 6 User profile types</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>User profile types</para>
                    </TD>
                    <TD>
                      <para>Requirements</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Light</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Access to web-based apps on-premises or in the cloud.</para>
                        </listItem>
                        <listItem>
                          <para>Access to corporate mobile apps.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Moderate</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Access to web-based apps on-premises or in the cloud.</para>
                        </listItem>
                        <listItem>
                          <para>Access to corporate mobile apps.</para>
                        </listItem>
                        <listItem>
                          <para>Access to virtualized business apps.</para>
                        </listItem>
                        <listItem>
                          <para>Access to files located in file servers on-premises.</para>
                        </listItem>
                        <listItem>
                          <para>Access to files located in the cloud.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Heavy</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Access to web-based apps on-premises or in the cloud.</para>
                        </listItem>
                        <listItem>
                          <para>Access to corporate mobile apps.</para>
                        </listItem>
                        <listItem>
                          <para>Access to files located in file servers on-premises.</para>
                        </listItem>
                        <listItem>
                          <para>Access to files located in the cloud.</para>
                        </listItem>
                        <listItem>
                          <para>Access to computers using Remote Desktop.</para>
                        </listItem>
                        <listItem>
                          <para>Access to other computers located on-premises.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para>You will need to determine which user profile is more suitable for your BYOD infrastructure solution. You might consider establishing multiple users’ profiles according to their job requirements. Ideally, the technology that you use to implement your BYOD infrastructure solution should be able accommodate all user profiles, because the requirements might vary according to each individual. Refer to <externalLink><linkText>4.2.3 Network</linkText><linkUri>http://technet.microsoft.com/library/dn656901.aspx#BKMK_423</linkUri></externalLink> for more information about the network options available.</para>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <section>
    <title>4.2.2 Device</title>
    <content>
      <para address="BKMK_422">IT must determine if it requires knowledge of devices. For example, one BYOD scenario is hourly employees checking their time sheets or reviewing corporate notices or social sites when out of the office. In many organizations, these requirements were traditionally LAN-only services, but now they may be opened to personal devices. Does someone checking their schedule require device management? Understanding the devices’ footprints will help IT to:</para>
      <list class="bullet">
        <listItem>
          <para>Track which user is registering devices: a user registering a number of devices every week might indicate suspicious activity.</para>
        </listItem>
        <listItem>
          <para>Understand devices’ footprints: knowing which types of devices are in use on the network can help IT support those devices.</para>
        </listItem>
      </list>
      <para>Consider having the link between the device and the user stored in a central location that can be later used by IT when performing auditing or reporting. IT needs to move from an unknown device state to a known device state to enable BYOD. This will allow IT to have more control of devices that are corporate assets. Usually, companies approach this requirement in three different ways:</para>
      <list class="bullet">
        <listItem>
          <para>Approach 1: Installing a management agent in each user’s device.</para>
        </listItem>
        <listItem>
          <para>Approach 2: Registering each device in a central repository without installing a management agent.</para>
        </listItem>
        <listItem>
          <para>Approach 3 (1+2): Registering and installing a management agent in each user’s device.</para>
        </listItem>
      </list>
      <para>The following table lists the advantages and disadvantages of each of these approaches.</para>
    </content>
    <sections>
      <section>
        <content/>
        <sections>
          <section>
            <title>Table 7 Unknown-to-known device options—advantages and disadvantages</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Unknown-to-known device options</para>
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
                      <para>Installing a management agent in each user’s device.</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>More control of users’ devices. </para>
                        </listItem>
                        <listItem>
                          <para>Remote wipe capability. </para>
                        </listItem>
                        <listItem>
                          <para>App deployment capability. </para>
                        </listItem>
                        <listItem>
                          <para>More security controls available for IT to control the device. </para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Requires users to install a management agent.</para>
                        </listItem>
                        <listItem>
                          <para>Management agent must be installable on different devices’ platforms.</para>
                        </listItem>
                        <listItem>
                          <para>More administrative overhead.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Registering each device in a central repository without installing a management agent.</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>No management agent required.</para>
                        </listItem>
                        <listItem>
                          <para>Less administrative overhead.</para>
                        </listItem>
                        <listItem>
                          <para>Second-factor authentication of devices.</para>
                        </listItem>
                        <listItem>
                          <para>Validation of the link between users and devices.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Less control of users’ devices.</para>
                        </listItem>
                        <listItem>
                          <para>Fewer security controls available.</para>
                        </listItem>
                        <listItem>
                          <para>Lack of capability to perform remote wipe and app deployment.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Registering and installing a management agent in each user’s device.</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>More control of users’ devices. </para>
                        </listItem>
                        <listItem>
                          <para>Remote wipe capability. </para>
                        </listItem>
                        <listItem>
                          <para>App deployment capability. </para>
                        </listItem>
                        <listItem>
                          <para>More security controls.</para>
                        </listItem>
                        <listItem>
                          <para>Second-factor authentication of devices.</para>
                        </listItem>
                        <listItem>
                          <para>Validation of the link between users and devices.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Requires users to install a management agent.</para>
                        </listItem>
                        <listItem>
                          <para>Management agent must be installable on different devices’ platforms.</para>
                        </listItem>
                        <listItem>
                          <para>More administrative overhead.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para>In Windows Server 2012 R2, the new concept of <externalLink><linkText>Workplace Join</linkText><linkUri>http://technet.microsoft.com/library/dn280945.aspx</linkUri></externalLink> allows IT to move the device from an unknown state to a known state. The device can also be used as second-factor authentication and single sign-on to workplace resources and apps. Workplace Join is natively available in Windows 8.1, but it is also supported in other platforms such as iOS and Android. Workplace Join leverages the Device Registration Service (DRS). For more information about DRS, read <externalLink><linkText>Configure a federation server with Device Registration Service</linkText><linkUri>http://technet.microsoft.com/library/dn486831.aspx</linkUri></externalLink>. Workplace Join is new technology and works with specific use cases. See <externalLink><linkText>Secure access to company resources from any location on any device</linkText><linkUri>http://technet.microsoft.com/library/dn550982.aspx</linkUri></externalLink> for more information about a solution that leverages Workplace Join with single sign-on.</para>
              <para>If you consider using DRS, understand that this feature does not provide management capabilities. If your company needs more security controls in order to have more options available to control users’ devices, consider using DRS in conjunction with <externalLink><linkText>mobile device enrollment</linkText><linkUri>http://technet.microsoft.com/library/jj733620.aspx</linkUri></externalLink> as the management agent solution. However, if you choose this option, you must have a Windows Intune subscription. For more information about Windows Intune, see the <externalLink><linkText>Windows Intune Getting Started Guide</linkText><linkUri>http://technet.microsoft.com/library/hh441719.aspx</linkUri></externalLink>.</para>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <section>
    <title>4.2.3 Network</title>
    <content>
      <para address="BKMK_423">Corporate network access from the user and device perspective must be addressed. How will users access company data while using their own devices? Most BYOD infrastructure solutions focus only minimally on remote access from users’ devices; however, from a people-centric approach, you must consider where users are physically located. You should focus on not only remote access, but also how users will access the data while on-premises. In addition, you will need to consider regulatory issues specific to your organization's geopolitical alignment. For example, how can users that are physically located in a different country have personalized network access?</para>
      <para>If your company has resources in the public cloud that will be accessible via the Internet from users’ devices, you must consider how traffic will be handled. Consider using encryption while the data is in flight from users’ devices to the cloud provider. When users are accessing internal resources, you should also use data encryption.</para>
      <para>The following table describes network connectivity options, and the advantages and disadvantages of each.</para>
    </content>
    <sections>
      <section>
        <content/>
        <sections>
          <section>
            <title>Table 8 Network connectivity options—advantages and disadvantages</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Connectivity options</para>
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
                      <para>Traditional VPN</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Mature technology. </para>
                        </listItem>
                        <listItem>
                          <para>Easy to configure. </para>
                        </listItem>
                        <listItem>
                          <para>Widely available on many platforms. </para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Protocol overhead from VPN and encryption protocols. </para>
                        </listItem>
                        <listItem>
                          <para>Must be launched before launching apps.</para>
                        </listItem>
                        <listItem>
                          <para>Requires user interaction to establish the connection.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Microsoft Direct Access</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Seamless experience for users (always on).</para>
                        </listItem>
                        <listItem>
                          <para>Supports selected server access and IPsec authentication with an Internet network server.</para>
                        </listItem>
                        <listItem>
                          <para>Supports end-to-end authentication and encryption.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Requires an on-premises infrastructure to support this capability.</para>
                        </listItem>
                        <listItem>
                          <para>Troubleshooting can be challenging.</para>
                        </listItem>
                        <listItem>
                          <para>Higher administrative overhead.</para>
                        </listItem>
                        <listItem>
                          <para>Not available on all platforms.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Automatic Trigger VPN</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Easy to configure. </para>
                        </listItem>
                        <listItem>
                          <para>Connection to on-premises server is launched when an app needs access to corporate resources.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Protocol overhead from VPN and encryption protocols. </para>
                        </listItem>
                        <listItem>
                          <para>Not available on all platforms.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Remote Desktop with VDI</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Seamless user experience.</para>
                        </listItem>
                        <listItem>
                          <para>More control over the desktop (hardening).</para>
                        </listItem>
                        <listItem>
                          <para>Widely available on many platforms.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Requires an on-premises infrastructure to support this capability.</para>
                        </listItem>
                        <listItem>
                          <para>Capacity planning for network, storage and compute must be carefully performed to avoid a performance bottleneck.</para>
                        </listItem>
                        <listItem>
                          <para>Each device requires a remote access client app.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Web Access</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Widely available on many platforms.</para>
                        </listItem>
                        <listItem>
                          <para>Encryption available using HTTPS.</para>
                        </listItem>
                        <listItem>
                          <para>Mature technology.</para>
                        </listItem>
                        <listItem>
                          <para>Easy to configure.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Requires certificates.</para>
                        </listItem>
                        <listItem>
                          <para>If the certificate infrastructure is internal, it requires a PKI infrastructure.</para>
                        </listItem>
                        <listItem>
                          <para>Requires an edge infrastructure to securely publish apps.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para>After you define the design for remote network access, consider how user-owned devices will connect to your network while they are physically connected to it. Users who bring their devices to work will likely be using Wi-Fi capabilities to connect to corporate resources. You should consider using network segmentation (physical or logical) for users’ devices in order to isolate them. You can also segment the devices that will connect to the Wi-Fi network according to the platform they run. Also consider how to secure their communication and authorization while they are on-premises accessing corporate resources.</para>
              <para>You can choose a physical segmentation on your wireless access point and network components (switches and routers) to isolate users who are connecting by using their own devices. You can also implement this type of segmentation by using <externalLink><linkText>Wi-Fi Profiles in Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/dn261221.aspx</linkUri></externalLink>. A wide range of security settings is available, such as certificates for server validation and client authentication that have been provisioned by using <externalLink><linkText>Configuration Manager certificate profiles</linkText><linkUri>http://technet.microsoft.com/library/dn270540.aspx</linkUri></externalLink>.</para>
            </content>
          </section>
          <section>
            <title>Table 9 Wi-Fi network segmentation options—advantages and disadvantages</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Wi-Fi network segmentation options</para>
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
                      <para>Physical segmentation</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Lower-level security segmentation.</para>
                        </listItem>
                        <listItem>
                          <para>Relatively easy to configure. </para>
                        </listItem>
                        <listItem>
                          <para>Abstracts itself from the platform (operating system). </para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Manageability may vary according to the vendor.</para>
                        </listItem>
                        <listItem>
                          <para>Integration among different hardware vendors could be challenging.</para>
                        </listItem>
                        <listItem>
                          <para>Higher cost to implement and maintain.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Logical segmentation (Wi-Fi profiles)</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Seamless experience for users.</para>
                        </listItem>
                        <listItem>
                          <para>Easier to manage (when compared to physical segmentation).</para>
                        </listItem>
                        <listItem>
                          <para>Lower cost to implement (when compared to physical segmentation).</para>
                        </listItem>
                        <listItem>
                          <para>Abstracts itself from the hardware used to connect devices.</para>
                        </listItem>
                        <listItem>
                          <para>Supports multiple platforms (operating systems).</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Does not provide the lower-level security segmentation that the hardware solution does.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Dynamic Segmentation</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Wireless Access Points use a common infrastructure and SSID.</para>
                        </listItem>
                        <listItem>
                          <para>End-user and device attributes dynamically provision network access.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Requires IPsec for Implementation using Microsoft <externalLink><linkText>Network Access Protection (NAP)</linkText><linkUri>http://technet.microsoft.com/library/cc731276(v=ws.10).aspx</linkUri></externalLink>, which can be a problem in a BYOD scenario that requires support for “any device.”</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para>For more information about Wi-Fi Profiles in Configuration Manager, see <externalLink><linkText>Introduction to Wi-Fi Profiles in Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/dn261224.aspx</linkUri></externalLink>.</para>
              <para>Network location plays an important role for user and device considerations. You can leverage multi-factor access control in AD FS to enable per-application authorization policies, whereby you can permit or deny access based on user, device, and network location. See <externalLink><linkText>Manage Risk with Multi-Factor Access Control</linkText><linkUri>http://technet.microsoft.com/library/dn280936.aspx</linkUri></externalLink> for more information about how to set up an environment to validate this capability.</para>
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
            <link xlink:href="a6319952-e9cd-4308-b9b9-b2e6005e6506"/>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="dcccd316-d550-4db8-bc7e-0b8e66a275a8"/>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="181eb917-119d-4e56-8ead-1182b1dc5cab"/>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="bf0d4210-5edc-4ad7-bcb5-372099049630"/>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="4b871c74-fec8-45e2-8b45-6ef0e62f7cc6"/>
          </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics/>
</developerConceptualDocument>
