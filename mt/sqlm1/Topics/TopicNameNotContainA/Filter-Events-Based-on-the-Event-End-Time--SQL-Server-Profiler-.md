---
title: Filter Events Based on the Event End Time (SQL Server Profiler)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 74628f9e-2d39-496a-a443-0a3887db223d
---
# Filter Events Based on the Event End Time (SQL Server Profiler)
  This topic describes how to filter trace events based on the event ending time by using [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)].  
  
### To filter events based on the event end time  
  
1.  On the **File** menu, click **New Trace**, and then connect to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
     The **Trace Properties**dialog box appears.  
  
    > [!NOTE]  
    >  If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead. To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.  
  
2.  In the **Trace Properties** dialog box, make sure the **General** tab is selected, and enter a name in the **TraceName** text box.  
  
3.  From the **Use the template**list, select a trace template.  
  
4.  Optionally, specify a destination file or table in which to save the trace results.  
  
5.  On the **Events Selection**tab, click the **EndTime** data column to launch the **Edit Filter** dialog box. You can also right\-click the column heading, and select **Edit Column Filter**.  
  
6.  Expand **Greater than** or **Less than**, and enter a **datetime**value in the field that appears beneath the comparison operator.  
  
## See Also  
 [SQL Server Profiler](../../Topics\TopicNameNotContainA/SQL-Server-Profiler.md)   
 [SQL Server Profiler](../../Topics\TopicNameNotContainA/SQL-Server-Profiler.md)  
  
  