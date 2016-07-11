---
title: How to Enable or Disable a Rule or Monitor
ms.custom: na
ms.prod: system-center-threshold
ms.reviewer: na
ms.suite: na
ms.technology: 
  - operations-manager
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9cae0db4-a0f7-4b64-bfd4-f5a86e25cb2e
---
# How to Enable or Disable a Rule or Monitor
In [!INCLUDE[om12long](../../om/manage/includes/om12long_md.md)], if a management pack's default settings contain a monitor or rule that is not necessary in your environment, you can use overrides to disable this monitor or rule. In addition, some management packs ship with some rules or monitors disabled; you should read the management pack guide to identify the workflows that are disabled by default and determine if you should enable any of them for your monitoring needs. For example, the management packs for network monitoring contain rules and monitors that are vendor\-specific, as listed in [Tuning Network Monitoring](../../om/manage/Tuning-Network-Monitoring.md). Many vendor\-specific rules and monitors in the network management pack are disabled to avoid performance impact. You should identify the devices used in your environment and use overrides to enable the rules and monitors specific to your devices.  
  
### To enable or disable a monitor or rule using overrides  
  
1.  Log on to the computer with an account that is a member of the Operations Manager Advanced Operator role.  
  
2.  In the Operations console, click **Authoring**.  
  
3.  In the **Authoring** workspace, click **Monitors** \(or **Rules** if you want to disable a rule\).  
  
4.  In the **Monitors** or **Rules** section, click the monitor or rule that you want to disable.  
  
5.  On the Operations console toolbar, click **Overrides** and then point to **Override the Monitor** \(or **Rule**\). You can choose to override this monitor or rule for objects of a specific type or for all objects within a group. After you choose which group of object type to override, the **Override Properties** dialog box opens, enabling you to view the default settings contained in this monitor or rule. For more information about applying an override, see [Using Classes and Groups for Overrides in Operations Manager](../../om/manage/Using-Classes-and-Groups-for-Overrides-in-Operations-Manager.md).  
  
6.  In the **Override Properties** dialog box, click to select the **Override** check box that corresponds to the **Enabled** parameter.  
  
    > [!NOTE]  
    > If you select **Disable** instead of **Override**, the **Override Properties** dialog box opens with the **Override** check box selected and the **Enabled** value set to **False**.  
  
7.  In the **Override Setting** column, click **True** to enable the rule or monitor or **False** to disable the rule or monitor.  
  
8.  In the **Select destination management pack** list, click the appropriate management pack in which to store the override or create a new unsealed management pack by clicking **New**. For more information about selecting a destination management pack, see [Creating a Management Pack for Overrides](../../om/manage/Creating-a-Management-Pack-for-Overrides.md).  
  
9. When you complete your changes, click **OK**.  
  
## See Also  
[Using Classes and Groups for Overrides in Operations Manager](../../om/manage/Using-Classes-and-Groups-for-Overrides-in-Operations-Manager.md)  
[How to Override a Rule or Monitor](../../om/manage/How-to-Override-a-Rule-or-Monitor.md)  
[Using the Enforced Attribute in Overrides](../../om/manage/Using-the-Enforced-Attribute-in-Overrides.md)  
[How to Enable Recovery and Diagnostic Tasks](../../om/manage/How-to-Enable-Recovery-and-Diagnostic-Tasks.md)  
  
