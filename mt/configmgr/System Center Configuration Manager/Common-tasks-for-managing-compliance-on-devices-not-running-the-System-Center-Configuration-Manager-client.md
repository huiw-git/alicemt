---
title: "Common tasks for managing compliance on devices not running the System Center Configuration Manager client"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 116cca2a-0a98-43fd-ac9e-e3daeddefce3
caps.latest.revision: 5
---
# Common tasks for managing compliance on devices not running the System Center Configuration Manager client
The scenarios in this topic give you an introduction to using [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] compliance settings by working through some common scenarios you might encounter.  
  
 If you are already familiar with compliance settings, detailed documentation about all the features you use can be found in the [Configuration items for devices managed without the System Center Configuration Manager client](../System Center Configuration Manager/Configuration-items-for-devices-managed-without-the-System-Center-Configuration-Manager-client.md) section.  
  
 Before you start, read [Get started with compliance settings in System Center Configuration Manager](../System Center Configuration Manager/Get-started-with-compliance-settings-in-System-Center-Configuration-Manager.md) to learn some basics about compliance settings, and also read [Plan for and configure compliance settings in System Center Configuration Manager](../System Center Configuration Manager/Plan-for-and-configure-compliance-settings-in-System-Center-Configuration-Manager.md) to implement any necessary prerequisites.  
  
## General information for each scenario  
 In each scenario, you'll create a configuration item that performs a specific task. open the Create Configuration Item Wizard, use the following steps:  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance**.  
  
2.  In the **Assets and Compliance** workspace, expand **Compliance Settings**, and then click **Configuration Items**.  
  
3.  On the **Home** tab, in the **Create** group, click **Create Configuration Item**.  
  
4.  On the **General** tab of the Create Configuration Item Wizard as shown below, specify a name and description for the configuration item, then choose the appropriate configuration item type for each scenario in this topic.  
  
     ![Shows general page of the create configuration item wizard.](../System Center Configuration Manager/medias/Compliance-Settings-Wizard---1.png "Compliance)  
  
## Scenarios for Windows 8.1 and Windows 10 devices managed without the Configuration Manager client  
  
### Scenario: Restrict access to the app store on all Windows PCs  
 In this scenario, you are the IT admin for a company that deals with highly sensitive information. Because of this, you restrict the apps that users can install. You want to stop users of all Windows 10 PCs from downloading apps from the Windows Store, so you take the following actions.  
  
##### Steps  
  
1.  On the **General** page of the Create Configuration Item wizard, select the **Windows 8.1 and Windows 10** configuration item type, then click **Next**.  
  
2.  On the **Supported Platforms** page of the wizard, select all of the Windows 10 platforms.  
  
3.  On the **Device Settings** page, select **Store**, then click **Next**.  
  
4.  On the **Store** page, select **Prohibited** as the value for **Application store**.  
  
5.  Select **Remediate noncompliant settings** to ensure the change is applied to all PCs.  
  
6.  Complete the wizard to create the configuration item.  
  
 You can now use the information in the [Common tasks for creating and deploying configuration baselines with System Center Configuration Manager](../System Center Configuration Manager/Common-tasks-for-creating-and-deploying-configuration-baselines-with-System-Center-Configuration-Manager.md) topic to help you deploy the configuration you have created to devices.  
  
## Scenarios for Windows Phone devices managed without the Configuration Manager client  
  
### Scenario: Disable the use of screen capture on a Windows Phone  
 In this scenario, you use Windows Phone 8.1 devices in your company. These devices run a sales app that contains sensitive information. To protect your company, you want to disable the use of screen capture on the device which could potentially be used to transmit sensitive information outside of your company.  
  
##### Steps  
  
1.  On the **General** page of the Create Configuration Item wizard, select the **Windows Phone** configuration item type, then click **Next**.  
  
2.  On the **Supported Platforms** page of the wizard, select **All Windows Phone 8.1** platforms.  
  
3.  On the **Device Settings** page, select **Device**, then click **Next**.  
  
4.  On the **Device** page, select **Disabled** as the value for **Screen capture**.  
  
5.  Select **Remediate noncompliant settings** to ensure the change is applied to all Windows Phone 8.1 devices.  
  
6.  Complete the wizard to create the configuration item.  
  
 You can now use the information in the [Common tasks for creating and deploying configuration baselines with System Center Configuration Manager](../System Center Configuration Manager/Common-tasks-for-creating-and-deploying-configuration-baselines-with-System-Center-Configuration-Manager.md) topic to help you deploy the configuration you have created to devices.  
  
## Scenarios for iOS and Mac OS X devices managed without the Configuration Manager client  
  
### Scenario: Disable the camera on iOS devices  
 In this scenario, your company produces blueprints for new product designs. These contain sensitive information that must not be leaked. As your company issues iPhones or iPads to all employees, you want to disable the use of the camera on these devices to prevent them being used to photograph the blueprints.  
  
##### Steps  
  
1.  On the **General** page of the Create Configuration Item wizard, select the **iOS and Mac OS X** configuration item type, then click **Next**.  
  
2.  On the **Supported Platforms** page of the wizard, select all iPhone and all iPad device platforms.  
  
3.  On the **Device Settings** page, select **Security**, then click **Next**.  
  
4.  On the **Security** page, select **Prohibited** as the value for **Camera**.  
  
5.  Select **Remediate noncompliant settings** to ensure the change is applied to all iOS devices.  
  
6.  Complete the wizard to create the configuration item.  
  
 You can now use the information in the [Common tasks for creating and deploying configuration baselines with System Center Configuration Manager](../System Center Configuration Manager/Common-tasks-for-creating-and-deploying-configuration-baselines-with-System-Center-Configuration-Manager.md) topic to help you deploy the configuration you have created to devices.  
  
## Scenarios for Android and Samsung KNOX devices managed without the Configuration Manager client  
  
### Scenario: Require a password on all Android 5 devices  
 In this scenario, you'll create a configuration item for Android 5 devices only that requires users to configure a password of at least 6 characters on their devices. Additionally, if a user enters an incorrect password 5 times, then the device will be wiped.  
  
##### Steps  
  
1.  On the **General** page of the Create Configuration Item wizard, select the **Android and Samsung KNOX** configuration item type, then click **Next**.  
  
2.  On the **Supported Platforms** page of the wizard, select only **Android 5** (to ensure that the settings only get applied to that platform).  
  
3.  On the **Device Settings** page, select **Password**, then click **Next**.  
  
4.  On the **Password** page, configure the following settings:  
  
    -   **Require password settings on devices** > **Required**  
  
    -   **Minimum password length (characters)** > **6**  
  
    -   **Number of failed logon attempts before device is wiped** > **5**  
  
5.  Complete the wizard to create the configuration item.  
  
 You can now use the information in the [Common tasks for creating and deploying configuration baselines with System Center Configuration Manager](../System Center Configuration Manager/Common-tasks-for-creating-and-deploying-configuration-baselines-with-System-Center-Configuration-Manager.md) topic to help you deploy the configuration you have created to devices.  
  
## See Also  
 [Common tasks for managing compliance with System Center Configuration Manager](../System Center Configuration Manager/Common-tasks-for-managing-compliance-with-System-Center-Configuration-Manager.md)