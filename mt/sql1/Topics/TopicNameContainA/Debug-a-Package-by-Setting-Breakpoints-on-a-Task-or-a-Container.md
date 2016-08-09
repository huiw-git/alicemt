---
title: "Debug a Package by Setting Breakpoints on a Task or a Container"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e7fa106a-2221-403a-bb74-efc9f12bb450
caps.latest.revision: 35
caps.handback.revision: 0
manager: jhubbard
---
# Debug a Package by Setting Breakpoints on a Task or a Container
This procedure describes how to set breakpoints in a package, a task, a For Loop container, a Foreach Loop container, or a Sequence container.  
  
### To set breakpoints in a package, a task, or a container  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] project that contains the package you want.  
  
2.  Double-click the package in which you want to set breakpoints.  
  
3.  In SSIS Designer, do the following:  
  
    -   To set breakpoints in the package object, click the **Control Flow** tab, place the cursor anywhere on the background of the design surface, right-click, and then click **Edit Breakpoints**.  
  
    -   To set breakpoints in a package control flow, click the **Control Flow** tab, right-click a task, a For Loop container, a Foreach Loop container, or a Sequence container, and then click **Edit Breakpoints**.  
  
    -   To set breakpoints in an event handler, click the **Event Handler** tab, right-click a task, a For Loop container, a Foreach Loop container, or a Sequence container, and then click **Edit Breakpoints**.  
  
4.  In the **Set Breakpoints <container name\>** dialog box, select the breakpoints to enable.  
  
5.  Optionally, modify the hit count type and the hit count number for each breakpoint.  
  
6.  To save the package, click **Save Selected Items** on the **File** menu.  
  
## See Also  
 [Troubleshooting Tools for Package Development](../../Topics/TopicNameNotContainA/Troubleshooting-Tools-for-Package-Development.md)   
 [Debug a Script by Setting Breakpoints in a Script Task and Script Component](assetId:///6c03464f-3f7d-4882-b7f8-8e396f8e2944)   
 [Coding and Debugging the Script Task](assetId:///687c262f-fcab-42e8-92ae-e956f3d92d69)   
 [Coding and Debugging the Script Component](assetId:///c3913c15-66aa-4b61-89b5-68488fa5f0a4)