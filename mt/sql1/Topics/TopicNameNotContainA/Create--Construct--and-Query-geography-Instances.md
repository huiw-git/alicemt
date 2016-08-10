---
title: "Create, Construct, and Query geography Instances"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-spatial
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b585851e-d15b-411f-adeb-aeabeb777c0b
caps.latest.revision: 15
caps.handback.revision: 0
manager: jhubbard
---
# Create, Construct, and Query geography Instances
The geography spatial data type, **geography**, represents data in a round-earth coordinate system. This type is implemented as a .NET common language runtime (CLR) data type in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] **geography** data type stores ellipsoidal (round-earth) data, such as GPS latitude and longitude coordinates.  
  
 The **geography** type is predefined and available in each database. You can create table columns of type **geography** and operate on **geography** data in the same manner as you would use other system-supplied types.  
  
##  <a name="creating"></a> Creating or constructing a new geography instance  
  
###  <a name="existing"></a> Creating a New geography Instance from an Existing Instance  
 The **geography** data type provides numerous built-in methods you can use to create new **geography** instances based on existing instances.  
  
 **To create a buffer around a geography**  
 [STBuffer (geography Data Type)](assetId:///cb4deab8-642b-44d9-b3d9-85114d64021e)  
  
 **To create a buffer around a geography, allowing for a tolerance**  
 [STBufferWithTolerance (geography Data Type)](assetId:///f1783e6b-0f17-464f-b1c7-1c3f7d8aa042)  
  
 **To create a geography from the intersection of two geography instances**  
 [STIntersection (geography Data Type)](assetId:///7e09468f-499f-4a38-ba4b-bb30b8821e3b)  
  
 **To create a geography from the union of two geography instances**  
 [STUnion (geography Data Type)](assetId:///9bf87691-efd8-4c53-bd2f-eefe0acd19ca)  
  
 **To create a geography from the points where one geography does not overlap another**  
 [STDifference (geography Data Type)](assetId:///1cde5054-b91a-41bb-812a-08c9308738af)  
  
###  <a name="wkt"></a> Constructing a geography Instance from Well-Known Text Input  
 The **geography** data type provides several built-in methods that generate a geography from the Open Geospatial Consortium (OGC) WKT representation. The WKT standard is a text string that allows geography data to be exchanged in textual form.  
  
 **To construct any type of geography instance from WKT input**  
 [STGeomFromText (geography Data Type)](assetId:///3717987b-77d8-4ccf-a1db-5a8016ac1083)  
  
 [Parse (geography Data Type)](assetId:///21c402fa-fd0f-4d09-a097-49cee0316d4e)  
  
 **To construct a geography Point instance from WKT input**  
 [STPointFromText (geography Data Type)](assetId:///e5fe54dc-0007-4631-8dde-7ae4d4c41f6e)  
  
 **To construct a geography MultiPoint instance from WKT input**  
 [STMPointFromText (geography Data Type)](assetId:///fe91a9f5-8de6-464e-88db-00650eae79b0)  
  
 **To construct a geography LineString instance from WKT input**  
 STLineFromText (geography Data Type)  
  
 **To construct a geography MultiLineString instance from WKT input**  
 [STMLineFromText (geography Data Type)](assetId:///66dfd722-a9bd-45d3-9788-f1946dd23e17)  
  
 **To construct a geography Polygon instance from WKT input**  
 [STPolyFromText (geography Data Type)](assetId:///d7e6a2bb-d301-49fb-9202-c70a9d169b4d)  
  
 **To construct a geography MultiPolygon instance from WKT input**  
 [STMPolyFromText (geography Data Type)](assetId:///15356c0f-5144-418d-aa96-3e7ea5fecea3)  
  
 **To construct a geography GeometryCollection instance from WKT input**  
 [STGeomCollFromText (geography Data Type)](assetId:///a5b3c344-1045-43a4-82fa-47f6206a288e)  
  
###  <a name="wkb"></a> Constructing a geography Instance from Well-Known Binary Input  
 WKB is a binary format specified by the OGC that permits **Geography** data to be exchanged between a client application and an SQL database. The following functions accept WKB input to construct geography instances:  
  
 **To construct any type of geography instance from WKB input**  
 [STGeomFromWKB (geography Data Type)](assetId:///79d39d88-5440-49a7-9247-190eafce3f4f)  
  
 **To construct a geography Point instance from WKB input**  
 [STPointFromWKB (geography Data Type)](assetId:///b3b4e3bb-47bc-4621-99c4-c97aa60cdf8b)  
  
 **To construct a geography MultiPoint instance from WKB input**  
 [STMPointFromWKB (geography Data Type)](assetId:///eeb7d806-3cbb-405d-8199-8b82282c53df)  
  
 **To construct a geography LineString instance from WKB input**  
 [STLineFromWKB (geography Data Type)](assetId:///8ac2b772-6673-4ba1-a7ab-3b4b5841560b)  
  
 **To construct a geography MultiLineString instance from WKB input**  
 [STMLineFromWKB (geography Data Type)](assetId:///05ca6d65-4799-4b9a-9672-cfebae95f23e)  
  
 **To construct a geography Polygon instance from WKB input**  
 [STPolyFromWKB (geography Data Type)](assetId:///d236e0ea-dabe-4341-a6eb-ecc210d1f056)  
  
 **To construct a geography MultiPolygon instance from WKB input**  
 [STMPolyFromWKB (geography Data Type)](assetId:///c4d0e649-0abb-4343-a3f0-3a702c8bbbdb)  
  
 **To construct a geography GeometryCollection instance from WKB input**  
 [STGeomCollFromWKB (geography Data Type)](assetId:///bbed028c-9cd6-4236-b5e5-8e914a21f2e4)STGeomCollFromWKB (geography Data Type)  
  
###  <a name="gml"></a> Constructing a geography Instance from GML Text Input  
 The **geography** data type provides a method that generates a **geography** instance from GML, an XML representation of a **geography** instance. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] supports a subset of GML.  
  
 For more information on Geography Markup Language, see the OGC Specification: [OGC Specifications, Geography Markup Language.](http://go.microsoft.com/fwlink/?LinkId=93629)  
  
 **To construct any type of geography instance from GML input**  
 [GeomFromGML (geography Data Type)](assetId:///470d0997-3cb0-4d34-9a45-b332fe432b14)  
  
##  <a name="returning"></a> Returning Well-Known Text and Well-Known Binary from a geography Instance  
 You can use the following methods to return either the WKT or WKB format of a **geography** instance:  
  
 **To return the WKT representation of a geography instance**  
 [STAsText (geography Data Type)](assetId:///d3d2635d-ca6c-4205-9d6c-eb939ee314fd)  
  
 [ToString (geography Data Type)](assetId:///045c12fa-8fc6-441a-9500-7021cb4ff13e)  
  
 **To return the WKT representation of a geography instance including any Z and M values**  
 [AsTextZM (geography Data Type)](assetId:///e9dc27f6-e945-4457-8498-7644db34008e)  
  
 **To return the WKB representation of a geography instance**  
 [STAsBinary (geography Data Type)](assetId:///99602a62-265d-4aa4-a8dc-92992ca55ba4)  
  
 **To return a GML representation of a geography instance**  
 [AsGml (geography Data Type)](assetId:///67795c64-d8d3-48dc-93ef-3c8a9274deb6)  
  
##  <a name="query"></a> Querying the Properties and Behaviors of geography Instances  
 All **geography** instances have a number of properties that can be retrieved through methods that [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] provides. The following topics define the properties and behaviors of geography types, and the methods for querying each one.  
  
###  <a name="valid"></a> Validity, Instance Type, and GeometryCollection Information  
 After a **geography** instance is constructed, you can use the following methods to return the instance type, or if it is a **GeometryCollection** instance, return a specific **geography** instance.  
  
 **To return the instance type of a geography**  
 [STGeometryType (geography Data Type)](assetId:///3e169ead-a98e-44af-8d33-fd59a955cae4)  
  
 **To determine if a geography is a given instance type**  
 [InstanceOf (geography Data Type)](assetId:///1eaed0e4-1c72-45a9-9926-5b513335cf33)  
  
 **To determine if a geography instance is well-formed for its instance type**  
 [STNumGeometries (geography Data Type)](assetId:///6ae7fac2-62f1-420f-9fc9-a09606be9605)  
  
 **To return a specific geography in a GeometryCollection instance**  
 [STGeometryN (geography Data Type)](assetId:///53755f69-cd50-475b-b3b8-a1a9157cf03a)STGeometryN (geography Data Type)  
  
###  <a name="number"></a> Number of Points  
 All nonempty **geography** instances are comprised of *points*. These points represent the latitude and longitude coordinates of the earth on which the **geography** instances are drawn. The data type **geography** provides numerous built-in methods for querying the points of an instance.  
  
 **To return the number of points that comprise an instance**  
 [STNumPoints (geography Data Type)](assetId:///25ff7ad1-ba5f-4cfb-816a-59255ac1591d)  
  
 **To return a specific point in an instance**  
 [STPointN (geography Data Type)](assetId:///8f0bb3b7-5cd9-42c2-b9f8-f04628653bd0)  
  
 **To return the start point of an instance**  
 [STStartPoint (geography Data Type)](assetId:///7df18a5f-b9ee-4e36-b765-a0790c1dee3d)  
  
 **To return the end point of an instance**  
 [STEndpoint (geography Data Type)](assetId:///8974cd07-8ec4-4126-8fc2-fdcf322ccedd)  
  
###  <a name="dimension"></a> Dimension  
 A nonempty **geography** instance can be 0-, 1-, or 2-dimensional. Zero-dimensional **geography** instances, such as **Point** and **MultiPoint**, have no length or area. One-dimensional objects, such as **LineString, CircularString**, **CompoundCurve**, and **MultiLineString**, have length. Two-dimensional instances, such as **Polygon, CurvePolygon**, and **MultiPolygon**, have area and length. Empty instances report a dimension of -1, and a **GeometryCollection** reports the maximum dimension of its contents.  
  
 **To return the dimension of an instance**  
 [STDimension (geography Data Type)](assetId:///4368b0f6-0678-4ade-87dc-b43d8b2e8d92)  
  
 **To return the length of an instance**  
 [STLength (geography Data Type)](assetId:///774560ab-4a4a-4058-b043-1e67cf6fb9eb)  
  
 **To return the area of an instance**  
 [STArea (geography Data Type)](assetId:///cfc0b0e0-7fde-431a-863f-d13f3b1b1bef)  
  
###  <a name="empty"></a> Empty  
 An *empty***geography** instance does not have any points. The length of empty **LineString, CircularString**, **CompoundCurve**, and **MultiLineString** instances is 0. The area of empty **Polygon, CurvePolygon** and **MultiPolygon** instances is 0.  
  
 **To determine if an instance is empty**  
 [STIsEmpty (geography Data Type)](assetId:///4cbc66e3-9035-4ecf-8f5a-6301f168c26c)  
  
###  <a name="closure"></a> Closure  
 A *closed***geography** instance is a figure whose start points and end points are the same. **Polygon** instances are considered closed. **Point** instances are not closed.  
  
 A ring is a simple, closed **LineString** instance.  
  
 **To determine if an instance is closed**  
 [STIsClosed (geography Data Type)](assetId:///eba1643f-07c4-4500-8643-b7e90f908147)  
  
 **To return the number of rings in a Polygon instance**  
 [NumRings (geography Data Type)](assetId:///0e4e4fa2-b608-4cc4-98ba-0845ddb4214c)  
  
 **To return a specified ring of a geography instance**  
 [RingN (geography Data Type)](assetId:///30f47275-2727-4d22-bbec-c0c54bcb3ac2)  
  
###  <a name="srid"></a> Spatial Reference ID (SRID)  
 The spatial reference ID (SRID) is an identifier specifying which ellipsoidal coordinate system the **geography** instance is represented in. Two **geography** instances with different SRIDs cannot be compared.  
  
 **To set or return the SRID of an instance**  
 [STSrid (geography Data Type)](assetId:///6b04f5a7-2e69-4d34-901e-b61ba6ca9c14)  
  
 This property can be modified.  
  
##  <a name="rel"></a> Determining Relationships between geography Instances  
 The **geography** data type provides many built-in methods you can use to determine relationships between two **geography** instances.  
  
 **To determine if two instances comprise the same point set**  
 [STEquals (geography Data Type)](assetId:///808f0e25-9e68-4ba7-9329-07ec950698f3)  
  
 **To determine if two instances are disjoint**  
 [STDisjoint (geography Data Type)](assetId:///90acdb21-e826-4d81-afe8-45a71f33282a)  
  
 **To determine if two instances intersect**  
 [STIntersects (geography Data Type)](assetId:///7c18f5be-5a29-422e-8ca7-d8a5f38e03f5)  
  
 **To determine the point or points where two instances intersect**  
 [STIntersection (geography Data Type)](assetId:///7e09468f-499f-4a38-ba4b-bb30b8821e3b)  
  
 **To determine the shortest distance between points in two geography instances**  
 [STDistance (geography Data Type)](assetId:///ac815bc7-5342-4cc4-af40-c80a1c4c8b68)  
  
 **To determine the difference in points between two geography instances**  
 [STDifference (geography Data Type)](assetId:///1cde5054-b91a-41bb-812a-08c9308738af)  
  
 **To derive the symmetric difference, or unique points, of one geography instance compared with another instance**  
 [STSymDifference (geography Data Type)](assetId:///82bbfa2c-a61b-4f41-9bf8-6f720f363bae)  
  
##  <a name="supportedsrid"></a> geography Instances Must Use Supported SRID  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] supports SRIDs based on the EPSG standards. A [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]-supported SRID for **geography** instances must be used when performing calculations or using methods with geography spatial data. The SRID must match one of the SRIDs displayed in the **sys.spatial_reference_systems** catalog view. As mentioned previously, when you perform calculations on your spatial data using the **geography** data type, your results will depend on which ellipsoid was used in the creation of your data, as each ellipsoid is assigned a specific spatial reference identifier (SRID).  
  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] uses the default SRID of 4326, which maps to the WGS 84 spatial reference system, when using methods on **geography** instances. If you use data from a spatial reference system other than WGS 84 (or SRID 4326), you will need to determine the specific SRID for your geography spatial data.  
  
##  <a name="examples"></a> Examples  
 The following examples show how to add and query geography data.  
  
-   The first example creates a table with an identity column and a `geography` column `GeogCol1`. A third column renders the `geography` column into its Open Geospatial Consortium (OGC) Well-Known Text (WKT) representation, and uses the `STAsText()` method. Two rows are then inserted: one row contains a `LineString` instance of `geography`, and one row contains a `Polygon` instance.  
  
    ```  
    IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
        DROP TABLE dbo.SpatialTable;  
    GO  
  
    CREATE TABLE SpatialTable   
        ( id int IDENTITY (1,1),  
        GeogCol1 geography,   
        GeogCol2 AS GeogCol1.STAsText() );  
    GO  
  
    INSERT INTO SpatialTable (GeogCol1)  
    VALUES (geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326));  
  
    INSERT INTO SpatialTable (GeogCol1)  
    VALUES (geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326));  
    GO  
    ```  
  
-   The second example uses the `STIntersection()` method to return the points where the two previously inserted `geography` instances intersect.  
  
    ```  
    DECLARE @geog1 geography;  
    DECLARE @geog2 geography;  
    DECLARE @result geography;  
  
    SELECT @geog1 = GeogCol1 FROM SpatialTable WHERE id = 1;  
    SELECT @geog2 = GeogCol1 FROM SpatialTable WHERE id = 2;  
    SELECT @result = @geog1.STIntersection(@geog2);  
    SELECT @result.STAsText();  
    ```  
  
## See Also  
 [Spatial Data (SQL Server)](../../Topics/TopicNameNotContainA/Spatial-Data--SQL-Server-.md)