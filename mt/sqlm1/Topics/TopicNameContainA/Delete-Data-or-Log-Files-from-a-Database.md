---
title: Delete Data or Log Files from a Database
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0db4018c-ce2c-4ba1-bb29-1e4f3791c925
---
# Delete Data or Log Files from a Database
  This topic describes how to delete data or log files in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Prerequisites](#Prerequisites)  
  
     [Security](#Security)  
  
-   **To delete data or logs files from a database, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   A file must be empty before it can be deleted. For more information, see [Shrink a File](../../Topics\TopicNameContainA/Shrink-a-File.md).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the database.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To delete data or log files from a database  
  
1.  In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] and then expand that instance.  
  
2.  Expand **Databases**, right\-click the database from which to delete the file, and then click **Properties**.  
  
3.  Select the **Files** page.  
  
4.  In the **Database files** grid, select the file to delete and then click **Remove**.  
  
5.  Click **OK**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To delete data or log files from a database  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example removes the file `test1dat4`.  
  
 [!CODE [DatabaseDDL#AlterDatabase4](../CodeSnippet/SQL15/tsql/databaseddl#alterdatabase4)]  
  
 For more examples, see [ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20File%20and%20Filegroup%20Options%20\(Transact-SQL\).md).  
  
## See Also  
 [Shrink a Database](../../Topics\TopicNameContainA/Shrink-a-Database.md)   
 [Add Data or Log Files to a Database](../../Topics\TopicNameContainA/Add-Data-or-Log-Files-to-a-Database.md)  
  
  