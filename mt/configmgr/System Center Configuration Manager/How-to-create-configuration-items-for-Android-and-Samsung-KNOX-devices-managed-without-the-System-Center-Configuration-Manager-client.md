---
title: "How to create configuration items for Android and Samsung KNOX devices managed without the System Center Configuration Manager client"
ms.custom: na
ms.date: 2016-07-22
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: c28d5ef5-3ea7-4ba2-af01-6600aa805d48
caps.latest.revision: 17
caps.handback.revision: 0
---
# How to create configuration items for Android and Samsung KNOX devices managed without the System Center Configuration Manager client
||  
|-|  
|[!INCLUDE[cm1602disclaimer](../System Center Configuration Manager/itokens/cm1602disclaimer_md.md)]|  
  
 Use the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] **Android and Samsung KNOX** configuration item to manage settings  for Android and Samsung KNOX devices that are enrolled in Microsoft Intune or managed on-premises by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
### To create an Android and Samsung KNOX configuration item  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and compliance**.  
  
2.  In the **Assets and Compliance** workspace, expand **Compliance Settings**, and then click **Configuration Items**.  
  
3.  On the **Home** tab, in the **Create** group, click **Create Configuration Item**.  
  
4.  On the **General** page of the **Create Configuration Item Wizard**, specify a name, and optional description for the configuration item.  
  
5.  Under **Specify the type of configuration item that you want to create**, select **Android and Samsung KNOX**.  
  
6.  Click **Categories** if you create and assign categories to help you search and filter configuration items in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
7.  On the **Supported Platforms** page of the wizard, select the specific Android or Samsung KNOX platforms that will evaluate the configuration item.  
  
