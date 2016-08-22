---
title: "Manage SharePoint Online access in System Center Configuration Manager"
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
ms.assetid: c1b3fb75-f3ab-4886-9421-d81da7ef589d
caps.latest.revision: 11
caps.handback.revision: 0
---
# Manage SharePoint Online access in System Center Configuration Manager
Use the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] **SharePoint Online** conditional access policy to manage access to OneDrive for Business files located on SharePoint online, based on conditions you specify.  
  
> [!IMPORTANT]  
>  Conditional access for PCs and Windows 10 Mobile devices with apps using modern authentication is not currently available to all Intune customers. If you are already using these features, you do not need to take any action. You can continue to use them.  
>   
>  If you have not created conditional access policies for PCs or Windows 10 Mobile for apps using modern authentication, you will need to submit a request for access. You can find out more information about known issues as well as how to get access to this feature at the [connect site](http://go.microsoft.com/fwlink/?LinkId=761472).  
  
 When a targeted user attempts to connect to a file using a supported app such as OneDrive on their device, the following evaluation occurs:  
  
 ![ConditionalAccess8&#45;6](../System Center Configuration Manager/medias/ConditionalAccess8-6.png "ConditionalAccess8-6")  
  
 To connect to the required files, the device running OneDrive must:  
  
-   Be enrolled with [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] or a domain joined PC.  
  
-   Register the device in Azure Active Directory (this happens automatically when the device is enrolled with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)].  
  
     For domain joined PCs, you must set it up to [automatically register](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/) with Azure Active Directory.  
  
-   Be compliant with any deployed [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] compliance policies  
  
 The device state is stored in Azure Active Directory which grants or blocks access to the files, based on the conditions you specify.  
  
 If a condition is not met, the user is presented with one of the following messages when they log in:  
  
-   If the device is not enrolled with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)], or is not registered in Azure Active Directory, a message is displayed with instructions about how to install the company portal app and enroll.  
  
-   If the device is not compliant, a message is displayed that directs the user to the [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] web portal where they can find information about the problem, and how to remediate it.  

- For mobile devices:

  You can restrict access to SharePoint Online when accessed from a     browser from **iOS** and **Android** devices.  Access will only be allowed from only supported browsers on compliant devices:
* Safari (iOS)
* Chrome (Android)
* Managed Browser (iOS and Android)

  Unsupported browsers will be blocked.
-   For a PC:  
  
    > [!IMPORTANT]  
    >  Conditional access for PCs is not currently available to all Intune customers. If you are already using conditional access for PCs, you do not need to take any action. You can continue to use it.  
    > If you have not created conditional access policies for PCs you will need to submit a request for access. You can find out more information about known issues as well as how to get access to this feature at the [connect site](http://go.microsoft.com/fwlink/?LinkId=761472).  
  
    -   If the policy is set to require domain join, and the PC is not domain joined, a message is displayed to contact the IT admin.  
  
    -   If the policy is set to require domain join or compliant, then the PC does not meet either requirement, a message is displayed with instructions about how to install the company portal app and enroll.  
  
 You can block access to SharePoint Online from the following apps:  
  
-   Microsoft Office Mobile (Android)  
  
-   Microsoft OneDrive (Android and iOS)  
  
-   Microsoft Word (Android and iOS)  
  
-   Microsoft Excel (Android and iOS)  
  
-   Microsoft PowerPoint (Android and iOS)  
  
-   Microsoft OneNote (Android and iOS)  
  
## Steps to configure conditional access for SharePoint Online  
  
### Step 1: Configure Active Directory security groups  
 Before you start, configure Azure Active Directory security groups for the conditional access policy. You can configure these groups in the **Office 365 admin center**, or the **Intune account portal**. These groups contain the users that will be targeted, or exempt from the policy. When a user is targeted by a policy, each device they use must be compliant in order to access resources.  
  
 You can specify two group types in a SharePoint Online policy:  
  
-   **Targeted groups** – Contains groups of users to which the policy will apply  
  
-   **Exempted groups** – Contains groups of users that are exempt from the policy (optional)  
  
 If a user is in both groups, they will be exempt from the policy.  
  
### Step 2: Configure and deploy a compliance policy  
 Ensure that you create and deploy a compliance policy to all devices that the SharePoint Online policy will be targeted to.  
  
> [!NOTE]  
>  While compliance policies are deployed to [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] groups, or [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] collections, conditional access policies are targeted to Azure Active Directory security groups.  
  
 For details about how to configure the compliance policy, see [Manage device compliance policies in System Center Configuration Manager](../System Center Configuration Manager/Manage-device-compliance-policies-in-System-Center-Configuration-Manager.md).  
  
> [!IMPORTANT]  
>  If you have not deployed a compliance policy and then enable the SharePoint Online policy, all targeted devices will be allowed access.  
  
 When you are ready, continue to **Step 3**.  
  
###  <a name="BKMK_OneDrive"></a> Step 3: Configure the SharePoint Online policy  
 Next, configure the policy to require that only managed and compliant devices can access SharePoint Online. This policy will be will be stored in Azure Active Directory.  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance**.  
  
2.  Select **Enable conditional access policy for SharePoint Online.**.  
  
     ![IntuneSASharePointOnlineCAPolicy](../System Center Configuration Manager/medias/IntuneSASharePointOnlineCAPolicy.png "IntuneSASharePointOnlineCAPolicy")  
  
3.  Under **Application access** for Outlook and apps that use modern authentication, you can choose to restrict access to only devices that are compliant for each platform.  
  
    > [!TIP]  
    >  **Modern authentication** brings Active Directory Authentication Library (ADAL)-based sign in to Office clients.  
    >   
    >  -   The ADAL based authentication enables Office clients to engage in browser-based authentication (also known as passive authentication).  To authenticate, the user is directed to a sign-in web page.  
    > -   This new sign-in method enables new scenarios such as, conditional access, based on **device compliance** and whether **multi-factor authentication** was performed.  
    >   
    >  This [article](https://support.office.com/en-US/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517) has more detailed information on how modern authentication works.  
  
     For windows PCs, the PC must either be domain joined, or enrolled with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] and compliant. You can set the following requirements:  
  
    -   **Devices must be domain joined or compliant.** This means that the PCs must either be domain joined or compliant with the policies set in [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)]. If the PC does not meet either of these requirements, the user is prompted to enroll the device with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)].  
  
    -   **Devices must be domain joined.** This means that the PCs must be domain joined to access Exchange Online. If the PC is not domain joined access to email is blocked and the user is prompted to contact the IT admin.  
  
    -   **Devices must be compliant.** This means that the PCs must be enrolled in [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] and compliant. If the PC is not enrolled, a message with instructions on how to enroll is displayed.  

