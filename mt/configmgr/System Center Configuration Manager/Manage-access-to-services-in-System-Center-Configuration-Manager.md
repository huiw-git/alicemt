---
title: "Manage access to services in System Center Configuration Manager"
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
ms.assetid: 76d86613-b87f-4fe5-9236-a573e00b613a
caps.latest.revision: 26
---
# Manage access to services in System Center Configuration Manager
Use **conditional access** in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] to help secure email and other services on devices that are enrolled with [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)], depending on conditions you specify.  
  
 For information about conditional access on PCs that are managed with System Center Configuration Manager and evaluated for compliance, see [Manage access to O365 services for PCs managed by System Center Configuration Manager](../System Center Configuration Manager/Manage-access-to-O365-services-for-PCs-managed-by-System-Center-Configuration-Manager.md).  
  
> [!IMPORTANT]  
>  Conditional access for PCs and Windows 10 Mobile devices with apps using modern authentication is not currently available to all Intune customers. If you are already using these features, you do not need to take any action. You can continue to use them.  
>   
>  **This does not apply to PCs or Windows 10 Mobile devices for conditional access to Exchange On-premises.**  
>   
>  If you have not created conditional access policies for PCs or Windows 10 Mobile for apps using modern authentication, you will need to submit a request for access. You can find out more information about known issues as well as how to get access to this feature at the [connect site](http://go.microsoft.com/fwlink/?LinkId=761472).  
  
 A typical flow for conditional access might look as follows:  
  
 ![ConditionalAccess4](../System Center Configuration Manager/medias/ConditionalAccess4.png "ConditionalAccess4")  
  
 Use conditional access to manage access to the following services:  
  
-   Microsoft Exchange On-premises  
  
-   Microsoft Exchange Online  
  
-   Exchange Online Dedicated  
  
-   SharePoint Online  
  
-   Skype for Business Online 

-   Dynamics CRM Online 
  
 You can control access to Exchange Online and Exchange On-premises from the built-in email client on the following platforms:  
  
-   Android 4.0 and later, Samsung Knox Standard 4.0 and later  
  
-   iOS 7.1 and later  
  
-   Windows Phone 8.1 and later  
  
-   Mail application on Windows 8.1 and later  
  
 You can control access to SharePoint Online from the following apps for the listed platforms:  
  
-   Microsoft Office Mobile (Android)  
  
-   Microsoft OneDrive (Android and iOS)  
  
-   Microsoft Word (Android and iOS)  
  
-   Microsoft Excel (Android and iOS)  
  
-   Microsoft PowerPoint (Android and iOS)  
  
-   Microsoft OneNote (Android and iOS)  
  
 Office desktop applications can access Exchange Online and SharePoint Online on PCs running:  
  
-   Office desktop 2013 and later with [modern authentication](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) enabled.  
  
-   Windows 7.0 or Windows 8.1  
  
> [!NOTE]  
>  PCs should be domain joined or be complaint with the policies set in [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)].  
  
 To implement conditional access, you configure two policy types in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]:  
  
-   **Compliance policies** are optional policies you can deploy to user collections and evaluate settings like:  
  
    -   Passcode  
  
    -   Encryption  
  
    -   Whether the device is jailbroken or rooted  
  
    -   Whether email on the device is managed by a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] or [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] policy  
  
     If no compliance policy is deployed to a device, then any applicable conditional access policies will treat the device as compliant.  
  
-   **Conditional access policies** are configured for a particular service, and define rules such as which Azure Active Directory security user groups or [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] user collections will be targeted, or exempt.  
  
     You configure the On-Premises Exchange conditional access policy from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. However, when you configure an Exchange Online or SharePoint Online policy, this opens the [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] admin console where you configure the policy.  
  
     Unlike other [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] or [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] policies, you do not deploy conditional access policies. Instead, you configure these once, and they apply to all targeted users.  
  
 When devices do not meet the conditions you configure, the user is guided though the process of enrolling the device and fixing the issue that prevents the device from being compliant.  
  
## Before you start  
 Before you start using conditional access, ensure that you have the correct requirements in place:  
  
