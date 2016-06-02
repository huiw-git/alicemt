---
title: Execute SQL Task
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bebb2e8c-0410-43b2-ac2f-6fc80c8f2e9e
---
# Execute SQL Task
  The Execute SQL task runs SQL statements or stored procedures from a package. The task can contain either a single SQL statement or multiple SQL statements that run sequentially. You can use the Execute SQL task for the following purposes:  
  
-   Truncate a table or view in preparation for inserting data.  
  
-   Create, alter, and drop database objects such as tables and views.  
  
-   Re\-create fact and dimension tables before loading data into them.  
  
-   Run stored procedures. If the SQL statement invokes a stored procedure that returns results from a temporary table, use the WITH RESULT SETS option to define metadata for the result set.  
  
-   Save the rowset returned from a query into a variable.  
  
 The Execute SQL task can be used in combination with the Foreach Loop and For Loop containers to run multiple SQL statements. These containers implement repeating control flows in a package and they can run the Execute SQL task repeatedly. For example, using the Foreach Loop container, a package can enumerate files in a folder and run an Execute SQL task repeatedly to execute the SQL statement stored in each file.  
  
## Connecting to a Data Source  
 The Execute SQL task can use different types of connection managers to connect to the data source where it runs the SQL statement or stored procedure. The task can use the connection types listed in the following table.  
  
|Connection type|Connection manager|  
|---------------------|------------------------|  
|EXCEL|[Excel Connection Manager](../../Topics\TopicNameNotContainA/Excel-Connection-Manager.md)|  
|OLE DB|[OLE DB Connection Manager](../../Topics\TopicNameNotContainA/OLE-DB-Connection-Manager.md)|  
|ODBC|[ODBC Connection Manager](../../Topics\TopicNameNotContainA/ODBC-Connection-Manager.md)|  
|ADO|[ADO Connection Manager](../../Topics\TopicNameNotContainA/ADO-Connection-Manager.md)|  
|ADO.NET|[ADO.NET Connection Manager](../../Topics\TopicNameNotContainA/ADO.NET-Connection-Manager.md)|  
|SQLMOBILE|[SQL Server Compact Edition Connection Manager](../../Topics\TopicNameNotContainA/SQL-Server-Compact-Edition-Connection-Manager.md)|  
  
