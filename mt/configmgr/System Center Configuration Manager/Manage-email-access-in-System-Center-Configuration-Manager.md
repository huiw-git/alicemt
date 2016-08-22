---
title: "Manage email access in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-06-20
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 4544088a-4752-4e3a-aa0a-049f10d8f178
caps.latest.revision: 23
---
# Manage email access in System Center Configuration Manager
Use [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] conditional access to manage access to Exchange email based on conditions you specify.  
  
||  
|-|  
|[!INCLUDE[cm1602disclaimer](../System Center Configuration Manager/itokens/cm1602disclaimer_md.md)]|  
  
 You can manage access to:  
  
-   Microsoft Exchange On-premises  
  
-   Microsoft Exchange Online  
  
-   Exchange Online Dedicated  
  
> [!IMPORTANT]  
>  Conditional access for PCs and Windows 10 Mobile devices with apps using modern authentication is not currently available to all Intune customers. If you are already using these features, you do not need to take any action. You can continue to use them.  
>   
>  **This does not apply to PCs or Windows 10 Mobile devices for conditional access to Exchange On-premises.**  
>   
>  If you have not created conditional access policies for PCs or Windows 10 Mobile for apps using modern authentication, you will need to submit a request for access. You can find out more information about known issues as well as how to get access to this feature at the [connect site](http://go.microsoft.com/fwlink/?LinkId=761472).  
  
 If you configure conditional access, before a user can connect to their email, the device they use must:  
  
-   Be enrolled with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] or a domain joined PC.  
  
-   Register the device in Azure Active Directory (this happens automatically when the device is enrolled with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] (for Exchange Online only). Additionally, the client Exchange ActiveSync ID must be registered with Azure Active Directory (does not apply to Windows and Windows Phone devices connecting to Exchange On-premises).  
  
     For a domain joined PC, you must set it to automatically register with Azure Active Directory.  **Conditional Access for PCs** section in the [Manage access to services in System Center Configuration Manager](../System Center Configuration Manager/Manage-access-to-services-in-System-Center-Configuration-Manager.md) topic lists the full set of requirements to enable conditional access for  PCs.  
  
-   Be compliant with any [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] compliance policies deployed to that device  
  
 If a conditional access condition is not met, the user is presented with one of the following messages when they log in:  
  
-   If the device is not enrolled with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)], or is not registered in Azure Active Directory, a message is displayed with instructions about how to install the company portal app, enroll the device, and (for Android and iOS devices), activate email, which associates the device’s Exchange ActiveSync ID with the device record in Azure Active Directory.  
  
-   If the device is not compliant, a message is displayed that directs the user to the [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] web portal where they can find information about the problem and how to remediate it.  

**For mobile devices:**

You can restrict access to **Outlook Web Access (OWA)** on Exchange Online when accessed from a browser on **iOS** and **Android** devices.  Access will only be allowed from only supported browsers on compliant devices:

* Safari (iOS)
* Chrome (Android)
* Managed Browser (iOS and Android)

Unsupported browsers will be blocked.The OWA apps for iOS and Android are not supported.  They should be blocked through ADFS claims rules:
* Setup ADFS claims rules to block non-modern authentication protocols. Detailed instructions are provided in scenario 3 - [block all access to O365 except browser based applications](https://technet.microsoft.com/library/dn592182.aspx).
 
 **For PCs:**  
  
-   If the conditional access policy requirement is to allow **domain joined** or **compliant**, a message with instructions about how to enroll the device is displayed. If the PC does not meet either of the requirements, the user will be asked to enroll the device with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)].  
  
-   If the conditional access policy requirement is set to allow only domain joined windows devices, the device is blocked and a message to contact the IT admin is displayed.  
  
 You can block access to Exchange email from the devices built-in Exchange ActiveSync email client on the following platforms:  
  
-   Android 4.0 and later, Samsung Knox Standard 4.0 and later  
  
-   iOS 7.1 and later  
  
-   Windows Phone 8.1 and later  
  
