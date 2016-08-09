---
title: "View the Table Definition"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-tables
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1865fb7c-f480-4100-9007-df5364cd002a
caps.latest.revision: 19
caps.handback.revision: 0
manager: jhubbard
---
# View the Table Definition
You can display properties for a table in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To display table properties, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 You can only see properties in a table if you either own the table or have been granted permissions to that table.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To show table properties in the Properties window  
  
1.  In Object Explorer, select the table for which you want to show properties.  
  
2.  Right-click the table and choose **Properties** from the shortcut menu. For more information, see [Table Properties - SSMS](../../Topics/TopicNameNotContainA/Table-Properties---SSMS.md).  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To show table properties  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. The example returns all columns from the `sys.tables` catalog view for the specified object.  
  
    ```  
    SELECT * FROM sys.tables  
    WHERE object_id = 1973582069;  
  
    ```  
  
 For more information, see [sys.tables (Transact-SQL)](assetId:///8c42eba1-c19f-4045-ac82-b97a5e994090).  
  
###  <a name="TsqlExample"></a>