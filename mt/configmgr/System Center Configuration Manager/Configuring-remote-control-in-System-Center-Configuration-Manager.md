---
title: "Configuring remote control in System Center Configuration Manager"
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
ms.assetid: 45affc27-aa11-4249-9493-082ac23a3a3d
caps.latest.revision: 4
caps.handback.revision: 0
author: barlanmsft
---
# Configuring remote control in System Center Configuration Manager
Before you can use remote control in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], you must perform the following configuration steps.  
  
## How to enable remote control and configure client settings  
 This procedure describes configuring the default client settings for remote control and applies to all computers in your hierarchy. If you want these settings to apply to only some computers, create a custom device client setting and assign it to a collection that contains the computers that you want to use in a remote control session. For more information about how to create custom device settings, see [How to configure client settings in System Center Configuration Manager](../System Center Configuration Manager/How-to-configure-client-settings-in-System-Center-Configuration-Manager.md).  
  
#### To enable remote control and configure client settings  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, click **Client Settings**.  
  
3.  Click **Default Client Settings**.  
  
4.  On the **Home** tab, in the **Properties** group, click **Properties**.  
  
5.  In the **Default**  dialog box, click **Remote Tools**.  
  
6.  Configure the remote control, Remote Assistance and Remote Desktop client settings that you require. For a list of remote tools client settings that you can configure, see the section [Remote Tools](../System Center Configuration Manager/About-client-settings-in-System-Center-Configuration-Manager.md#BKMK_RemoteToolsDeviceSettings) in the topic [About client settings in System Center Configuration Manager](../System Center Configuration Manager/About-client-settings-in-System-Center-Configuration-Manager.md).  
  
    > [!NOTE]  
    >  You can change the company name that appears in the **ConfigMgr Remote Control** dialog box by configuring a value for **Organization name displayed in Software Center** in the **Computer Agent** client settings.  
  
    > [!IMPORTANT]  
    >  To use Remote Assistance or Remote Desktop, it must be installed and configured on the computer that runs the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. For more information about how to install and configure Remote Assistance or Remote Desktop, see your Windows documentation.  
  
7.  Click **OK** to close the **Default Settings** dialog box.  
  
 Client computers are configured with these settings the next time they download client policy. To initiate policy retrieval for a single client, see [How to manage clients in System Center Configuration Manager](../System Center Configuration Manager/How-to-manage-clients-in-System-Center-Configuration-Manager.md).  
  
## See Also  
 [Remote control technical reference for System Center Configuration Manager](../System Center Configuration Manager/Remote-control-technical-reference-for-System-Center-Configuration-Manager.md)