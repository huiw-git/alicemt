---
title: "Debugging Script"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fddf57d8-8607-4f88-85a0-1b683087b491
caps.latest.revision: 58
caps.handback.revision: 0
manager: jhubbard
---
# Debugging Script
You write the scripts that the Script task and Script component use, in [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[vsprvs](../../Topics/TopicNameContainA/tokens/vsprvs_md.md)] Tools for Applications (VSTA).  
  
 You set and script breakpoints in VSTA. You can manage breakpoints in VSTA, but you can also manage the breakpoints using the **Set Breakpoints** dialog box that [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer provides. For more information, see [Debugging Control Flow](../../Topics/TopicNameNotContainA/Debugging-Control-Flow.md).  
  
 The **Set Breakpoints** dialog box includes the script breakpoints. These breakpoints appear at the bottom of the breakpoint list, and display the line number and the name of the function in which the breakpoint appears. You can delete a script breakpoint from the **Set Breakpoints** dialog box.  
  
 At run time, the breakpoints set on lines of code in script are integrated with the breakpoints set on the package or the tasks and containers in the package. The debugger can run from a breakpoint in the script to a breakpoint set on the package, task, or container, and vice versa. For example, a package might have breakpoints set on the break conditions that occur when the package receives the **OnPreExecute** and **OnPostExecute** events, and also have a Script task that has breakpoints on lines of its script. In this scenario, the package can suspend execution on the break condition associated with the **OnPreExecute** event, run to the breakpoints in the script, and finally run to the break condition associated with the **OnPostExecute** event.  
  
 For more information about debugging the Script task and Script component, see [Coding and Debugging the Script Task](assetId:///687c262f-fcab-42e8-92ae-e956f3d92d69) and [Coding and Debugging the Script Component](assetId:///c3913c15-66aa-4b61-89b5-68488fa5f0a4).  
  
### To set a breakpoint in Visual Studio for Applications  
  
-   [How to: Set a Breakpoint in Script Using Microsoft Visual Studio for Applications](assetId:///6c03464f-3f7d-4882-b7f8-8e396f8e2944)  
  
## See Also  
 [Troubleshooting Tools for Package Development](../../Topics/TopicNameNotContainA/Troubleshooting-Tools-for-Package-Development.md)