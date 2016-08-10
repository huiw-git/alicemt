---
title: "Event Handlers Tab"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 94fc8916-8032-490c-b9d5-ded8b6217e49
caps.latest.revision: 23
caps.handback.revision: 0
manager: jhubbard
---
# Event Handlers Tab
Use the **Event Handlers** tab of [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer to build a control flow in an [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] package. An event handler runs in response to an event raised by the package or by a task or container in the package.  
  
## Options  
 **Executable**  
 Select the executable for which you want to build an event handler. The executable can be the package, or a task or containers in the package.  
  
 **Event handler**  
 Select a type of event handler. Create the event handler by dragging items from the **Toolbox**.  
  
 **Delete**  
 Select an event handler, and remove it from the package by clicking **Delete**.  
  
 **Click here to create an <event handler name\> for the executable <executable name\>**  
 Click to create the event handler.  
  
 Create the control flow by dragging graphical objects that represent [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] tasks and containers from the **Toolbox** to the design surface of the **Event Handlers** tab, and then connecting the objects by using precedence constraints to define the sequence in which they run.  
  
 Additionally, to add annotations, right-click the design surface, and then on the menu, click **Add Annotation**.  
  
## See Also  
 [Integration Services (SSIS) Event Handlers](../../Topics/TopicNameNotContainA/Integration-Services--SSIS--Event-Handlers.md)   
 [Control Flow](../../Topics/TopicNameNotContainA/Control-Flow.md)   
 [SSIS Designer](../../Topics/TopicNameNotContainA/SSIS-Designer.md)   
 [Integration Services (SSIS) Event Handlers](../../Topics/TopicNameNotContainA/Integration-Services--SSIS--Event-Handlers.md)