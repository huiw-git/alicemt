---
title: "How to create configuration items for iOS and Mac OS X devices managed without the System Center Configuration Manager client"
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
ms.assetid: c378e0f7-be49-4b96-a46b-7c5d9638bd96
caps.latest.revision: 15
caps.handback.revision: 0
---
# How to create configuration items for iOS and Mac OS X devices managed without the System Center Configuration Manager client
Use the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]**iOS and Mac OS X** configuration item to manage settings  for iOS and Mac OS X devices that are enrolled in Microsoft Intune or managed on-premises by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
### To create an iOS and Mac OS X configuration item  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and compliance**.  
  
2.  In the **Assets and Compliance** workspace, expand **Compliance Settings**, and then click **Configuration Items**.  
  
3.  On the **Home** tab, in the **Create** group, click **Create Configuration Item**.  
  
4.  On the **General** page of the **Create Configuration Item Wizard**, specify a name, and optional description for the configuration item.  
  
5.  Under **Specify the type of configuration item that you want to create**, select **iOS and Mac OS X**.  
  
6.  Click **Categories** if you create and assign categories to help you search and filter configuration items in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
7.  On the **Supported Platforms** page of the wizard, select the specific iOS, or Mac OS X platforms that will evaluate the configuration item.  
  
8.  On the **Device Settings** page of the wizard, select the settings group that you want to configure. See [iOS and Mac OS X configuration item settings reference](#BKMK_Setref) in this topic for details, and then click **Next**.  
  
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
  
##  <a name="BKMK_Setref"></a> iOS and Mac OS X configuration item settings reference  
  
###  <a name="BKMK_Password"></a> Password  
  
|Setting name|Details|  
|------------------|-------------|  
|**Require password settings on mobile devices**|Require a password on supported devices.|  
|**Minimum password length (characters)**|The minimum length for the password.|  
|**Password expiration in days**|The number of days before a password must be changed.|  
|**Number of passwords remembered**|Prevents re-using previously used passwords.|  
|**Number of failed logon attempts before device is wiped**|Wipes the device if this number of login attempts fail.<br /><br /> (iOS only)|  
|**Password complexity**|Choose whether you can specify a PIN such as ‘1234’, or whether you must supply a strong password.|  
  
###  <a name="BKMK_Device"></a> Device  
 These settings apply to both iOS and Mac OS X devices.  
  
|Setting name|Details|  
|------------------|-------------|  
|**Voice dialing**|Allows use of the voice dialing feature on the device.|  
|**Voice assistant**|Allows use of a voice assistance app like Siri.|  
|**Voice assistant while locked**|Allows use of a voice assistance app like Siri when the device is locked.|  
|**Screen capture**|Allows you to take a screenshot of the device display.|  
|**Video chat client**|Allows use of video chat apps like Facetime.|  
|**Add game center friends**|Allows you to add friends in the game center app.|  
|**Multiplayer gaming**|Allows you to play games with other players on the Internet.|  
|**Personal wallet software while locked**|Allows use of personal wallet software like Passbook.|  
|**Diagnostic data submission**|Allow submission of app log files.|  
  
###  <a name="BKMK_Store"></a> Store  
 These settings apply to iOS devices only.  
  
|Setting name|Details|  
|------------------|-------------|  
|**Application store**|Allows access to the app store on the device.|  
|**Enter a password to access the application store**|Users must enter a password to access the app store.|  
|**In-app purchases**|Allows users to make in-app purchases.|  
  
###  <a name="BKMK_Browser"></a> Browser  
 These settings apply to iOS devices only.  
  
|Setting name|Details|  
|------------------|-------------|  
|**Default browser**|User can change the default Internet browser.|  
|**Autofill**|User can change autocomplete settings in the browser.|  
|**Active scripting**|Browser can run scripts, such as Active X scripts.|  
|**Pop-up blocker**|Enables or disables the browser pop-up blocker.|  
|**Cookies**|Allow cookies to be saved on the device.|  
|**Fraud warning**|Enable or disable warnings of potential fraudulent websites.|  
  
###  <a name="BKMK_Rating"></a> Content rating  
 These settings apply to iOS devices only.  
  
|Setting name|Details|  
|------------------|-------------|  
|**Explicit content in media store**|Specify if you want to allow adult content to be accessed from the app store.|  
|**Ratings region**|Specifies the country for which you want to apply ratings restrictions.|  
|**Movie rating**|Specify the maximum rating of movie content you want to allow.|  
|**TV show rating**|Specify the maximum rating of TV show content you want to allow.|  
|**App rating**|Specify the maximum rating of app content you want to allow.|  
  
> [!NOTE]  
>  The ratings you can select will vary depending on the **Ratings region** you selected.  
  
###  <a name="BKMK_Cloud"></a> Cloud  
 These settings apply to iOS devices only.  
  
|Setting name|Details|  
|------------------|-------------|  
|**Cloud backup**|Allow backup to a cloud service like iCloud.|  
|**Encrypted backup**|Allow the backup to a cloud service to be encrypted.|  
|**Document synchronization**|Allow document synchronization to a cloud service.|  
|**Photo synchronization**|Allow photo synchronization to a cloud service.|  
  
###  <a name="BKMK_Security"></a> Security  
 These settings apply to iOS devices only.  
  
|Setting name|Details|  
|------------------|-------------|  
|**Camera**|Allow use of the device camera.|  
  
###  <a name="BKMK_Roamin"></a> Roaming  
 These settings apply to iOS devices only.  
  
|Setting name|Details|  
|------------------|-------------|  
|**Voice roaming**|Allows voice calls when roaming.|  
|**Automatic synchronization while roaming**|Allows the device t automatically synchronize when roaming.|  
|**Data roaming**|Allow roaming between networks when accessing data.|  
  
###  <a name="BKMK_SysSecurity"></a> System security  
 These settings apply to iOS devices only.  
  
|Setting name|Details|  
|------------------|-------------|  
|**User to accept untrusted TLS certificates**|If **Allowed**, lets the user accept these certificates. If **Prohibited**, automatically rejects untrusted certificates.|
|**Allow Activation Lock (supervised mode only)**|Use this setting to enable iOS Activation Lock on **supervised** iOS devices that you manage. For more information about Activation Lock, see [Manage iOS Activation Lock with System Center Configuration Manager](../System Center Configuration Manager/Manage-iOS-Activation-Lock-with-System-Center-Configuration-Manager.md).
|**Lock screen control center**|Controls whether the control center app can be accessed when the device is locked.|  
|**Lock screen notification view**|Controls whether notifications can be viewed when the device is locked.|  
|**Lock screen today view**|Controls whether the Today view can be seen when the device is locked.|  
|**Fingerprint for unlocking**|Allow the use of the fingerprint sensor to unlock the device.|  
  
###  <a name="BKMK_Dataprot"></a> Data protection  
 These settings apply to iOS devices only.  
  
|Setting name|Details|  
|------------------|-------------|  
|**Open documents in managed apps in other unmanaged apps**|For use with apps managed by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] application management policies.|  
|**Open documents in unmanaged apps in other managed apps**|For use with apps managed by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] application management policies.|  
  
