---
title: Envisioning the BYOD Infrastructure Solution
ms.custom: na
ms.reviewer: na
ms.service: multiple
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ecb6271f-8f38-42bd-aae7-10ba5e17a5f1
author: YuriDio
---
# Envisioning the BYOD Infrastructure Solution
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>After clearly defining the BYOD problem you are trying to solve, you can begin to define a solution to the problem and define detailed requirements for the solution.</para>
  </introduction>
  <section>
    <title>3.1 Solution definition</title>
    <content>
      <para>To solve the problems previously identified and assist organizations to encourage users to bring their own devices to work and access corporate data with their devices, a company must switch from a device-centric IT approach to a people-centric IT approach. The design considerations in this document can be used when defining your own BYOD infrastructure solution to: </para>
      <list class="bullet">
        <listItem>
          <para>Provide users the flexibility to use their own devices to access corporate apps and data. </para>
        </listItem>
        <listItem>
          <para>Manage devices that are accessing corporate resources when on-premises and from the cloud. </para>
        </listItem>
        <listItem>
          <para>Enable an IT department to protect corporate data stored on devices by using encryption and rights management to safeguard against unauthorized local access, and remotely wiping corporate data over the Internet when a device is lost or retired, or during an employee’s termination process.</para>
        </listItem>
        <listItem>
          <para>Provide users a common identity when they are accessing resources when on-premises and from the cloud.</para>
        </listItem>
        <listItem>
          <para>Enable IT to manage multiple identities and keep information in sync across different environments.</para>
        </listItem>
        <listItem>
          <para>Enable enterprise authentication services such as multi-factor authentication and single sign-on.</para>
        </listItem>
        <listItem>
          <para>Provide for information security and compliance activities such as attestation of compliance. </para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>3.2 Solution requirements</title>
    <content>
      <para>Before enabling users to bring their own devices and have access to a company’s resources, the existing infrastructure’s technical capabilities must be revised. The goal of this revision is to understand if the solution requirements for this new model are already in place or if new technologies must be introduced to resolve the problem. You must first define a number of requirements for doing so, as well as the constraints for the environment. Some of the requirements and constraints are defined by the consumers of the capabilities; others are defined by your existing environment, in terms of existing technical capabilities, services, policies, and processes.</para>
      <para>Determining the requirements, constraints, and design to allow users to have access to company resources from their managed devices is a key process. Initial requirements, coupled with the constraints of your environment, may drive an initial design that cannot meet all of the initial requirements, necessitating changes to the initial requirements and subsequent design. Multiple iterations through the definition of requirements and the solution design are necessary before finalizing the requirements and the design. Therefore, do not expect that your first run through this document will be your last. You might find that decisions you make early in the process exclude more preferred options made available to you later in the process.</para>
      <para>The considerations regarding the BYOD problem domain presented in this guide will be divided into subdomains. Each subdomain will have a collection of components. The subdomains for the BYOD problem domain presented in this guide are:</para>
      <list class="bullet">
        <listItem>
          <para>Users and devices</para>
        </listItem>
        <listItem>
          <para>Data access and protection</para>
        </listItem>
        <listItem>
          <para>Management</para>
        </listItem>
        <listItem>
          <para>Apps</para>
        </listItem>
      </list>
      <para>Your answers to the questions in the next sections build a comprehensive list of requirements for enabling users to access company resources from their devices, which can be managed by IT while keeping the data protected. These questions are not vendor specific and can be applied to any BYOD infrastructure solution. </para>
    </content>
    <sections>
      <section>
        <title>3.2.1 User and device requirements</title>
        <content>
          <para>Before enabling users to access company resources from their devices, answer the questions in the sections that follow by working with the consumers of these resources in your environment and with your IT department. Figure 2 shows the interactions between users and devices, with the ultimate goal of accessing and consuming data. Note that the diagram does not address geographical location. Although geographical location is an important consideration (and it will be covered later in this document), the intent of Figure 2 is to illustrate the core components of users and devices. Design considerations must be made to enable this communication to occur.</para>
          <para>
            <mediaLinkInline>
              <image xlink:href="c369f274-9781-4043-b0a1-cd973976cc76" />
            </mediaLinkInline>
          </para>
          <para>
            <legacyBold>Figure  SEQ Figure \* ARABIC 2 Interactions between users and devices</legacyBold>
          </para>
          <para>The outcome of this process is a clear definition of the functionality to be provided. The following table contains questions about users and devices that you will need to answer in order to formulate the requirements for your solution design.</para>
        </content>
        <sections>
          <section>
            <content />
            <sections>
              <section>
                <title>Table 1 User and device requirements—questions to ask</title>
                <content>
                  <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                    <thead>
                      <tr>
                        <TD>
                          <para>User and device requirements</para>
                        </TD>
                        <TD>
                          <para>Questions to ask</para>
                        </TD>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <TD>
                          <para>Profile</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>What are the types of user profiles that you have in your enterprise (such as remote workers, occasional travelers, and full-time home-office workers)?</para>
                            </listItem>
                            <listItem>
                              <para>Do all users have the same requirements to perform their jobs?</para>
                            </listItem>
                            <listItem>
                              <para>Do you have a matrix that establishes users’ needs according to jobs/roles? </para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>Devices</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>What are the types of devices that users will be bringing (such as smartphones, tablets, and laptops)? </para>
                            </listItem>
                            <listItem>
                              <para>Do you plan to provide remote wipe capability to all types of devices? </para>
                            </listItem>
                            <listItem>
                              <para>Do you plan to manage users’ devices? </para>
                            </listItem>
                            <listItem>
                              <para>Do you have any scenario in which it is not necessary to manage the device, but you will need to track who owns the device anyway?</para>
                            </listItem>
                            <listItem>
                              <para>Do you plan to authenticate devices according to the users who brought the devices to the company? </para>
                            </listItem>
                            <listItem>
                              <para>Does your company follow any compliance requirements that must be applied to all devices that will potentially have access to your company’s data?</para>
                            </listItem>
                            <listItem>
                              <para>Does your company have a policy in place to deal with stolen devices?</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>Network</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Does your company have any resources in the cloud that will be accessible via the Internet from users’ devices? </para>
                            </listItem>
                            <listItem>
                              <para>Does your company have policy restrictions for users accessing the company’s data from different geographical locations?</para>
                            </listItem>
                            <listItem>
                              <para>Do you plan to provide network encryption to allow users to access company resources from their devices? </para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, does the current list of supported devices support the encryption protocol that will be used?</para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>Do you have network segmentation in place? </para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, will you have all users’ devices connected to a separate network to isolate them from the production network? </para>
                                </listItem>
                              </list>
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
        <title>3.2.2 Data access and protection requirements</title>
        <content>
          <para>One of the most critical elements when enabling users to access company resources from their own devices is to preserve the company’s data and keep that information secure. Your company might have a variety of compliance requirements that must be in place to ensure data is secure no matter where it is located. Figure 3 shows the interactions between users and devices when accessing data and which components must be considered for this subdomain.</para>
          <para>
            <mediaLinkInline>
              <image xlink:href="c244fccd-7618-4792-96e0-6d67a6897aa6" />
            </mediaLinkInline>
          </para>
          <para>
            <legacyBold>Figure 3 Interactions between users and devices when accessing data</legacyBold>
          </para>
          <para>The following table contains questions about data access and protection that you will need to answer in order to formulate the requirements for your solution design.</para>
        </content>
        <sections>
          <section>
            <content />
            <sections>
              <section>
                <title>Table 2 Direct access and protection requirements—questions to ask</title>
                <content>
                  <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                    <thead>
                      <tr>
                        <TD>
                          <para>Data access and protection requirements</para>
                        </TD>
                        <TD>
                          <para>Questions to ask</para>
                        </TD>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <TD>
                          <para>Storage</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>While the data is at rest in the datacenter, do you have encryption enabled? </para>
                            </listItem>
                            <listItem>
                              <para>Will your company provide offline access to data located in the datacenter’s storage (in other words, will you sync data to users’ devices)? </para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, does your company want to keep the same data format (encrypted or plain) on users’ devices? </para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>Do you have any storage quota currently implemented in your system on a per-user basis? </para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, do you plan to increase this quota for users who are authorized to user their own devices?</para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>Does your company policy allow users to use external storage drives on corporate computers?</para>
                              <list class="bullet">
                                <listItem>
                                  <para>If not, do you plan to extend this policy for users who are accessing data from their own devices?</para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>Does your company policy allow users to use cloud-based storage from corporate computers?</para>
                              <list class="bullet">
                                <listItem>
                                  <para>If not, do you plan to extend this policy for users who are accessing data from their own devices?</para>
                                </listItem>
                              </list>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>Network</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Do you have any type of network encryption on-premises? </para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, is it limited to server–to-server communication, or is the entire network encrypted?</para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>Do you plan to have different requirements for data access while users are physically outside the corporate network and when they are physically inside the corporate network? </para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, what are the requirements? </para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>Do you foresee any increase in network activity when you enable users to use their own devices on the corporate network? </para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, is your current network capacity able to handle this new traffic? </para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>Does your company use any network inspection mechanisms? </para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, do you plan to extend this capability for users who are bringing their own devices and connecting to the corporate network?</para>
                                </listItem>
                              </list>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>Directory</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Does your company use a single user directory, or does it have multiple providers? </para>
                            </listItem>
                            <listItem>
                              <para>Is your company directory located on-premises, in the cloud, or in both locations (hybrid)? </para>
                            </listItem>
                            <listItem>
                              <para>When users are accessing apps from their devices, against which directory will they be authenticating? </para>
                            </listItem>
                            <listItem>
                              <para>Does your company plan to federate authentication between on-premises and cloud services?</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>Authentication</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Which type of authentication is used today in your environment?</para>
                            </listItem>
                            <listItem>
                              <para>Do you plan to preserve this authentication method, or do you want to enhance it before enabling users to use their own devices to access company resources?</para>
                            </listItem>
                            <listItem>
                              <para>Do you have multi-factor authentication in place in your current environment? </para>
                            </listItem>
                            <listItem>
                              <para>Do you plan to authenticate users’ devices or users only?</para>
                            </listItem>
                            <listItem>
                              <para>Do you plan to enable single sign-on for apps that are accessed from users’ devices?</para>
                            </listItem>
                            <listItem>
                              <para>Do you plan to leverage cloud resources to provide an additional level of authentication for remote users?</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>Authorization</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>In the current environment, after users are authenticated, do you have any other controls in place to validate if users are authorized to access the information they are requesting?</para>
                            </listItem>
                            <listItem>
                              <para>Do you plan to provide conditional access based on a set of predefined rules for remote users?</para>
                            </listItem>
                            <listItem>
                              <para>Does your company perform authorization enforcement for data located on-premises or in the cloud?</para>
                            </listItem>
                            <listItem>
                              <para>Does your company use the <externalLink><linkText>principle of need to know</linkText><linkUri>http://en.wikipedia.org/wiki/Need_to_know</linkUri></externalLink> in order to authorize data access?</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>Policy and Compliance</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Does your company have policies in place to define how data access is classified? </para>
                            </listItem>
                            <listItem>
                              <para>Does your company need to be compliant with any regulations for data handling and privacy?</para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, how do these regulations drive the current data access policies for on-premises resources? </para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>Does your company have policies in place for <externalLink><linkText>Mobile Device Management (MDM)</linkText><linkUri>http://en.wikipedia.org/wiki/Mobile_device_management</linkUri></externalLink> and <externalLink><linkText>Mobile Application Management (MAM</linkText><linkUri>http://en.wikipedia.org/wiki/Mobile_application_management</linkUri></externalLink>)?</para>
                            </listItem>
                            <listItem>
                              <para>Does your company have policies in place for device confiscation in case of litigation or criminal investigation?</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                </content>
              </section>
              <section>
                <title>3.2.3 Management requirements</title>
                <content>
                  <para>Device management is one of the foundations of any people-centric strategy, and it must be evaluated against a company’s requirements. Depending on the maturity level of the company, a management system might be in place already that will need to be expanded to cover the BYOD scenarios that the company is adopting. Figure 4 shows management interactions when managing users, devices, and data. Considerations must be made for each component of the Management subdomain.</para>
                  <para>
                    <mediaLinkInline>
                      <image xlink:href="92e4e3f4-d12b-4375-989f-76ab01c3fe3f" />
                    </mediaLinkInline>
                  </para>
                  <para>
                    <legacyBold>Figure  SEQ Figure \* ARABIC 4 Management interactions when managing users, devices, and data</legacyBold>
                  </para>
                  <para>When considering management capability requirements, you should start by asking the questions in the following table. </para>
                </content>
              </section>
              <section>
                <title>Table 3 Management requirements—questions to ask</title>
                <content>
                  <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                    <thead>
                      <tr>
                        <TD>
                          <para>Management requirements</para>
                        </TD>
                        <TD>
                          <para>Questions to ask</para>
                        </TD>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <TD>
                          <para>Monitoring</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Does your company need to monitor compliance settings such as password, camera, and encryption on users’ devices? </para>
                            </listItem>
                            <listItem>
                              <para>Does your company want to differentiate device ownership (company-owned devices versus user-owned devices)?</para>
                            </listItem>
                            <listItem>
                              <para>Does your company want to allow users to reset their passwords from their own devices?</para>
                            </listItem>
                            <listItem>
                              <para>Does your company need to have logging capability built into the management system?</para>
                            </listItem>
                            <listItem>
                              <para>Does your company need auditing capabilities built into the management system?</para>
                            </listItem>
                            <listItem>
                              <para>Does your company aggregate this type of logging in a single repository?</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>Reporting</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Does your company need reporting capabilities for its BYOD model?</para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, which types of reports (such as updates, software installed, and inventory) will be necessary?</para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>Does the management system in place have these reporting requirements?</para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, is it possible to customize them?</para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>Is there any differentiation in the reporting requirements for domain-joined devices and non-domain joined devices?</para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, what are the requirements for each scenario?</para>
                                </listItem>
                              </list>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>Configuration</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Does your company need a management system that requires users’ devices to be domain-joined in order to be managed?</para>
                            </listItem>
                            <listItem>
                              <para>Does your company need a management system that integrates with your current directory?</para>
                            </listItem>
                            <listItem>
                              <para>Does your company need a management system that manages just apps, or should it also manage the operating system running on users’ devices?</para>
                            </listItem>
                            <listItem>
                              <para>Does your company need a management system that can enforce policies on users’ devices?</para>
                            </listItem>
                            <listItem>
                              <para>Does your company need a management system that can be integrated with cloud services?</para>
                            </listItem>
                            <listItem>
                              <para>Does your company plan to perform selective wipe in case a user no longer needs access to the apps that were installed?</para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, does the management system in place support selective wipe capability?</para>
                                </listItem>
                              </list>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>Compute</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>What are the compute capabilities required to run the management system on back-end servers?</para>
                            </listItem>
                            <listItem>
                              <para>What are the compute capabilities required to run the management system on users’ devices?</para>
                            </listItem>
                            <listItem>
                              <para>Does the management system support leveraging cloud capability to expand on-premises compute resources?</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>Storage</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>What are the storage requirements to run the management system on back-end servers?</para>
                            </listItem>
                            <listItem>
                              <para>What are the storage requirements to run the management system on users’ devices?</para>
                            </listItem>
                            <listItem>
                              <para>Does the management system support leveraging cloud capabilities to expand on-premises storage resources?</para>
                            </listItem>
                            <listItem>
                              <para>Does the company need to manage external storage drives that are added to users’ devices?</para>
                            </listItem>
                            <listItem>
                              <para>Does the company need a management system that is also capable of integrating with cloud storage?</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>Automation</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Which operations does your company plan to automate for BYOD scenarios?</para>
                            </listItem>
                            <listItem>
                              <para>What are the automation requirements for the management system that your company plans to adopt?</para>
                            </listItem>
                            <listItem>
                              <para>Does your current management system support built-in command-line or script automation?</para>
                            </listItem>
                            <listItem>
                              <para>Does your company have a management system that integrates with cloud services and provides automation capabilities?</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>Deployment and Provisioning</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>What are the requirements for management agent deployment for your current management system?</para>
                            </listItem>
                            <listItem>
                              <para>Will any services be offered to remote users that can be instantly provisioned via a portal?</para>
                            </listItem>
                            <listItem>
                              <para>Are personal devices registered with the company by IT, or are they registered personally?</para>
                            </listItem>
                            <listItem>
                              <para>Will a plan be in place to allow users to provision services using their own devices?</para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, does the management system natively enable users to perform this operation from their devices?</para>
                                </listItem>
                              </list>
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
        <title>3.2.4 App requirements</title>
        <content>
          <para>Every organization uses a variety of technical capabilities to enable their workforce to perform their tasks in an optimized manner, and most of the time, the primary tool is an app. These capabilities could be combined in a multiplatform approach in which different technologies are used to achieve a certain goal or by creating a custom app that will be able to perform a task or automate certain processes. Apps are important to consider when designing the BYOD strategy. Users will use different form factors to consume these apps; therefore, you need to consider the variety of capabilities that these apps should support. Figure 5 shows how users and devices use apps to consume data and the considerations for each component of the Apps subdomain.</para>
          <para>
            <mediaLinkInline>
              <image xlink:href="c2f2b786-a8a1-4032-a035-638db0ecc72e" />
            </mediaLinkInline>
          </para>
          <para>
            <legacyBold>Figure  SEQ Figure \* ARABIC 5 How users and devices use apps to consume data</legacyBold>
          </para>
          <para>The following table contains questions about app requirements that you will need to answer in order to formulate the requirements for your solution design.</para>
        </content>
        <sections>
          <section>
            <content />
            <sections>
              <section>
                <title>Table 4 App requirements—questions to ask</title>
                <content>
                  <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                    <thead>
                      <tr>
                        <TD>
                          <para>App requirements</para>
                        </TD>
                        <TD>
                          <para>Questions to ask</para>
                        </TD>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <TD>
                          <para>Experience</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Do you plan to preserve the same user experience, regardless of the devices on which apps will run? </para>
                            </listItem>
                            <listItem>
                              <para>Do the apps require Internet access from users’ devices? </para>
                            </listItem>
                            <listItem>
                              <para>Do the apps require input via keyboard?</para>
                            </listItem>
                            <listItem>
                              <para>Do the apps collect any user information, such as geographic location?</para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, do the apps inform users about privacy issues and data collection while being installed?</para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>Do the apps require integration with cloud services?</para>
                            </listItem>
                            <listItem>
                              <para>Which types of apps do you plan to make available for BYOD users (such as web-based apps and modern apps)?</para>
                            </listItem>
                            <listItem>
                              <para>Were the apps developed to run on a specific operating system, or are they capable of running on any operating system?</para>
                            </listItem>
                            <listItem>
                              <para>Do you plan to enable users to use apps via Remote Desktop from their own devices?</para>
                            </listItem>
                            <listItem>
                              <para>Do the apps require full-time access to corporate resources, or can they run in offline mode?</para>
                            </listItem>
                            <listItem>
                              <para>Do the apps have any integration with social networks?</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>Platform</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>What type of back-end platform is necessary for these apps to run? </para>
                            </listItem>
                            <listItem>
                              <para>Do you foresee any increase in activity with the BYOD adoption that will require upgrading the back-end platform for the apps that you plan to allow remote users to use?</para>
                            </listItem>
                            <listItem>
                              <para>Is the back-end platform that will support the apps located in the same infrastructure as the other servers?</para>
                            </listItem>
                            <listItem>
                              <para>Is the platform that will support these apps fully on-premises, or are there also servers located in the cloud?</para>
                            </listItem>
                            <listItem>
                              <para>If there are servers located in the cloud, how does the traffic flow between the apps (running in users’ devices) and the back end?</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>Deployment</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Do you know which apps will be available to BYOD users? </para>
                            </listItem>
                            <listItem>
                              <para>How do you plan to deploy these apps to users’ devices?</para>
                            </listItem>
                            <listItem>
                              <para>What are the deployment options for these apps?</para>
                            </listItem>
                            <listItem>
                              <para>Does the installation requirement vary according to the target device, or is it the same?</para>
                            </listItem>
                            <listItem>
                              <para>Do the apps require any mobile device management (MDM) in order to work properly?</para>
                            </listItem>
                            <listItem>
                              <para>Will you use the Windows Store or any other app store to deploy these apps?</para>
                            </listItem>
                            <listItem>
                              <para>Do the apps install any digital certificates during the deployment?</para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, which certificate authority will be used (private or public)?</para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>Do users need to be physically connected to the corporate network to perform the installation, or is it possible to install the app via the Internet?</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>Storage</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>How much space in a target device is necessary in order to install each app? </para>
                            </listItem>
                            <listItem>
                              <para>Do the apps encrypt the data located in a device’s storage? </para>
                            </listItem>
                            <listItem>
                              <para>Is it possible to install the apps in external storage on a target device?</para>
                            </listItem>
                            <listItem>
                              <para>Do you foresee any increase in storage activity on the back-end app server with the BYOD adoption?</para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, do you have plans to extend the app server’s storage capacity?</para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>Is the data consumed by apps located in storage on-premises, in the cloud, or in both locations?</para>
                            </listItem>
                            <listItem>
                              <para>Is the data consumed by apps encrypted in datacenter storage or in the cloud?</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>Network</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>What are the network requirements for the apps that you plan to deploy for BYOD users?</para>
                            </listItem>
                            <listItem>
                              <para>Do the apps encrypt the data before transmitting it through the network from the users’ devices to the app server on the back end?</para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, which encryption method do the apps use?</para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>Do you foresee any increase in network activity with the BYOD adoption?</para>
                            </listItem>
                            <listItem>
                              <para>Do the apps require full network connectivity in order to work?</para>
                            </listItem>
                            <listItem>
                              <para>Do the apps work in a low-latency network? </para>
                            </listItem>
                            <listItem>
                              <para>Can the apps be remotely uninstalled via the network, or do they need to be uninstalled via the devices’ consoles?</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>Security</para>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Were the apps developed using any security development method?</para>
                            </listItem>
                            <listItem>
                              <para>Do the apps provide authentication capabilities?</para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, which authentication method do the apps use?</para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>Does the authentication method leverage cloud services?</para>
                            </listItem>
                            <listItem>
                              <para>Do the apps provide authorization capabilities?</para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, what levels of authorization do the apps provide?</para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>Do the apps leverage the existing infrastructure to handle authorization?</para>
                            </listItem>
                            <listItem>
                              <para>Do the apps provide logging capabilities?</para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, what data do they log? Is it possible to control the logging level?</para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>Do the apps provide input validation?</para>
                            </listItem>
                            <listItem>
                              <para>Do the company’s policies have specific standards for input validation and handling?</para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, will the apps be compliant with such requirements?</para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>Is there a common input validation or sanitization subsystem that processes data from outside the system?</para>
                            </listItem>
                            <listItem>
                              <para>Will those apps consume any external library such as JavaScript Library?</para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, did you perform a security risk assessment for these external calls?</para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>Were the apps validated using the STRIDE (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, and Elevation of Privilege) method?</para>
                            </listItem>
                            <listItem>
                              <para>Will the apps handle personally identifiable data?</para>
                            </listItem>
                            <listItem>
                              <para>Did you perform any privacy analysis for these apps?</para>
                            </listItem>
                            <listItem>
                              <para>Will the apps use live tiles?</para>
                              <list class="bullet">
                                <listItem>
                                  <para>If so, could these live tiles inadvertently cause information disclosure?</para>
                                </listItem>
                              </list>
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
    </sections>
  </section>
  <section>
    <title>See also</title>
    <content>
      <list class="bullet">
        <listItem>
          <para>
            <link xlink:href="0da8559b-8371-40c6-aa10-0439aa24e130" />
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="bc4d8a1d-9b5b-4a26-8620-d5917871e34c" />
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