---
title: "View the Windows Application Log (Windows)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 168a6c6e-12df-46a9-9904-55d63ca8fe14
caps.latest.revision: 25
manager: jhubbard
---
# View the Windows Application Log (Windows)
When [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is configured to use the Windows application log, each [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] session writes new events to that log. Unlike the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] error log, a new application log is not created each time you start an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
### To view the Windows application log  
  
1.  On the **Start** menu, point to **All Programs**, point to **Administrative Tools**, and then click **Event Viewer**.  
  
2.  In Event Viewer, click **Application**.  
  
3.  [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] events are identified by the entry **MSSQLSERVER** (named instances are identified with **MSSQL$***<instance_name>*) in the **Source** column. SQL Server Agent events are identified by the entry SQLSERVERAGENT (for named instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent events are identified with **SQLAgent$**<*instance_name*>). Microsoft Search service events are identified by the entry **Microsoft Search**.  
  
4.  To view the log of a different computer, right-click **Event Viewer**, click **Connect to another computer,** and complete the **Select Computer**dialog box.  
  
5.  Optionally, to display only [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] events, on the **View** menu click **Filter**, and in the **Event source** list, select **MSSQLSERVER**. To view only [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent events, instead select **SQLSERVERAGENT** in the **Event source** list.  
  
6.  To view more information about an event, double-click the event.  
  
## See Also  
 [View the SQL Server Error Log (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/View-the-SQL-Server-Error-Log--SQL-Server-Management-Studio-.md)