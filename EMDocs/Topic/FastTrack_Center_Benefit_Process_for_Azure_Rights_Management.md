---
title: FastTrack Center Benefit Process for Azure Rights Management
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d85708b-a837-4865-aef9-0dd4488b23e9
---
# FastTrack Center Benefit Process for Azure Rights Management
If your organization is eligible for the FastTrack Center Benefit for Microsoft Azure Rights Management, you can work remotely with Microsoft specialists to get your Azure RMS environment ready for use. To learn whether your organization is eligible, see [FastTrack Center Benefit for Azure Rights Management](../Topic/FastTrack_Center_Benefit_for_Azure_Rights_Management.md).

This article provides the following:

-   [Overview of the onboarding process](#overview_rms)

-   [Expectations for your source environment](#expectations_src_environ_rms)

-   [Phases of the onboarding process](#phases_onboarding_process_rms)

-   [Microsoft responsibilities](#microsoft_responsibilities_rms) for each phase

-   [Your responsibilities](#your_responsibilities_rms) for each phase

Here’s what you can expect when onboarding is complete:

-   Your Microsoft Azure RMS tenant is created.

-   Licensed users can access Azure RMS services by using one of the following identity options:

    -   Cloud Identities (unique Microsoft Azure AD accounts).

    -   Synchronized Identities: Microsoft Azure AD accounts synchronized from your on-premises Active Directory with the Azure Active Directory Connect (Azure AD Connect)  tool for customers with a single forest or multiple Active Directory forests.

    -   Federated Identities--with Microsoft Azure AD accounts that are:

        -   Synchronized from Active Directory with the Microsoft Azure AD Connect tool for customers with a single Active Directory forest configuration.

        -   Federated with Active Directory Federation Services (AD FS) 2.0 or later from your on-premises Active Directory.

## <a name="overview_rms"></a>Overview of the onboarding process
Onboarding has two major components:

-   **Core capabilities** - tasks required for tenant configuration and integration with Azure AD, if needed. Core capabilities also provide the baseline for onboarding other Microsoft Online eligible services.

-   **Service onboarding** - tasks required to configure Azure RMS standalone or with Azure AD Connect directory synchronization or AD FS.

The following diagram describes the timeline for using the FastTrack Center benefit.

![](../Image/1-rms_onboarding_process.png)

The basic process is as follows:

-   Microsoft will attempt to contact you within 30 days from the date you purchase an eligible plan. You can also request assistance from the [FastTrack Center](http://fasttrack.microsoft.com/) if you are ready to deploy these services for your organization. To request assistance, sign in to the FastTrack Center (http://fasttrack.microsoft.com), go to the dashboard, select your company name, click the Offers tab, and click the request assistance button for the eligible service.

-   The Microsoft team will help you with core capabilities, and then will help you onboard once for each eligible service.

All onboarding support will be provided remotely by assigned Microsoft personnel:

-   Microsoft will remotely assist you with various onboarding activities by using a combination of tools, documentation, and guidance. If you want Microsoft to do certain configuration tasks for you, you may choose to provide appropriate access and permissions to Microsoft for carrying out these tasks.

-   Onboarding support is provided by the FastTrack Center, and is available during normal business hours for a given region.

-   Onboarding support is available in Traditional Chinese, English, French, German, Italian, Japanese, Portuguese (Brazil), or Spanish.

-   The Microsoft team can work directly with you or your representative, as you may designate.

## <a name="expectations_src_environ_rms"></a>Expectations for your source environment
You may already have Microsoft Active Directory on-premise in your source environment that you want to integrate with Microsoft Azure Active Directory for leveraging rich identity management from a single console. The FastTrack Center benefit includes helping you integrate Microsoft Azure Active Directory with your existing on-premise implementation. If integration is required, your source environment must be at a minimum level for that application.

The following table shows what is expected in your existing source environment for onboarding.

|Activity|Source environment expectation|
|------------|----------------------------------|
|Core capabilities|Active Directory forests with the functional forest level set to Windows Server 2008 or above, with the following forest configuration:<br /><br />-   Single Active Directory forest<br />-   Multiple Active Directory forests **Note:** For all multiple forests configurations, AD FS deployment is out of scope for the FastTrack Center Benefit.|
|Service onboarding<br /><br />-   Azure RMS|On-premises Active Directory and environment have been prepared for Azure RMS, which includes remediation of identified issues that would prevent integration with Azure AD and Azure RMS features.|

## <a name="phases_onboarding_process_rms"></a>Phases of the onboarding process
Azure RMS onboarding has five primary phases, as shown in the following figure:

-   Initiate

-   Assess

-   Remediate

-   Enable

![](../Image/Intune_onboarding_phases_9-15-15.png)

For detailed tasks for each phase, see the [Microsoft responsibilities](#microsoft_responsibilities_rms) and  [Your responsibilities](#your_responsibilities_rms) sections.

### Initiate phase
After you have purchased the appropriate number of licenses, follow the guidance from the purchase confirmation email to associate the licenses to your existing tenant or new tenant. Microsoft will verify your eligibility for the FastTrack Center Benefit. Microsoft will attempt to contact you within 30 days from the date you purchase an eligible plan. You can also request assistance from the [FastTrack Center](http://fasttrack.microsoft.com/) if you are ready to deploy these services for your organization. To request assistance, sign in to the FastTrack Center (http://fasttrack.microsoft.com), go to the dashboard, select your company name, click the Offers tab, and click the request assistance button for the eligible service.

During this phase, we’ll discuss the onboarding process, verify data, and set up a kick-off meeting.

![](../Image/Microsoft_Azure_AD_Premium_initiate_phase_1.png)

### Assess phase
Once the onboarding process begins, Microsoft will work with you to assess your source environment and the requirements. Tools will be run to assess your environment, and Microsoft will guide you through assessing your on-premises Active Directory, Internet browsers, client devices' operating systems, DNS, network, infrastructure, and identity system to determine if any changes are required for onboarding. Based on your current setup, we’ll provide a remediation plan that will bring your source environment up to the minimum requirements for successful onboarding to Azure RMS. We’ll also set up appropriate checkpoint calls for the remediation phase.

![](../Image/Microsoft_Azure_AD_Premium_assess_phase_v6.png)

### Remediate phase
If needed, you’ll do the tasks in the remediation plan on your source environment so that you meet the requirements for onboarding each service.

![](../Image/Microsoft_Azure_AD_Premium_remediate_phase_1.png)

Before beginning the Enable phase, we’ll jointly verify the outcomes of the remediation activities to make sure you’re ready to proceed.

### Enable phase
When all remediation activities are complete, the project shifts to configuring the core infrastructure for service consumption and to provisioning Azure RMS.

**Enable phase - Core capabilities**

Enabling core capabilities involves service provisioning and tenant and identity integration. It also includes steps for providing a foundation for onboarding Microsoft Azure RMS.

Onboarding for Azure RMS can begin when core onboarding is finished.

**Enable phase – Azure RMS**

The Azure RMS environment can be set up with Azure AD Connect directory synchronization and Active Directory Federation Services (AD FS), as needed.

For Azure RMS scenarios that include synchronizing on-premises identities to the cloud, we’ll help you by adding IT administrators and users to your subscription, configuring management prerequisites, setting up Azure RMS, setting up directory synchronization using Azure AD Connect, and Active Directory Federation Services using Azure AD Connect, configuring test users and validating your core use cases for the service.

Azure RMS setup includes enabling the following features:

-   RMS Service Enablement

-   IRM Configuration for Exchange Online and Sharepoint Online

-   Rights Management Connector with Exchange on-premise and Sharepoint on-premise

-   RMS Sharing Application for Windows and non-Windows devices

![](../Image/Microsoft_Azure_AD_Premium_enable_phase_2.png)

## <a name="microsoft_responsibilities_rms"></a>Microsoft responsibilities

### General

-   Provide remote support assistance to you for the required configuration activities, as described in the detailed phase descriptions.

-   Provide available documentation and software tools, admin consoles, and scripts to help you reduce or eliminate configuration tasks.

Providing access and permissions to Microsoft isn’t required to use the FastTrack Center benefit. In some cases, you can choose to give Microsoft the appropriate access and permissions to perform specific activities on your behalf.

### Initiate phase

-   Contact you within 30 days of the purchase of eligible licenses for a new tenant.

-   Define which eligible services you want to onboard.

### Assess phase

-   Provide an administrative overview.

-   Provide guidance with:

    -   DNS, network, and infrastructure needs.

    -   Client needs (Internet browser, client operating system, and services' needs).

    -   User identity and provisioning.

    -   Identification of Directory Synchronization requirements.

    -   Enabling of eligible services that have been purchased and defined to be part of the onboarding.

    -   Identification of required piloting and test environment requirements.

-   Establish the timeline for remediation activities.

-   Provide a remediation checklist.

### Remediate phase

-   Hold conference calls with you according to the agreed-upon schedule to review the progress of the remediation activities.

-   Assist with running tools to identify and remediate issues, and with interpreting the results.

### Enable phase
Provide guidance about:

-   Activating your Azure RMS tenant.

-   Configuring firewall ports.

-   Configuring DNS for eligible services.

-   Validating connectivity to Azure RMS services.

-   For a single-forest environment:

    -   Installing a directory synchronization between your Active Directory Domain Services (AD DS) and Azure AD Connect, if required.

    -   Configuring password synchronization with the Azure AD Connect tool.

-   For a multiple forest environment:

    -   Installing Azure AD Connect synchronization, set up for multiple forest scenarios. Note that password hash sync and password writeback support multiple forest.  However, other writeback scenarios are not supported.

    -   Configure synchronization between on-premises Active Directory forests and Microsoft Azure AD directory (Azure Active Directory).

        > [!NOTE]
        > Development and implementation for custom rules extensions are out of scope.

-   For a single forest when the target is federated identities: Installing and configuring Active Directory Federation Services (AD FS) for local domain authentication with Microsoft Azure AD in a single-site, fault-tolerant configuration, if required.

    > [!NOTE]
    > For all multiple forest configurations, AD FS deployments are out of scope.

-   Testing single sign-on (SSO) functionality, if deployed.

-   Adding additional information security administrators to manage templates.

-   Assigning a super user account to Azure RMS.

-   Licensing two pilot users for Azure RMS.

-   Configuring two test distribution groups to validate policies.

-   Configuring one custom Azure RMS template for your directory.

-   Providing guidance in setting up SharePoint Online and Exchange Online integration with Azure RMS, including:

    -   Configuring and validating Exchange Online integration with Azure RMS.

    -   Setting up one test mail flow rule to encrypt sensitive messages sent to recipients outside your organization.

    -   Configuring and validating SharePoint Online protection of one test Library to be protected with Azure RMS.

-   Configuring one server on-premises with the RMS Connector, when applicable:

    -   Configuring and validating Exchange 2013/2010 on-premises integration with Azure RMS.

    -   Setting up one test mail flow rule to encrypt sensitive messages sent to recipients outside your organization using the Connector.

    -   Configuring and Validating SharePoint 2013/2010 on-premises protection of one test Library to be protected with Azure RMS.

-   Setting up RMS Sharing Application for Windows and non-Windows devices.

## <a name="your_responsibilities_rms"></a>Your responsibilities
This section describes some of your responsibilities during the onboarding process.

### General

-   Any enhancements and integrations to your Azure RMS tenant beyond the configurable options listed in this article.

-   Overall program and project management of your resources.

-   End-user communications, documentation, training, and change management.

-   Helpdesk documentation and training.

-   Producing any reports, presentations, or meeting minutes that are specific to your organization.

-   Creating architectural and technical documentation specific to your organization.

-   Designing, procuring, installing, and configuring hardware and networking.

-   Procuring, installing, and configuring software.

-   Managing, configuring, and applying security policies beyond those created for testing your Azure RMS services baseline configuration and functionality.

-   Enrolling user accounts beyond those used to test the Azure RMS services baseline configuration and functionality.

-   Network configuration, analysis, bandwidth validation, testing, and monitoring.

-   Managing a technical change management approval process and creating supporting documentation.

-   Modifying your operational model and operation guides.

-   Decommissioning and removing source environments and services previously used by the customer.

-   Constructing and maintaining your test environment.

-   Installing service packs and other required updates on infrastructure servers.

-   Providing and configuring any public SSL certificates.

-   Writing the organization’s Terms of Use (TOU) statement to be configured and displayed on devices owned by end users.

### Initiate phase

-   Work with the Microsoft team to begin onboarding of eligible services.

-   Participate in the engagement kick-off meeting, manage and lead participants from your organization, and confirm remediation timelines.

### Assess phase

-   Identify appropriate stakeholders (including a project manager) to complete the necessary assessment activities.

-   If you choose to, share your screen with Microsoft if guidance is needed when running evaluation tools against your environment or your Azure RMS subscription.

-   Participate in the meetings to create the remediation checklist and to contribute to the overall plan, including infrastructure, network, administration, directory synchronization preparation, network security, and federated identity topics.

-   Participate in the meetings to outline the user-provisioning approach.

-   Participate in the meetings to plan online service configuration.

-   Create a support plan for migration readiness.

### Remediate phase

-   Perform required steps to complete remediation activities identified in the Assess phase.

-   Participate in checkpoint meetings.

### Enable phase

-   If you choose to, share your screen with Microsoft if guidance is needed when making changes to your environment or to your Azure RMS subscription.

-   Manage resources as appropriate.

-   Configure network-related items per guidance from Microsoft.

-   Perform directory readiness and configure directory synchronization per guidance from Microsoft.

-   Configure security-related infrastructure (such as firewall ports) per guidance from Microsoft.

-   Implement the appropriate client infrastructure.

-   Implement a user-provisioning approach per guidance from Microsoft.

-   Enable various services per guidance from Microsoft.

## Want to learn more?
See [Microsoft Azure Rights Management](http://products.office.com/business/microsoft-azure-rights-management) and [Enterprise Mobility Suite](http://www.microsoft.com/en-us/server-cloud/products/enterprise-mobility-suite/default.aspx).

