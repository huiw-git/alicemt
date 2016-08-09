---
title: "MultiPoint"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-spatial
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2aaab211-3aba-4dbd-90b7-095d997b1f62
caps.latest.revision: 16
manager: jhubbard
---
# MultiPoint
A **MultiPoint** is a collection of zero or more points. The boundary of a **MultiPoint** instance is empty.  
  
## Examples  
 The following example creates a `geometry MultiPoint` instance with SRID 23 and two points: one point with the coordinates (2, 3), one point with the coordinates (7, 8), and a Z value of 9.5.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 This `MultiPoint` instance can also be expressed using `STMPointFromText()` as shown below.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STMPointFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 The following example uses the method `STGeometryN()` to retrieve a description of the first point in the collection.  
  
```  
SELECT @g.STGeometryN(1).STAsText();  
```  
  
## See Also  
 [Point](../../Topics/TopicNameNotContainA/Point.md)   
 [Spatial Data (SQL Server)](../../Topics/TopicNameNotContainA/Spatial-Data--SQL-Server-.md)