-   The **Mail** application on Windows 8.1 and later  
  
 Outlook app for iOS and Android, and Outlook desktop 2013 and above  is supported for only Exchange Online.  
  
 The **on-premises Exchange connector** between [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and Exchange is required for conditional access to work.  
  
 You can configure a conditional access policy for Exchange On-premises from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. When you configure a conditional access policy for Exchange Online, you can begin the process in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, which launches the [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] console where you can complete the process.  
  
## Step 1: Evaluate the effect of the conditional access policy  
 Once you have configured the **on-premises Exchange connector**, you can use the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]**List of devices by Conditional Access State** report to identify devices that will be blocked from accessing Exchange after you configure the conditional access policy. This report also requires:  
  
-   A subscription to [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)]  
  
-   The service connection point should be configured and deployed  
  
 In the report parameters, select the [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] group you want to evaluate and, if required, the device platforms to which the policy will apply.  
  
 For more information about how to run reports, see [Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md).  
  
 After you run the report, examine these four columns to determine whether a user will be blocked:  
  
-   **Management Channel** – Indicates whether the device is managed by Intune, Exchange ActiveSync, or both.  
  
-   **Registered with AAD** – Indicates whether the device is registered with Azure Active Directory (known as Workplace Join).  
  
-   **Compliant** – Indicates whether the device is compliant with any compliance policies you deployed.  
  
-   **EAS Activated** – iOS and Android devices are required to have their Exchange ActiveSync ID associated with the device registration record in Azure Active Directory. This happens when the user clicks the **Activate Email** link in the quarantine email.  
  
    > [!NOTE]  
    >  Windows Phone devices always display a value in this column.  
  
 Devices that are part of a targeted group or collection will be blocked from accessing Exchange unless the column values match those listed in the following table:  
  
|Management channel|AAD registered|Compliant|EAS Activated|Resulting action|  
|------------------------|--------------------|---------------|-------------------|----------------------|  
|**Managed by Microsoft Intune and Exchange ActiveSync**|Yes|Yes|**Yes** or **No** is displayed|Email access allowed|  
|Any other value|No|No|No value is displayed|Email access blocked|  
  
 You can export the contents of the report and use the **Email Address** column to help you inform users that they will be blocked.  
  
## Step 2: Configure user groups or collections for the conditional access policy  
 You target conditional access policies to different groups or collections of users depending on the policy types. These groups contain the users that will be targeted, or exempt from the policy. When a user is targeted by a policy, each device they use must be compliant in order to access email.  
  
-   **For the Exchange Online policy** – to Azure Active Directory security user groups. You can configure these groups in the **Office 365 admin center**, or the **Intune account portal**.  
  
-   **For the Exchange On-premises policy** – to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] user collections. You can configure these in the **Assets and Compliance** workspace.  
  
 You can specify two group types in each policy:  
  
-   **Targeted groups** – User groups or collections to which the policy is applied  
  
-   **Exempted groups** – User groups or collections that are exempt from the policy (optional)  
  
 If a user is in both, they will be exempt from the policy.  
  
 Only the groups or collections which are targeted by the conditional access policy are evaluated for Exchange access.  
  
## Step 3: Configure and deploy a compliance policy  
 Ensure that you have created and deployed a compliance policy to all devices that the Exchange conditional access policy will be targeted to.  
  
 For details about how to configure the compliance policy, see [Manage device compliance policies in System Center Configuration Manager](../System Center Configuration Manager/Manage-device-compliance-policies-in-System-Center-Configuration-Manager.md).  
  
> [!IMPORTANT]  
>  If you have not deployed a compliance policy and then enable an Exchange conditional access policy, all targeted devices will be allowed access.  
  
 When you are ready, continue to **Step 4**.  
  
## Step 4: Configure the conditional access policy  
  
