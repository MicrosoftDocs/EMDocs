---
# required metadata

title: Role of Azure Information Protection in securing data | Microsoft Docs
description: This article describes the role of Azure Information Protection in keeping your organization's data secure.
author: yuridio
ms.author: msmbaldwin
manager: barbkess
ms.date: 04/16/2019
ms.topic: solution
ms.service: rights-management

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

[Azure Information Protection (AIP)](/azure/information-protection/what-is-information-protection) provides customers with the ability to classify, label their data, and protect it using encryption. Azure Information Protection enables IT Administrators to:

- Automatically classify emails and documents based on preset rules
- Add markers to content like custom headers, footers, and watermarks
- Protect company's confidential files with Rights Management, which allows them to:
	- Use RSA 2048-bit keys for public key cryptography and SHA-256 for signing operations.
	- Encrypt the files to a specific set of recipients both inside and outside their organization
	- Apply specific set of rights to restrict the usability of the file    
	- Decrypt content based on the user’s identity and authorization in the rights policy

These capabilities enable enterprises to have a greater end-to-end control over their data. In this context, Azure Information Protection plays an important role in securing company's data.

> [!IMPORTANT]
> For more information on how Azure Information Protection works, read [How does Azure RMS work? Under the hood](/azure/information-protection/how-does-it-work).

## The state of enterprise protection today

Many enterprises today do not have any protection technology in place, with documents and emails being shared in cleartext and data custodians not having the clarity on which users have access to privileged content. Protection technologies like SMIME are complicated and ACLs do not necessarily travel with emails and documents.

![No document protection](./media/azure-information-protection-securing-data/aip-securing-data-fig1.png)

In a largely unprotected environment, Azure Information Protection provides a measure of security that was not available earlier. And while security is a constantly evolving subject and no organization can claim 100% protection at any point in time, Azure Information Protection when properly deployed increases the security footprint of an organization.

## Security principles for sharing content

When using Azure Information Protection within the organization, IT administrators have full control over the client device and over user identity management, and this builds the right platform of trust for sharing within the organization. Sending information outside the organization is inherently less trustworthy. In thinking about the approach to information protection, there are some principles that you must perform a risk assessment. While performing this risk assessment, consider the following points:

- The recipient has physical access to an unmanaged device, and is therefore in control of everything that happens on the device.
- The recipient is authenticated to a degree of confidence related to non-impersonation.

In a situation where the IT administrator doesn’t control the device or the identity, IT cannot control what happens to the protected information. Once a user authenticates and opens protected information, it’s no longer your information to control. At this point, you’re trusting the recipient that they honor the policies placed on the content.

It is not possible to completely stop a malicious external recipient with authorized access to the protected content. Azure Information Protection helps establish ethical boundaries and with the use of enlightened applications helps keep people honest on how they access the document. Azure Information Protection helps when there is implicit trust within the defined boundary of access given based on identity.

However, detecting and mitigating future access is simpler. The Document Tracking feature of the Azure Information Protection service can track access and the organization can act by revoking access to the specific document or revoking the access of the user.

If the content is very sensitive and the organization cannot trust the recipient, additional security of the content becomes paramount. The recommendation is to turn the dial in favor of security and place access controls on the document.

## Identity based security

The sections that follow will explore three major scnearios of attacks on protected content, and how a combination of environment controls and Azure Information Protection can be used to mitigate malicious access to the content.

### Attacks by unauthorized users

The basis of protection in Azure Information Protection is that access to protected content is based on authenticated identity and authorization. This means that with Azure Information Protection *no authentication* or *authorization* implies *no access*. This is the primary reason to deploy Azure Information Protection, it enables enterprises to go from a state of unrestricted access to a state where access to information is based on user authentication and authorization.

By using this Azure Information Protection capability, enterprises are able to compartmentalize information. For example: keeping sensitive information of the Human Resources (HR) department isolated within the department; and keeping the finance department’s data restricted to the finance department. Azure Information Protection provides *access based on identity, rather than nothing at all*.

The diagram below has an example of an user (Bob) sending a document to Tom. In this case Bob is from the Finance department and Tom is from the Sales department. Tom cannot get access to the document, if no rights were granted.

![No access](./media/azure-information-protection-securing-data/aip-securing-data-fig2.png)

