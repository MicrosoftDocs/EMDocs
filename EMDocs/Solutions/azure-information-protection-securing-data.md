---
# required metadata

title: Role of Azure Information Protection in securing data | Microsoft Docs
description: This article describes the role of Azure Information Protection in keeping your organization's data secure.
author: yuridio
ms.author: yurid
manager: mbaldwin
ms.date: 01/23/17
ms.topic: solution
ms.prod:
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 2f906e2e-3d99-40e6-b5cc-8d903fcda444

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: v-craic
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# The role of Azure Information Protection in securing data

[Azure Information Protection (AIP)](/information-protection/understand-explore/what-is-information-protection.md) provides customers with the ability to classify, label their data, and protect it using encryption. Azure Information Protection enables IT Administrators to:

- Automatically classify emails and documents based on preset rules
- Add markers to content like custom headers, footers, and watermarks
- Protect company's confidential files with Rights Management, which allows them to:
	- Use RSA 2048-bit keys for public key cryptography and SHA-256 for signing operations. 
	- Encrypt the files to a specific set of recipients both inside and outside their organization
	- Apply specific set of rights to restrict the usability of the file    
	- Decrypt content based on the user’s identity and authorization in the rights policy

These capabilities enable enterprises to have a greater end-to-end control over their data. In this context, Azure Information Protection plays an important role in securing company's data. 

> [!IMPORTANT]
> For more information on how Azure Information Protection works, read [How does Azure RMS work? Under the hood](/information-protection/understand-explore/how-does-it-work.md).

## The state of enterprise protection today

Many enterprises today do not have any protection technology in place, with documents and emails being shared in cleartext and data custodians not having the clarity on which users have access to privileged content. Protection technologies like SMIME are complicated and ACLs do not necessarily travel with emails and documents. 

![No document protection](./media/azure-information-protection-securing-data/aip-securing-data-fig1.png)

In a largely unprotected environment, Azure Information Protection provides a measure of security that was not available earlier. And while security is a constantly evolving subject and no organization can claim 100% protection at any point in time, Azure Information Protection when properly deployed increases the security footprint of an organization.


## Identity based security

The sections that follow will explore three major scenarios that Azure Information Protection can be used to protect company's data against malicious access.

### Attacks by unauthorized users

The basis of protection in Azure Information Protection is that access to protected content is based on authenticated identity and authorization. This means that with Azure Information Protection *no authentication* or *authorization* implies *no access*. This is the primary reason to deploy Azure Information Protection, it enables enterprises to go from a state of unrestricted access to a state where access to information is based on user authentication and authorization.
 
By using this Azure Information Protection capability, enterprises are able to compartmentalize information. For example: keeping sensitive information of the Human Resources (HR) department isolated within the department; and keeping the finance department’s data restricted to the finance department. Azure Information Protection provides *access based on identity, rather than nothing at all*. 

The diagram below has an example of an user (Bob) sending a document to Tom. In this case Bob is from the Finance department and Tom is from the Sales department. Tom cannot get access to the document, if no rights were granted. 

![No access](./media/azure-information-protection-securing-data/aip-securing-data-fig2.png)

The key takeaway on this scenario is that Azure Information Protection can stop attacks from unauthorized users. For more information about cryptographic controls in Azure Information Protection, read [Cryptographic controls used by Azure RMS: Algorithms and key lengths](/information-protection/understand-explore/how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths).

### Access by malicious programs on behalf of users

Malicious program accessing on behalf of a user is usually something that takes place without the user's knowledge. Trojans , viruses, and other malware are classic examples of malicious programs that can act on behalf of the user. If such a program can impersonate the user's identity or leverage user's privileges to take an action, then it can use the [Azure Information Protection SDK](/information-protection/develop/developers-guide.md) to decrypt content on behalf of an unwitting user. Since this action takes place under the user’s context, there isn’t a simple way to prevent this attack.

![Malicious programs](./media/azure-information-protection-securing-data/aip-securing-data-fig3.png)

The intent here is to enhance the security of the user's identity, this will assist mitigating rogue applications to hijack user's identity. Azure Active Directory provides several solutions that can help secure the user identity, for example, using two-factor authentication. In addition, there are other capabilities that come as a part of Azure Activity Directory Identity Protection that should be explored to keep the user identity secure. 

One important fact to takeaway from this scenarios is that securing identities falls outside the scope of Azure Information Protection.

> [!IMPORTANT]
> It is also important to focus on a “managed” environment to remove the presence of malicious programs. This will be covered in the next scenario. 

### Malicious users with authorization

Access by a malicious user is essentially a compromise of trust. The enabler in this scenario needs to be a program crafted to escalate user's privileges, because unlike the previous scenario, this user voluntarily provides credentials to break trust. 

![Malicious users](./media/azure-information-protection-securing-data/aip-securing-data-fig4.png)

