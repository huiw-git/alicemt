---
title: Increase the Size of a Database
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 14f4206d-3afa-4ba9-9849-23e81d63306d
---
# Increase the Size of a Database
  This topic describes how to increase the size of a database in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. The database is expanded by either increasing the size of an existing data or log file or by adding a new file to the database.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To increase the size of a database, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   You cannot add or remove a file while a BACKUP statement is running.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the database.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To increase the size of a database  
  
1.  In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], and then expand that instance.  
  
2.  Expand **Databases**, right\-click the database to increase, and then click **Properties**.  
  
3.  In **Database Properties**, select the **Files** page.  
  
4.  To increase the size of an existing file, increase the value in the **Initial Size \(MB\)** column for the file. You must increase the size of the database by at least 1 megabyte.  
  
5.  To increase the size of the database by adding a new file, click **Add** and then enter the values for the new file. For more information, see [Add Data or Log Files to a Database](../../Topics\TopicNameContainA/Add-Data-or-Log-Files-to-a-Database.md).  
  
6.  Click **OK**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To increase the size of a database  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example increases the size of the file `test1dat3`.  
  
 [!CODE [DatabaseDDL#AlterDatabase5](../CodeSnippet/SQL15/tsql/databaseddl#alterdatabase5)]  
  
 For more examples, see [ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20File%20and%20Filegroup%20Options%20\(Transact-SQL\).md).  
  
## See Also  
 [Add Data or Log Files to a Database](../../Topics\TopicNameContainA/Add-Data-or-Log-Files-to-a-Database.md)   
 [Shrink a Database](../../Topics\TopicNameContainA/Shrink-a-Database.md)  
  
  