The key takeaway in this scenario is that Azure Information Protection can stop attacks from unauthorized users. For more information about cryptographic controls in Azure Information Protection, read [Cryptographic controls used by Azure RMS: Algorithms and key lengths](/azure/information-protection/how-does-it-work).

### Access by malicious programs on behalf of users

Malicious program accessing on behalf of a user is usually something that takes place without the user's knowledge. Trojans , viruses, and other malware are classic examples of malicious programs that can act on behalf of the user. If such a program can impersonate the user's identity or leverage user's privileges to take an action, then it can use the [Azure Information Protection SDK](/azure/information-protection/develop/developers-guide) to decrypt content on behalf of an unwitting user. Since this action takes place in the user’s context, there isn’t a simple way to prevent this attack.

![Malicious programs](./media/azure-information-protection-securing-data/aip-securing-data-fig3.png)

The intent here is to enhance the security of the user's identity, this will assist in mitigating the ability of rogue applications to hijack user's identity. Azure Active Directory provides several solutions that can help secure the user identity, for example, using two-factor authentication. In addition, there are other capabilities that come as a part of Azure Activity Directory Identity Protection that should be explored to keep the user identity secure.

Securing identities falls outside the scope of Azure Information Protection, and falls in the realm of administrator responsibility.

> [!IMPORTANT]
> It is also important to focus on a “managed” environment to remove the presence of malicious programs. This will be covered in the next scenario.

### Malicious users with authorization

Access by a malicious user is essentially a compromise of trust. The enabler in this scenario needs to be a program crafted to escalate user's privileges, because unlike the previous scenario, this user voluntarily provides credentials to break trust.

![Malicious users](./media/azure-information-protection-securing-data/aip-securing-data-fig4.png)

Azure Information Protection was designed to make applications located on the client device responsible for enforcing the rights associated with the document. By all measures, the weakest link in the security of protected content today is on the client device, where the content is visible to the end user in plaintext. The client applications like Microsoft Office honor the rights correctly, and so a malicious user cannot use these applications to escalate privileges. However, with the Azure Information Protection SDK, a motivated attacker can create applications that do not honor the rights, and this is the essence of a *malicious program*.

The focus of this scenario is to secure the client device and applications, so that rogue applications cannot be used. Some steps that the IT administrator can take are listed below:

- Use [Windows AppLocker](https://technet.microsoft.com/library/dd759117(v=ws.11).aspx) to help ensure that unwanted programs cannot be executed
- Use [Intune](https://docs.microsoft.com/intune/) and [System Center Configuration Manager](https://docs.microsoft.com/sccm/) to help ensure the device is ‘healthy’
- Ensure that the anti-virus on the device is up-to-date
- Use applications that support [Microsoft Identity Brokers](https://technet.microsoft.com/library/ms166045(v=sql.105).aspx) for authentication and [SSO](https://azure.microsoft.com/resources/videos/overview-of-single-sign-on/)

An important takeaway from this scenario is that securing client machines and applications is an important part of the trust that underpins Azure Information Protection.

Since Azure Information Protection is not designed to protect against malicious misuse by users that are granted access to the content, it cannot be expected to protect content against malicious modification by said users. While any sort of modification of the content requires in practice that the user has been granted access to the protected data in the first place, and the policies and rights associated with a document are themselves properly signed and tamper-evident, once a user has been granted access to the required encryption/decryption keys the user can be assumed to be technically able to decrypt the data, modify it and re-encrypt it. There are many solutions that can be implemented to provide document signing, authorship attestation, tamper-proofing and non-repudiation to Office documents, both within Microsoft products (e.g. Office document signing support, s/MIME support in Outlook) and from third parties. You should not rely on the protection capabilities of AIP alone to protect you from malicious modification by authorized users. 

## Summary

Full security goes beyond one technology. Through a variety of interdependent means, an IT administrator can reduce the attack surface on protected content in the real world.

- **Azure Information Protection**: prevents unauthorized access to content
- **Microsoft Intune, System Center Configuration Manager, and other device management products**: enables a managed and controlled environment free of malicious apps
- **Windows AppLocker**: enables a managed and controlled environment free of malicious apps
- **Azure AD Identity Protection**: enhances trust in the user identity
- **EMS Conditional Access**: enhances trust in the device and identity