Azure Information Protection was designed to enable applications located on the client device to be responsible for enforcing the rights associated with the document. By all measures, the weakest link in the security of your content today is the client device, where the content is visible to the end user in plaintext. The client applications of Microsoft Office honor the rights correctly, and so a malicious user cannot use these applications to escalate privileges. However with Azure Information Protection SDK, a motivated attacker can create applications that do not honor the rights, and this is the essence of a *malicious program*.

The focus of this scenario is to secure the client device and applications, so that rogue applications cannot be used. Some steps that the IT administrator can take are listed below:

- Use [Windows AppLocker](https://technet.microsoft.com/library/dd759117(v=ws.11).aspx) to help ensure that unwanted programs cannot be executed
- Use [Intune](https://docs.microsoft.com/intune/) and [System Center Configuration Manager](https://docs.microsoft.com/sccm/) to help ensure the device is ‘healthy’
- Ensure that the anti-virus on the device is up-to-date
- Use applications that support [Microsoft Identity Brokers](https://technet.microsoft.com/library/ms166045(v=sql.105).aspx) for authentication and [SSO](https://azure.microsoft.com/resources/videos/overview-of-single-sign-on/)

An important takeaway from this scenarios is that securing client machines falls outside the scope of Azure Information Protection.
 
## Security Principles for sharing content externally

When using Azure Information Protection within the organization, IT administrators have full control over the    client device and over user identity management, and this builds the right platform of trust for sharing within the organization. Sending information outside the organization is inherently less trustworthy. In thinking about the approach to information protection, there are some principles that you must perform a risk assessment. While performing this risk assessment, consider the following points:

- The recipient has physical access to an unmanaged device, and is therefore in control of everything that happens on the device.
- The recipient is authenticated to a degree of confidence related to non-impersonation.

In a situation where the IT administrator doesn’t control the device or the identity, IT cannot control what happens to the protected information. Once a user authenticates and opens protected information, it’s no longer your information to control. At this point, you’re trusting the recipient that they honor the policies placed on the content.

It is not possible to completely stop a malicious external recipient with authorized access to the protected content. Azure Information Protection helps establish ethical boundaries and with the use of enlightened applications helps keep people honest on how they access the document. Azure Information Protection helps when there is implicit trust within the defined boundary of access given based on identity.

However, detecting and mitigating future access is simpler. The [Document Tracking](/information-protection/rms-client/client-track-revoke.md) feature of the Azure Information Protection service can track access and the organization can act by revoking access to the specific document or revoking the access of the user, where an escalation is suspected.

If the content is very sensitive and the organization cannot trust the recipient, additional security of the content becomes paramount. The recommendation is to turn the dial in favor of security and place access controls on the document. Azure Information Protection does make it harder for trust-based attacks to take place by enabling [conditional access rules](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/27/protect-your-data-at-the-front-door-with-conditional-access-from-enterprise-mobility-security/), as shown in the following examples:

- Deny access to *Highly Confidential* documents that are not on domain-joined machines. 
- Deny access to *Secret documents* on unmanaged devices.
- Require [multi-factor authentication](https://azure.microsoft.com/services/multi-factor-authentication/) for access to protected emails/documents

## More to come

Fortunately, this is not where Azure Information Protection stops as a product. We have been adding new functionality over the years and will continue to improve the security aspects of Azure Information Protection. Here is a sample of what’s coming up:

- **Access throttling**:  to prevent bulk decryption by a malicious user, the Azure Information Protection administrator can set a throttle on the number of decrypt operations done in a day. If the number exceeds the admin-defined threshold, access can be denied and/or the admin is alerted.
- **Improving integrity checks**:  this is specifically aimed at mitigating some attacks based on the document content and integrity of the original protected content
- **Enabling conditional access**:  by having the right rules in place, Azure Information Protection will help ensure that the most important content always gets a stronger ‘client environment check’. 


## Summary

Through a variety of interdependent means, Azure Information Protection is able reduce the attack surface in the real world. 

- **Azure Information Protection**: prevents unauthorized access  
- **Microsoft Intune, System Center Configuration Manager, and other device management products**: enables a managed and controlled environment free of malicious apps
- **Windows AppLocker**: enables a managed and controlled environment free of malicious apps
- **Azure AD Identity Protection**: enhances trust in the user identity
- **EMS Conditional Access**: enhances trust in the device and identity

Full security goes beyond one technology, and IT admins need to do their part in building and maintaining a conducive environment. 

Microsoft is committed to providing the best-in-class   information protection systems to our customers. Still, we continue to innovate on ensuring that the security bar continues to be high and our customers benefit from it.
 
## Additional Resources

The scenarios below will go in more details on how Azure Information Protection can help you to protect your data:

- [Secure data using classification, labeling and protection](infoprotect-secure-classify-scenario.md)
- [Share sensitive data internally and externally](share-sensitive-data.md)
- [Track usage of shared data and respond to data abuse](infoprotect-track-usage-scenario.md)
 


