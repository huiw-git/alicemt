---
title: "How to create user data and profiles configuration items in System Center Configuration Manager"
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
ms.assetid: 9fcbcc81-cd6f-496e-b075-ef1afa2b8ccc
caps.latest.revision: 6
caps.handback.revision: 0
---
# How to create user data and profiles configuration items in System Center Configuration Manager
Use the following procedures to create, deploy, and monitor [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] user data and profiles configuration items.  
  
 Before you use this procedure, ensure you have read the introductory information and prerequisites in [Working with user data and profiles configuration items in System Center Configuration Manager](../System Center Configuration Manager/Working-with-user-data-and-profiles-configuration-items-in-System-Center-Configuration-Manager.md).  
  
 Unlike other configuration items in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], you do not add user data and profile configuration items to a configuration baseline which you then deploy. Instead, you deploy the configuration item directly by using the **Deploy User Data and Profiles Configuration Item** dialog box.  
  
### To create a user data and profiles configuration item  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance**.  
  
2.  In the **Assets and Compliance** workspace, expand **Compliance Settings**, and then click **User Data and Profiles**.  
  
3.  On the **Home** tab, in the **Create** group, click **Create User Data and Profiles Configuration Item**.  
  
4.  On the **General** page of the **Create User Data and Profiles Configuration Item Wizard**, specify the following information:  
  
    -   **Name:** Enter a unique name for the configuration item. You can use a maximum of 256 characters.  
  
    -   **Description:** Provide a description that gives an overview of the configuration item and other relevant information that helps to identify it in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. You can use a maximum of 256 characters.  
  
    -   **Folder redirection:** Check this box if you want to configure settings for folder redirection for this configuration item.  
  
    -   **Offline files:** Check this box if you want to configure settings for offline files for this configuration item.  
  
    -   **Roaming user profiles:** Check this box if you want to configure settings for roaming user profiles for this configuration item.  
  
5.  On the **Folder Redirection** page of the **Create User Data and Profiles Configuration Item Wizard**, specify how you want the client computers of users that receive this configuration item to manage folder redirection. You can configure settings for any device the user logs onto or for only the user’s primary devices. For more information about folder redirection, see your Windows Server documentation.  
  
    > [!NOTE]  
    >  This page of the wizard appears only if you checked the box **Folder redirection** on the **General** page of the wizard.  
  
6.  On the **Offline Files** page of the **Create User Data and Profiles Configuration Item Wizard**, you can enable or disable the use of offline files for users that receive this configuration item and configure settings for the behavior of the offline files. You can also specify offline files that will always be available on any computer that the user logs on to. For more information about offline files, see your Windows Server documentation.  
  
    > [!NOTE]  
    >  This page of the wizard appears only if you checked the box **Offline files** on the **General** page of the wizard.  
  
7.  On the **Roaming Profiles** page of the **Create User Data and Profiles Configuration Item Wizard**, you can configure whether roaming profiles are available on computers that the user logs onto and also configure further information about how these profiles behave. For more information about roaming profiles, see your Windows Server documentation.  
  
    > [!NOTE]  
    >  This page of the wizard appears only if you checked the box **Roaming user profiles** on the **General** page of the wizard.  
  
8.  Complete the wizard.  
  
 The new user data and profiles configuration item is shown in the **User Data and Profiles** node of the **Assets and Compliance** workspace.  
  
### To deploy a user data and profiles configuration item  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance**.  
  
2.  In the **Assets and Compliance** workspace, expand **Compliance Settings**, and then click **User Data and Profiles**.  
  
3.  Select the user data and profiles configuration item you want to deploy and then, in the **Home** tab, in the **Deployment** group, click **Deploy**.  
  
4.  In the **Deploy User Data and Profiles Configuration Item** dialog box, specify the following information.  
  
    -   **Collection** - Click **Browse** to select the user collection where you want to deploy the configuration item.  
  
        > [!IMPORTANT]  
        >  You can only deploy user data and profiles configuration items to user collections.  
  
    -   **Remediate noncompliant rules when supported** – Enable this option to automatically remediate any rules that are evaluated as noncompliant on client computers.  
  
    -   **Allow remediation outside the maintenance window** – If a maintenance window has been configured for the collection to which you are deploying the configuration item, enable this option to let compliance settings remediate the value outside of the maintenance window. For more information about maintenance windows, see [How to use maintenance windows in System Center Configuration Manager](../System Center Configuration Manager/How-to-use-maintenance-windows-in-System-Center-Configuration-Manager.md).  
  
    -   **Generate an alert** – Enable this option to configure an alert that is generated if the configuration item compliance is less than a specified percentage by a specified date and time. You can also specify whether you want an alert to be sent to System Center Operations Manager.  
  
    -   **Specify the compliance evaluation schedule for this configuration item** -  Specifies the schedule by which the deployed configuration item is evaluated on client computers. This can be either a simple or a custom schedule.  
  
5.  Click **OK** to close the **Deploy User Data and Profiles Configuration Item** dialog box and to create the deployment.  
  
## Monitor a user data and profiles configuration item  
 You monitor this typ of configuration item in the same way that you monitor other compliance settings.  
  
 For more information, see [How to monitor compliance settings in System Center Configuration Manager](../System Center Configuration Manager/How-to-monitor-compliance-settings-in-System-Center-Configuration-Manager.md).  
  
## See Also  
 [Compliance settings technical reference for System Center Configuration Manager](../System Center Configuration Manager/Compliance-settings-technical-reference-for-System-Center-Configuration-Manager.md)