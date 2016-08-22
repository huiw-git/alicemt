---
title: "Manage access to O365 services for PCs managed by System Center Configuration Manager"
ms.custom: na
ms.date: 2016-08-16
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ccdb424a-b603-4ccc-af36-558924248022
caps.latest.revision: 15
---
# Manage access to O365 services for PCs managed by System Center Configuration Manager
  
 
 Beginning with version 1602 of Configuration Manager, you can configure conditional access for PCs managed by System Center Configuration Manager.  
  
> [!IMPORTANT]  
>  This is a pre-release feature available in update 1602 and update 1606. Pre-release features are included in the product for early testing in a production environment, but should not be considered production ready. For more information, see [Use pre-release features from updates](../System Center Configuration Manager/Install-in-console-updates-for-System-Center-Configuration-Manager.md#bkmk_prerelease).
> - After you install update 1602, the feature type displays as released even though it is pre-release.
> - If you then update from 1602 to 1606, the feature type displays as released even through it remains pre-release.
> - If you update from version 1511 directly to 1606, the feature type displays as pre-release.
  
 If you are looking for information on how to configure conditional access for devices enrolled  and managed by Intune, or PCs that are domain joined and are not evaluated for compliance, see [Manage access to services in System Center Configuration Manager](../System Center Configuration Manager/Manage-access-to-services-in-System-Center-Configuration-Manager.md).  
  
> [!IMPORTANT]  
>  Conditional access for PCs and Windows 10 Mobile devices with apps using modern authentication is not currently available to all **Intune** customers. If you are already using these features in **Intune**, you do not need to take any action. You can continue to use them.  
>   
>  **This does not apply to PCs or Windows 10 Mobile devices for conditional access to Exchange On-premises.**  
>   
>  If you have not created conditional access policies for PCs or Windows 10 Mobile for apps using modern authentication, you will need to submit a request for access. You can find out more information about known issues as well as how to get access to this feature at the [connect site](http://go.microsoft.com/fwlink/?LinkId=761472).  
  
## Supported Services  
  
-   Exchange Online  
  
-   SharePoint Online  
  
## Supported PCs  
  
-   Windows 7  
  
-   Windows 8.1  
  
-   Windows 10 is not yet fully supported.  If you try to set to conditional access for Windows 10 PCs, you may encounter some issues.  See [Known issues](#bkmk_KnownIssues) for more details.  
  
## Configure conditional access  
 To setup conditional access, you must first create a compliance policy and configure conditional access policy. When you configure conditional access policies for PCs you can require that the PCs be compliant with the compliance policy in order to access Exchange Online and SharePoint Online services.  
  
### Prerequisites  
  
-   ADFS Sync, and an O365 subscription. The O365 subscription is for setting up Exchange Online and SharePoint Online.  
  
-   A Microsoft Intune Subscription. The Microsoft Intune Subscription should be configured in Configuration Manager Console. This still requires that you are in a hybrid deployment.  
  
 The PCs must meet the following requirements:  
  
-   [Prerequisites](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1) for automatic device registration with Azure Active Directory  
  
     You can register PCs with Azure AD through the compliance policy.  
  
    -   For Windows 8.1 and Windows 10 PCs, you can use an Active Directory Group Policy to configure your devices to register automatically with Azure AD.  
  
    -   o   For Windows 7 PCs, you must deploy the device registration software package to your Windows 7 PC through System Center Configuration Manager. The [Automatic device registration with Azure Active Directory for Windows Domain-Joined Devices](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1) topic has more details.  
  
-   Must use Office 2013 or Office 2016 with modern authentication [enabled](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a).  
  
 The steps described below apply to both Exchange Online and SharePoint Online  
  
### Step 1. Configure compliance policy  
 In the Configuration Manager Console, create a compliance policy with the following rules:  
  
-   Require registration in Azure Active Directory: This rule checks if the user’s device is work-place joined to Azure AD, and if not, the device is automatically registered in Azure AD. Automatic registration is only supported on Windows 8.1. For Windows 7 PCs, deploy an MSI to perform the auto registration. For more details, see [Automatic device registration with Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1)  
  
-   **All required updates installed with a deadline older than a certain number of days:** This rule checks to see if the user’s device has all required updates (specified in the Required automatic updates rule) within deadline and grace period specified by you, and automatically install the any pending required updates.  
  
-   **Require BitLocker drive encryption:** This is a check to see if the primary drive (e.g. C:\\) on the device is BitLocker encrypted. If Bitlocker encryption is not enabled on the primary device access to email and SharePoint services is blocked.  
  
-   **Require Antimalware:** This is a check to see if the antimalware software (System Center Endpoint Protection or Windows Defender only) is enabled and running. If it is not enabled, access to email and SharePoint services is blocked.  
  
### Step 2. Evaluate the effect of conditional access  
 Run the Conditional Access Compliance Report. It can be found in Monitoring section under Reports >Compliance and Settings Management . This displays the compliance status for all devices.  Devices that are reported as not compliant will be blocked from accessing  Exchange Online and SharePoint Online.  
  
 ![CA&#95;compliance&#95;report](../System Center Configuration Manager/medias/CA_compliance_report.png "CA_compliance_report")  
  
### Configure Active Directory Security Groups  
 You target conditional access policies to groups of users depending on the policy types. These groups contain the users that will be targeted, or exempt from the policy. When a user is targeted by a policy, each device they use must be compliant in order to be able to access the service.  
  
 Active Directory security user groups. These user groups should be synchronized to Azure Active Directory. You can also configure these groups in the Office 365 admin center, or the Intune account portal.  
  
 You can specify two group types in each policy:  
  
-   **Targeted groups** – User groups  to which the policy is applied  
  
-   **Exempted groups** – User groups that are exempt from the policy (optional)  
    If a user is in both, they will be exempt from the policy.  
  
     Only the groups, which are targeted by the conditional access policy, are evaluated.  
  
### Step 3.  Create a conditional access policy, for Exchange Online and SharePoint Online  
  
1.  In the Configuration Manager console, click **Assets and Compliance**.  
  
2.  To create a policy for Exchange Online, select **Enable conditional access policy for Exchange Online**.  
  
     To create a policy for SharePoint Online, select **Enable conditional access policy for Exchange Online**.  
  
3.  On the **Home** tab, in the **Links** group, click **Configure Conditional Access Policy in the Intune Console**. You might need to supply the user name and password of the account used to connect Configuration Manager with Intune.  
  
     The Intune admin console will open.  
  
4.  For Exchange Online, in the Microsoft Intune administration console, click **Policy > Conditional Access > Exchange Online Policy**.  
  
     For SharePoint Online, in the Microsoft Intune administration console, click **Policy > Conditional Access > SharePoint Online Policy**.  
  
5.  Set the Windows PC requirement  to**Devices must be compliant option**.  
  
6.  Under **Targeted Groups**, click **Modify** to select the Azure Active Directory security groups to which the policy will apply.  
  
    > [!NOTE]  
    >  The users groups to which the conditional access policies are applied should also have the compliance policy applied to them.  
  
     Under **Exempted Groups**, optionally, click **Modify** to select the Azure Active Directory security groups that are exempt from this policy.  
  
7.  Click **Save** to create and save the policy  
  
 End-users who are blocked due to noncompliance will view compliance information in the System Center Configuration Manager Software Center and will initiate a new policy evaluation when compliance issues are remediated.  
  
##  <a name="bkmk_KnownIssues"></a> Known issues  
 You may see the following issues when using this feature:  
  
-   In this 1602 update,  the 5 day compliance is not enforced. Even if compliance check on the end-user’s device has happened more than 5 days ago, users still can access Office 365 and SharePoint online.  
  
-   When a device is not compliant with the compliance policy, the reason is not automatically displayed. The end- user must go to the new Software Center to find the reason for non-compliance. The reason is displayed in the Device compliance section of the Software Center.  
  
-   Windows 10 users may see multiple access failures when trying to reach O365 and/or SharePoint online resources. Note that conditional access is not fully supported for Windows 10.  
  
> [!IMPORTANT]  
>  Conditional access for PCs is not currently available to all Intune customers. If you are already using conditional access for PCs with **Intune**, you do not need to take any action. You can continue to use it.  
> If you have not created conditional access policies for PCs you will need to submit a request for access. You can find out more information about known issues as well as how to get access to this feature at the [connect site](http://go.microsoft.com/fwlink/?LinkId=761472).  
  
## See Also  
 [Protect data and site infrastructure with System Center Configuration Manager](../System Center Configuration Manager/Protect-data-and-site-infrastructure-with-System-Center-Configuration-Manager.md)