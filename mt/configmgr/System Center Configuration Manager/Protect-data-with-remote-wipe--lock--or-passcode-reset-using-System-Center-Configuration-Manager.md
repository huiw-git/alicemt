---
title: "Protect data with remote wipe, lock, or passcode reset using System Center Configuration Manager"
ms.custom: na
ms.date: 2016-08-12
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 770da7bd-02dd-474a-9604-93ff1ea0c1e4
caps.latest.revision: 18
caps.handback.revision: 0
---
# Protect data with remote wipe, lock, or passcode reset using System Center Configuration Manager
[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] provides selective wipe, full wipe, remote lock, and passcode reset capabilities. Mobile devices can store sensitive corporate data and provide access to many corporate resources. To protect devices you can issue:  
  
-   A full wipe to restore the device to its factory settings.  
  
-   A selective wipe to remove only company data.  
  
-   A remote lock to help secure a device that might be lost.  
  
-   Reset the device passcode.  
  
##  <a name="BKMK_Wipe"></a> Full Wipe  
 You might issue a wipe command to a device when you need to secure a lost device or when you retire a device from active use.  
  
 Issue a **full wipe** to a device to restore the device to its factory defaults. This removes all company and user data and settings.  You can do a full wipe on Windows Phone, iOS, Android, and Windows 10 devices.  
 
> [!NOTE]
> Wiping Windows 10 devices on versions earlier than version 1511 with less than 4 GB of RAM might leave the device unresponsive. [Learn more.](https://technet.microsoft.com/library/mt592024.aspx#full-wipe-disables-windows-10-devices-with-less-than-4-gb-ram) 
  
#### To initiate a remote wipe from the Configuration Manager console  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance** and select **Devices**. Alternatively, you can click **Device Collections** and select a collection.  
  
2.  Select the device that you want to retire/wipe.  
  
3.  Click **Remote Device Actions** in the **Device Group**, and then select **Retire/Wipe**.  
  
### Selective Wipe  
 Issue a **selective wipe** to a device to remove only company data. The following table describes by platform what data is removed and the effect on data that remains on the device after a selective wipe.  
  
 **iOS**  
  
|Content removed when retiring a device|iOS|  
|--------------------------------------------|---------|  
|Company apps and associated data installed by using [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)].|Apps are uninstalled. Company app data is removed.|  
|VPN and Wi-Fi profiles|Removed.|  
|Certificates|Removed and revoked.|  
|Settings|Removed, except for: **Allow voice roaming**, **Allow data roaming**, and **Allow automatic synchronization while roaming**.|  
|Management agent|Management profile is removed.|  
|Email profiles|For email profiles provisioned by [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)], the email account and email are removed.|  
  
 **Android and Android Samsung KNOX**  
  
|Content removed when retiring a device|Android|Samsung KNOX|  
|--------------------------------------------|-------------|------------------|  
|Company apps and associated data installed by using [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)].|Apps and data remain installed.|Apps are uninstalled.|  
|VPN and Wi-Fi profiles|Removed.|Removed.|  
|Certificates|Revoked.|Revoked.|  
|Settings|Requirements removed.|Requirements removed.|  
|Management agent|Device Administrator privilege is revoked.|Device Administrator privilege is revoked.|  
|Email profiles|Not applicable.|For email profiles provisioned by [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)], the email account and email are removed.|  
  
 **Windows 10, Windows 8.1,  Windows RT 8.1, and Windows RT**  
  
||||  
|-|-|-|  
|Content removed when retiring a device|Windows 10, Windows 8.1 and Windows RT 8.1|Windows RT|  
|Company apps and associated data installed by using [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)].|Apps are uninstalled and sideloading keys are removed. Apps using Windows Selective Wipe will have the encryption key revoked and data will no longer be accessible.|Sideloading keys are removed but apps remain installed.|  
|VPN and Wi-Fi profiles|Removed.|Not applicable.|  
|Certificates|Removed and revoked.|Not applicable.|  
|Settings|Requirements removed.||  
|Management agent|Not applicable. Management agent is built-in.|Not applicable. Management agent is built-in.|  
|Email profiles|Removes email that is EFS-enabled which includes the Mail app for Windows email and attachments.|Not applicable.|  
  
 **Windows 10 Mobile, Windows Phone 8.0 and Windows Phone 8.1**  
  
|||  
|-|-|  
|Content removed when retiring a device|Windows 10 Mobile, Windows Phone 8 and Windows Phone 8.1|  
|Company apps and associated data installed by using [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)].|Apps are uninstalled. Company app data is removed.|  
|VPN and Wi-Fi profiles|Removed for Windows 10 Mobile and Windows Phone 8.1|  
|Certificates|Removed for Windows Phone 8.1.|  
|Management agent|Not applicable. Management agent is built-in|  
|Email profiles|Removed (except Windows Phone 8.0)|  
  
 The following settings are also removed from Windows 10 Mobile and Windows Phone 8.1 devices:  
  
-   Require a password to unlock mobile devices  
  
-   Allow simple passwords  
  
-   Minimum password length  
  
-   Required password type  
  
-   Password expiration (days)  
  
-   Remember password history  
  
-   Number of repeated sign-in failures to allow before the device is wiped  
  
-   Minutes of inactivity before password is required  
  
