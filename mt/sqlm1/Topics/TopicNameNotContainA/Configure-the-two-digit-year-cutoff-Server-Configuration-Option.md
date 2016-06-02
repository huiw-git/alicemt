---
title: Configure the two digit year cutoff Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d94e81b6-f2e6-47ef-b497-ec3d827a1646
---
# Configure the two digit year cutoff Server Configuration Option
  This topic describes how to configure the **two digit year cutoff** server configuration option in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. The **two digit year cutoff** option specifies an integer from 1753 to 9999 that represents the cutoff year for interpreting two\-digit years as four\-digit years. The default time span for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is 1950\-2049, which represents a cutoff year of 2049. This means that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] interprets a two\-digit year of 49 as 2049, a two\-digit year of 50 as 1950, and a two\-digit year of 99 as 1999. To maintain backward compatibility, leave the setting at the default value.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To configure the two digit year cutoff option, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After you configure the two digit year cutoff option](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] technician.  
  
-   OLE Automation objects use 2030 as the two\-digit cutoff year. You can use the **two digit year cutoff** option to provide consistency in date values between [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and client applications. However, to avoid ambiguity with dates, use four\-digit years in your data.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Execute permissions on **sp\_configure** with no parameters or with only the first parameter are granted to all users by default. To execute **sp\_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server\-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To configure the two digit year cutoff option  
  
1.  In Object Explorer, right\-click a server and select **Properties**.  
  
2.  Click the **Misc server settings** node.  
  
3.  Under **Two digit year support**, in the **When a two digit year is entered**, **interpret it as a year between** box, type or select a value that is the ending year of the time span.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To configure the two digit year cutoff option  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp\_configure](../Topic/sp_configure%20\(Transact-SQL\).md) to set the value of the `two digit year cutoff` option to `2030`.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'two digit year cutoff', 2030 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 For more information, see [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md).  
  
##  <a name="FollowUp"></a> Follow Up: After you configure the two digit year cutoff option  
 The setting takes effect immediately without restarting the server.  
  
## See Also  
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)   
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)  
  
  