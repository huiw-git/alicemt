---
title: How to Override a Rule or Monitor
ms.custom: na
ms.prod: system-center-threshold
ms.reviewer: na
ms.suite: na
ms.technology: 
  - operations-manager
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b8b52d9e-404f-4d3c-a890-48f5c698c99d
manager:cfreeman
---
# How to Override a Rule or Monitor
Overrides change the configuration of [!INCLUDE[om12long](../../om/manage//om12long_md.md)] monitoring settings for monitors, attributes, object discoveries, and rules. When you create an override, you can apply it to a single managed object or to a group of managed objects. You must have Advanced Operator user rights to create and edit overrides.  
  
The use of overrides is key to controlling the amount of data that is collected by Operations Manager. When you create a monitor, rule, or attribute you target it at an object type, but often the available object types are broad in scope. You can then use groups and overrides together to narrow the focus of the monitor, rule, attribute, or object discovery. You can also override existing monitors, rules, attributes, or object discoveries that are from management packs.  
  
Overrides that apply to a class are applied first, then overrides that apply to a group, and finally overrides that apply to a specific object. For more information, see [Using Classes and Groups for Overrides in Operations Manager](../../om/manage/Using-Classes-and-Groups-for-Overrides-in-Operations-Manager.md) and [Using the Enforced Attribute in Overrides](../../om/manage/Using-the-Enforced-Attribute-in-Overrides.md).  
  
The following procedure overrides a monitor, but you can also use these steps to override a rule, attribute, or object discovery. You must have Advanced Operator or Administrator user rights to create an override.  
  
### To override a monitor  
  
1.  Log on to the computer with an account that is a member of the Operations Manager Advanced Operator role.  
  
2.  In the Operations console, click **Authoring**.  
  
3.  In the **Authoring** workspace, expand **Management Pack Objects** and then click **Monitors**.  
  
4.  In the **Monitors** pane, expand an object type completely and then click a monitor.  
  
5.  On the Operations console toolbar, click **Overrides** and then point to **Override the Monitor**. You can choose to override this monitor for objects of a specific type or for all objects within a group. After you choose which group of object type to override, the **Override Properties** dialog box opens, enabling you to view the default settings contained in this monitor. You can then choose whether to override each individual setting contained in the monitor. For more information about applying an override, see [Using Classes and Groups for Overrides in Operations Manager](../../om/manage/Using-Classes-and-Groups-for-Overrides-in-Operations-Manager.md).  
  
    > [!NOTE]  
    > If the **Overrides** button is not available, make sure you have selected a monitor and not a container object in the **Monitors** pane.  
  
6.  Click to place a check mark in the **Override** column next to each parameter that you want to override. The **Override Value** can now be edited. Change the value in **Override Value** to the value you want the parameter to use.  
  
7.  Either select a management pack from the **Select destination management pack** list or create a new unsealed management pack by clicking **New**. For more information about selecting a destination management pack, see [Creating a Management Pack for Overrides](../../om/manage/Creating-a-Management-Pack-for-Overrides.md).  
  
8.  When you complete your changes, click **OK**.  
  
## See Also  
[Using Classes and Groups for Overrides in Operations Manager](../../om/manage/Using-Classes-and-Groups-for-Overrides-in-Operations-Manager.md)  
[How to Enable or Disable a Rule or Monitor](../../om/manage/How-to-Enable-or-Disable-a-Rule-or-Monitor.md)  
[Using the Enforced Attribute in Overrides](../../om/manage/Using-the-Enforced-Attribute-in-Overrides.md)  
[How to Enable Recovery and Diagnostic Tasks](../../om/manage/How-to-Enable-Recovery-and-Diagnostic-Tasks.md)  
  