### For Exchange Online (and tenants in the new Exchange Online Dedicated environment)  
 The following flow is used by conditional access policies for Exchange Online to evaluate whether to allow or block devices.  
  
 ![ConditionalAccess8&#45;1](../System Center Configuration Manager/medias/ConditionalAccess8-1.png "ConditionalAccess8-1")  
  
 To access email, the device must:  
  
-   Enroll with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)]  
  
-   PCs must either be domain joined or be enrolled and compliant with the policies set in [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)].  
  
-   Register the device in Azure Active Directory (this happens automatically when the device is enrolled with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)].  
  
     For domain joined PCs, you must  set it up to [automatically register the device](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/) with Azure Active Directory.  
  
-   Have activated email, which associates the device’s Exchange ActiveSync ID with the device record in Azure Active Directory (applies to iOS and Android devices only).  
  
-   Be compliant with any deployed compliance policies  
  
 The device state is stored in Azure Active Directory which grants or blocks access to email, based on the evaluated conditions.  
  
 If a condition is not met, the user will be presented with one of the following messages when they log in:  
  
-   If the device is not enrolled, or registered in Azure Active Directory, a message is displayed with instructions about how to install the company portal app and enroll  
  
-   If the device is not compliant, a message is displayed that directs the user to the [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] Company Portal website or the Company Portal app where they can find information about the problem and how to remediate it.  
  
-   For a PC:  
  
    -   If the policy is set to require domain join, and the PC is not domain joined, a message is displayed to contact the IT admin.  
  
    -   If the policy is set to require domain join or compliant, then the PC does not meet either requirement, a message is displayed with instructions about how to install the company portal app and enroll.  
  
 The message is displayed on the device for Exchange Online users and tenants in the new Exchange Online Dedicated environment, and is delivered to the users email inbox for Exchange On-premises and legacy Exchange Online Dedicated devices.  
  
> [!NOTE]  
>  [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] conditional access rules override, allow, block and quarantine rules that are defined in the Exchange Online admin console.  
  
> [!NOTE]  
>  Conditional access policy must be configured in the Intune console. The following steps begin by accessing the Intune console through Configuration Manager. If prompted, log in using the same credentials that were used to set up the service connection point between Configuration Manager and Intune.  
  
##### To enable the Exchange Online policy  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance**.  
  
2.  Expand **Compliance Settings**, expand **Conditional Access**, and then click **Exchange Online**.  
  
3.  On the **Home** tab, in the **Links** group, click **Configure Conditional Access Policy in the Intune Console**. You might need to provide the user name and password of the account used to connect [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] with any global administrator for the [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] service.  
  
     The [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] admin console opens.  
  
4.  In the [Microsoft Intune administration console](https://manage.microsoft.com), click **Policy** > **Conditional Access** > **Exchange Online Policy**.  
  
     ![HybridOnlineSetupIntune](../System Center Configuration Manager/medias/HybridOnlineSetupIntune.png "HybridOnlineSetupIntune")  
  
5.  On the **Exchange Online Policy** page, select **Enable conditional access policy for Exchange Online**. If you check this, the device must be compliant. If this is not checked then conditional access is not applied.  
  
    > [!NOTE]  
    >  If you have not deployed a compliance policy and then enable the Exchange Online policy, all targeted devices are reported as compliant.  
    >   
    >  Regardless of the compliance state, all users who are targeted by the policy will be required to enroll their devices with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)].  
  
6.  Under **Application access**, for outlook and other apps using modern authentication, you can choose to restrict access only to devices that are compliant for each platform.  Windows devices must either be domain joined, or be enrolled in Intune and compliant.  
  
    > [!TIP]  
    >  **Modern authentication** brings Active Directory Authentication Library (ADAL)-based sign in to Office clients.  
    >   
    >  -   The ADAL based authentication enables Office clients to engage in browser-based authentication (also known as passive authentication).  To authenticate, the user is directed to a sign-in web page.  
    > -   This new sign-in method enables new scenarios such as, conditional access, based on **device compliance** and whether **multi-factor authentication** was performed.  
    >   
    >  This [article](https://support.office.com/en-US/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517) has more detailed information on how modern authentication works.  
  
     Using Exchange Online with Configuration Manager and Intune, you can not only manage mobile devices with conditional access, but also desktop computers as well. PCs must either be domain joined, or be enrolled in Intune and compliant. You can set the following requirements:  
  
    -   **Devices must be domain joined or compliant.** PCs must either be domain joined or compliant with the policies. If a PC does not meet either of these requirements, the user is prompted to enroll the device with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)].  
  
    -   **Devices must be domain joined.** PCs must be domain joined to access Exchange Online. If a  PC is not domain joined, access to email is blocked and the user is prompted to contact the IT admin.  
  
    -   **Devices must be compliant.** PCs must be enrolled in [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] and compliant. If a PC is not enrolled, a message with instructions on how to enroll is displayed.  
    