###  <a name="BKMK_CompiOS"></a> Compliant and noncompliant apps (iOS)  
 Let’s you specify a list of iOS apps that are compliant, or not compliant in your company. You can then use reports to display devices that have noncompliant apps installed, and the associated user.  
  
 You cannot specify both compliant and noncompliant apps in the same configuration item.  
  
##### To specify the compliant or noncompliant apps list  
  
1.  On the **Compliant and Noncompliant Apps (iOS)** page, specify the following information:  
  
    -   **Noncompliant apps list** - Select this option if you want to specify a list of apps that will be reported as noncompliant if installed by users.  
  
    -   **Compliant apps list** - Select this option if you want to specify a list of apps that users are allowed to install. Any other installed apps will be reported as noncompliant.  
  
    -   **Add** - Adds an app to the selected list. Specify a name of your choice, optionally the app publisher, and the URL to the app in the app store.  
  
         To specify the URL, from the iTunes App Store, search for the app you want to use.  
  
         Open the app’s page, and copy the URL to the clipboard. You can now use this as the URL in either the compliant or noncompliant apps list.  
  
         **Example:** Search the store for the **Microsoft Word for iPad** app. The URL you use will be **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.  
  
    -   **Edit** - Let’s you edit the name, publisher and URL of the selected app.  
  
    -   **Remove** - Deletes the selected app from the list.  
  
    -   **Import** - Imports a list of apps you have specified in a comma-separated values file. Use the format, application name, publisher, app URL in the file.  
  
2.  When you are finished, click **Next**.  
  
 You can use one of the following reports monitor compliant and noncompliant apps:  
  
-   **List of noncompliant Apps and Devices for a specified user** - Displays information about users and devices that have apps installed that are not compliant with a policy you specified.  
  
