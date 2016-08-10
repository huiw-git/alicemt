---
title: "Spatial Results Window"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c2d5a477-6496-4d01-adee-7322ebdfadf3
caps.latest.revision: 9
caps.handback.revision: 0
manager: jhubbard
---
# Spatial Results Window
The **Spatial results** window provides visual mapping tools for viewing spatial data. To view spatial results, your query results must include a spatial column with either geometry or geography data.  
  
> [!NOTE]  
>  The **Spatial results** window is only available if your results are returned to a grid in the **Results** window. If you specify that your results are returned as text, this window is not available.  
  
## Options  
 **Select spatial column**  
 Specify the spatial column you want to view from the spatial columns in the query results. Only one column can be selected at a time.  
  
 **Select label column**  
 Specify the non-spatial column from the columns returned in the query results to label the spatial data. Only one column can be selected at a time.  
  
 This option is not available when only point instances are returned in a query.  
  
 **Select projection**  
 Display geography data in one of four projections: Equirectangular, Mercator, Robinson, or Bonne.  
  
 This option is not available for geometry data.  
  
 **Zoom**  
 Adjust the map display on an exponential scale.  
  
 **Show grid lines**  
 Toggle coordinate gridlines on or off.  
  
 For polygon shapes, the label is displayed only when the shape is large enough to hold the label text. To display labels for small shapes, adjust the zoom.  
  
> [!NOTE]  
>  Point instances cannot be labeled.  
  
## See Also  
 [View Spatial Data in Object Explorer](../../Topics/TopicNameNotContainA/View-Spatial-Data-in-Object-Explorer.md)   
 [Spatial Data (SQL Server)](../../Topics/TopicNameNotContainA/Spatial-Data--SQL-Server-.md)   
 [Database Engine Query Editor (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Database-Engine-Query-Editor--SQL-Server-Management-Studio-.md)   
 [Query and Text Editors (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Query-and-Text-Editors--SQL-Server-Management-Studio-.md)