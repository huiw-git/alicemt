---
title: SQL Destination Editor (Connection Manager Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 423e1654-54af-47c6-ab6f-98670534557d
---
# SQL Destination Editor (Connection Manager Page)
  Use the **Connection Manager** page of the **SQL Destination Editor** dialog box to specify data source information, and to preview the results. The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] destination loads data into tables or views in a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database.  
  
 To learn more about the SQL Server destination, see [SQL Server Destination](../../Topics\TopicNameNotContainA/SQL-Server-Destination.md).  
  
## Options  
 **OLE DB connection manager**  
 Select an existing connection from the list, or create a new connection by clicking **New**.  
  
 **New**  
 Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.  
  
 **Use a table or view**  
 Select an existing table or view from the list, or create a new connection by clicking **New**.  
  
 **New**  
 Create a new table by using the **Create Table** dialog box.  
  
> [!NOTE]  
>  When you click **New**, [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] generates a default CREATE TABLE statement based on the connected data source. This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared. To run an [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database. Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box. For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../Topic/Binary%20Large%20Object%20\(Blob\)%20Data%20\(SQL%20Server\).md).  
  
 **Preview**  
 Preview results by using the **Preview Query Results** dialog box. Preview can display up to 200 rows.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [SQL Destination Editor &#40;Mappings Page&#41;](../Topic/SQL%20Destination%20Editor%20\(Mappings%20Page\).md)   
 [SQL Destination Editor &#40;Advanced Page&#41;](../Topic/SQL%20Destination%20Editor%20\(Advanced%20Page\).md)   
 [Bulk Load Data by Using the SQL Server Destination](../../Topics\TopicNameNotContainA/Bulk-Load-Data-by-Using-the-SQL-Server-Destination.md)  
  
  