---
title: "Corporate-owned device (COD) management using Configuration Manager with Microsoft Intune"
ms.custom: na
ms.date: 2016-03-30
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 2721c10a-b800-4f5c-a8a8-f9bceb21cfad
caps.latest.revision: 24
caps.handback.revision: 0
robots: noindex,nofollow
---
# Corporate-owned device (COD) management using Configuration Manager with Microsoft Intune
You can enroll corporate-owned iOS devices so they can be managed by [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] with [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)]. Intune supports the enrollment of corporate-owned iOS devices using the Apple Device Enrollment Program (DEP) or the [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) tool running on a Mac computer.  
  
 You can enroll corporate-enrolled iOS devices in the following ways:  
  
-   [Device Enrollment Program (DEP) enrollment](https://technet.microsoft.com/library/mt629419.aspx#BKMK_DEPtok) – Deploys an enrollment profile “over the air” that includes setup assistant options for the device. Devices enrolled through DEP cannot be un-enrolled by users.  
  
-   [Apple Configurator enrollment via Setup Assistant](https://technet.microsoft.com/library/mt629419.aspx#BKMK_SAE) – Factory resets the device using Apple Configurator, enrolls the device, and prepares it with Setup Assistant options via a USB connection.  
  
 After setting up management for company-owned devices, end users must [complete setup on the iOS device](https://technet.microsoft.com/library/mt629419.aspx#BKMK_iOSCP).  
  
## Apple DEP enrollment for iOS devices  
 To manage corporate-owned iOS devices with the Apple Device Enrollment Program (DEP), companies must complete the steps with Apple to participate in the program and acquire devices through that program. Details of that process are available at:  [https://deploy.apple.com](https://deploy.apple.com). Advantages of the program include hands-free set up of devices without USB-connecting each device to a computer.  
  
 Before you can enroll corporate-owned iOS devices with the DEP, you need a DEP token from Apple. This token allows [!INCLUDE[wit_nextref](../System Center Configuration Manager/itokens/wit_nextref_md.md)] to sync information about DEP-participating devices owned by your corporation. It also lets [!INCLUDE[wit_nextref](../System Center Configuration Manager/itokens/wit_nextref_md.md)] upload enrollment profiles to Apple and assign devices to those profiles.  
  
###  <a name="BKMK_DEPtok"></a> Enable DEP enrollment in Configuration Manager with Intune  
  
1.  **Start managing iOS devices with Configuration Manager**   
    Before you can enroll iOS Device Enrollment Program (DEP) devices, you must complete steps to [Set up iOS hybrid device management with System Center Configuration Manager and Microsoft Intune](../System Center Configuration Manager/Set-up-iOS-hybrid-device-management-with-System-Center-Configuration-Manager-and-Microsoft-Intune.md).  
  
2.  **Create a DEP token request**   
    In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, in the **Administration** workspace, expand **Hierarchy Configuration**, expand **Cloud Services**, and click **Windows Intune Subscriptions**. Click **Create DEP Token Request** on the **Home** tab, click **Browse** to specify the download location for the DEP token request, and then click **Download**. Save the DEP token request (.pem) file locally. The .pem file is used to request a trusted token (.p7m) from the Apple Device Enrollment Program portal.  
  
3.  **Get a Device Enrollment Program token**   
    Go to the [Device Enrollment Program portal](https://deploy.apple.com) (https://deploy.apple.com) and sign in with your company Apple ID. This Apple ID must be used in future to renew your DEP token.  
  
    1.  In the [Device Enrollment Program portal](https://deploy.apple.com), go to **Device Enrollment Program** > **Manage Servers**, and then click **Add MDM Server**.  
  
    2.  Enter the **MDM Server Name**, and then click **Next**. The server name is for your reference to identify the MDM server. It is not the name or URL of the [!INCLUDE[wit_nextref](../System Center Configuration Manager/itokens/wit_nextref_md.md)] or [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] server.  
  
    3.  The **Add <ServerName\>** dialog box opens. Click **Choose File…** to upload the .pem file that you created in the previous step, and then click **Next**.  
  
    4.  The **Add <ServerName\>** dialog box displays a **Your Server Token** link. Download the server token (.p7m) file to your computer, and then click **Done**.  
  
     This certificate (.p7m) file is used to establish a trust relationship between Intune and Apple’s Device Enrollment Program servers.  
  
4.  **Add the DEP token to Configuration Manager**   
    In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, in the **Administration** workspace, expand **Hierarchy Configuration** and click **Windows Intune Subscriptions**. Click **Configure Platforms** on the **Home** tab and click **iOS**. Select **Enable Device Enrollment Program**, browse to the certificate (.p7m) file, click **Open**, click **Upload**, and then click **OK**.  
  
#### Set up enrollment for Apple Device Enrollment Program (DEP) iOS devices  
  
1.  **Add a Corporate Device Enrollment policy**   
    In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, in the **Assets and Compliance** workspace, expand **Overview**, expand **All Corporate-owned Devices**, expand **iOS**, and click **Enrollment Profiles**. Click **Create Profile** on the **Home** tab to open the Create Profile wizard. Configure the settings on the following pages:  
  
    1.  On the **General** page, specify the following information, and then click **Next**.  
  
        -   **Name** – Name of the device enrollment profile. (Not visible to users)  
  
        -   **Description** - Description of the device enrollment profile. (Not visible to users)  
  
        -   **User affinity** – Specifies how devices are enrolled.  
  
            -   **Prompt for user affinity**: The device must be affiliated with a user during initial setup and could then be permitted to access company data and email as that user.  User affinity should be configured for DEP-managed devices that belong to users and need to use the company portal (i.e. to install apps). See [Enroll devices with User Affinity](https://technet.microsoft.com/library/mt629419.aspx#BKMK_iOSCP).  
  
            -   **No user affinity**: The device is not affiliated with a user. Use this affiliation for devices that perform tasks without accessing local user data. Apps requiring user affiliation won’t work. See [devices with no user affinity.](https://technet.microsoft.com/library/mt629419.aspx#BKMK_noUA)  
  
    2.  On the **Device Enrollment Program** page, specify the following information, and then click **Next**.  
  
        -   **Department**: Enter a department associated with this profile.  
  
        -   **Support phone number**: Enter a phone number assigned to this profile.  
  
        -   **Preparation mode**: Specify whether the assigned devices are in supervised mode or are unsupervised.  
  
        -   **Lock enrollment profile to device**: Choose whether to lock this enrollment profile on the assigned devices.  
  
    3.  On the **Setup Assistant** page, configure the settings that customize the iOS Setup Assistant that starts when the device is first powered on, and then click **Next**. These settings include:  
  
        -   **Passcode**  
  
        -   **Location Services**  
  
        -   **Restore**  
  
        -   **Apple ID**  
  
        -   **Terms and Conditions**  
  
        -   **Siri**  
  
        -   **Send diagnostic data to Apple**  
  
    4.  On the **Additional Management** page, specify whether additional management settings can be configured during device enrollment, and then complete the wizard. When you select **Require certificate**, you must import an Apple Configurator management certificate to use for this profile.  
  
2.  **Assign DEP Devices for management**   
    Go to the [Device Enrollment Program portal](https://deploy.apple.com) (https://deploy.apple.com) and sign in with your company Apple ID. Go to **Deployment Program** > **Device Enrollment Program** > **Manage Devices**. Specify how you will **Choose Devices**, provide device information and specify details by device **Serial Number**, **Order Number**, or **Upload CSV File**. Next, select **Assign to Server** and select the <*ServerName*> that you specified in step 3, and then click **OK**.  
  
3.  **Synchronize DEP-managed devices**   
    In the **Assets and Compliance** workspace, go to **All Corporate-owned Devices** > **iOS** > **Device Information**. On the **Home** tab, click **DEP Sync**. A sync request is sent to Apple. After synchronization completes, the DEP-managed devices are displayed. The **Enrollment Status** for managed devices reads **Not contacted** until the device is powered on and runs the Setup Assistant to enroll the device.  
  
4.  **Distribute devices to users**   
    You can now give your corporate-owned devices to users. When an iOS device is turned on it will be enrolled for management by Intune.  
  
##  <a name="BKMK_iOSCP"></a> Enrollment of company-owned iOS devices with user affinity  
 Devices configured with **user affinity** can install and run the Company Portal app to download apps and manage devices. Once users receive their devices they must complete a number of additional steps  to complete the Setup Assistant and install the Company Portal app.  
  
#### How to enroll iOS devices with user affinity  
  
1.  When users power on their device, they are prompted to complete the Setup Assistant. During setup, users are prompted for their credentials. They must use the credentials (i.e. the unique personal name or UPN) associated with their subscription in Intune.  
  
2.  During setup, users are prompted for an Apple ID. An Apple ID must be provided to allow the device to install the Company Portal. An Apple ID can also be provided after setup is complete from the iOS settings menu.  
  
3.  After completing setup, the iOS device must install the Company Portal app from the App Store, for example [Company Portal app](https://itunes.apple.com/us/app/id719171358).  
  
4.  The user can now login to the Company Portal using the UPN used when setting up the device.  
  
5.  After logging in, the user is prompted to enroll their device. The first step is to **Identify their device**. The app presents a list of iOS devices that have already been corporate-enrolled and assigned to the end-user’s Intune account. Choose the matching device.  
  
     If this device is not already corporate-enrolled, select “new device” to continue with the standard enrolment flow.  
  
6.  On the next screen, the user must confirm the serial of the new device. The user can tap on the link “confirm the Serial Number” to launch the Settings app to verify the serial number. The user must then enter the last 4 characters of the serial number into the Company Portal app.  
  
     This step verifies that the device is the corporate device enrolled in Intune. If the serial number on the device does not match, the wrong device was selected. Go back to the previous screen and select a different device.  
  
7.  After the serial number is verified, the Company Portal app redirects to the Company Portal website to finalize enrolment, and then prompts the user to return to the app.  
  
8.  Enrollment is now complete. You can now use this device with the full set of capabilities.  
  
###  <a name="BKMK_noUA"></a> About corporate-owned managed devices with no user affinity  
 Devices configured with **no user affinity** do not support the Company Portal and should not install the app. The Company Portal is designed for users who have corporate credentials and require access to personalized corporate resources (e.g. email). Device enrolled with **no user affinity** are not intended to have a dedicated user sign in. Kiosk, point of sale (POS), or shared utility devices are typical use-cases for devices enrolled with no user affinity. If user affinity is required, be sure the device’s enrollment profile has **User Affinity** selected prior to enrolling the device. To change the affinity status on a device you must retirement and re-enroll the device.  
  
## See Also  
 [Hybrid mobile device management (MDM) with System Center Configuration Manager and Microsoft Intune](../System Center Configuration Manager/Hybrid-mobile-device-management--MDM--with-System-Center-Configuration-Manager-and-Microsoft-Intune.md)