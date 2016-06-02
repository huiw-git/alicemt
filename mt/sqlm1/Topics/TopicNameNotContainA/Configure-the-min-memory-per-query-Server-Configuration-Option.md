---
title: Configure the min memory per query Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ecd3fb79-b4a6-432f-9ef5-530e0d42d5a6
---
# Configure the min memory per query Server Configuration Option
  This topic describes how to configure the **min memory per query** server configuration option in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. The **min memory per query** option specifies the minimum amount of memory \(in kilobytes\) that will be allocated for the execution of a query. For example, if **min memory per query** is set to 2,048 KB, the query is guaranteed to get at least that much total memory. The default value is 1,024 KB. The minimum value 512 KB, and the maximum is 2,147,483,647 KB \(2 GB\).  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To configure the min memory per query option, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After you configure the min memory per query option](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   The amount of min memory per query has precedence over the [index create memory Option](../../Topics\TopicNameNotContainA/Configure-the-index-create-memory-Server-Configuration-Option.md). If you modify both options and the index create memory is less than min memory per query, you receive a warning message, but the value is set. During query execution you receive another similar warning.  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] technician.  
  
-   The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] query processor tries to determine the optimal amount of memory to allocate to a query. The min memory per query option lets the administrator specify the minimum amount of memory any single query receives. Queries generally receive more memory than this if they have hash and sort operations on a large volume of data. Increasing the value of min memory per query may improve performance for some small to medium\-sized queries, but doing so could lead to increased competition for memory resources. The min memory per query option includes memory allocated for sorting.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Execute permissions on **sp\_configure** with no parameters or with only the first parameter are granted to all users by default. To execute **sp\_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server\-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To configure the min memory per query option  
  
1.  In Object Explorer, right\-click a server and select **Properties**.  
  
2.  Click the **Memory** node.  
  
3.  In the **Minimum memory per query** box, enter the minimum amount of memory \(in kilobytes\) that will be allocated for the execution of a query.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To configure the min memory per query option  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp\_configure](../Topic/sp_configure%20\(Transact-SQL\).md) to set the value of the `min memory per query` option to `3500` KB.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'min memory per query', 3500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
##  <a name="FollowUp"></a> Follow Up: After you configure the min memory per query option  
 The setting takes effect immediately without restarting the server.  
  
## See Also  
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)   
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)   
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)   
 [Configure the index create memory Server Configuration Option](../../Topics\TopicNameNotContainA/Configure-the-index-create-memory-Server-Configuration-Option.md)  
  
  