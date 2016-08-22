---
title: "Plan for and configure compliance settings in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 9ea20b01-676a-4cc2-b328-0098a41b202e
caps.latest.revision: 8
---
# Plan for and configure compliance settings in System Center Configuration Manager
Before you start working with [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] compliance settings, there are a few prerequisites you need to know about, and some configuring tasks you'll need to perform.  
  
## Prerequisites for compliance settings  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] compliance settings requires the following:  
  
|Prerequisite|More information|  
|------------------|----------------------|  
|Windows [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients must be enabled and configured for compliance evaluation.|[Configuring compliance settings for Windows computers](#BKMK_Configure)|  
|If you want to run reports, then you must configure reporting for your site.|[Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md)|  
|Admins must be granted the necessary security permissions.|The Compliance Settings Manager security role includes the necessary permissions to manage compliance settings, user data and profiles configuration items, and remote connection profiles.<br /><br /> [Configure role-based administration for System Center Configuration Manager](../System Center Configuration Manager/Configure-role-based-administration-for-System-Center-Configuration-Manager.md)|  
  
##  <a name="BKMK_Configure"></a> Configuring compliance settings for Windows computers  
 Once you have the necessary prerequisites in place, you can configure compliance settings in your hierarchy.  
  
 This procedure configures the default client settings for compliance settings and applies to all computers in your hierarchy. If you want these settings to apply to only some computers, create a custom device client setting and assign it to a collection that contains the computers for which you want to use compliance settings. For more information about how to create custom device settings, see [How to configure client settings in System Center Configuration Manager](../System Center Configuration Manager/How-to-configure-client-settings-in-System-Center-Configuration-Manager.md).  
  
> [!TIP]  
>  Other device types require no specific configuration to evaluate compliance settings.  
  
#### To enable and configure compliance settings for Windows computers  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, click **Client Settings** > **Default Settings**.  
  
3.  On the **Home** tab, in the **Properties** group, click **Properties**.  
  
4.  In the **Default Settings** dialog box, click **Compliance Settings**.  
  
5.  Configure the following client settings for compliance settings:  
  
    |Client setting name|More information|  
    |-------------------------|----------------------|  
    |**Enable compliance evaluation on clients**|Set to **True** if you want to evaluate compliance on client devices.|  
    |**Schedule compliance evaluation**|Click **Schedule** if you want to modify the default compliance evaluation schedule on client devices.|  
    |**Enable User Data and Profiles**|Enable this option if you want to create and deploy user data and profiles configuration items to Windows computers. For details, see [Working with user data and profiles configuration items in System Center Configuration Manager](../System Center Configuration Manager/Working-with-user-data-and-profiles-configuration-items-in-System-Center-Configuration-Manager.md).|  
  
6.  Click **OK** to close the **Default Settings** dialog box.  
  
 Client computers are configured with these settings the next time they download client policy.  
  
## See Also  
 [Ensure device compliance with System Center Configuration Manager](../System Center Configuration Manager/Ensure-device-compliance-with-System-Center-Configuration-Manager.md)