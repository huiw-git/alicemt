---
title: "Configuring power management in System Center Configuration Manager"
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
ms.assetid: 435c923c-ea30-4dce-8afd-48962ed85502
caps.latest.revision: 5
caps.handback.revision: 0
---
# Configuring power management in System Center Configuration Manager
Before you can use power management in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], you must perform the following configuration steps.  
  
## Enable and configure power management client settings  
 This procedure configures the default client settings for power management and will apply to all the computers in your hierarchy. If you want these settings to apply to only some computers, create a custom device client setting and assign it to a collection that contains the computers that you want to use power management. For more information about how to create custom device settings, see [How to configure client settings in System Center Configuration Manager](../System Center Configuration Manager/How-to-configure-client-settings-in-System-Center-Configuration-Manager.md).  
  
#### To enable power management and configure client settings  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, click **Client Settings**.  
  
3.  Click **Default Client Settings**.  
  
4.  On the **Home** tab, in the **Properties** group, click **Properties**.  
  
5.  In the **Default Client Settings** dialog box, click **Power Management**.  
  
6.  Configure the following value for the power management client settings:  
  
    -   **Allow power management of devices** – From the drop-down list, select **True** to enable power management.  
  
7.  Configure the client settings that you require. For a list of power management client settings that you can configure, see the [Power Management](../System Center Configuration Manager/About-client-settings-in-System-Center-Configuration-Manager.md#BKMK_PowMgmtDeviceSettings) section in the [About client settings in System Center Configuration Manager](../System Center Configuration Manager/About-client-settings-in-System-Center-Configuration-Manager.md) topic.  
  
8.  Click **OK** to close the **Default Client Settings** dialog box.  
  
 Client computers will be configured with these settings when they next download client policy. To initiate policy retrieval for a single client, see [How to manage clients in System Center Configuration Manager](../System Center Configuration Manager/How-to-manage-clients-in-System-Center-Configuration-Manager.md).  
  
## Exclude computers from power management  
 You can prevent collections of computers from receiving power management settings. If a computer is a member of any collection that is excluded from power management settings, that computer does not apply power management settings, even if it is a member of another collection that applies power management settings.  
  
 You might want to exclude computers from power management for any of the following reasons:  
  
-   You have a business requirement for computers to be turned on at all times.  
  
-   You have created a control collection of computers on which you do not want to apply power management settings.  
  
-   Some of your computers are incapable of applying power management settings.  
  
-   You want to exclude computers that run Windows Server from power management.  
  
> [!NOTE]  
>  If the option **Allow users to exclude their device from power management** is configured in client settings, users can exclude their own computers from power management by using Software Center.  
  
 To find out which computers have been excluded from power management, run the report **Computers Excluded**. For more information about this report see [Computers Excluded](../System Center Configuration Manager/How-to-monitor-and-plan-for-power-management-in-System-Center-Configuration-Manager.md#BKMK_Excluded) in [How to monitor and plan for power management in System Center Configuration Manager](../System Center Configuration Manager/How-to-monitor-and-plan-for-power-management-in-System-Center-Configuration-Manager.md).  
  
> [!IMPORTANT]  
>  Power settings that are applied to computers that run Windows XP or Windows Server 2003 are not reverted to their original values, even if you exclude the computer from power management. On later versions of Windows, excluding a computer from power management causes all power settings to be reverted to their original values. You cannot revert individual power settings to their original values.  
  
#### To exclude a collection of computers from power management  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance**.  
  
2.  In the **Assets and Compliance** workspace, click **Device Collections**.  
  
3.  In the **Device Collections** list, select the collection that you want to exclude from power management and then, in the **Home** tab, in the **Properties** group, click **Properties**.  
  
4.  In the **Power Management** tab of the *<Collection Name\>***Properties** dialog box, select **Never apply power management settings to computers in this collection**.  
  
5.  Click **OK** to close the *<Collection Name\>***Properties** dialog box and to save your settings.  
  
## See Also  
 [Power management technical reference for System Center Configuration Manager](../System Center Configuration Manager/Power-management-technical-reference-for-System-Center-Configuration-Manager.md)