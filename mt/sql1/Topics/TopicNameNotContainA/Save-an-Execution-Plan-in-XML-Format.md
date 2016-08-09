---
title: "Save an Execution Plan in XML Format"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c439e53b-56f3-4442-97c6-dabd48a203d8
caps.latest.revision: 25
caps.handback.revision: 0
manager: jhubbard
---
# Save an Execution Plan in XML Format
Use [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] to save execution plans as an XML file, and to open them for viewing.  
  
 To use the execution plan feature in [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)], or to use the XML Showplan SET options, users must have the appropriate permissions to execute the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] query for which an execution plan is being generated, and they must be granted the SHOWPLAN permission for all databases referenced by the query.  
  
### To save a query plan by using the XML Showplan SET options  
  
1.  In [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] open a query editor and connect to [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  Turn SHOWPLAN_XML on with the following statement:  
  
    ```  
    SET SHOWPLAN_XML ON;  
    GO  
    ```  
  
     To turn STATISTICS XML on, use the following statement:  
  
    ```  
    SET STATISTICS XML ON;  
    GO  
    ```  
  
     SHOWPLAN_XML generates compile-time query execution plan information for a query, but does not execute the query. STATISTICS XML generates run-time query execution plan information for a query, and executes the query.  
  
3.  Execute a query. Example:  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SET SHOWPLAN_XML ON;  
    GO  
    -- Execute a query.  
    SELECT BusinessEntityID   
    FROM HumanResources.Employee  
    WHERE NationalIDNumber = '509647174';  
    GO  
    SET SHOWPLAN_XML OFF;  
    ```  
  
4.  In the **Results** pane, right-click the **Microsoft SQL Server XML Showplan** that contains the query plan, and then click **Save Results As**.  
  
5.  In the **Save** <Grid or Text\> **Results** dialog box, in the **Save as type** box, click **All files (\*.\*)**.  
  
6.  In the **File name** box provide a name, in the format <name**>.sqlplan**, and then click **Save**.  
  
### To save an execution plan by using SQL Server Management Studio options  
  
1.  Generate either an estimated execution plan or an actual execution plan by using [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)]. For more information, see [Display the Estimated Execution Plan](../../Topics/TopicNameNotContainA/Display-the-Estimated-Execution-Plan.md) or [Display an Actual Execution Plan](../../Topics/TopicNameNotContainA/Display-an-Actual-Execution-Plan.md).  
  
2.  In the **Execution plan** tab of the results pane, right-click the graphical execution plan, and choose **Save Execution Plan As**.  
  
     As an alternative, you can also choose **Save Execution Plan As** on the **File** menu.  
  
3.  In the **Save As** dialog box, make sure that the **Save as type** is set to **Execution Plan Files (\*.sqlplan)**.  
  
4.  In the **File name** box provide a name, in the format <name**>.sqlplan**, and then click **Save**.  
  
### To open a saved XML query plan in SQL Server Management Studio  
  
1.  In [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], on the **File** menu, choose **Open**, and then click **File**.  
  
2.  In the **Open File** dialog box, set **Files of type** to **Execution Plan Files (\*.sqlplan)** to produce a filtered list of saved XML query plan files.  
  
3.  Select the XML query plan file that you want to view, and click **Open**.  
  
     As an alternative, in Windows Explorer, double-click a file with extension **.sqlplan**. The plan opens in [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)].  
  
## See Also  
 [SET SHOWPLAN_XML (Transact-SQL)](assetId:///a467a1b3-10a5-43c4-9085-13d8aed549c9)   
 [SET STATISTICS XML (Transact-SQL)](assetId:///2b6d4c5a-a7f5-4dd1-b10a-7632265b1af7)