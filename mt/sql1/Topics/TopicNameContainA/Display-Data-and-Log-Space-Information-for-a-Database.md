---
title: "Display Data and Log Space Information for a Database"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c7b99463-4bab-4e9b-9217-fcb0898dc757
caps.latest.revision: 28
caps.handback.revision: 0
manager: jhubbard
---
# Display Data and Log Space Information for a Database
This topic describes how to display the data and log space information for a database in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To display data and log space information for a database, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Permission to execute **sp_spaceused** is granted to the **public** role. Only members of the **db_owner** fixed database role can specify the **@updateusage** parameter.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To display data and log space information for a database  
  
1.  In Object Explorer, connect to an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and then expand that instance.  
  
2.  Expand **Databases**.  
  
3.  Right-click a database, point to **Reports**, point to **Standard Reports,**, and then click **Disk Usage**.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To display data and log space information for a database by using sp_spaceused  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example uses the [sp_spaceused](assetId:///c6253b48-29f5-4371-bfcd-3ef404060621) system stored procedure to report disk space information for the `Vendor` table and its indexes.  
  
```tsql  
USE AdventureWorks2012;  
GO  
EXEC sp_spaceused N'Purchasing.Vendor';  
GO  
```  
  
#### To display data and log space information for a database by querying sys.database_files  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example queries the [sys.database_files](assetId:///0f5b0aac-c17d-4e99-b8f7-d04efc9edf44) catalog view to return specific information about the data and log files in the [!INCLUDE[ssSampleDBobject](../../Topics/TopicNameContainA/tokens/ssSampleDBobject_md.md)] database.  
  
```tsql  
USE AdventureWorks2012;  
GO  
SELECT file_id, name, type_desc, physical_name, size, max_size  
FROM sys.database_files ;  
GO  
  
```  
  
## See Also  
 [SELECT (Transact-SQL)](assetId:///dc85caea-54d1-49af-b166-f3aa2f3a93d0)   
 [sys.database_files (Transact-SQL)](assetId:///0f5b0aac-c17d-4e99-b8f7-d04efc9edf44)   
 [sp_spaceused (Transact-SQL)](assetId:///c6253b48-29f5-4371-bfcd-3ef404060621)   
 [Add Data or Log Files to a Database](../../Topics/TopicNameContainA/Add-Data-or-Log-Files-to-a-Database.md)   
 [Delete Data or Log Files from a Database](../../Topics/TopicNameContainA/Delete-Data-or-Log-Files-from-a-Database.md)