4.  Under **Browser access** to SharePoint Online and OneDrive for Business, you can choose to allow access to Exchange Online only through the supported browsers: Safari (iOS), and Chrome (Android). Access from other browsers will be blocked.  The same platform restrictions you selected for Application access for OneDrive also apply here.

    On **Android** devices, users must enable the browser access.  To do this the end-user must enable the “Enable Browser Access” option on the enrolled device as follows:
    1.  Launch the **Company Portal app**.
    2.  Go to the **Settings** page from the triple dots (…) or the hardware menu button.
    3.  Press the **Enable Browser Access** button.
    4.  In the Chrome browser, sign out of Office 365 and restart Chrome.

    On **iOS and Android** platforms, To identify the device that is used to access the service, Azure Active Directory will issue a Transport layer security ( TLS) certificate to the device.  The device displays the certificate with a prompt to the end-user to select the certificate as seen in the screenshots below. The end-user must select this certificate before they can continue to use the browser.

     **iOS**

     ![screenshot of the certificate prompt on an ipad](../System Center Configuration Manager/medias/mdm-browser-ca-ios-cert-prompt_v2.png)

     **Android**

      ![screenshot of the certificate prompt on an Android device](../System Center Configuration Manager/medias/mdm-browser-ca-android-cert-prompt.png)
  
4.  On the **Home** tab, in the **Links** group, click **Configure Conditional Access Policy in the Intune Console**. You might need to supply the user name and password of the account used to connect [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)].  
  
     The [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] admin console will open.  
  
5.  In the [Microsoft Intune administration console](https://manage.microsoft.com), click **Policy** > **Conditional Access** > **SharePoint Online Policy**.  
  
6.  Select **Block apps from accessing SharePoint Online if the device is noncompliant**.  
  
7.  Under **Targeted Groups**, click **Modify** to select the Azure Active Directory security groups to which the policy will apply.  
  
8.  Under **Exempted Groups**, optionally, click **Modify** to select the Azure Active Directory security groups that are exempt from this policy.  
  
9. When you are done, click **Save**.  
  
 You do not have to deploy the conditional access policy, it takes effect immediately.  
  
 See [Manage SharePoint Online access with Microsoft Intune](https://technet.microsoft.com/library/dn705844.aspx) for information about how you can monitor the policy from the [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] console.  
  
## See Also  
 [Manage access to services in System Center Configuration Manager](../System Center Configuration Manager/Manage-access-to-services-in-System-Center-Configuration-Manager.md)