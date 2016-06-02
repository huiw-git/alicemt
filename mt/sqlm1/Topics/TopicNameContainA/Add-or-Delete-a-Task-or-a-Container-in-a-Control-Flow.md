---
title: Add or Delete a Task or a Container in a Control Flow
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 653084c6-87a3-45d5-b458-914ecf24d56a
---
# Add or Delete a Task or a Container in a Control Flow
  When you are working in the control flow designer, the Toolbox in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer lists the tasks that [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] provides for building control flow in a package. For more information about the Toolbox, see [SSIS Toolbox](../../Topics\TopicNameNotContainA/SSIS-Toolbox.md).  
  
 A package can include multiple instances of the same task. Each instance of a task is uniquely identified in the package, and you can configure each instance differently.  
  
 If you delete a task, the precedence constraints that connect the task to other tasks and containers in the control flow are also deleted.  
  
 The following procedures describe how to add or delete a task or container in the control flow of a package.  
  
### To add a task or a container to a control flow  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project that contains the package you want.  
  
2.  In Solution Explorer, double\-click the package to open it.  
  
3.  Click the **Control Flow** tab.  
  
4.  To open the **Toolbox**, click **Toolbox** on the **View** menu.  
  
5.  Expand **Control Flow Items** and **Maintenance Tasks**.  
  
6.  Drag tasks and containers from the **Toolbox** to the design surface of the **Control Flow** tab.  
  
7.  Connect a task or container within the package control flow by dragging its connector to another component in the control flow.  
  
8.  To save the updated package, click **Save Selected Items** on the **File** menu.  
  
### To delete a task or a container from a control flow  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project that contains the package you want.  
  
2.  In Solution Explorer, double\-click the package to open it. Do one of the following:  
  
    -   Click the **Control Flow** tab, right\-click the task or container that you want to remove, and then click **Delete**.  
  
    -   Open **Package Explorer**. From the **Executables** folder, right\-click the task or container that you want to remove, and then click **Delete**.  
  
3.  To save the updated package, click **Save Selected Items** on the **File** menu.  
  
## See Also  
 [Integration Services Tasks](../../Topics\TopicNameNotContainA/Integration-Services-Tasks.md)   
 [Integration Services Containers](../../Topics\TopicNameNotContainA/Integration-Services-Containers.md)   
 [Control Flow](../../Topics\TopicNameNotContainA/Control-Flow.md)  
  
  