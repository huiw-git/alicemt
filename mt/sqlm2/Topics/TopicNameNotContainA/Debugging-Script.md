---
title: Debugging Script
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fddf57d8-8607-4f88-85a0-1b683087b491
---
# Debugging Script
  You write the scripts that the Script task and Script component use, in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[vsprvs](../../Token\Other/vsprvs_md.md)] Tools for Applications \(VSTA\).  
  
 You set and script breakpoints in VSTA. You can manage breakpoints in VSTA, but you can also manage the breakpoints using the **Set Breakpoints** dialog box that [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer provides. For more information, see [Debugging Control Flow](../../Topics\TopicNameNotContainA/Debugging-Control-Flow.md).  
  
 The **Set Breakpoints** dialog box includes the script breakpoints. These breakpoints appear at the bottom of the breakpoint list, and display the line number and the name of the function in which the breakpoint appears. You can delete a script breakpoint from the **Set Breakpoints** dialog box.  
  
 At run time, the breakpoints set on lines of code in script are integrated with the breakpoints set on the package or the tasks and containers in the package. The debugger can run from a breakpoint in the script to a breakpoint set on the package, task, or container, and vice versa. For example, a package might have breakpoints set on the break conditions that occur when the package receives the **OnPreExecute** and **OnPostExecute** events, and also have a Script task that has breakpoints on lines of its script. In this scenario, the package can suspend execution on the break condition associated with the **OnPreExecute** event, run to the breakpoints in the script, and finally run to the break condition associated with the **OnPostExecute** event.  
  
 For more information about debugging the Script task and Script component, see [Coding and Debugging the Script Task](../Topic/Coding%20and%20Debugging%20the%20Script%20Task.md) and [Coding and Debugging the Script Component](../Topic/Coding%20and%20Debugging%20the%20Script%20Component.md).  
  
### To set a breakpoint in Visual Studio for Applications  
  
-   [Debug a Script by Setting Breakpoints in a Script Task and Script Component](../Topic/Debug%20a%20Script%20by%20Setting%20Breakpoints%20in%20a%20Script%20Task%20and%20Script%20Component.md)  
  
## See Also  
 [Troubleshooting Tools for Package Development](../../Topics\TopicNameNotContainA/Troubleshooting-Tools-for-Package-Development.md)  
  
  