-   **Summary of Users who have Noncompliant Apps** - Displays information about users that have apps installed that are not compliant with a policy you specified.  
  
 For information about how to use reports, see [Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md).  
  
###  <a name="BKMK_CompiOS1"></a> Compliant and noncompliant apps (Mac OS X)  
 Let’s you specify a list of Mac OS X  apps that are compliant, or not compliant in your company. You can then use reports to display devices that have noncompliant apps installed, and the associated user.  
  
 You cannot specify both compliant and noncompliant apps in the same configuration item.  
  
##### To specify the compliant or noncompliant apps list  
  
1.  On the **Compliant and Noncompliant Apps (Mac OS X)** page, specify the following information:  
  
    -   **Noncompliant apps list** - Select this option if you want to specify a list of apps that will be reported as noncompliant if installed by users.  
  
    -   **Compliant apps list** - Select this option if you want to specify a list of apps that users are allowed to install. Any other installed apps will be reported as noncompliant.  
  
    -   **Add** - Adds an app to the selected list. Specify a name of your choice, optionally the app publisher, and the  bundle ID of the app.  
  
        > [!TIP]  
        >  To find the bundle ID of an app, use the following steps on a Mac computer that has the app installed:  
        >   
        >  1.  Open the folder in which the app is installed (for example, **/Applications**)  
        > 2.  Select the *<App Name\>***.app** bundle, and choose **Show Package Contents**  
        > 3.  Open the **Info.plist** file  
        > 4.  Check the value associated with the key **CFBundleIdentifier**  
        >   
        >  The format for Bundle ID is **com.contoso.appname**  
  
    -   **Edit** - Let’s you edit the name, publisher and bundle ID of the selected app.  
  
    -   **Remove** - Deletes the selected app from the list.  
  
    -   **Import** - Imports a list of apps you have specified in a comma-separated values file. Use the format, app name, publisher, app bundle ID in the file.  
  
2.  When you are finished, click **Next**.  
  
 You can use one of the following reports monitor compliant and noncompliant apps:  
  
-   **List of noncompliant Apps and Devices for a specified user** - Displays information about users and devices that have apps installed that are not compliant with a policy you specified.  
  
-   **Summary of Users who have Noncompliant Apps** - Displays information about users that have apps installed that are not compliant with a policy you specified.  
  
 For information about how to use reports, see [Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md).  
  
### iOS and Mac OS X custom profile settings  
 Use **iOS and Mac OS X Custom Profiles** to deploy settings that you created using the [Apple Configurator tool](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) to iOS and Mac OS X devices. This tool lets you create many settings that control the operation of these devices and export them to a configuration profile. You can then import this configuration profile into an iOS and Mac OS X custom profile and deploy the settings to users and devices in your organization.  
  