8.  On the **Device Settings** page of the wizard, select the settings group that you want to configure. See [Android and Samsung KNOX configuration item settings reference](#BKMK_setref) in this topic for details, and then click **Next**.  
  
    > [!TIP]  
    >  If the setting that you want is not listed, select the **Configure additional settings that are not in the default setting groups check box**.  
  
9. On each settings page, configure the settings you require, and whether you want to remediate them when they are not compliant on devices (when this is supported).  
  
10. For each settings group, you can also configure the severity that will be reported when a configuration item is found to be noncompliant from:  
  
    -   **None** - Devices that fail this compliance rule do not report a failure severity for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports.  
  
    -   **Information** - Devices that fail this compliance rule report a failure severity of **Information** for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports.  
  
    -   **Warning** - Devices that fail this compliance rule report a failure severity of **Warning** for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports.  
  
    -   **Critical** - Devices that fail this compliance rule report a failure severity of **Critical** for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports.  
  
    -   **Critical with event** - Devices that fail this compliance rule report a failure severity of **Critical** for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports. This severity level is also be logged as a Windows event in the application event log.  
  
11. On the **Platform Applicability** page of the wizard, review any settings that are not compatible with the supported platforms you selected earlier. You can go back and remove these settings, or you can continue.  
  
    > [!TIP]  
    >  Unsupported settings are not assessed for compliance.  
  
12. Complete the wizard.  
  
 You can view the new configuration item in the **Configuration Items** node of the **Assets and Compliance** workspace.  
  
##  <a name="BKMK_setref"></a> Android and Samsung KNOX configuration item settings reference  
  
### Password  
 These settings apply to both Android and Samsung KNOX devices.  
  
|Setting|Details|  
|-------------|-------------|  
|**Require password settings on mobile devices**|Require a password on supported devices.|  
|**Minimum password length (characters)**|The minimum length for the password.|  
|**Password expiration in days**|The number of days before a password must be changed.|  
|**Number of passwords remembered**|Prevents re-using previously used passwords.|  
|**Number of failed logon attempts before device is wiped**|Wipes the device if this number of login attempts fail.|  
|**Idle time before device is locked**|Select the amount of time before the device will be locked if it is not being used.|
|**Password quality**|Select the password complexity level required and also whether biometric devices can be used.|  
|**Allow Smart Lock and other trust agents**|Let’s you control the Smart Lock feature on compatible Android devices. This phone capability, sometimes known as trust agents lets you disable or bypass the device lock screen password if the device is in a trusted location such as when it is connected to a specific Bluetooth device, or when it is near to an NFC tag. You can use this setting to prevent end users from configuring Smart Lock.|
  
###  <a name="BKMK_Device"></a> Device  
 These settings apply to Samsung KNOX devices only.  
  
|Setting name|Details|  
|------------------|-------------|  
|**Factory reset**|Allow the user to perform a factory reset on the device.|  
|**Clipboard share between applications**|Use the clipboard to copy and paste between apps.|  
  
### Cloud  
 These settings apply to Samsung KNOX devices only.  
  
|Setting|Details|  
|-------------|-------------|  
|**Google backup**|Allows use of Google backup.|  
|**Google account auto sync**|Allows Google account settings to be automatically synchronized.|  
  
### Security  
  
|Setting|Details|  
|-------------|-------------|  
|**Camera**|Allows the use of the device camera.<br /><br /> Applies to Android and Samsung KNOX devices.|  
|**YouTube**|Allows use of the YouTube app on the device.<br /><br /> Applies to Samsung KNOX devices only.|  
|**Power off**|Allows the device to be powered off.<br /><br /> Applies to Samsung KNOX devices only.|  
  
### Encryption  
 These settings apply to both Android and Samsung KNOX devices.  
  
|Setting|Details|  
|-------------|-------------|  
|**File encryption on device**|Requires that files on the mobile device are encrypted.|  
  
### Kiosk mode (Samsung KNOX only)  
 Kiosk mode allows you to lock a device to only allow certain features to work. For example, you can allow a device to only run one managed app that you specify, or you can disable the volume buttons on a device. These settings might be used for a demonstration model of a device, or a device that is dedicated to performing only one function, such as a point of sale device.  
  
##### To configure kiosk mode for a Samsung KNOX device  
  
1.  On the **Configure Kiosk Mode Settings for Samsung KNOX Devices** page of the **Create Configuration Item Wizard**, specify the following information:  
  
    |Setting|More information|  
    |-------------|----------------------|  
    |**Select app**|Click **Browse** to select a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Android application (with the extension **.apk**) that will be allowed to run when the device is in kiosk mode. No other apps will be allowed to run on the device.|  
    |**Volume buttons**|Enables or disables the use of the volume buttons on the device.|  
    |**Screen sleep and wake button**|Enables or disables the screen sleep wake button on the device.|  
  
###  <a name="BKMK_Compliantdroid"></a> Compliant and noncompliant apps (Android)  
 Let’s you specify a list of Android apps that are compliant, or not compliant in your company. You can then use reports to display devices that have noncompliant apps installed, and the associated user.  
  
 You cannot specify both compliant and noncompliant apps in the same configuration item.  
  
##### To specify the compliant or noncompliant apps list  
  
1.  On the **Compliant and Noncompliant Apps (Android)** page, specify the following information:  
  
    |Setting|More information|  
    |-------------|----------------------|  
    |**Noncompliant apps list**|Select this option if you want to specify a list of apps that will be reported as noncompliant if installed by users.|  
    |**Compliant apps list**|Select this option if you want to specify a list of apps that users are allowed to install. Any other installed apps will be reported as noncompliant.|  
    |**Add**|Adds an app to the selected list. Specify a name of your choice, optionally the app publisher, and the URL to the app in the app store.<br /><br /> To specify the URL, from the [apps section of Google Play](https://play.google.com/store/apps), search for the app you want to use.<br /><br /> Open the app’s page, and copy the URL to the clipboard. You can now use this as the URL in either the compliant or noncompliant apps list.<br /><br /> **Example:** Search Google Play for **Microsoft Office Mobile**. The URL you use will be **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.|  
    |**Edit**|Let’s you edit the name, publisher and URL of the selected app.|  
    |**Remove**|Deletes the selected app from the list.|  
    |**Import**|Imports a list of apps you have specified in a comma-separated values file. Use the format, application name, publisher, app URL in the file.|  
  
2.  When you are finished, click **Next**.  
  
 You can use one of the following reports monitor compliant and noncompliant apps:  
  
-   **List of noncompliant Apps and Devices for a specified user** - Displays information about users and devices that have apps installed that are not compliant with a policy you specified.  
  
-   **Summary of Users who have Noncompliant Apps** - Displays information about users that have apps installed that are not compliant with a policy you specified.  
  
 For information about how to use reports, see [Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md).  
  
## See Also  
 [Configuration items for devices managed without the System Center Configuration Manager client](../System Center Configuration Manager/Configuration-items-for-devices-managed-without-the-System-Center-Configuration-Manager-client.md)