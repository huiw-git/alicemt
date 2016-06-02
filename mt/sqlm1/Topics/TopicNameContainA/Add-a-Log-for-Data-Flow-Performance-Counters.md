---
title: Add a Log for Data Flow Performance Counters
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b500d166-33ba-4b82-a92d-b0a333924e8d
---
# Add a Log for Data Flow Performance Counters
  This procedure describes how to add a log for the performance counters that the data flow engine provides.  
  
> [!NOTE]  
>  If you install [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] on a computer that is running [!INCLUDE[winxpsvr](../../Token\Other/winxpsvr_md.md)], and then upgrade that computer to [!INCLUDE[firstref_longhorn](../../Token\Other/firstref_longhorn_md.md)], the upgrade process removes the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] performance counters from the computer. To restore the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] performance counters on the computer, run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup in repair mode.  
  
### To add logging of performance counters  
  
1.  In **Control Panel**, if you are using Classic view, click **Administrative Tools**. If you are using Category view, click **Performance and Maintenance** and then click **Administrative Tools**.  
  
2.  Click **Performance**.  
  
3.  In the **Performance** dialog box, expand **Performance Logs and Alerts**, right\-click **Counter Logs**, and then click **New Log Settings**. Type the name of the log. For example, type **MyLog**.  
  
4.  Click **OK**.  
  
5.  In the **MyLog** dialog box, click **Add Counters**.  
  
6.  Click **Use local computer counters** to log performance counters on the local computer, or click **Select counters from computer** and then select a computer from the list to log performance counters on the specified computer.  
  
7.  In the **Add Counters** dialog box, select **SQL Server:SSIS Pipeline** in the **Performance object** list.  
  
8.  To select performance counters, do one of the following:  
  
    -   Select **All Counters** to log all performance counters.  
  
    -   Select **Select counters in list** and select the performance counters to use.  
  
9. Click **Add**.  
  
10. Click **Close**.  
  
11. In the **MyLog** dialog box, review the list of logging performance counters in the **Counters** list.  
  
12. To add additional counters, repeat steps 5 through 10.  
  
13. Click **OK**.  
  
    > [!NOTE]  
    >  You must start the Performance Logs and Alerts service using a local account or a domain account that is a member of the Administrators group.  
  
## See Also  
 [Performance Counters](../../Topics\TopicNameNotContainA/Performance-Counters.md)   
 [View Log Entries in the Log Events Window](../../Topics\TopicNameNotContainA/View-Log-Entries-in-the-Log-Events-Window.md)  
  
  