---
title: Text-based Query Designer User Interface
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 44b7c664-03aa-494e-a484-052b318e810c
robots: noindex,nofollow
---
# Text-based Query Designer User Interface
  Use the text\-based query designer to specify a query using the query language supported by the data source, run the query, and view the results at design time. You can specify multiple [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements, query or command syntax for custom data processing extensions, and queries that are specified as expressions. Because the text\-based query designer does not preprocess the query and can accommodate any kind of query syntax, this is the default query designer tool for many data source types.  
  
 The text\-based query designer displays a toolbar and the following two panes:  
  
-   **Query** Shows the query text, table name, or stored procedure name.  
  
-   **Result** Shows the results of running the query at design time.  
  
## Text\-based Query Designer Toolbar  
 The text\-based query designer provides a single toolbar for all the command types. The following table lists each button on the toolbar and its function.  
  
|Button|Description|  
|------------|-----------------|  
|**Edit As Text**|Toggle between the text\-based query designer and the graphical query designer. Not all data source types support graphical query designers.|  
|**Import**|Import an existing query from a file or report. Only file types sql and rdl are supported. For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../Topic/Report%20Embedded%20Datasets%20and%20Shared%20Datasets%20\(Report%20Builder%20and%20SSRS\).md).|  
|![Run the query](../../Images\Image\ImageNotContaina/rsQDIcon_Run.gif "rsQDIcon_Run")|Run the query and display the result set in the Result pane.|  
|**Command Type**|Select **Text**, **StoredProcedure**, or **TableDirect**. If a stored procedure has parameters, the **Define Query Parameters** dialog box appears when you click **Run** on the toolbar, and you can fill in values as needed. **Note:**  If a stored procedure returns more than one result set, only the first result set is used to populate the dataset. <br /><br /> Support for command type varies by data source type. For example, only OLE DB and ODBC support **TableDirect**.|  
  
### Command Type Text  
 When you create a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] dataset, Report Designer displays the graphical query designer by default. To switch to the text\-based query designer, click the **Edit As Text** toggle button on the toolbar. The text\-based query designer presents two panes: the Query pane and the Result pane. The following figure labels each pane.  
  
 ![Generic query designer, for relational data query](../../Images\Image\ImageNotContaina/rsQD_DSAW_SQL_Generic.gif "rsQD_DSAW_SQL_Generic")  
  
 The following table describes the function of each pane.  
  
|Pane|Function|  
|----------|--------------|  
|Query|Displays the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] query text. Use this pane to write or edit a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] query.|  
|Result|Displays the results of the query. To run the query, right\-click in any pane and click **Run**, or click the **Run** button on the toolbar.|  
  
#### Example  
 The following query returns the list of last names from the [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] database **Contact** table.  
  
```  
SELECT LastName FROM Person.Person;  
```  
  
 You can use any [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement for Command type Text, including **EXEC** statements. The following query calls the [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] stored procedure **uspGetEmployeeManagers** and returns the chain\-of\-command for the employee with identification number 1.  
  
```  
EXEC uspGetEmployeeManagers 1;  
```  
  
 When you click **Run** on the toolbar, the command in the **Query** pane runs and the results are displayed in the **Result** pane.  
  
### Command Type StoredProcedure  
 When you select **Command typeStoredProcedure**, the text\-based query designer presents two panes: the Query pane and the Result pane. Enter the stored procedure name in the Query pane and click **Run** on the toolbar. The Define Query Parameters dialog box opens. Enter the parameter values for the stored procedure. A report parameter is created for every stored procedure parameter.  
  
#### Example  
 The following query calls the [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] stored procedure **uspGetEmployeeManagers**. You must enter a value for the employee identification number parameter when you run the query.  
  
```  
uspGetEmployeeManagers;  
```  
  
### Command Type TableDirect  
 When you select **Command typeTableDirect**, the text\-based query designer presents two panes: the Query pane and the Result pane. When you enter a table and click the **Run** button, all the columns for that table are returned.  
  
#### Example  
 The following query returns a result set for all customers in the [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] database.  
  
 `Sales.Customer`  
  
 When you enter the table name Sales.Customer, it is the equivalent of creating the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement `SELECT * FROM Sales.Customer;`.  
  
## See Also  
 [Query Design Tools &#40;SSRS&#41;](../Topic/Query%20Design%20Tools%20\(SSRS\).md)   
 [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../Topic/Report%20Embedded%20Datasets%20and%20Shared%20Datasets%20\(Report%20Builder%20and%20SSRS\).md)   
 [SQL Server Connection Type &#40;SSRS&#41;](../Topic/SQL%20Server%20Connection%20Type%20\(SSRS\).md)   
 [OLE DB Connection Type &#40;SSRS&#41;](../Topic/OLE%20DB%20Connection%20Type%20\(SSRS\).md)   
 [ODBC Connection Type &#40;SSRS&#41;](../Topic/ODBC%20Connection%20Type%20\(SSRS\).md)   
 [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../Topic/Report%20Embedded%20Datasets%20and%20Shared%20Datasets%20\(Report%20Builder%20and%20SSRS\).md)   
 [RSReportDesigner Configuration File](../../Topics\TopicNameNotContainA/RSReportDesigner-Configuration-File.md)  
  
  