---
title: Copy Package Objects
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99b85e5c-d6bd-4e7c-afe4-51f6ce151c2f
---
# Copy Package Objects
  This topic describes how to copy control flow items, data flow items, and connection managers within a package or between packages.  
  
### To copy control and data flow items  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project that contains the packages that you want work with.  
  
2.  In Solution Explorer, double\-click the packages that you want to copy between.  
  
3.  In [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the tab for the package that contains the items to copy and click the **Control Flow**, **Data Flow**, or **Event Handlers** tab.  
  
4.  Select the control flow or data flow items to copy. You can either select items one at a time by pressing the Shift key and clicking the item or select items as a group by dragging the pointer across the items you want to select.  
  
    > [!IMPORTANT]  
    >  The precedence constraints and paths that connect items are not selected automatically when you select the two items that they connect. To copy an ordered workflow—a segment of control flow or data flow—make sure to also copy the precedence constrains and the paths.  
  
5.  Right\-click a selected item and click **Copy**.  
  
6.  If copying items to a different package, click the package that you want to copy to, and then click the appropriate tab for the item type.  
  
    > [!IMPORTANT]  
    >  You cannot copy a data flow to a package unless the package contains at least one Data Flow task.  
  
7.  Right\-click and click **Paste**.  
  
### To copy connection managers  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project that contains the package that you want to work with.  
  
2.  In Solution Explorer, double\-click the package.  
  
3.  In [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the **Control Flow**, **Data Flow**, or **Event Handler** tab.  
  
4.  In the **Connection Managers** area, right\-click the connection manager, and then click **Copy**. You can copy only one connection manager at a time.  
  
5.  If you are copying items to a different package, click the package that you want to copy to and then click the **Control Flow**, **Data Flow**, or **Event Handler** tab.  
  
6.  Right\-click in the **Connection Managers** area and click **Paste**.  
  
## See Also  
 [Control Flow](../../Topics\TopicNameNotContainA/Control-Flow.md)   
 [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md)   
 [Integration Services &#40;SSIS&#41; Connections](../Topic/Integration%20Services%20\(SSIS\)%20Connections.md)   
 [Copy Project Items](../../Topics\TopicNameNotContainA/Copy-Project-Items.md)  
  
  