## Creating SQL Statements  
 The source of the SQL statements used by this task can be a task property that contains a statement, a connection to a file that contains one or multiple statements, or the name of a variable that contains a statement. The SQL statements must be written in the dialect of the source database management system \(DBMS\). For more information, see [Integration Services &#40;SSIS&#41; Queries](../Topic/Integration%20Services%20\(SSIS\)%20Queries.md).  
  
 If the SQL statements are stored in a file, the task uses a File connection manager to connect to the file. For more information, see [File Connection Manager](../../Topics\TopicNameNotContainA/File-Connection-Manager.md).  
  
 In [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, you can use the **Execute SQL Task Editor** dialog box to type SQL statements, or use **Query Builder**, a graphical user interface for creating SQL queries. For more information, see [Execute SQL Task Editor &#40;General Page&#41;](../Topic/Execute%20SQL%20Task%20Editor%20\(General%20Page\).md) and [Query Builder](../../Topics\TopicNameNotContainA/Query-Builder.md).  
  
> [!NOTE]  
>  Valid SQL statements written outside the Execute SQL task may not be parsed successfully by the Execute SQL task.  
  
> [!NOTE]  
>  The Execute SQL Task uses the **RecognizeAll** ParseMode enumeration value. For more information, see [ManagedBatchParser Namespace](http://go.microsoft.com/fwlink/?LinkId=223617).  
  
## Sending Multiple Statements in a Batch  
 If you include multiple statements in an Execute SQL task, you can group them and run them as a batch. To signal the end of a batch, use the GO command. All the SQL statements between two GO commands are sent in a batch to the OLE DB provider to be run. The SQL command can include multiple batches separated by GO commands.  
  
 There are restrictions on the kinds of SQL statements that you can group in a batch. For more information, see [Batches of Statements](../Topic/Batches%20of%20Statements.md).  
  
 If the Execute SQL task runs a batch of SQL statements, the following rules apply to the batch:  
  
-   Only one statement can return a result set and it must be the first statement in the batch.  
  
-   If the result set uses result bindings, the queries must return the same number of columns. If the queries return a different number of columns, the task fails. However, even if the task fails, the queries that it runs, such as DELETE or INSERT queries, may succeed.  
  
-   If the result bindings use column names, the query must return columns that have the same names as the result set names that are used in the task. If the columns are missing, the task fails.  
  
-   If the task uses parameter binding, all the queries in the batch must have the same number and types of parameters.  
  
## Running Parameterized SQL Commands  
 SQL statements and stored procedures frequently use input parameters, output parameters, and return codes. The Execute SQL task supports the **Input**, **Output**, and **ReturnValue** parameter types. You use the **Input** type for input parameters, **Output** for output parameters, and **ReturnValue** for return codes.  
  
> [!NOTE]  
>  You can use parameters in an Execute SQL task only if the data provider supports them.  
  
 For information on using parameters and return codes in the Execute SQL task, see [Parameters and Return Codes in the Execute SQL Task](../../Topics\TopicNameNotContainA/Parameters-and-Return-Codes-in-the-Execute-SQL-Task.md).  
  
## Specifying a Result Set Type  
 Depending on the type of SQL command, a result set may or may not be returned to the Execute SQL task. For example, a SELECT statement typically returns a result set, but an INSERT statement does not. The result set from a SELECT statement can contain zero rows, one row, or many rows. Stored procedures can also return an integer value, called a return code, that indicates the execution status of the procedure. In that case, the result set consists of a single row.  
  
 For information on retrieving result sets from SQL commands in the Execute SQL task, see [Result Sets in the Execute SQL Task](../../Topics\TopicNameNotContainA/Result-Sets-in-the-Execute-SQL-Task.md).  
  
## Troubleshooting the Execute SQL Task  
 You can log the calls that the Execute SQL task makes to external data providers. You can use this logging capability to troubleshoot the SQL commands that the Execute SQL task runs. To log the calls that the Execute SQL task makes to external data providers, enable package logging and select the **Diagnostic** event at the package level. For more information, see [Troubleshooting Tools for Package Execution](../../Topics\TopicNameNotContainA/Troubleshooting-Tools-for-Package-Execution.md).  
  
 Sometimes a SQL command or stored procedure returns multiple result sets. These result sets include not only rowsets that are the result of **SELECT** queries, but single values that are the result of errors of **RAISERROR** or **PRINT** statements. Whether the task ignores errors in result sets that occur after the first result set depends on the type of connection manager that is used:  
  
-   When you use OLE DB and ADO connection managers, the task ignores the result sets that occur after the first result set. Therefore, with these connection managers, the task ignores an error returned by an SQL command or a stored procedure when the error is not part of the first result set.  
  
-   When you use ODBC and ADO.NET connection managers, the task does not ignore result sets that occur after the first result set. With these connection managers, the task will fail with an error when a result set other than the first result set contains an error.  
  
### Custom Log Entries  
 The following table describes the custom log entry for the Execute SQL task. For more information, see [Integration Services &#40;SSIS&#41; Logging](../Topic/Integration%20Services%20\(SSIS\)%20Logging.md) and [Custom Messages for Logging](../../Topics\TopicNameNotContainA/Custom-Messages-for-Logging.md).  
  
|Log entry|Description|  
|---------------|-----------------|  
|**ExecuteSQLExecutingQuery**|Provides information about the execution phases of the SQL statement. Log entries are written when the task acquires connection to the database, when the task starts to prepare the SQL statement, and after the execution of the SQL statement is completed. The log entry for the prepare phase includes the SQL statement that the task uses.|  
  
## Configuring the Execute SQL Task  
 You can configure the Execute SQL task in the following ways:  
  
-   Specify the type of connection manager to use to connect to a database.  
  
-   Specify the type of result set that the SQL statement returns.  
  
-   Specify a time\-out for the SQL statements.  
  
-   Specify the source of the SQL statement.  
  
-   Indicate whether the task skips the prepare phase for the SQL statement.  
  
-   If you use the ADO connection type, you must indicate whether the SQL statement is a stored procedure. For other connection types, this property is read\-only and its value is always **false**.  
  
 You can set properties programmatically or through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click one of the following topics:  
  
-   [Execute SQL Task Editor &#40;General Page&#41;](../Topic/Execute%20SQL%20Task%20Editor%20\(General%20Page\).md)  
  
-   [Execute SQL Task Editor &#40;Parameter Mapping Page&#41;](../Topic/Execute%20SQL%20Task%20Editor%20\(Parameter%20Mapping%20Page\).md)  
  
-   [Execute SQL Task Editor &#40;Result Set Page&#41;](../Topic/Execute%20SQL%20Task%20Editor%20\(Result%20Set%20Page\).md)  
  
-   [Expressions Page](../../Topics\TopicNameNotContainA/Expressions-Page.md)  
  
 For more information about how to set these properties in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the following topic:  
  
-   [Set the Properties of a Task or Container](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md)  
  
## Configuring the Execute SQL Task Programmatically  
 For more information about programmatically setting these properties, click the following topic:  
  
-   [ExecuteSQLTask](assetId:///T:Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask.ExecuteSQLTask)  
  
## Related Tasks  
  
-   [Map Query Parameters to Variables in an Execute SQL Task](../../Topics\TopicNameNotContainA/Map-Query-Parameters-to-Variables-in-an-Execute-SQL-Task.md)  
  
-   [Map Result Sets to Variables in an Execute SQL Task](../../Topics\TopicNameNotContainA/Map-Result-Sets-to-Variables-in-an-Execute-SQL-Task.md)  
  
## Related Content  
  
-   [Parameters and Return Codes in the Execute SQL Task](../../Topics\TopicNameNotContainA/Parameters-and-Return-Codes-in-the-Execute-SQL-Task.md)  
  
-   [Result Sets in the Execute SQL Task](../../Topics\TopicNameNotContainA/Result-Sets-in-the-Execute-SQL-Task.md)  
  
-   [Transact-SQL Reference &#40;Database Engine&#41;](../Topic/Transact-SQL%20Reference%20\(Database%20Engine\).md)  
  
-   Blog entry, [New Date and Time Functions in SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=239783), on mssqltips.com  
  
  