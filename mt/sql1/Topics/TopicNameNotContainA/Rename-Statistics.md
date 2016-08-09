---
title: "Rename Statistics"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-statistics
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a3bed7b7-3dc5-4b33-b1c6-67c27f573764
caps.latest.revision: 12
caps.handback.revision: 0
manager: jhubbard
---
# Rename Statistics
You can rename a statistics object in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To rename a statistics object, using:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
 By default, creating an index creates a statistic on the key columns of that index. Therefore, renaming the index automatically renames the statistics object, and vice versa.  
  
 Changing any part of an object name can break scripts and stored procedures. Instead of renaming, we recommend that you drop the statistics object and re-create it with the new name.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the table or view.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To rename a statistics object  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_rename N'AK_Employee_LoginID', N'AK_Emp_Login', N'STATISTICS';   
    GO  
    ```  
  
 For more information, see [sp_rename (Transact-SQL)](assetId:///bc3548f0-143f-404e-a2e9-0a15960fc8ed).