|Policy type|Requirements|  
|-----------------|------------------|  
|Exchange Online (using the shared multi-tenant environment)|Conditional access to Exchange Online supports devices that run:<br /><br /> -   Windows 8.1 and later (when enrolled with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)])<br />-   Windows 7.0 or Windows 8.1 (when domain joined)<br />-   Windows Phone 8.1 and later<br />-   iOS 7.1 and later<br />-   Android 4.0 and later, Samsung Knox Standard 4.0 and later<br /><br /> Additionally:<br /><br /> -   Devices must be workplace joined, which registers the device with the Azure Active Directory Device Registration Service (AAD DRS).<br />     Domain joined PCs must be automatically registered with Azure Active Directory through group policy or MSI. The **Conditional access for PCs** section in this topic describes all the requirements for enabling conditional access for a PC.<br />     AAD DRS will be activated automatically for Intune and Office 365 customers. Customers who have already deployed the ADFS Device Registration Service will not see registered devices in their on-premises Active Directory.<br />-   You must use an Office 365 subscription that includes Exchange Online (such as E3) and users must be licensed for Exchange Online.<br />-   The optional **Exchange Server connector** is optional and connects [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to Microsoft Exchange Online and helps you monitor device information through the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console (see [Manage mobile devices with System Center Configuration Manager and Exchange](../System Center Configuration Manager/Manage-mobile-devices-with-System-Center-Configuration-Manager-and-Exchange.md)). You do not need to use the connector to use compliance policies or conditional access policies, but is required to run reports that help evaluate the impact of conditional access.|  
|Exchange Online Dedicated|Conditional access to Exchange Online Dedicated supports devices that run:<br /><br /> -   Windows 8 and later (when enrolled with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)])<br />-   Windows 7.0 or Windows 8.1 (when domain joined)<br />     Conditional access to domain joined PCs only to tenants in the new Exchange Online dedicated environment.<br />-   Windows Phone 8 and later<br />-   Any iOS device that uses an Exchange ActiveSync (EAS) email client<br />-   Android 4 and later.<br />-   For tenants in the legacy Exchange Online Dedicated environment:<br />     You must use the  **Exchange Server connector** which connects [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to Microsoft Exchange On-premises. This lets you manage mobile devices and enables conditional access (see [Manage mobile devices with System Center Configuration Manager and Exchange](../System Center Configuration Manager/Manage-mobile-devices-with-System-Center-Configuration-Manager-and-Exchange.md)).<br />-   For tenants in the new Exchange Online Dedicated environment:<br />     The optional **Exchange Server connector** connects [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to Microsoft Exchange Online and helps you manage device information (see [Manage mobile devices with System Center Configuration Manager and Exchange](../System Center Configuration Manager/Manage-mobile-devices-with-System-Center-Configuration-Manager-and-Exchange.md)). You do not need to use the connector to use compliance policies or conditional access policies, but is required to run reports that help evaluate the impact of conditional access.|  
|Exchange On-premises|Conditional access to Exchange On-premises supports:<br /><br /> -   Windows 8 and later (when enrolled with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)])<br />-   Windows Phone 8 and later<br />-   Native email app on iOS<br />-   Native email app on Android 4 or later<br />-   Microsoft Outlook app is not supported (Android and iOS).<br /><br /> Additionally:<br /><br /> <ul><li>Your Exchange version must be Exchange 2010 or later. Exchange server Client Access Server (CAS) array is supported. **Tip:**      If your Exchange environment is in a CAS server configuration, then you must configure the on-premises Exchange connector to point to one of the CAS servers.</li><li>You must use the **Exchange Server connector** which connects [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to Microsoft Exchange On-premises. This lets you manage mobile devices  and enables conditional access (see [Manage mobile devices with System Center Configuration Manager and Exchange](../System Center Configuration Manager/Manage-mobile-devices-with-System-Center-Configuration-Manager-and-Exchange.md)).<br /><br /> <ul><li>Make sure that you are using the latest version of the **on-premises Exchange connector**. The on-premises Exchange connector should be configured through the Configuration Manager console. For a detailed walkthrough, see [Manage mobile devices with System Center Configuration Manager and Exchange](../System Center Configuration Manager/Manage-mobile-devices-with-System-Center-Configuration-Manager-and-Exchange.md).</li><li>The connector must  be configured only on the System Center Configuration Manager Primary Site.</li><li>This connector  supports Exchange CAS environment. <br />        When configuring the connector, you must set it so it talk to the one of the Exchange CAS servers.</li></ul></li><li>Exchange ActiveSync can be configured with certificate based authentication, or user credential entry</li></ul>|  
|Skype for Business Online|Conditional access to SharePoint Online supports devices that run:<br /><br /> -   iOS 7.1 and later<br />-   Android 4.0 and later<br />-   Samsung Knox Standard 4.0 or later<br /><br /> Additionally, you must enable modern authentication for Skype for Business Online. Fill this [connect form](https://connect.microsoft.com/office/Survey/NominationSurvey.aspx?SurveyID=17299&ProgramID=8715) to be enrolled in the modern authentication program.<br />All your end-users must be using the Skype for Business Online. If you have a deployment with both Skype for Business Online and Skype for Business on-premises, conditional access policy will not be applied to end-users who are in the on-premises deployment.|  
|SharePoint Online|Conditional access to SharePoint Online supports devices that run:<br /><br /> -   Windows 8.1 and later (when enrolled with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)])<br />-   Windows 7.0 or Windows 8.1 (when domain joined)<br />-   Windows Phone 8.1 and later<br />-   iOS 7.1 and later<br />-   Android 4.0 and later, Samsung Knox Standard 4.0 and later<br /><br /> Additionally:<br /><br /> -   Devices must be workplace joined, which registers the device with the Azure Active Directory Device Registration Service (AAD DRS).<br />     Domain joined PCs must be automatically registered with Azure Active Directory through group policy or MSI. The **Conditional access for PCs** section in this topic describes all the requirements for enabling conditional access for a PC.<br />     AAD DRS will be activated automatically for Intune and Office 365 customers. Customers who have already deployed the ADFS Device Registration Service will not see registered devices in their on-premises Active Directory.<br />-   A SharePoint Online subscription is required and users must be licensed for SharePoint Online.|  
|Conditional access for PCs|You can setup conditional access for PCs that run Office desktop applications to access **Exchange Online** and **SharePoint Online** for PCs that meet the following requirements:<br /><br /> -   The PC must be running Windows 7.0 or Windows 8.1.<br />-   The PC must either be domain joined or compliant.<br />     In order to be compliant, the PC must be enrolled in [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] and comply with the policies.<br />     For domain joined PCs, you must  set it up to [automatically register the device](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/) with Azure Active Directory.<br />-   [Office 365 modern authentication must be enabled](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/), and have all the latest Office updates.<br />     Modern authentication brings Active Directory Authentication Library (ADAL) based sign-in to Office 2013 Windows clients and enables better security like **multi-factor authentication**, and **certificate-based authentication**.<br />-   Setup ADFS claims rules to block non-modern authentication protocols.|  
  
## Next Steps  
 Read the following topics to learn how to configure compliance policies and conditional access policies for your required scenario:  
  
-   [Manage device compliance policies in System Center Configuration Manager](../System Center Configuration Manager/Manage-device-compliance-policies-in-System-Center-Configuration-Manager.md)  
  
-   [Manage email access in System Center Configuration Manager](../System Center Configuration Manager/Manage-email-access-in-System-Center-Configuration-Manager.md)  
  
-   [Manage SharePoint Online access in System Center Configuration Manager](../System Center Configuration Manager/Manage-SharePoint-Online-access-in-System-Center-Configuration-Manager.md)  
  
-   [Manage Skype for Business Online access](../System Center Configuration Manager/Manage-Skype-for-Business-Online-access.md)  
  
## See Also  
 [Get started with compliance settings in System Center Configuration Manager](../System Center Configuration Manager/Get-started-with-compliance-settings-in-System-Center-Configuration-Manager.md)