7.  Under **Outlook web access (OWA)**, you can choose to allow access to Exchange Online only through the supported browsers: Safari (iOS), and Chrome (Android). Access from other browsers will be blocked. The same platform restrictions you selected for Application access for Outlook also apply here.

    On **Android** devices, users must enable the browser access.  To do this the end-user must enable the “Enable Browser Access” option on the enrolled device as follows:
     1. Launch the **Company Portal app**.
     2. Go to the **Settings** page from the triple dots (…) or the hardware menu button.
      3.    Press the **Enable Browser Access** button.
      4.    In the Chrome browser, sign out of Office 365 and restart Chrome.

     On **iOS and Android** platforms, To identify the device that is used to access the service, Azure Active Directory will issue a Transport layer security ( TLS) certificate to the device.  The device displays the certificate with a prompt to the end-user to select the certificate as seen in the screenshots below. The end-user must select this certificate before they can continue to use the browser.

     **iOS**

     ![screenshot of the certificate prompt on an ipad](../System Center Configuration Manager/medias/mdm-browser-ca-ios-cert-prompt_v2.png)

    **Android**

    ![screenshot of the certificate prompt on an Android device](../System Center Configuration Manager/medias/mdm-browser-ca-android-cert-prompt.png)
  
7.  For**Exchange ActiveSync mail apps**, you can choose to block email from accessing Exchange Online if the device is noncompliant, and select whether to allow or block access to email when Intune cannot manage the device.  
  
8.  Under **Targeted Groups**, select the Active Directory security groups of users to which the policy will apply.  
  
    > [!NOTE]  
    >  For users that are in the Targeted groups, the Intune polices will replace Exchange rules and policies.  
    >   
    >  Exchange will only enforce Exchange allow, block and quarantine rules, and Exchange policies if:  
    >   
    >  -   The user is not licensed for Intune.  
    > -   The user is licensed for Intune, but the user does not belong to any security groups targeted in the conditional access policy.  
  
9. Under **Exempted Groups**, select the Active Directory security groups of users that are exempt from this policy. If a user  is in both the targeted and exempted groups, they will be exempt from the policy and will have access to their email.  
  
10. When you are finished, click **Save**.  
  
-   You do not have to deploy the conditional access policy; it takes effect immediately.  
  
-   After a user creates an email account, the device is blocked immediately.  
  
-   If a blocked user enrolls the device with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] (or remediates noncompliance), email access is unblocked within 2 minutes.  
  
-   If the user un-enrolls their device, email is blocked after about 6 hours.  
  
