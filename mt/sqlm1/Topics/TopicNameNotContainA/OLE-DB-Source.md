---
title: OLE DB Source
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f87cc5f6-b078-40f3-9d87-7a65e13e4c86
---
# OLE DB Source
  The OLE DB source extracts data from a variety of OLE DB\-compliant relational databases by using a database table, a view, or an SQL command. For example, the OLE DB source can extract data from tables in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Office Access or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] databases.  
  
> [!NOTE]  
>  If the data source is [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Office Excel 2007, the data source requires a different connection manager than earlier versions of Excel. For more information, see [Connect to an Excel Workbook](../../Topics\TopicNameNotContainA/Connect-to-an-Excel-Workbook.md).  
  
 The OLE DB source provides four different data access modes for extracting data:  
  
-   A table or view.  
  
-   A table or view specified in a variable.  
  
-   The results of an SQL statement. The query can be a parameterized query.  
  
-   The results of an SQL statement stored in a variable.  
  
> [!NOTE]  
>  When you use an SQL statement to invoke a stored procedure that returns results from a temporary table, use the WITH RESULT SETS option to define metadata for the result set.  
  
 If you use a parameterized query, you can map variables to parameters to specify the values for individual parameters in the SQL statements.  
  
 This source uses an OLE DB connection manager to connect to a data source, and the connection manager specifies the OLE DB provider to use. For more information, see [OLE DB Connection Manager](../../Topics\TopicNameNotContainA/OLE-DB-Connection-Manager.md).  
  
 An [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project also provides the data source object from which you can create an OLE DB connection manager, making data sources and data source views available to the OLE DB source.  
  
 Depending on the OLE DB provider, some limitations apply to the OLE DB source:  
  
-   The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] OLE DB provider for Oracle does not support the Oracle data types BLOB, CLOB, NCLOB, BFILE, OR UROWID, and the OLE DB source cannot extract data from tables that contain columns with these data types.  
  
-   The IBM OLE DB DB2 provider and [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] OLE DB DB2 provider do not support using an SQL command that calls a stored procedure. When this kind of command is used, the OLE DB source cannot create the column metadata and, as a result, the data flow components that follow the OLE DB source in the data flow have no column data available and the execution of the data flow fails.  
  
 The OLE DB source has one regular output and one error output.  
  
## Using Parameterized SQL Statements  
 The OLE DB source can use an SQL statement to extract data. The statement can be a SELECT or an EXEC statement.  
  
 The OLE DB source uses an OLE DB connection manager to connect to the data source from which it extracts data. Depending on the provider that the OLE DB connection manager uses and the Relational Database Management System \(RDBMS\) that the connection manager connects to, different rules apply to the naming and listing of parameters. If the parameter names are returned from the RDBMS, you can use parameter names to map parameters in a parameter list to parameters in an SQL statement; otherwise, the parameters are mapped to the parameter in the SQL statement by their ordinal position in the parameter list. The types of parameter names that are supported vary by provider. For example, some providers require that you use the variable or column names, whereas some providers require that you use symbolic names such as 0 or Param0. You should see the provider\-specific documentation for information about the parameter names to use in SQL statements.  
  
 When you are use an OLE DB connection manager, you cannot use parameterized subqueries, because the OLE DB source cannot derive parameter information through the OLE DB provider. However, you can use an expression to concatenate the parameter values into the query string and to set the SqlCommand property of the source.In [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, you configure an OLE DB source by using the **OLE DB Source Editor** dialog box and map the parameters to variables in the **Set Query Parameter** dialog box.  
  
### Specifying Parameters by Using Ordinal Positions  
 If no parameter names are returned, the order in which the parameters are listed in the **Parameters** list in the **Set Query Parameter** dialog box governs which parameter marker they are mapped to at run time. The first parameter in the list maps to the first ? in the SQL statement, the second to the second ?, and so on.  
  
 The following SQL statement selects rows from the **Product** table in the [!INCLUDE[ssSampleDBUserInputNonLocal](../../Token\Other/ssSampleDBUserInputNonLocal_md.md)] database. The first parameter in the **Mappings** list maps to the first parameter to the **Color** column, the second parameter to the **Size** column.  
  
 `SELECT * FROM Production.Product WHERE Color = ? AND Size = ?`  
  
 The parameter names have no effect. For example, if a parameter is named the same as the column to which it applies, but not put in the correct ordinal position in the **Parameters** list, the parameter mapping that occurs at run time will use the ordinal position of the parameter, not the parameter name.  
  
 The EXEC command typically requires that you use the names of the variables that provide parameter values in the procedure as parameter names.  
  
### Specifying Parameters by Using Names  
 If the actual parameter names are returned from the RDBMS, the parameters used by a SELECT and EXEC statement are mapped by name. The parameter names must match the names that the stored procedure, run by the SELECT statement or the EXEC statement, expects.  
  
 The following SQL statement runs the **uspGetWhereUsedProductID** stored procedure, available in the [!INCLUDE[ssSampleDBUserInputNonLocal](../../Token\Other/ssSampleDBUserInputNonLocal_md.md)] database.  
  
 `EXEC uspGetWhereUsedProductID ?, ?`  
  
 The stored procedure expects the variables, `@StartProductID` and `@CheckDate`, to provide parameter values. The order in which the parameters appear in the **Mappings** list is irrelevant. The only requirement is that the parameter names match the variable names in the stored procedure, including the @ sign.  
  
### Mapping Parameters to Variables  
 The parameters are mapped to variables that provide the parameter values at run time. The variables are typically user\-defined variables, although you can also use the system variables that [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] provides. If you use user\-defined variables, make sure that you set the data type to a type that is compatible with the data type of the column that the mapped parameter references. For more information, see [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md).  
  
## Troubleshooting the OLE DB Source  
 You can log the calls that the OLE DB source makes to external data providers. You can use this logging capability to troubleshoot the loading of data from external data sources that the OLE DB source performs. To log the calls that the OLE DB source makes to external data providers, enable package logging and select the **Diagnostic** event at the package level. For more information, see [Troubleshooting Tools for Package Execution](../../Topics\TopicNameNotContainA/Troubleshooting-Tools-for-Package-Execution.md).  
  
## Configuring the OLE DB Source  
 You can set properties programmatically or through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer.  
  
 For more information about the properties that you can set in the **OLE DB Source Editor** dialog box, click one of the following topics:  
  
-   [OLE DB Source Editor &#40;Connection Manager Page&#41;](../Topic/OLE%20DB%20Source%20Editor%20\(Connection%20Manager%20Page\).md)  
  
-   [OLE DB Source Editor &#40;Columns Page&#41;](../Topic/OLE%20DB%20Source%20Editor%20\(Columns%20Page\).md)  
  
-   [OLE DB Source Editor &#40;Error Output Page&#41;](../Topic/OLE%20DB%20Source%20Editor%20\(Error%20Output%20Page\).md)  
  
 The **Advanced Editor** dialog box reflects the properties that can be set programmatically. For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:  
  
-   [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md)  
  
-   [OLE DB Custom Properties](../../Topics\TopicNameNotContainA/OLE-DB-Custom-Properties.md)  
  
## Related Tasks  
  
-   [Extract Data by Using the OLE DB Source](../../Topics\TopicNameNotContainA/Extract-Data-by-Using-the-OLE-DB-Source.md)  
  
-   [Map Query Parameters to Variables in a Data Flow Component](../../Topics\TopicNameContainA/Map-Query-Parameters-to-Variables-in-a-Data-Flow-Component.md)  
  
-   [Set the Properties of a Data Flow Component](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md)  
  
-   [Sort Data for the Merge and Merge Join Transformations](../../Topics\TopicNameNotContainA/Sort-Data-for-the-Merge-and-Merge-Join-Transformations.md)  
  
## Related Content  
 Wiki article, [SSIS with Oracle Connectors](http://go.microsoft.com/fwlink/?LinkId=220670), on social.technet.microsoft.com.  
  
## See Also  
 [OLE DB Destination](../../Topics\TopicNameNotContainA/OLE-DB-Destination.md)   
 [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md)   
 [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md)  
  
  