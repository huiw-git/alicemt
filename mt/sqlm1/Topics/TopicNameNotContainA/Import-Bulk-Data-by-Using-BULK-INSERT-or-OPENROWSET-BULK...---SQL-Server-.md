---
title: Import Bulk Data by Using BULK INSERT or OPENROWSET(BULK...) (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-bulk-import-export
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 18a64236-0285-46ea-8929-6ee9bcc020b9
---
# Import Bulk Data by Using BULK INSERT or OPENROWSET(BULK...) (SQL Server)
  This topic provides an overview of how to use the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] BULK INSERT statement and the INSERT...SELECT \* FROM OPENROWSET\(BULK...\) statement to bulk import data from a data file into a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table. This topic also describes security considerations for using BULK INSERT and OPENROWSET\(BULK…\), and using these methods to bulk import from a remote data source.  
  
> [!NOTE]  
>  When you use BULK INSERT or OPENROWSET\(BULK…\), it is important to understand how [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] version handles impersonation. For more information, see "Security Considerations," later in this topic.  
  
## BULK INSERT Statement  
 BULK INSERT loads data from a data file into a table. This functionality is similar to that provided by the **in** option of the **bcp** command; however, the data file is read by the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] process. For a description of the BULK INSERT syntax, see [BULK INSERT &#40;Transact-SQL&#41;](../Topic/BULK%20INSERT%20\(Transact-SQL\).md).  
  
### Examples  
 For BULK INSERT examples, see:  
  
-   [BULK INSERT &#40;Transact-SQL&#41;](../Topic/BULK%20INSERT%20\(Transact-SQL\).md)  
  
-   [Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;](../Topic/Examples%20of%20Bulk%20Import%20and%20Export%20of%20XML%20Documents%20\(SQL%20Server\).md)  
  
-   [Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;](../Topic/Keep%20Identity%20Values%20When%20Bulk%20Importing%20Data%20\(SQL%20Server\).md)  
  
-   [Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;](../Topic/Keep%20Nulls%20or%20Use%20Default%20Values%20During%20Bulk%20Import%20\(SQL%20Server\).md)  
  
-   [Specify Field and Row Terminators &#40;SQL Server&#41;](../Topic/Specify%20Field%20and%20Row%20Terminators%20\(SQL%20Server\).md)  
  
-   [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](../Topic/Use%20a%20Format%20File%20to%20Bulk%20Import%20Data%20\(SQL%20Server\).md)  
  
-   [Use Character Format to Import or Export Data &#40;SQL Server&#41;](../Topic/Use%20Character%20Format%20to%20Import%20or%20Export%20Data%20\(SQL%20Server\).md)  
  
-   [Use Native Format to Import or Export Data &#40;SQL Server&#41;](../Topic/Use%20Native%20Format%20to%20Import%20or%20Export%20Data%20\(SQL%20Server\).md)  
  
-   [Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;](../Topic/Use%20Unicode%20Character%20Format%20to%20Import%20or%20Export%20Data%20\(SQL%20Server\).md)  
  
-   [Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;](../Topic/Use%20Unicode%20Native%20Format%20to%20Import%20or%20Export%20Data%20\(SQL%20Server\).md)  
  
-   [Use a Format File to Skip a Table Column &#40;SQL Server&#41;](../Topic/Use%20a%20Format%20File%20to%20Skip%20a%20Table%20Column%20\(SQL%20Server\).md)  
  
-   [Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;](../Topic/Use%20a%20Format%20File%20to%20Map%20Table%20Columns%20to%20Data-File%20Fields%20\(SQL%20Server\).md)  
  
## OPENROWSET\(BULK…\) Function  
 The OPENROWSET bulk rowset provider is accessed by calling the OPENROWSET function and specifying the BULK option. The OPENROWSET\(BULK…\) function allows you to access remote data by connecting to a remote data source, such as a data file, through an OLE DB provider.  
  
 To bulk import data, call OPENROWSET\(BULK…\) from a SELECT…FROM clause within an INSERT statement. The basic syntax for bulk importing data is:  
  
 INSERT ... SELECT \* FROM OPENROWSET\(BULK...\)  
  
 When used in an INSERT statement, OPENROWSET\(BULK...\) supports table hints. In addition to the regular table hints, such as TABLOCK, the BULK clause can accept the following specialized table hints: IGNORE\_CONSTRAINTS \(ignores only the CHECK constraints\), IGNORE\_TRIGGERS, KEEPDEFAULTS, and KEEPIDENTITY. For more information, see [Table Hints &#40;Transact-SQL&#41;](../Topic/Table%20Hints%20\(Transact-SQL\).md).  
  
 For information about additional uses of the BULK option, see [OPENROWSET &#40;Transact-SQL&#41;](../Topic/OPENROWSET%20\(Transact-SQL\).md).  
  
### Examples  
 For examples of INSERT...SELECT \* FROM OPENROWSET\(BULK...\) statements, see the following topics:  
  
-   [Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;](../Topic/Examples%20of%20Bulk%20Import%20and%20Export%20of%20XML%20Documents%20\(SQL%20Server\).md)  
  
-   [Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;](../Topic/Keep%20Identity%20Values%20When%20Bulk%20Importing%20Data%20\(SQL%20Server\).md)  
  
-   [Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;](../Topic/Keep%20Nulls%20or%20Use%20Default%20Values%20During%20Bulk%20Import%20\(SQL%20Server\).md)  
  
-   [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](../Topic/Use%20a%20Format%20File%20to%20Bulk%20Import%20Data%20\(SQL%20Server\).md)  
  
-   [Use Character Format to Import or Export Data &#40;SQL Server&#41;](../Topic/Use%20Character%20Format%20to%20Import%20or%20Export%20Data%20\(SQL%20Server\).md)  
  
-   [Use a Format File to Skip a Table Column &#40;SQL Server&#41;](../Topic/Use%20a%20Format%20File%20to%20Skip%20a%20Table%20Column%20\(SQL%20Server\).md)  
  
-   [Use a Format File to Skip a Data Field &#40;SQL Server&#41;](../Topic/Use%20a%20Format%20File%20to%20Skip%20a%20Data%20Field%20\(SQL%20Server\).md)  
  
-   [Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;](../Topic/Use%20a%20Format%20File%20to%20Map%20Table%20Columns%20to%20Data-File%20Fields%20\(SQL%20Server\).md)  
  
## Security Considerations  
 If a user uses a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login, the security profile of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] process account is used. A login using SQL Server authentication cannot be authenticated outside of the Database Engine. Therefore, when a BULK INSERT command is initiated by a login using SQL Server authentication, the connection to the data is made using the security context of the SQL Server process account \(the account used by the SQL Server Database Engine service\). To successfully read the source data you must grant the account used by the SQL Server Database Engine, access to the source data. In contrast, if a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] user logs on by using Windows Authentication, the user can read only those files that can be accessed by the user account, regardless of the security profile of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] process.  
  
 For example, consider a user who logged in to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] by using Windows Authentication. For the user to be able to use BULK INSERT or OPENROWSET to import data from a data file into a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table, the user account requires read access to the data file. With access to the data file, the user can import data from the file into a table even if the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] process does not have permission to access the file. The user does not have to grant file\-access permission to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] process.  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows can be configured to enable an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to connect to another instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] by forwarding the credentials of an authenticated Windows user. This arrangement is known as *impersonation* or *delegation*. Understanding how [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] version handle security for user impersonation is important when you use BULK INSERT or OPENROWSET. User impersonation allows the data file to reside on a different computer than either the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] process or the user. For example, if a user on **Computer\_A** has access to a data file on **Computer\_B**, and the delegation of credentials has been set appropriately, the user can connect to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that is running on **Computer\_C**, access the data file on **Computer\_B**, and bulk import data from that file into a table on **Computer\_C**.  
  
## Bulk Importing from a Remote Data File  
 To use BULK INSERT or INSERT...SELECT \* FROM OPENROWSET\(BULK...\) to bulk import data from another computer, the data file must be shared between the two computers. To specify a shared data file, use its universal naming convention \(UNC\) name, which takes the general form, **\\\\***Servername***\\***Sharename***\\***Path***\\***Filename*. Additionally, the account used to access the data file must have the permissions that are required for reading the file on the remote disk.  
  
 For example, the following `BULK INSERT` statement bulk imports data into the `SalesOrderDetail` table of the `AdventureWorks` database from a data file that is named `newdata.txt`. This data file resides in a shared folder named `\dailyorders` on a network share directory named `salesforce` on a system named `computer2`.  
  
```  
BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
   FROM '\\computer2\salesforce\dailyorders\neworders.txt';  
GO  
```  
  
> [!NOTE]  
>  This restriction does not apply to the **bcp** utility because the client reads the file independently of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
## See Also  
 [INSERT &#40;Transact-SQL&#41;](../Topic/INSERT%20\(Transact-SQL\).md)   
 [SELECT Clause &#40;Transact-SQL&#41;](../Topic/SELECT%20Clause%20\(Transact-SQL\).md)   
 [Bulk Import and Export of Data &#40;SQL Server&#41;](../Topic/Bulk%20Import%20and%20Export%20of%20Data%20\(SQL%20Server\).md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../Topic/OPENROWSET%20\(Transact-SQL\).md)   
 [SELECT &#40;Transact-SQL&#41;](../Topic/SELECT%20\(Transact-SQL\).md)   
 [FROM &#40;Transact-SQL&#41;](../Topic/FROM%20\(Transact-SQL\).md)   
 [bcp Utility](../../Topics\TopicNameNotContainA/bcp-Utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../Topic/BULK%20INSERT%20\(Transact-SQL\).md)  
  
  