### For Exchange on-premises (and tenants in the legacy Exchange Online Dedicated environment)  
 The following flow is used by conditional access policies for Exchange on-premises and tenants in the legacy Exchange Online Dedicated environment to evaluate whether to allow or block devices.  
  
 ![ConditionalAccess8&#45;2](../System Center Configuration Manager/medias/ConditionalAccess8-2.png "ConditionalAccess8-2")  
  
##### To enable the Exchange On-premises policy  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance**.  
  
2.  Expand **Compliance Settings**, expand **Conditional Access**, and then click **On-Premises Exchange**.  
  
3.  On the **Home** tab, in the **On-Premises Exchange** group, click **Configure Conditional Access Policy**.  
  
4.  **Beginning in version 1602 of Configuration Manager**, On the **General** page of the **Configure Conditional Access Policy Wizard**, specify whether you want to override the Exchange Active Sync default rule. Click this option if you want enrolled and compliant devices to always have access to email, even when the default rule is set to quarantine or block access.  
  
    > [!NOTE]  
    >  There is an issue with the default override for Android devices. If the default access rule of the Exchange server is set to **Block** and the Exchange conditional access policy is enabled with the default rule override option, then the Android devices of the targeted users may not get unblocked even after the devices are Intune enrolled and compliant.  To workaround this issue, set the Exchange default access rule to **Quarantine**. The device does not get access to Exchange by default, and the administrator can get a report from the Exchange server on the list of devices that are being quarantined.  
  
     If you have not setup a notification email account when you set up the Exchange connector, you will see a warning on this page, and the **Next** button is disabled.  Before you can proceed, you must first configure the notification email settings in the Exchange Connector and then  come back to the **Configure Conditional Access Policy Wizard** to complete the process.  
  
     ![HybridCondAccessWiz1](../System Center Configuration Manager/medias/HybridCondAccessWiz1.PNG "HybridCondAccessWiz1")  
  
     Click **Next**.  
  
5.  On the **Targeted Collections** page, add one or more user collections. In order to access Exchange, users in these collections must enroll their devices with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] and also be compliant with any compliance policies you deployed.  
  
     ![HybridCondAccessWiz2](../System Center Configuration Manager/medias/HybridCondAccessWiz2.PNG "HybridCondAccessWiz2")  
  
     Click **Next**.  
  
6.  On the **Exempted Collections** page, add any user collections that you want to be exempt from the conditional access policy. Users in these groups, do not need to enroll their devices with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] and do not need to be compliant with any deployed compliance policies in order to access Exchange.  
  
     ![HybridCondAccessWiz3](../System Center Configuration Manager/medias/HybridCondAccessWiz3.png "HybridCondAccessWiz3")  
  
     If a user appears in both the targeted and exempted lists, they will be exempt from the conditional access policy.  
  
     Click **Next**.  
  
7.  On the **Edit User Notification** page, configure the email that [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] sends to users with instructions about how to unblock their device (in addition to the email that Exchange sends).  
  
     You can edit the default message and use HTML tags to format how the text appears. You can also send an email in advance to your employees notifying them of the upcoming changes and providing them with instructions about enrolling their devices.  
  
     ![HybridCondAccessWiz4](../System Center Configuration Manager/medias/HybridCondAccessWiz4.PNG "HybridCondAccessWiz4")  
  
    > [!NOTE]  
    >  Because the Intune notification email containing remediation instructions is delivered to the user’s Exchange mailbox, in the event that the user’s device gets blocked before they receive the email message, they can use an unblocked device or other method to access Exchange and view the message.  
  
    > [!NOTE]  
    >  In order for Exchange to be able to send the notification email, you must configure the account that will be used to send the notification email. You do this when you configure the properties of the Exchange Server connector.  
    >   
    >  For details, see [Manage mobile devices with System Center Configuration Manager and Exchange](../System Center Configuration Manager/Manage-mobile-devices-with-System-Center-Configuration-Manager-and-Exchange.md).  
  
     Click **Next**.  
  
8.  On the  **Summary** page, review your settings, and then complete the wizard.  
  
-   You do not have to deploy the conditional access policy, it takes effect immediately.  
  
-   After a user sets up an Exchange ActiveSync profile, it might take from 1-3 hours for the device to be blocked (if it is not managed by [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)]).  
  
-   If a blocked user then enrolls the device with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] (or remediates noncompliance), email access will be unblocked within 2 minutes.  
  
-   If the user un-enrolls from [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] it might take from 1-3 hours for the device to be blocked.  
  
## See Also  
 [Manage access to services in System Center Configuration Manager](../System Center Configuration Manager/Manage-access-to-services-in-System-Center-Configuration-Manager.md)