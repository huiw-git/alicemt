---
title: "Managing Mobile Devices by Using Configuration Manager"
ms.custom: na
ms.date: 08/22/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 52e39a67-8794-4e9b-9cb6-cadf08247a3b
caps.latest.revision: 5
---
# Managing Mobile Devices by Using Configuration Manager
You can use the following solutions to manage mobile devices in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]:  
  
-   You can use the [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] connector to enroll mobile devices that run Windows Phone 8, Windows RT, and iOS. This solution uses the built-in management client and does not install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client, but does automatically install PKI certificates on the mobile devices. This solution does not require you to have your own PKI, but does require a [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] subscription.  
  
-   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] can enroll mobile devices and deploy the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client on supported mobile operating systems when the mobile device and site system roles use PKI certificates. This solution automatically installs PKI certificates onto the mobile devices but requires you to run Active Directory Certificate Services and an enterprise certification authority.  
  
-   When the mobile devices run Windows CE or Windows Mobile 6.0, you must install the mobile device legacy client by using a package and program. This solution also requires PKI certificates that must be installed independently from [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
-   If you cannot use the other mobile device management solutions, you can use the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Exchange Server connector to find and manage mobile devices that connect to Microsoft Exchange Server or Exchange Online. Because a management client is not installed, management is more limited for this solution than the others. For example, with the exception of Android devices that use the [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] connector, you cannot deploy applications to these mobile devices. However, you can retrieve some inventory information, define settings and access rules, and issue **wipe** commands for these mobile devices in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
 For more information about these mobile device management solutions, see [Determine How to Manage Mobile Devices in Configuration Manager](../System Center Configuration Manager/Determine-How-to-Manage-Mobile-Devices-in-Configuration-Manager.md).  
  
 For more information about how to install the mobile device legacy client for Windows CE mobile devices, see [Mobile Device Management in Configuration Manager](http://go.microsoft.com/fwlink/p/?LinkId=242730) in the [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] documentation library.  
  
## What’s New in Configuration Manager for Mobile Devices  
  
> [!NOTE]  
>  [!INCLUDE[cm5reuse]()] the [Getting Started with Configuration Manager 2012](assetId:///ff235204-7390-4f48-b211-f3707dee3035) guide.  
  
 The following items are new for mobile devices since [!INCLUDE[sccmshortname]()]:  
  
-   Enrollment for mobile devices in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] is now natively supported by using the two new enrollment site system roles (the enrollment point and the enrollment proxy point) and a Microsoft enterprise certification authority. For more information about how to configure and enroll mobile devices in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [How to Enroll Mobile Device Clients in Configuration Manager 2012](assetId:///b420da33-e374-4ebe-ba9f-3cdf870c3acf).  
  
-   New in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], the Exchange Server connector lets you find and manage devices that connect to Exchange Server, on-premise or hosted, by using the Exchange ActiveSync protocol. Use this mobile device management process when you cannot install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client on the mobile device. For more information, see [How to Manage Mobile Devices by Using the Exchange Server Connector in Configuration Manager 2012](assetId:///825bc5d1-5779-4280-9ba2-7b45db357a00).  
  
-   If you have mobile devices that you managed with [!INCLUDE[sccmshortname]()], and you cannot enroll them by using [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)], you can continue to use them with [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)]. The installation for this mobile device client is still the same. However, whereas [!INCLUDE[sccmshortname]()] did not require PKI certificates, [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] requires PKI certificates on the mobile device and the management points and distribution points. File collection is no longer supported for these mobile device clients in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]and, unlike the mobile devices that you can enroll with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] or manage by using the Exchange Server connector, you cannot manage settings for these mobile devices. In addition, the mobile device management inventory extension tool (DmInvExtension.exe) is no longer supported. This functionality is replaced with the Exchange Server connector.  
  
## What’s New in Configuration Manager SP1 for Mobile Devices  
 The following items are new for mobile devices in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] SP1:  
  
-   The client settings group to configure mobile device enrollment settings is no longer named **Mobile Devices** and is now named **Enrollment**. This change and associated changes, such as the change from the client setting of **Mobile device enrollment profile** to **Enrollment profile**, reflects that the enrollment functionality is now extended to Mac computers.  
  
    > [!IMPORTANT]  
    >  The client certificates for mobile devices and Mac computers have different requirements. Therefore, if you configure client settings enrollment for mobile devices and Mac computers, do not configure the certificate templates to use the same user accounts.  
  
-   Mobile devices that are enrolled by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] SP1 now use the client policy polling interval setting in the **Client Policy** client setting group and no longer use the polling interval in the renamed **Enrollment** client setting group. This change lets you configure different client policy intervals for mobile devices that are enrolled by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], by using custom device client settings. You cannot create custom device client settings for **Enrollment**.  
  
-   You can enroll mobile devices that run Windows Phone 8, Windows RT, and iOS when you use the [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] connector. For more information, see [How to Manage Mobile Devices by Using the Microsoft Intune Connector in Configuration Manager](assetId:///2c6bd0e5-d436-41c8-bf38-30152d76be10).  
  
-   Users who have mobile devices that are enrolled by [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] and Android devices that are managed by the Exchange Server connector can install apps from the company portal. The company portal is the Application Catalog equivalent for these mobile devices.  
  
-   The new **Retire** option for mobile devices in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console is supported only for mobile devices that are enrolled by [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)].  
  
## What’s New in System Center 2012 R2 Configuration Manager for Mobile Devices  
 The following items are new for mobile device management in [!INCLUDE[sccm2012r2_1](../System Center Configuration Manager/itokens/sccm2012r2_1_md.md)]:  
  
-   Users can enroll Android devices by using the company portal app which will be available on Google Play. The company portal app is supported on Android devices as of Android 4.0. When users download the company portal app the installation includes the management agent. The management agent gives you the following management capabilities.  
  
    -   You can manage compliance settings which include password, camera, and encryption settings.  
  
    -   When you deploy apps to Android devices, you now have the option to install the apps directly to the device  
  
    -   Users are prompted to take required actions, such as app installations or updating device passcodes by using Android notifications.  
  
-   Users can enroll iOS devices by using the iOS company portal app which will be available in the App store. The company portal app can be installed on iOS devices as of iOS 6. The company portal app will allow users to perform the following actions:  
  
    -   Change or reset passwords.  
  
    -   Download and install company apps.  
  
    -   Enroll, unenroll, or wipe company content from their devices.  
  
-   Devices that run Windows RT, iOS and Android now support a deployment purpose of **Required**. This allows you to deploy apps automatically to devices according to a configured schedule.  
  
-   Wipe and retire functions now include the option to only remove company content from devices, see the table in [Help protect your data with remote wipe, remote lock, or passcode reset using Configuration Manager](assetId:///d83dc9ac-331a-49e5-b67f-f3b075d008df) for information about what company content is removed.  
  
-   You can configure enrolled devices as company-owned or personal-owned. Company-owned allows you to get software inventory on on all mobile devices. You can configure devices as personal-owned or company-owned by using the **Change ownership** action. Change ownership is only available for devices that are not domain-joined and do not have the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client installed.All mobile devices will report software inventory on company content when they are personal-owned or company-owned. iOS and Android will report a full software inventory on the device if they are set as Company-owned. You can configure enrolled devices as company-owned or personal-owned. Company-owned allows you to get software inventory on company content on all devices.  
  
-   You can use [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] to manage Windows 8.1 devices that are not joined to the domain and do not have the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client installed.