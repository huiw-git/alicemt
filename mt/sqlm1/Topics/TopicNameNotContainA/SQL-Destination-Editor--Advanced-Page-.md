---
title: SQL Destination Editor (Advanced Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b46bcf8-ddaf-4d7d-90a6-80bc19517e9b
---
# SQL Destination Editor (Advanced Page)
  Use the **Advanced** page of the **SQL Destination Editor** dialog box to specify advanced bulk insert options.  
  
 To learn more about the SQL Server destination, see [SQL Server Destination](../../Topics\TopicNameNotContainA/SQL-Server-Destination.md).  
  
## Options  
 **Keep identity**  
 Specify whether the task should insert values into identity columns. The default value of this property is **False**.  
  
 **Keep nulls**  
 Specify whether the task should keep null values. The default value of this property is **False**.  
  
 **Table lock**  
 Specify whether the table is locked when the data is loaded. The default value of this property is **True**.  
  
 **Check constraints**  
 Specify whether the task should check constraints. The default value of this property is **True**.  
  
 **Fire triggers**  
 Specify whether the bulk insert should fire triggers on tables. The default value of this property is **False**.  
  
 **First Row**  
 Specify the first row to insert. The default value of this property is **\-1**, indicating that no value has been assigned.  
  
> [!NOTE]  
>  Clear the text box in the **SQL Destination Editor** to indicate that you do not want to assign a value for this property. Use \-1 in the **Properties** window, the **Advanced Editor**, and the object model.  
  
 **Last Row**  
 Specify the last row to insert. The default value of this property is **\-1**, indicating that no value has been assigned.  
  
> [!NOTE]  
>  Clear the text box in the **SQL Destination Editor** to indicate that you do not want to assign a value for this property. Use \-1 in the **Properties** window, the **Advanced Editor**, and the object model.  
  
 **Maximum number of errors**  
 Specify the number of errors that can occur before the bulk insert stops. The default value of this property is **–1**, indicating that no value has been assigned.  
  
> [!NOTE]  
>  Clear the text box in the **SQL Destination Editor** to indicate that you do not want to assign a value for this property. Use \-1 in the **Properties** window, the **Advanced Editor**, and the object model.  
  
 **Timeout**  
 Specify the number of seconds to wait before the bulk insert stops because of a time\-out.  
  
 **Order columns**  
 Type the names of the sort columns. Each column can be sorted in ascending or descending order. If you use multiple sort columns, delimit the list with commas.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [SQL Destination Editor &#40;Connection Manager Page&#41;](../Topic/SQL%20Destination%20Editor%20\(Connection%20Manager%20Page\).md)   
 [SQL Destination Editor &#40;Mappings Page&#41;](../Topic/SQL%20Destination%20Editor%20\(Mappings%20Page\).md)   
 [Bulk Load Data by Using the SQL Server Destination](../../Topics\TopicNameNotContainA/Bulk-Load-Data-by-Using-the-SQL-Server-Destination.md)  
  
  