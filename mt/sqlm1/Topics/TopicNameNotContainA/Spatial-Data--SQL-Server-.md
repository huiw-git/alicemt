---
title: Spatial Data (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-spatial
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 41a132a1-09e2-4426-b9df-225270cb8e15
---
# Spatial Data (SQL Server)
  Spatial data represents information about the physical location and shape of geometric objects. These objects can be point locations or more complex objects such as countries, roads, or lakes.  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] supports two spatial data types: the **geometry** data type and the **geography** data type.  
  
-   The **geometry** type represents data in a Euclidean \(flat\) coordinate system.  
  
-   The **geography** type represents data in a round\-earth coordinate system.  
  
 Both data types are implemented as .NET common language runtime \(CLR\) data types in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
> [!IMPORTANT]  
>  For a detailed description and examples of spatial features introduced in [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], download the white paper, [New Spatial Features in SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=226407).  
  
##  <a name="reltasks"></a> Related Tasks  
 [Create, Construct, and Query geometry Instances](../../Topics\TopicNameNotContainA/Create,-Construct,-and-Query-geometry-Instances.md)  
 Describes the methods that you can use with instances of the geometry data type.  
  
 [Create, Construct, and Query geography Instances](../../Topics\TopicNameNotContainA/Create,-Construct,-and-Query-geography-Instances.md)  
 Describes the methods that you can use with instances of the geography data type.  
  
 [Query Spatial Data for Nearest Neighbor](../../Topics\TopicNameNotContainA/Query-Spatial-Data-for-Nearest-Neighbor.md)  
 Describes the common query pattern that is used to find the closest spatial objects to a specific spatial object.  
  
 [Create, Modify, and Drop Spatial Indexes](../../Topics\TopicNameNotContainA/Create,-Modify,-and-Drop-Spatial-Indexes.md)  
 Provides information about creating, altering, and dropping a spatial index.  
  
## Related Content  
 [Spatial Data Types Overview](../../Topics\TopicNameNotContainA/Spatial-Data-Types-Overview.md)  
 Introduces the spatial data types.  
  
-   [Point](../../Topics\TopicNameNotContainA/Point.md)  
  
-   [LineString](../../Topics\TopicNameNotContainA/LineString.md)  
  
-   [CircularString](../../Topics\TopicNameNotContainA/CircularString.md)  
  
-   [CompoundCurve](../../Topics\TopicNameNotContainA/CompoundCurve.md)  
  
-   [Polygon](../../Topics\TopicNameNotContainA/Polygon.md)  
  
-   [CurvePolygon](../../Topics\TopicNameNotContainA/CurvePolygon.md)  
  
-   [MultiPoint](../../Topics\TopicNameNotContainA/MultiPoint.md)  
  
-   [MultiLineString](../../Topics\TopicNameNotContainA/MultiLineString.md)  
  
-   [MultiPolygon](../../Topics\TopicNameNotContainA/MultiPolygon.md)  
  
-   [GeometryCollection](../../Topics\TopicNameNotContainA/GeometryCollection.md)  
  
 [Spatial Indexes Overview](../../Topics\TopicNameNotContainA/Spatial-Indexes-Overview.md)  
 Introduces spatial indexes and describes tessellation and tessellation schemes.  
  
  