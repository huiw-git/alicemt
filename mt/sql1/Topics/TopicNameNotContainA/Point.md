---
title: "Point"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-spatial
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a596ec4-8b2f-4962-bcb4-e5c8f77edad5
caps.latest.revision: 20
manager: jhubbard
---
# Point
In [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] spatial data, a **Point** is a 0-dimensional object representing a single location and may contain Z (elevation) and M (measure) values.  
  
## Geography Data Type  
 The Point type for the geography data type represents a single location where *Lat* represents latitude and *Long* represents longitude. The values for latitude and longitude are measured in degrees. Values for latitude always lie in the interval [-90, 90], and values that are inputted outside this range will throw an exception. Values for longitude always lie in the interval (-180, 180], and values inputted outside this range are wrapped around to fit in this range. For example, if 190 is inputted for longitude, then it will be wrapped to the value -170. *SRID* represents the spatial reference ID of the **geography** instance that you wish to return.  
  
## Geometry Data Type  
 The Point type for the geometry data type represents a single location where *X* represents the X-coordinate of the Point being generated and *Y* represents the Y-coordinate of the Point being generated. *SRID* represents the spatial reference ID of the **geometry** instance that you wish to return.  
  
## Examples  
 The following example creates a `geometry Point`instance representing the point (3, 4) with an SRID of 0.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT (3 4)', 0);  
```  
  
 The next example creates a `geometry``Point` instance representing the point (3, 4) with a Z (elevation) value of 7, an M (measure) value of 2.5, and the default SRID of 0.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 7 2.5)');  
```  
  
 The final example returns the X, Y, Z, and M values for the `geometry``Point` instance.  
  
```  
SELECT @g.STX;  
SELECT @g.STY;  
SELECT @g.Z;  
SELECT @g.M;  
```  
  
 Z and M values may be explicitly specified as NULL, as shown in the following example.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 NULL NULL)');  
```  
  
## See Also  
 [MultiPoint](../../Topics/TopicNameNotContainA/MultiPoint.md)   
 [STX](assetId:///2aef77e8-0460-43f9-bad6-2aae6d8c36f9)   
 [STY](assetId:///f72e0eaa-7d1d-4052-88fd-a172d8cb0d71)   
 [Spatial Data (SQL Server)](../../Topics/TopicNameNotContainA/Spatial-Data--SQL-Server-.md)