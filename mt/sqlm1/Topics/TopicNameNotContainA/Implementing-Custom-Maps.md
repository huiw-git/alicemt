---
title: Implementing Custom Maps
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 20537597-f211-4284-a7bf-3be957b4bd41
---
# Implementing Custom Maps
## Implementing Custom Maps  
  
Geographic maps in [!INCLUDE[PRODUCT_NAME](../../Token\Other/PRODUCT_NAME.md)] are defined in a format known as *ESRI shapefiles*.  
  
Initially designed by a private company, this is now a widespread semi-open format used in a large portion of GIS applications. In accordance with this format, [!INCLUDE[PRODUCT_NAME](../../Token\Other/SHORT_PRODUCT_NAME.md)] requires two files to be provided when defining a map:  
  
- a .SHP file for shape geometries  
- a .DBF file for meta data  
  
The base files names must match (e.g. *canada.shp* and *canada.dbf*). The metadata must include the field *NAME* with the value of the corresponding shape's name (key), to be used when populating the map with data.  
  
For information on how to make custom maps available for inclusion in mobile reports, see [Managing Custom Maps](Managing%20Custom%20Maps.md).  
  
## Information & Resources  
  
More specific information can be found by visiting some of the following links:  
  
**Technical information**  
  
- The official specification: [http://www.esri.com/library/whitepapers/pdfs/shapefile.pdf](http://www.esri.com/library/whitepapers/pdfs/shapefile.pdf)  
- The Wikipedia shapefile article: [http://en.wikipedia.org/wiki/Shapefile](http://en.wikipedia.org/wiki/Shapefile)  
  
**Creating & editing map geometry**  
  
Creating and editing shapefiles is a complex process that is beyond the scope of this document. Here are some resources and applications to help you get started:  
  
- ArcGIS: [http://www.arcgis.com/](http://www.arcgis.com/)  
- MAPublisher plug-in for Adobe Illustrator: [http://www.avenza.com/mapublisher](http://www.avenza.com/mapublisher)  
- QuantumGIS (free): [http://www.qgis.org/](http://www.qgis.org/)  
- Manco ShapeFile Editor: [http://www.mancosoftware.com/ShapeFileEditor](http://www.mancosoftware.com/ShapeFileEditor)  
  
**Existing shapefiles**  
  
Many existing shapefiles can be downloaded from the Web, from sites like these:  
  
- Diva-GIS: [http://www.diva-gis.org/Data](http://www.diva-gis.org/Data)  
- OpenStreetMap: [http://openstreetmapdata.com/data](http://openstreetmapdata.com/data)  
- GeoCommons: [http://www.geocommons.com/](http://www.geocommons.com/)  
