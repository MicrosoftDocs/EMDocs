---
title: BYOD data access and protection considerations
ms.custom: na
ms.reviewer: na
ms.service: multiple
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 181eb917-119d-4e56-8ead-1182b1dc5cab
author: YuriDio
---
# BYOD data access and protection considerations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Loss of sensitive data is an operation risk for any company, and with the advent of BYOD, information resides in more places than ever before. This translates to a bigger threat landscape and higher risks that must be correctly mitigated. Because of a range of legislative, corporate, and industry regulations that governs the protection of sensitive data, data protection can be a complex process. It is important to take these legal requirements, internal corporate policies, and industry regulations into account.</para>
    <para>As part of the BYOD infrastructure strategy it is essential that after the policies and data classifications have been defined, the data must be physically located, placed in proper classification levels, and have the appropriate security settings applied. IT needs a way to validate users’ identities and may wish to apply additional conditions on the types of devices that are able to access the information and apps provided by the company.</para>
    <para>The sections that follow are based on components for the Data Access and Protection subdomain shown in Figure 1 in <link xlink:href="bc4d8a1d-9b5b-4a26-8620-d5917871e34c">BYOD Problem Definition</link>, which is the conceptual diagram for the BYOD problem domain.</para>
  </introduction>
  <section>
    <title>4.3.1 Storage</title>
    <content>
      <para address="BKMK_431">How data will be stored in users’ devices can directly impact how you choose to address data access and protection for BYOD. Data encryption must be considered, and devices must allow IT to control when data encryption is enabled and for which types of data. Companies must review their policies and regulations to understand which types of data are allowed to leave the datacenter and be at rest in remote devices’ storage.</para>
      <para>Data encryption at rest in the datacenter’s storage is crucial. If your company is not yet performing this task, it must be considered as part of the strategy for a BYOD infrastructure. Ideally, the data should be encrypted throughout the path (see Figure 6 in <link xlink:href="181eb917-119d-4e56-8ead-1182b1dc5cab#BKMK_432">4.3.2 Network</link> to better understand these paths).</para>
      <para>With Windows Server 2012 R2, it is possible to encrypt data at rest in users’ devices by using <externalLink><linkText>Work Folders</linkText><linkUri>http://technet.microsoft.com/library/dn265974.aspx</linkUri></externalLink>. IT administrators can use Work Folders to gain more control over corporate data and users’ devices, and centralize work data so that they can apply the appropriate processes and tools to keep their company in compliance. This can range from simply having a copy of the data if the user leaves the company to a wide range of capabilities such as backup, retention, classification, and automated encryption. If you decide to use Work Folders, ensure that the servers that will host the sync shares are well planned from the performance perspective. Read <externalLink><linkText>Performance Considerations for Work Folders Deployments</linkText><linkUri>http://blogs.technet.com/b/filecab/archive/2013/11/01/performance-considerations-for-large-scale-work-folders-deployments.aspx</linkUri></externalLink> for more information.</para>
      <para>If you think of storage as a container of content, great value comes with protecting the consumption of that content. Data leakage can be prevented by enforcing policies that will affect how the content that resides in the storage will be used by the end user. <externalLink><linkText>Active Directory Rights Management Services (AD RMS)</linkText><linkUri>http://technet.microsoft.com/library/hh831554.aspx</linkUri></externalLink> can be used to augment the security strategy for your organization by protecting documents that use information rights management (IRM). AD RMS allows individuals and administrators through IRM policies to specify access permissions to documents, workbooks, and presentations. This helps prevent sensitive information from being printed, forwarded, or copied by unauthorized people. After permission for a file has been restricted by using IRM, the access and usage restrictions are enforced no matter where the information is, because the permission to a file is stored in the file itself.</para>
      <para>Other storage technologies available in the Windows operating system can also be used to enhance the overall protection of the data, such as <externalLink><linkText>BitLocker</linkText><linkUri>http://technet.microsoft.com/library/cc732774.aspx</linkUri></externalLink> for drive encryption and <externalLink><linkText>Encrypting File System (EFS)</linkText><linkUri>http://technet.microsoft.com/library/cc962103.aspx</linkUri></externalLink> for file encryption. Use the following table to see the advantages and disadvantage for storage protection. Keep in mind that these options are not mutually exclusive. In other words, your design decision might conclude that you need all of these options in your BYOD infrastructure solution for storage protection.</para>
    </content>
    <sections>
      <section>
        <content/>
        <sections>
          <section>
            <title>Table 10 Storage protection options—advantages and disadvantages</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Storage protection options</para>
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
                      <para>Encrypting File System (EFS)</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Provides file-level encryption.</para>
                        </listItem>
                        <listItem>
                          <para>Encryption process is transparent to users because the encryption does not happen at the app level (it happens at the file-system level).</para>
                        </listItem>
                        <listItem>
                          <para>Provides backup capability with a key recovery agent.</para>
                        </listItem>
                        <listItem>
                          <para>Available in all supported versions of the Windows operating system.</para>
                        </listItem>
                        <listItem>
                          <para>Can be enabled by using Group Policy.</para>
                        </listItem>
                        <listItem>
                          <para>Compliant with Suite B cryptography requirements as defined by the National Security Agency to meet the needs of United States government agencies for protecting classified information.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>If the data owner is unavailable and you do not have the key recovery agent, you cannot decrypt an EFS file.</para>
                        </listItem>
                        <listItem>
                          <para>Certificate management must be in place to manage the private keys that are associated with recovery certificates.</para>
                        </listItem>
                        <listItem>
                          <para>Not available on other platforms that are not Windows.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>BitLocker</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Provides drive encryption capability.</para>
                        </listItem>
                        <listItem>
                          <para>Provides system integrity and verification by leveraging Trusted Platform Module (TPM).</para>
                        </listItem>
                        <listItem>
                          <para>Enhances protection to mitigate offline software-based attacks.</para>
                        </listItem>
                        <listItem>
                          <para>Provides a method to check that early boot file integrity has been maintained.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Not available in all versions of Windows.</para>
                        </listItem>
                        <listItem>
                          <para>Requires TPM version 1.2.</para>
                        </listItem>
                        <listItem>
                          <para>Requires that the system BIOS (for TPM computers and non-TPM computers) support the USB mass storage device class.</para>
                        </listItem>
                        <listItem>
                          <para>Not available for clusters prior to Windows Server 2012.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Work Folders</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Leverages EFS for file encryption.</para>
                        </listItem>
                        <listItem>
                          <para>Allows IT to encrypt data at rest in users’ devices.</para>
                        </listItem>
                        <listItem>
                          <para>Can be enabled by using Group Policy on a per-user or per-device basis.</para>
                        </listItem>
                        <listItem>
                          <para>Integration with Windows Intune, which allows selective wipe for data located in Work Folders on users’ devices.</para>
                        </listItem>
                        <listItem>
                          <para>Can force users to reauthenticate before they can access data located in Work Folders.</para>
                        </listItem>
                        <listItem>
                          <para>Enables integration with Microsoft Rights Management services for data classification.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Available only for Windows 8.1 and Windows RT 8.1.</para>
                        </listItem>
                        <listItem>
                          <para>Requires Windows Server 2012 R2 for hosting the sync shares.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Active Directory Rights Management Services (AD RMS)</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Prevent an authorized recipient of restricted content from forwarding, copying, modifying, printing, faxing, or pasting the content for unauthorized use.</para>
                        </listItem>
                        <listItem>
                          <para>Support file expiration so that content in documents can no longer be viewed after a specified period of time.</para>
                        </listItem>
                        <listItem>
                          <para>Prevent restricted content from being copied by using the Print Screen feature in Microsoft Windows.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Requires the deployment of a new server role (AD RMS).</para>
                        </listItem>
                        <listItem>
                          <para>Does not restrict content from being copied by using third-party screen-capture programs.</para>
                        </listItem>
                        <listItem>
                          <para>Does not prevent content from being lost or corrupted because of the actions of computer viruses.</para>
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
  <section address="BKMK_432">
    <title>4.3.2 Network</title>
    <content>
      <para>It is essential to consider the factors involved in enabling users to use their devices and for data to be secure through the entire path between datacenter (on-premises) or cloud and users’ devices. These factors are highlighted in Figure 6.</para>
      <para address="BKMK_Figure6">
        <mediaLinkInline>
          <image xlink:href="2ae4f3db-28cc-460f-ba4b-93348f45a415"/>
        </mediaLinkInline>
      </para>
      <para>
        <legacyBold>Figure 6 Areas where data protection must be considered for a BYOD infrastructure</legacyBold>
      </para>
      <para>Figure 6 highlights the critical areas where data protection must be considered for a BYOD infrastructure. These areas are described in more detail in the following table.</para>
    </content>
    <sections>
      <section>
        <content/>
        <sections>
          <section>
            <title>Table 11 Data protection—locations and considerations</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Data location</para>
                    </TD>
                    <TD>
                      <para>Considerations</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>(1) Data at rest in the datacenter.</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Storage encryption: consider a storage solution that supports encryption (see <externalLink><linkText>Section 4.3.1</linkText><linkUri>http://technet.microsoft.com/library/dn656895.aspx#BKMK_431</linkUri></externalLink> for more information about storage encryption).</para>
                        </listItem>
                        <listItem>
                          <para>Key management: the key used to encrypt storage should be backed up, and a key recovery agent should be available, in case you need it.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>(2) Data in flight from the datacenter to the edge of the corporate network.</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Network encryption: consider using a standard web protocol for encryption, such as SSL.</para>
                        </listItem>
                        <listItem>
                          <para>Public key infrastructure (PKI): if your company has a PKI, you can use it to encrypt this communication channel.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>(3) Data in flight from the edge of the corporate network to users’ devices.</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Network encryption: consider using a standard web protocol for encryption, such as SSL.</para>
                        </listItem>
                        <listItem>
                          <para>PKI: because this channel will be accessed by users using their personal devices, you should consider using a public certificate, which will likely be already trusted by users’ devices.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>(3.1) Data in flight from the edge of the corporate network to the cloud service provider (optional—applies only if your company is using cloud services for BYOD).</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Network encryption: consider using a standard web protocol for encryption, such as SSL.</para>
                        </listItem>
                        <listItem>
                          <para>PKI: because this channel will be accessed by users using their personal devices, consider using a public certificate, which will likely be already trusted by users’ devices.</para>
                        </listItem>
                        <listItem>
                          <para>Site-to-site VPN: if you have a <externalLink><linkText>hybrid cloud infrastructure</linkText><linkUri>http://blogs.technet.com/b/cloudsolutions/archive/2013/08/22/hybrid-it-infrastructure-solution-for-enterprise-it-overview.aspx</linkUri></externalLink> that is connected with Cloud Services, consider using site-to-site VPN to keep the secure channel available for use by apps located on users’ devices.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>(3.2) Data at rest in the cloud service provider’s datacenter (optional—applies only if your company is using cloud services for BYOD).</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Cloud service provider: consider the options that the cloud service provider can offer to encrypt data at rest.</para>
                        </listItem>
                        <listItem>
                          <para>Key management: verify with the cloud service provider how key management is handled and how the backup process occurs. Also consider integration between cloud services with an on-premises key management system.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>(4) Data at rest in users’ devices.</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Storage encryption: consider a storage solution that supports encryption (see <externalLink><linkText>Section 4.3.1</linkText><linkUri>http://technet.microsoft.com/library/dn656895.aspx#BKMK_431</linkUri></externalLink> for more information about storage encryption).</para>
                        </listItem>
                        <listItem>
                          <para>Key management: the key used to encrypt storage should be backed up, and a key recovery agent should be available, in case you need it.</para>
                        </listItem>
                        <listItem>
                          <para>Remote wipe: the data that resides on users’ devices can be deleted remotely, in case it is necessary.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para>Windows Server 2012 R2 enables the use of <externalLink><linkText>HTTPS</linkText><linkUri>http://msdn.microsoft.com/library/aa767735(v=vs.85).aspx</linkUri></externalLink> to publish resources via <externalLink><linkText>Web Application Proxy</linkText><linkUri>http://technet.microsoft.com/library/dn280944.aspx</linkUri></externalLink> to protect data while in transit through the network. Communication between back-end servers can also be encrypted using <externalLink><linkText>IPsec</linkText><linkUri>http://technet.microsoft.com/library/cc757613(v=ws.10).aspx</linkUri></externalLink> or <externalLink><linkText>SMB Encryption</linkText><linkUri>http://support.microsoft.com/kb/2709568</linkUri></externalLink>, if the network traffic is purely based on <externalLink><linkText>SMB protocol</linkText><linkUri>http://technet.microsoft.com/library/hh831795.aspx</linkUri></externalLink>. Use the following table to evaluate which network protection option best fits your design requirements for back-end server communication.</para>
            </content>
          </section>
          <section>
            <title>Table 12 Network protection options—advantages and disadvantages</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Network protection options</para>
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
                      <para>SSL</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Wide range of supportability from many devices.</para>
                        </listItem>
                        <listItem>
                          <para>Strong authentication, message privacy, and integrity.</para>
                        </listItem>
                        <listItem>
                          <para>Interoperability.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Requires a certificate infrastructure, unless you use public SSL certificates.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>IPsec</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Provides encryption of the entire IP datagram.</para>
                        </listItem>
                        <listItem>
                          <para>Provides computer-level authentication.</para>
                        </listItem>
                        <listItem>
                          <para>Widely supported on many platforms and available in all Windows-supported versions.</para>
                        </listItem>
                        <listItem>
                          <para>Internet Key Exchange (IKE) authentication to limit network access to trusted computers.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Requires a certificate infrastructure, unless you use a preshared key.</para>
                        </listItem>
                        <listItem>
                          <para>IPsec happens at the host level, so it cannot be controlled at the app level.</para>
                        </listItem>
                        <listItem>
                          <para>Difficult to troubleshoot.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>SMB Encryption</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Encrypts data in transit using SMB protocol.</para>
                        </listItem>
                        <listItem>
                          <para>Easy to implement in the UI and via Windows PowerShell.</para>
                        </listItem>
                        <listItem>
                          <para>Flexible because it can be implemented per server or per share.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>It works only for Windows 8 and later for client computers and Windows Server 2012 and later for server computers.</para>
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
    <title>4.3.3 Directory</title>
    <content>
      <para>User attributes should be stored in the directory, allowing IT to easily query for user information such as roles and groups. You should also consider how the relationship between users and devices will be tracked. Every unknown device that becomes known or manageable by IT also should have a record in the management database or in the directory that allows IT to audit the device.</para>
      <para>In hybrid environments where there will be different authentication repositories, companies should consider how to enable users to authenticate using the same credential regardless of where they are located and where the apps are located. Consider using Active Directory Federation Services (AD FS) if you want to centralize the authentication on-premises instead of replicating the directory with the cloud service provider. Use the following table to evaluate the directory options for a BYOD infrastructure.</para>
    </content>
    <sections>
      <section>
        <content/>
        <sections>
          <section>
            <title>Table 13 Directory options—advantages and disadvantages</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Directory options</para>
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
                      <para>Centralized on-premises</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>All security controls are physically located on-premises, and IT has full control.</para>
                        </listItem>
                        <listItem>
                          <para>IT can perform hardening of the server that holds the directory role.</para>
                        </listItem>
                        <listItem>
                          <para>Richer auditing and logging capabilities.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Higher cost to maintain when compared to cloud services.</para>
                        </listItem>
                        <listItem>
                          <para>Lack of integration with cloud services.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Centralized in the cloud</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Lower cost to maintain when compared to an on-premises solution.</para>
                        </listItem>
                        <listItem>
                          <para>Easier to manage when compared to an on-premises solution.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Lack of customization.</para>
                        </listItem>
                        <listItem>
                          <para>Depends on the cloud service provider to obtain auditing and logging data.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Directory Synchronization between on-premises and cloud</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Integrated on-premises and in the cloud directory.</para>
                        </listItem>
                        <listItem>
                          <para>Enables single sign-on for users.</para>
                        </listItem>
                        <listItem>
                          <para>IT can still perform hardening of the server that holds the directory role on-premises.</para>
                        </listItem>
                        <listItem>
                          <para>Seamless login experience for users.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Requires password hash synchronization.</para>
                        </listItem>
                        <listItem>
                          <para>Requires a signature service.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Federated between on-premises and the cloud</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Integrated on-premises and in the cloud directory.</para>
                        </listItem>
                        <listItem>
                          <para>Enables single sign-on for users.</para>
                        </listItem>
                        <listItem>
                          <para>IT can still perform hardening of the server that holds the directory role on-premises.</para>
                        </listItem>
                        <listItem>
                          <para>Seamless login experience for users.</para>
                        </listItem>
                        <listItem>
                          <para>More robust for solutions that need integration with other directory services.</para>
                        </listItem>
                        <listItem>
                          <para>Requires synchronization, but does not sync passwords.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Requires a signature service.</para>
                        </listItem>
                        <listItem>
                          <para>Requires a server infrastructure for federation.</para>
                        </listItem>
                        <listItem>
                          <para>Requires certificate to secure the communication between the federation server and the cloud service.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para>Hybrid environments that require users to have connectivity with cloud services from their own devices can take advantage of the integration between <externalLink><linkText>Windows Azure Active Directory</linkText><linkUri>http://www.windowsazure.com/services/active-directory/</linkUri></externalLink> and Active Directory Domain Services (AD DS). In a <externalLink><linkText>hybrid identity scenario</linkText><linkUri>http://technet.microsoft.com/library/dn550987.aspx</linkUri></externalLink>, companies that want to preserve seamless user authentication can choose from the following options:</para>
              <list class="bullet">
                <listItem>
                  <para>Directory Synchronization with Password Sync: using DirSync with <externalLink><linkText>password hash sync</linkText><linkUri>http://technet.microsoft.com/library/dn246918.aspx</linkUri></externalLink> between AD DS and Windows Azure AD.</para>
                </listItem>
                <listItem>
                  <para>Federated authentication with single sign-on: user attributes are synchronized using DirSync. Authentication is passed back through federation (AD FS) and completed against AD DS.</para>
                </listItem>
              </list>
              <para>When using Device Registration Service (see <externalLink><linkText>Section 4.2.2</linkText><linkUri>http://technet.microsoft.com/library/dn656901.aspx#BKMK_422</linkUri></externalLink> for more information) in Windows 8.1, a certificate is installed in a user’s device and a device record is created in AD DS with the certificate’s thumbprint number. This link between the device and the user allows IT to track which devices are getting registered by each user. This capability does not require an Enterprise PKI.</para>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <section>
    <title>4.3.4 Authentication and authorization</title>
    <content>
      <para>The decision to enable users to access apps and data from their devices must guarantee that users are identified in a trustworthy authentication process and also that users are authorized to use the resources that are requested. Companies should review their current authentication and authorization policies and consider the following questions:</para>
      <list class="bullet">
        <listItem>
          <para>What are the authentication requirements for users to be able to remotely access company apps from their devices?</para>
        </listItem>
        <listItem>
          <para>Is the current platform able to enforce authorization per user and per app without having to rewrite the apps?</para>
        </listItem>
        <listItem>
          <para>Is it possible to enforce Multi-Factor Authentication according to a user’s location?</para>
        </listItem>
      </list>
      <para>Authentication and authorization are handled by AD FS in connection with AD DS. The data in flight in the datacenter will also use the HTTPS protocol when connecting with the File Server role and Authentication Services.</para>
      <para>To enforce Multi-Factor Authentication, companies can use the built-in capabilities in AD FS or use Windows Azure Active Authentication (previously known as PhoneFactor). By leveraging this capability in Windows Azure, IT has the ability to enforce multi-factor authentication for users who are accessing company resources via an extranet. For more information about multi-factor authentication, see <externalLink><linkText>Manage Risk with Additional Multi-Factor Authentication for Sensitive Applications</linkText><linkUri>http://technet.microsoft.com/library/dn280949.aspx</linkUri></externalLink>.</para>
      <para>To enforce authorization per app on users who are accessing apps either from an external or internal network, IT can leverage Web Application Proxy. By using Web Application Proxy, IT can create specific rules to enforce authentication and authorization in conjunction with AD FS. Web Application Proxy publishing works for any user device; they can use personal laptops, tablets, or smartphones. In addition, users are not required to install any additional software on their devices to access published apps. Web Application Proxy serves as a reverse proxy for any apps published through it, and as such, the user experience is the same as if users’ devices were connected directly to the apps. For more information about Web Application Proxy, see <externalLink><linkText>Web Application Proxy Overview</linkText><linkUri>http://technet.microsoft.com/library/dn280944.aspx</linkUri></externalLink>.</para>
    </content>
  </section>
  <section>
    <title>4.3.5 Policy and compliance</title>
    <content>
      <para>Policy and compliance considerations should be a priority of any strategy that embraces BYOD. Some companies might have hard requirements that will not fit into this model because of business regulations. The company that is moving to a people-centric strategy must understand current policies and how these policies will be affected by embracing BYOD. Consider the requirements regarding data classification and how IT can have control of the data classification, even when the data is at rest in the device storage. When thinking of data classification, it is important to be able to classify the data while some operations (such as editing a file) are taking place.</para>
      <para>Policies should be enforced from a centralized location to enable IT to rapidly respond in case of ad hoc changes that will affect all users. Also consider robust auditing capabilities for mobile devices. If a breach occurs, it is essential that IT is able to track which policy was infringed, who infringed upon it, and when it happened.</para>
    </content>
    <sections>
      <section>
        <content/>
        <sections>
          <section>
            <title>Table 14 Policy and compliance—capabilities and considerations</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Policy and compliance capabilities</para>
                    </TD>
                    <TD>
                      <para>Considerations</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Data classification</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Apply data classification as the content is saved and as it changes.</para>
                        </listItem>
                        <listItem>
                          <para>IT must be able to classify data at rest in the datacenter and in users’ device.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Centralized management</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>IT must be able to manage data classification from a single location, even if the data is located in multiple devices.</para>
                        </listItem>
                        <listItem>
                          <para>Hybrid IT environments should be able to manage resources located on-premises and in the cloud.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Integration with directory services</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>IT should be able to leverage its current directory service as the identity repository.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Audit and logging</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>IT should be able to audit access to resources and increase logging capability, when necessary.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para>Applying data governance across file servers to control who can access information and to audit who has accessed information is a key element for BYOD. In Windows Server 2012 R2, this can be performed by using <externalLink><linkText>Dynamic Access Control</linkText><linkUri>http://technet.microsoft.com/library/dn408191.aspx</linkUri></externalLink>, which is based on infrastructure investments that can be used by partners and line-of-business applications. The features of Dynamic Access Control can provide great value for organizations that use Active Directory Domain Services.</para>
              <para>When leveraging Dynamic Access Control capabilities, you can identify data by using automatic and manual classification of files. For example, you can tag data in file servers across the organization. It is also possible to control access to files by applying safety-net policies that use central access policies. Dynamic Access Control also leverages Rights Management Services (RMS) protection by using automatic RMS encryption for sensitive documents. For example, you can configure RMS to encrypt all documents that contain Health Insurance Portability and Accountability Act (HIPAA) information. For forensic investigation and auditing, you can leverage the central audit policies for compliance reporting and forensic analysis. You can identify who has accessed highly sensitive information.</para>
              <para>Dynamic Access Control, a function of the File Server role, enables IT with the capabilities shown in the preceding table. For more information about Dynamic Access Control, see <externalLink><linkText>Dynamic Access Control: Scenario Overview</linkText><linkUri>http://technet.microsoft.com/library/hh831717.aspx</linkUri></externalLink>.</para>
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
            <link xlink:href="d1653116-3922-40d3-bc4f-3d845b6aaecb"/>
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