-   Required password type – minimum number of character sets  
  
-   Allow camera  
  
-   Require encryption on mobile device  
  
-   Allow removable storage  
  
-   Allow web browser  
  
-   Allow application store  
  
-   Allow screen capture  
  
-   Allow geolocation  
  
-   Allow Microsoft Account  
  
-   Allow copy and paste  
  
-   Allow Wi-Fi tethering  
  
-   Allow automatic connection to free Wi-Fi hotspots  
  
-   Allow Wi-Fi hotspot reporting  
  
-   Allow factory reset  
  
-   Allow Bluetooth  
  
-   Allow NFC  
  
-   Allow Wi-Fi  
  
##### To initiate a remote wipe from the Configuration Manager console  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance** and select **Devices**. Alternatively, you can click **Device Collections** and select a collection.  
  
2.  Select the device that you want to retire/wipe.  
  
3.  Click **Remote Device Actions** in the **Device Group**, and then select **Retire/Wipe**.  
  
### Wiping Encrypting File System (EFS)-enabled content  
 Selective wipe of EFS-encrypted content is supported by Windows 8.1 and Windows RT 8.1. The following apply to a selective wipe of EFS-enabled content:  
  
-   Only apps and data that are protected by EFS using the same Internet domain as the [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] account are selectively wiped. For more information, see [Windows Selective Wipe for Device Data Management](http://technet.microsoft.com/library/dn486874.aspx).  
  
-   If there are any changes are made to the domain associated with EFS, the changes can take up to 48 hours before apps and data using the new domain can be selectively wiped.  
  
-   Each domain that is registered with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] is the domain that will be wiped.  
  
 The data and apps that are currently supported by EFS selective wipe are:  
  
-   Mail app for Windows  
  
-   Work Folders  
  
-   Files and folders encrypted by EFS. For more information, see [Best practices for the Encrypting File System](http://support.microsoft.com/kb/223316).  
  
### Best Practices for Selective Wipe  
  
-   For successful wipe of email, provision email profiles to iOS and Windows Phone 8.1 devices.  
  
-   For successful wipe of apps, make sure the apps are distributed through mobile device app management.  
  
-   For iOS, configure the setting “Allow backup to iCloud” to “Disallow” so that users can’t restore content using iCloud.  
  
-   If an account has been deactivated, then after one year, the account will be retired by Intune and a selective wipe will be performed.  
  
##  <a name="BKMK_Reset"></a> Passcode Reset  
 If a user forgets their passcode, you can help them by removing the passcode from a device or by forcing a new temporary passcode on a device. The table below lists how passcode reset works on different mobile platforms.  
  
|Platform|Passcode Reset|  
|--------------|--------------------|  
|iOS|Supported for clearing the passcode from a device. Does not create a new temporary passcode.|  
|Android|Supported and a temporary passcode is created.|  
|Windows 10|Not supported at this time.|  
|Windows Phone 8 and Windows Phone 8.1|Supported|  
|Windows RT 8.1 and Windows RT|Not Supported|  
|Windows 8.1|Not Supported|  
  
#### To reset the passcode on a mobile device remotely in Configuration Manager  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance** and select **Devices**. Alternatively, you can click **Device Collections** and select a collection.  
  
2.  Select the device or devices on which to reset the passcode.  
  
3.  Click **Remote Device Actions** in the **Device Group**, and then select **Passcode Reset**.  
  
#### To show the state of the passcode reset  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance** and select **Devices**. Alternatively, you can click **Device Collections** and select a collection.  
  
2.  Select the device or devices on which to show the state of the passcode reset.  
  
3.  Click **Remote Device Actions** in the **Device Group**, and then select **Show Passcode State**.  
  
##  <a name="BKMK_Lock"></a> Remote Lock  
 If a user loses their device you can lock the device remotely. The following table lists how remote lock works on different mobile platforms.  
  
|Platform|Remote Lock|  
|--------------|-----------------|  
|iOS|Supported|  
|Android|Supported|  
|Windows 10|Not supported at this time.|  
|Windows Phone 8 and Windows Phone 8.1|Supported|  
|Windows RT 8.1 and Windows RT|Supported if the current user of the device is the same user who enrolled the device.|  
|Windows 8.1|Supported if the current user of the device is the same user who enrolled the device.|  
  
#### To lock a mobile device remotely through the Configuration Manager console  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance** and select **Devices**. Alternatively, you can click **Device Collections** and select a collection.  
  
2.  Select the device or devices to lock.  
  
3.  Click **Remote Device Actions** in the **Device Group**, and then select **Remote Lock**.  
  
#### To show the state of the remote lock  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance** and select **Devices**. Alternatively, you can click **Device Collections** and select a collection.  
  
2.  Select the device on which to show the state of the remote lock.  
  
3.  Click **Remote Device Actions** in the **Device Group**, and then select **Show Remote Lock State**.  
  
## See Also  
 [Windows Selective Wipe for Device Data Management](http://technet.microsoft.com/library/dn486874.aspx)   
 [Hybrid mobile device management (MDM) with System Center Configuration Manager and Microsoft Intune](../System Center Configuration Manager/Hybrid-mobile-device-management--MDM--with-System-Center-Configuration-Manager-and-Microsoft-Intune.md)