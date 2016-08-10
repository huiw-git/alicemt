---
title: "Create, Construct, and Query geometry Instances"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-spatial
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c6b5c852-37d2-48d0-a8ad-e43bb80d6514
caps.latest.revision: 27
caps.handback.revision: 0
manager: jhubbard
---
# Create, Construct, and Query geometry Instances
The planar spatial data type, **geometry**, represents data in a Euclidean (flat) coordinate system. This type is implemented as a common language runtime (CLR) data type in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
 The **geometry** type is predefined and available in each database. You can create table columns of type **geometry** and operate on **geometry** data in the same manner as you would use other CLR types.  
  
 The **geometry** data type (planar) supported by [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] conforms to the Open Geospatial Consortium (OGC) Simple Features for SQL Specification version 1.1.0.  
  
 For more information on OGC specifications, see the following:  
  
-   [OGC Specifications, Simple Feature Access Part 1 - Common Architecture](http://go.microsoft.com/fwlink/?LinkId=93628)  
  
-   [OGC Specifications, Simple Feature Access Part 2 – SQL Options](http://go.microsoft.com/fwlink/?LinkId=93629)  
  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] supports a subset of the existing GML 3.1 standard which is defined in the following schema: [http://schemas.microsoft.com/sqlserver/profiles/gml/SpatialGML.xsd](http://go.microsoft.com/fwlink/?LinkId=230959).  
  
##  <a name="creating"></a> Creating or constructing a new geometry instance  
  
###  <a name="existing"></a> Creating a New geometry Instance from an Existing Instance  
 The **geometry** data type provides numerous built-in methods you can use to create new **geometry** instances based on existing instances.  
  
 **To create a buffer around a geometry**  
 [STBuffer (geometry Data type)](assetId:///ca6bf2dc-1d38-4503-b87e-f2ea033d36ba)  
  
 [BufferWithTolerance (geometry Data Type)](assetId:///7049d37a-3e72-4e93-87a1-c96a6f0e2b99)  
  
 **To create a simplified version of a geometry**  
 [Reduce (geometry Data Type)](assetId:///132184bf-c4d2-4a27-900d-8373445dce2a)  
  
 **To create the convex hull of a geometry**  
 [STConvexHull (geometry Data type)](assetId:///60a520a6-1a7c-486b-8d91-34401edf6233)  
  
 **To create a geometry from the intersection of two geometries**  
 [STIntersection (geometry Data type)](assetId:///354843f5-cc14-478c-974a-04f363f9530f)  
  
 **To create a geometry from the union of two geometries**  
 [STUnion (geometry Data type)](assetId:///5b168118-137d-402f-9173-fee3f365a89c)  
  
 **To create a geometry from the points where one geometry does not overlap another**  
 [STDifference (geometry Data type)](assetId:///737f39bb-8750-4ffb-8594-23febc2f1075)  
  
 **To create a geometry from the points where two geometries do not overlap**  
 [STSymDifference (geometry Data type)](assetId:///1d4cf35a-ca89-4aa4-ae30-e61a0ff18b53)  
  
 **To create an arbitrary Point instance that lies on an existing geometry**  
 [STPointOnSurface (geometry Data type)](assetId:///23b2b8eb-4176-49fb-ace0-92398928d60e)  
  
 [&#91;TOP&#93;](#TOP)  
  
###  <a name="wkt"></a> Constructing a geometry Instance from Well-Known Text Input  
 The **geometry** data type provides several built-in methods that generate a geometry from the Open Geospatial Consortium (OGC) WKT representation. The WKT standard is a text string that allows geometry data to be exchanged in textual form.  
  
 **To construct any type of geometry instance from WKT input**  
 [STGeomFromText (geometry Data Type)](assetId:///20cace39-02e5-46c1-a9a5-841d04d0da16)  
  
 [Parse (geometry Data Type)](assetId:///6e080919-4b64-46cd-8dd2-254a9c232e53)  
  
 **To construct a geometry Point instance from WKT input**  
 [STPointFromText (geometry Data Type)](assetId:///1d71dfd8-9d80-44c3-b6e1-64e99cde1fa0)  
  
 **To construct a geometry MultiPoint instance from WKT input**  
 [STMPointFromText (geometry Data Type)](assetId:///37059074-5ee8-4f55-9414-1e958fd3adaf)  
  
 **To construct a geometry LineString instance from WKT input**  
 [STLineFromText (geometry Data Type)](assetId:///430508ad-207b-4dee-a4d1-4ddf25e6b4a9)  
  
 **To construct a geometry MultiLineString instance from WKT input**  
 [STMLineFromText (geometry Data Type)](assetId:///39fe8559-c4c2-4d61-8508-86eb0a103807)  
  
 **To construct a geometry Polygon instance from WKT input**  
 [STPolyFromText (geometry Data Type)](assetId:///a7c1c9f0-1dd5-493b-b206-83bbfa33452b)  
  
 **To construct a geometry MultiPolygon instance from WKT input**  
 [STMPolyFromText (geometry Data Type)](assetId:///f087a61c-f063-4fb8-8f1c-251a2fed76a1)  
  
 **To construct a geometry GeometryCollection instance from WKT input**  
 [STGeomCollFromText (geometry Data Type)](assetId:///19e757b3-cb2e-4852-87b9-40a815ab707e)  
  
 [&#91;TOP&#93;](#TOP)  
  
###  <a name="wkb"></a> Constructing a geometry Instance from Well-Known Binary Input  
 WKB is a binary format specified by the Open Geospatial Consortium (OGC) that permits **geometry** data to be exchanged between a client application and an SQL database. The following functions accept WKB input to construct geometries:  
  
 **To construct any type of geometry instance from WKB input**  
 [STGeomFromWKB (geometry Data Type)](assetId:///6546ddb0-4a5f-46e5-ba04-8007486c95ec)  
  
 **To construct a geometry Point instance from WKB input**  
 [STPointFromWKB (geometry Data Type)](assetId:///1157c172-2dc7-4393-bae6-b85406171a34)  
  
 **To construct a geometry MultiPoint instance from WKB input**  
 [STMPointFromWKB (geometry Data Type)](assetId:///01d4117f-01a0-4bc3-8762-7382a1cdbd6c)  
  
 **To construct a geometry LineString instance from WKB input**  
 [STLineFromWKB (geometry Data Type)](assetId:///e674c8c4-c67f-4fc1-9873-d9c2ed46c659)  
  
 **To construct a geometry MultiLineString instance from WKB input**  
 [STMLineFromWKB (geometry Data Type)](assetId:///00a8a8e7-11d6-47a0-b971-00e60f7877ce)  
  
 **To construct a geometry Polygon instance from WKB input**  
 [STPolyFromWKB (geometry Data Type)](assetId:///8e8f0c41-0c62-4919-9d4c-d37c93fdd31c)  
  
 **To construct a geometry MultiPolygon instance from WKB input**  
 [STMPolyFromWKB (geometry Data Type)](assetId:///cac25868-08ef-46fc-9c3d-a15e43794a7a)  
  
 **To construct a geometry GeometryCollection instance from WKB input**  
 [STGeomCollFromWKB (geometry Data Type)](assetId:///6c55032c-7f5e-4181-8e67-c0265032db63)  
  
 [&#91;TOP&#93;](#TOP)  
  
###  <a name="gml"></a> Constructing a geometry Instance from GML Text Input  
 The **geometry** data type provides a method that generates a **geometry** instance from GML, an XML representation of geometric objects. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] supports a subset of GML.  
  
 **To construct any type of geometry instance from GML input**  
 [GeomFromGML (geometry Data Type)](assetId:///a3f2c84b-a49f-4ce3-ba25-b903fb0c99b4)  
  
 [&#91;TOP&#93;](#TOP)  
  
##  <a name="returning"></a> Returning Well-Known Text and Well-Known Binary from a geometry Instance  
 You can use the following methods to return either the WKT or WKB format of a **geometry** instance:  
  
 **To return the WKT representation of a geometry instance**  
 [STAsText (geometry Data type)](assetId:///e0decf5e-2858-4c56-b61a-6123f47fb51c)  
  
 [ToString (geometry Data Type)](assetId:///2e55fa98-aa22-4baa-a516-7c233a33e212)  
  
 **To return the WKT representation of a geometry instance including any Z and M values**  
 [AsTextZM (geometry Data Type)](assetId:///08ac8aa0-aff7-4b22-87e0-1a1d55dcbc04)  
  
 **To return the WKB representation of a geometry instance**  
 [STAsBinary (geometry Data type)](assetId:///65353777-e3e6-461c-9504-ea4d83312692)  
  
 **To return a GML representation of a geometry instance**  
 [AsGml (geometry Data type)](assetId:///f6c2e130-05f3-4ef3-921b-d78b51437d48)  
  
 [&#91;TOP&#93;](#TOP)  
  
##  <a name="querying"></a> Querying the Properties and Behaviors of geometry Instances  
 All **geometry** instances have a number of properties that can be retrieved through methods that [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] provides. The following topics define the properties and behaviors of geometry types, and the methods for querying each one.  
  
###  <a name="valid"></a> Validity, Instance Type, and GeometryCollection Information  
 Once a **geometry** instance is constructed, you can use the following methods to determine if it is well-formed, return the instance type, or, if it is a collection instance, return a specific **geometry** instance.  
  
 **To return the instance type of a geometry**  
 [STGeometryType (geometry Data type)](assetId:///224cdc83-aa83-4ad4-bb82-b7481031e910)  
  
 **To determine if a geometry is a given instance type**  
 [InstanceOf (geometry Data Type)](assetId:///fdea1248-29a4-4bab-a60d-a1b359b5e109)  
  
 **To determine if a geometry instance is well-formed for its instance type**  
 [STIsValid (geometry Data type)](assetId:///6da39bea-0f67-4660-98fc-d7214f9b2138)  
  
 **To convert a geometry instance to a well-formed geometry instance with an instance type**  
 [MakeValid (geometry Data Type)](assetId:///38673010-ab77-4ebb-9c4d-b26b79e3b7ea)  
  
 **To return the number of geometries in a geometry collection instance**  
 [STNumGeometries (geometry Data type)](assetId:///9402b03d-3039-42ca-ac59-f96b7f1a48de)  
  
 To return a specific geometry in a geometry collection instance  
 [STGeometryN (geometry Data type)](assetId:///348c7047-3442-4590-8879-fe841e79058c)STGeometryN (geometry Data type)  
  
 [&#91;TOP&#93;](#TOP)  
  
###  <a name="number"></a> Number of Points  
 All nonempty **geometry** instances are comprised of *points*. These points represent the X- and Y-coordinates of the plane on which the geometries are drawn. **geometry** provides numerous built-in methods for querying the points of an instance.  
  
 **To return the number of points that comprise an instance**  
 [STNumPoints](assetId:///a19520fc-7f91-4a2c-856f-4d8b99a7e496)  
  
 **To return a specific point in an instance**  
 [STPointN](assetId:///8f0bb3b7-5cd9-42c2-b9f8-f04628653bd0)  
  
 **To return an arbitrary point that lies on an instance**  
 [STPointOnSurface](assetId:///23b2b8eb-4176-49fb-ace0-92398928d60e)  
  
 **To return the start point of an instance**  
 [STStartPoint](assetId:///049917db-3f76-4053-8cd2-bc54158e89bc)  
  
 **To return the end point of an instance**  
 [STEndpoint](assetId:///61773c45-b568-4e0c-94da-1310c42de7f5)  
  
 **To return the X-coordinate of a Point instance**  
 [STX](assetId:///2aef77e8-0460-43f9-bad6-2aae6d8c36f9)  
  
 **To return the Y-coordinate of a Point instance**  
 [STY](assetId:///f72e0eaa-7d1d-4052-88fd-a172d8cb0d71)  
  
 **To return the geometric center point of a Polygon, CurvePolygon, or MultiPolygon instance**  
 [STCentroid](assetId:///4dc5a004-7a53-4cce-81dd-9f5e1dd0db78)  
  
 [&#91;TOP&#93;](#TOP)  
  
###  <a name="dimension"></a> Dimension  
 A nonempty **geometry** instance can be 0-, 1-, or 2-dimensional. Zero-dimensional **geometries**, such as **Point** and **MultiPoint**, have no length or area. One-dimensional objects, such as **LineString, CircularString, CompoundCurve**, and **MultiLineString**, have length. Two-dimensional instances, such as **Polygon**, **CurvePolygon**, and **MultiPolygon**, have area and length. Empty instances will report a dimension of -1, and a **GeometryCollection** will report an area dependent on the types of its contents.  
  
 **To return the dimension of an instance**  
 [STDimension](assetId:///4fbd27dd-317b-4916-a8ae-4df1b8a6f27c)  
  
 **To return the length of an instance**  
 [STLength](assetId:///e34dc620-2a65-4248-b099-fff91830ab98)  
  
 **To return the area of an instance**  
 [STArea](assetId:///a7dd6083-c649-4ac3-885d-1234e0db62f1)  
  
 [&#91;TOP&#93;](#TOP)  
  
###  <a name="empty"></a> Empty  
 An *empty***geometry** instance does not have any points. The length of empty **LineString, CircularString**, **CompoundCurve**, and **MultiLineString** instances is zero. The area of empty **Polygon**, **CurvePolygon**, and **MultiPolygon** instances is 0.  
  
 **To determine if an instance is empty**  
 [STIsEmpty](assetId:///dcbd6ae1-5d63-485f-9d58-28bfd504524e).  
  
 [&#91;TOP&#93;](#TOP)  
  
###  <a name="simple"></a> Simple  
 For a **geometry** of the instance to be *simple*, it must meet both of these requirements:  
  
-   Each figure of the instance must not intersect itself, except at its endpoints.  
  
-   No two figures of the instance can intersect each other at a point that is not in both of their boundaries.  
  
> [!NOTE]  
>  Empty geometries are always simple.  
  
 **To determine if an instance is simple**  
 [STIsSimple](assetId:///da8f45d4-4f9c-405d-b883-760eb5344a71).  
  
 [&#91;TOP&#93;](#TOP)  
  
###  <a name="boundary"></a> Boundary, Interior, and Exterior  
 The *interior* of a **geometry** instance is the space occupied by the instance, and the *exterior* is the space not occupied it.  
  
 *Boundary* is defined by the OGC as follows:  
  
-   **Point** and **MultiPoint** instances do not have a boundary.  
  
-   **LineString** and **MultiLineString** boundaries are formed by the start points and end points, removing those that occur an even number of times.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 1, 0 0, 1 0, 0 1), (1 1, 1 0))');  
SELECT @g.STBoundary().ToString();  
```  
  
 The boundary of a **Polygon** or **MultiPolygon** instance is the set of its rings.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0), (1 1, 1 2, 2 2, 2 1, 1 1))');  
SELECT @g.STBoundary().ToString();  
```  
  
 **To return the boundary of an instance**  
 [STBoundary](assetId:///f0551674-e6e8-4926-9038-df03f2c807d7)  
  
 [&#91;TOP&#93;](#TOP)  
  
###  <a name="envelope"></a> Envelope  
 The *envelope* of a **geometry** instance, also known as the *bounding box*, is the axis-aligned rectangle formed by the minimum and maximum (X,Y) coordinates of the instance.  
  
 **To return the envelope of an instance**  
 [STEnvelope](assetId:///781d22e9-38df-4c23-836f-6dd0bdef49c5)  
  
 [&#91;TOP&#93;](#TOP)  
  
###  <a name="closure"></a> Closure  
 A *closed***geometry** instance is a figure whose start points and end points are the same. **Polygon** instances are considered closed. **Point** instances are not closed.  
  
 A ring is a simple, closed **LineString** instance.  
  
 **To determine if an instance is closed**  
 [STIsClosed](assetId:///14edbb22-df7b-4b8a-b16c-ac477a5d32c1)  
  
 **To determine if an instance is a ring**  
 [STIsRing](assetId:///ea0063be-1c74-4cc4-ac6f-b65321ddfa54)  
  
 **To return the exterior ring of a Polygon instance**  
 [STExteriorRing](assetId:///b402b36f-05bf-4c6d-8cd6-76c0fff19db2)  
  
 **To return the number of interior rings in a Polygon**  
 [STNumInteriorRing](assetId:///48e78948-5b14-41dd-85d1-169bba1c4195)  
  
 **To return a specified interior ring of a Polygon**  
 [STInteriorRingN](assetId:///47310f9f-2cdb-41e0-a6da-7c3cfbf139ac)  
  
 [&#91;TOP&#93;](#TOP)  
  
###  <a name="srid"></a> Spatial Reference ID (SRID)  
 The spatial reference ID (SRID) is an identifier specifying which coordinate system the **geometry** instance is represented in. Two instances with different SRIDs are incomparable.  
  
 **To set or return the SRID of an instance**  
 [STSrid](assetId:///5e0de983-a0fe-48b7-9e08-30588d7271e2)  
  
 This property can be modified.  
  
 [&#91;TOP&#93;](#TOP)  
  
##  <a name="rel"></a> Determining Relationships between geometry Instances  
 The **geometry** data type provides many built-in methods you can use to determine relationships between two **geometry** instances.  
  
 **To determine if two instances comprise the same point set**  
 [STEquals](assetId:///808f0e25-9e68-4ba7-9329-07ec950698f3)  
  
 **To determine if two instances are disjoint**  
 [STDisjoint](assetId:///90acdb21-e826-4d81-afe8-45a71f33282a)  
  
 **To determine if two instances intersect**  
 [STIntersects](assetId:///7c18f5be-5a29-422e-8ca7-d8a5f38e03f5)  
  
 **To determine if two instances touch**  
 [STTouches](assetId:///af3650b4-26da-4600-9cc2-1be71dd76a14)  
  
 **To determine if two instances overlap**  
 [STOverlaps](assetId:///1813cba1-5780-456a-9489-6b40a79569b3)  
  
 **To determine if two instances cross**  
 [STCrosses](assetId:///3e3fc065-555a-4bee-8b71-e92f3dc62a4f)  
  
 **To determine if one instance is within another**  
 [STWithin](assetId:///f845d28c-8029-4e2b-bcf0-71c52a592501)  
  
 **To determine if one instance contains another**  
 [STContains](assetId:///865ceca1-9200-45ed-a7d8-e286e2679fdc)  
  
 **To determine if one instance overlaps another**  
 [STOverlaps](assetId:///1813cba1-5780-456a-9489-6b40a79569b3)  
  
 **To determine if two instances are spatially related**  
 [STRelate](assetId:///9dcb5f58-35ab-4bb3-86ee-2d29eefba6d3)  
  
 **To determine the shortest distance between points in two geometries**  
 [STDistance](assetId:///ac815bc7-5342-4cc4-af40-c80a1c4c8b68)  
  
 [&#91;TOP&#93;](#TOP)  
  
##  <a name="defaultsrid"></a> geometry Instances Default to Zero SRID  
 The default SRID for **geometry** instances in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is 0. With **geometry** spatial data, the specific SRID of the spatial instance is not required to perform calculations; thus, instances can reside in undefined planar space. To indicate undefined planar space in the calculations of **geometry** data type methods, the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] uses SRID 0.  
  
##  <a name="examples"></a> Examples  
 The following two examples show how to add and query geometry data.  
  
-   The first example creates a table with an identity column and a `geometry` column `GeomCol1`. A third column renders the `geometry` column into its Open Geospatial Consortium (OGC) Well-Known Text (WKT) representation, and uses the `STAsText()` method. Two rows are then inserted: one row contains a `LineString` instance of `geometry`, and one row contains a `Polygon` instance.  
  
    ```  
    IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
        DROP TABLE dbo.SpatialTable;  
    GO  
  
    CREATE TABLE SpatialTable   
        ( id int IDENTITY (1,1),  
        GeomCol1 geometry,   
        GeomCol2 AS GeomCol1.STAsText() );  
    GO  
  
    INSERT INTO SpatialTable (GeomCol1)  
    VALUES (geometry::STGeomFromText('LINESTRING (100 100, 20 180, 180 180)', 0));  
  
    INSERT INTO SpatialTable (GeomCol1)  
    VALUES (geometry::STGeomFromText('POLYGON ((0 0, 150 0, 150 150, 0 150, 0 0))', 0));  
    GO  
    ```  
  
-   The second example uses the `STIntersection()` method to return the points where the two previously inserted `geometry` instances intersect.  
  
    ```  
    DECLARE @geom1 geometry;  
    DECLARE @geom2 geometry;  
    DECLARE @result geometry;  
  
    SELECT @geom1 = GeomCol1 FROM SpatialTable WHERE id = 1;  
    SELECT @geom2 = GeomCol1 FROM SpatialTable WHERE id = 2;  
    SELECT @result = @geom1.STIntersection(@geom2);  
    SELECT @result.STAsText();  
    ```  
  
 [&#91;TOP&#93;](#TOP)  
  
## See Also  
 [Spatial Data (SQL Server)](../../Topics/TopicNameNotContainA/Spatial-Data--SQL-Server-.md)