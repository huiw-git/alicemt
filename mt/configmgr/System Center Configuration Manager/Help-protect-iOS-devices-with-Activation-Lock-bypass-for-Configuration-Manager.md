---
title: "Help protect iOS devices with Activation Lock bypass for Configuration Manager"
ms.custom: na
ms.date: 2016-02-24
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: c2e53d99-f19d-4a24-b422-9f54813aa2e2
caps.latest.revision: 14
---
# Help protect iOS devices with Activation Lock bypass for Configuration Manager
[!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] can help you manage iOS Activation Lock, a feature of the Find My iPhone app for iOS 7.1 and later devices. Activation Lock is enabled automatically when the Find My iPhone app is used on a device. After it is enabled, the user's Apple ID and password must be entered before anyone can:  
  
-   Turn off Find My iPhone  
  
-   Erase the device  
  
-   Reactivate the device  
  
> [!IMPORTANT]  
>  **Current known issues with Activation Lock bypass in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Technical Preview**  
>   
>  -   Due to an issue with decrypting the Activation Lock bypass code, the retrieval code displayed in the **Activation Lock Bypass** dialog box will not work. If you click **Refresh code**, you might see a message that a new code has been requested, but this process will not complete.  
>   
>      Because of this issue, you cannot currently see which devices are using Activation Lock.  
> -   When you wipe an Android device, you will see a dialog box asking if you want to bypass Activation Lock. Because this feature is not used by Android devices, you can safely ignore this message.  
  
## How Activation Lock affects you  
 While Activation Lock helps secure iOS devices and improves the chances of recovery if they are lost and stolen, this capability can present you, as an IT admin, with a number of challenges. For example:  
  
-   One of your users sets up Activation Lock on a device. The user then leaves the company and returns the device. Without the user's Apple ID and password, there is no way to reactivate the device.  
  
-   You need a report of all devices that have Activation Lock enabled.  
  
-   During a device refresh in your organization, you want to reassign some devices to a different department. You can only reassign devices that do not have Activation Lock enabled.  
  
 To help solve these problems, Apple introduced Activation Lock bypass in iOS 7.1. This lets you remove the Activation Lock from supervised devices without the user's Apple ID and password. Supervised devices can generate a device-specific Activation Lock bypass code, which is stored on Apple's activation server.  
  
> [!TIP]  
>  Supervised mode for iOS devices lets you use the Apple Configurator Tool to lock down a device to limit functionality to specific business purposes. Supervised mode is generally only for corporate-owned devices.  
  
## How Configuration Manager helps you manage Activation Lock  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] can request the Activation Lock status of both supervised and unsupervised devices that run iOS 7.1 and later. For supervised devices, Intune can retrieve the Activation Lock bypass code and directly issue it to the device. If the device has been wiped, you can directly access the device using the code as the username, and a blank password).  
  
 **The business benefits of this are:**  
  
-   The user gets the security benefits of the Find My iPhone app  
  
-   You can enable the user to do their work knowing that when the device needs to be repurposed, you can retire or unlock it  
  
## How to use Activation Lock bypass from the Configuration Manager console  
  
> [!IMPORTANT]  
>  After you bypass the Activation Lock on a device, it will automatically apply a new Activation Lock if the Find My iPhone app is opened. Because of this, **you should be in physical possession of the device before you follow this procedure**.  
  
-   In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance**.  
  
-   In the **Assets and Compliance** workspace, click **Devices**.  
  
-   Select an enrolled device that is in supervised mode, whose Activation Lock you want to bypass and then, on  the **Home** tab, click **Remote Device Actions** > **Activation Lock Bypass**.  
  
-   In the **Activation Lock Bypass** dialog box, the Activation Lock Bypass code for the selected device is displayed. Click **Send Bypass Command** to continue.  
  
-   Read the warning messages in the **Confirm Activation Lock Bypass** dialog box, and click **Yes** when you are ready to proceed.  
  
 You can examine the status of the unlock request from the **Activation Lock Bypass** dialog box.  
  
## See Also  
 [Hybrid mobile device management (MDM) with System Center Configuration Manager and Microsoft Intune](../System Center Configuration Manager/Hybrid-mobile-device-management--MDM--with-System-Center-Configuration-Manager-and-Microsoft-Intune.md)