> [!NOTE]  
>  Ensure that the settings you export from the Apple Configurator tool are compatible with the version of iOS or Mac OS X on the devices to which you deploy the profile. For information about how incompatible settings are resolved, search for Configuration Profile Reference and Mobile Device Management Protocol Reference on the [Apple Developer](https://developer.apple.com/) web site.  
  
##### To create an iOS and Mac OS X custom profile  
  
1.  On the **Configure iOS and Mac OS X custom profile settings** page of the **Create Configuration Item Wizard**, specify the following information:  
  
    -   **Custom configuration profile name (displayed to users)** - Provide a name for the policy as it will be displayed on the device, and in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports.  
  
    -   **Import** - Choose a file that you exported from the Apple Configurator tool.  
  
    -   **Configuration profile details** - Displays the file that you imported.  
  
    -   **Remediate noncompliant settings** -  
  
         Select if you want to remediate noncompliant configuration settings (when supported).  
  
    -   **Noncompliance severity for reports** - Specify the severity level that is reported if this compliance policy is evaluated as noncompliant. The available severity levels are the following:  
  
        > [!NOTE]  
        >  When a Mac OS X device is in Sleep mode, policies and profiles cannot be delivered or inventoried. As a result, the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console might temporarily display the status Policy settings in error until the next time the device wakes from Sleep mode.  
  
        -   **None** Devices that fail this compliance rule do not report a failure severity for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports.  
  
        -   **Information** Devices that fail this compliance rule report a failure severity of **Information** for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports.  
  
        -   **Warning** Devices that fail this compliance rule report a failure severity of **Warning** for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports.  
  
        -   **Critical** Devices that fail this compliance rule report a failure severity of **Critical** for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports.  
  
        -   **Critical with event** Devices that fail this compliance rule report a failure severity of **Critical** for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports. This severity level is also be logged as a Windows event in the application event log.  
  
#### How to create a configuration profile file  
 You can create the configuration profile file used by the custom policy in two ways:  
  
-   Export the file (with the extension **.mobileconfig**) from the Apple Configurator tool.  
  
-   Author the file yourself using the appropriate schema from the [Apple Configuration Profile Key Reference](https://developer.apple.com/library/ios/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html).  
  
###  <a name="BKMK_KioskiOS"></a> Kiosk mode (iOS)  
 Kiosk mode allows you to lock a device to only allow certain features to work. For example, you can allow a device to only run one managed app that you specify, or you can disable the volume buttons on a device. These settings might be used for a demonstration model of a device, or a device that is dedicated to performing only one function, such as a point of sale device.  
  
##### To configure kiosk mode for iOS devices  
  
1.  On the **Configure Kiosk Mode Settings for iOS Devices** page of the **Create Configuration Item Wizard**, specify the following information:  
  
    -   **Select App** - Select the app that will be allowed to run when the device is in kiosk mode. No other apps will be allowed to run on the device. Choose from:  
  
        -   **Managed App** – Click Browse, then select a managed app.  
  
        -   **Store App** – specify the URL to an app on the app store then click **Get App ID** to populate the **App ID** field.  
  
         To find the app URL:  
  
        -   Using a search engine, find the app you want to use in the iTunes App Store and open the page for the app.  
  
        -   Copy the URL of the page and use this as the URL to specify the app you want to run in kiosk mode.  
  
        -   **Example:** Search for **Microsoft Word for iPad**. The URL you use will be **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.  
  
    -   **Touch** - Enables or disables the touch screen on the device.  
  
    -   **Screen rotation** - Enables or disables changing the screen orientation when you rotate the device.  
  
    -   **Volume buttons** - Enables or disables the use of the volume buttons on the device.  
  
    -   **Ringer switch** - Enables or disables the ringer (mute) switch on the device.  
  
    -   **Screen sleep and wake button** - Enables or disables the screen sleep wake button on the device.  
  
    -   **Auto lock** - Enables or disables automatic locking of the device.  
  
    -   **Mono audio** - Enables or disables the accessibility setting **Mono audio**.  
  
    -   **Voice over** - Enables or disables the accessibility setting **VoiceOver** which reads aloud text on the device display.  
  
    -   **Voice over adjustments** - Enables or disables voiceover adjustments which let you adjust the VoiceOver function (for example, how fast on-screen text is read aloud).  
  
    -   **Zoom** - Enables or disables the **Zoom** accessibility setting which lets you use touch to zoom into the device display.  
  
    -   **Zoom adjustments** - Enables or disables zoom adjustments which let you adjust the zoom function.  
  
    -   **Invert colors** - Enables or disables the **Invert Colors** accessibility setting which adjusts the display to help users with visual impairments.  
  
    -   **Invert colors adjustments** - Enables or disables invert colors adjustments which let you adjust the invert colors function.  
  
    -   **Assistive touch** - Enables or disables the **Assistive Touch** accessibility setting which helps users perform on screen gestures which might be difficult for them to perform.  
  
    -   **Assistive touch adjustments** - Enables or disables assistive touch adjustments which let you adjust the assistive touch function.  
  
    -   **Speech selection** - Enables or disables the **Speak Selection** accessibility settings which can read aloud the text you select.  
  
    -   **Remediate noncompliant settings** - Select if you want to remediate noncompliant configuration settings (when supported).  
  
    -   **Noncompliance severity for reports** - Specify the severity level that is reported if this compliance policy is evaluated as noncompliant. The available severity levels are:  
  
        -   **None** Devices that fail this compliance rule do not report a failure severity for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports.  
  
        -   **Information** Devices that fail this compliance rule report a failure severity of **Information** for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports.  
  
        -   **Warning** Devices that fail this compliance rule report a failure severity of **Warning** for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports.  
  
        -   **Critical** Devices that fail this compliance rule report a failure severity of **Critical** for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports.  
  
        -   **Critical with event** Devices that fail this compliance rule report a failure severity of **Critical** for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] reports. This severity level is also be logged as a Windows event in the application event log.  
  
## See Also  
 [Configuration items for devices managed without the System Center Configuration Manager client](../System Center Configuration Manager/Configuration-items-for-devices-managed-without-the-System-Center-Configuration-Manager-client.md)