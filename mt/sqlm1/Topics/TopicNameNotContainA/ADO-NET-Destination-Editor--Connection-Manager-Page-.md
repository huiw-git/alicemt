---
title: ADO NET Destination Editor (Connection Manager Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a3b11286-32c8-40e1-8ae7-090e2590345a
---
# ADO NET Destination Editor (Connection Manager Page)
  Use the **Connection Manager** page of the **ADO NET Destination Editor** dialog box to select the [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] connection for the destination. This page also lets you select a table or view from the database.  
  
 To learn more about the ADO NET destination, see [ADO NET Destination](../../Topics\TopicNameNotContainA/ADO-NET-Destination.md).  
  
 **To open the Connection Manager page**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package that has the ADO NET destination.  
  
2.  On the **Data Flow** tab, double\-click the ADO NET destination.  
  
3.  In the **ADO NET Destination Editor**, click **Connection Manager**.  
  
## Static Options  
 **Connection manager**  
 Select an existing connection manager from the list, or create a new connection by clicking **New**.  
  
 **New**  
 Create a new connection manager by using the **Configure ADO.NET Connection Manager** dialog box.  
  
 **Use a table or view**  
 Select an existing table or view from the list, or create a new table by clicking **New**..  
  
 **New**  
 Create a new table or view by using the **Create Table** dialog box.  
  
> [!NOTE]  
>  When you click **New**, [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] generates a default CREATE TABLE statement based on the connected data source. This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared. To run an [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database. Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box. For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../Topic/Binary%20Large%20Object%20\(Blob\)%20Data%20\(SQL%20Server\).md).  
  
 **Preview**  
 Preview results by using the **Preview Query Results** dialog box. Preview can display up to 200 rows.  
  
 **Use bulk insert when available**  
 Specify whether to use the [System.Data.SqlClient.SqlBulkCopy](assetId:///T:System.Data.SqlClient.SqlBulkCopy) interface to improve the performance of bulk insert operations.  
  
 Only ADO.NET providers that return a [System.Data.SqlClient.SqlConnection](assetId:///T:System.Data.SqlClient.SqlConnection) object support the use of the [SqlBulkCopy](assetId:///T:System.Data.SqlClient.SqlBulkCopy) interface. The .NET Data Provider for SQL Server \(SqlClient\) returns a [SqlConnection](assetId:///T:System.Data.SqlClient.SqlConnection) object, and a custom provider may return a [SqlConnection](assetId:///T:System.Data.SqlClient.SqlConnection) object.  
  
 You can use the .NET Data Provider for SQL Server \(SqlClient\) to connect to [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssSDSFull](../../Token\Other/ssSDSfull_md.md)].  
  
 If you select **Use bulk insert when available**, and set the **Error** option to **Redirect the row**, the batch of data that the destination redirects to the error output may include good rows.For more information about handling errors in bulk operations, see [Error Handling in Data](../../Topics\TopicNameNotContainA/Error-Handling-in-Data.md). For more information about the **Error** option, see [ADO NET Destination Editor &#40;Error Output Page&#41;](../Topic/ADO%20NET%20Destination%20Editor%20\(Error%20Output%20Page\).md).  
  
> [!NOTE]  
>  If a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or Sybase source table includes an identity column, you must use Execute SQL tasks to run a SET IDENTITY\_INSERT statement before and after the ADO NET destination. The identity column property specifies an incremental value for the column. The SET IDENTITY\_INSERT statement enables explicit values to be inserted into the identity column. To run the CREATE TABLE and SET IDENTITY statements on the same database connection, set the **RetainSameConnection** property of the [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] connection manager to **True**. Also, use the same [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] connection manager for the Execute SQL tasks and the ADO NET destination.  
>   
>  For more information, see [SET IDENTITY_INSERT &#40;Transact-SQL&#41;](../Topic/SET%20IDENTITY_INSERT%20\(Transact-SQL\).md) and [IDENTITY &#40;Property&#41; &#40;Transact-SQL&#41;](../Topic/IDENTITY%20\(Property\)%20\(Transact-SQL\).md).  
  
## External Resources  
 Technical article, [Loading data to Windows Azure SQL Database the fast way](http://go.microsoft.com/fwlink/?LinkId=244333), on sqlcat.com  
  
## See Also  
 [ADO NET Destination Editor &#40;Mappings Page&#41;](../Topic/ADO%20NET%20Destination%20Editor%20\(Mappings%20Page\).md)   
 [ADO NET Destination Editor &#40;Error Output Page&#41;](../Topic/ADO%20NET%20Destination%20Editor%20\(Error%20Output%20Page\).md)   
 [ADO.NET Connection Manager](../../Topics\TopicNameNotContainA/ADO.NET-Connection-Manager.md)   
 [Execute SQL Task](../../Topics\TopicNameNotContainA/Execute-SQL-Task.md)  
  
  