---
title: Analysis Services
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49d186f4-4b4d-4a5a-bb1a-e2699c64a731
---
# Analysis Services
  [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] is an online analytical data engine used in decision support and business analytics, providing the analytical data for business reports and client applications such as Power BI, Excel, Reporting Services reports, and other data visualization tools.  
  
 A typical workflow for [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] includes authoring a Multidimensional or Tabular data model, deploying the model as a database to an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance, processing the database to load it with data or metadata, setting up data refresh, and assigning permissions to allow data access by end\-users. When it's ready to go, this multi\-purpose semantic data model can be accessed by any client application supporting [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] as a data source.  
  
 Models are populated with data from external data systems, usually data warehouses hosted on a SQL Server or Oracle relational database engine \(Tabular models support additional data source types\). Models specify query objects, such as cubes, but also specify dimensions that can be used in multiple cubes, calculations and KPIs that encapsulate business logic, and interactions such as navigation and drill\-through behaviors.  
  
## Server mode  
 When installing Analysis Services by using [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Setup, during configuration you specify a server mode for that instance.  Each mode includes different features unique to a particular  Analysis Services solution.  
  
-   **Multidimensional and Data Mining Mode** \- Implement OLAP modeling constructs \(cubes, dimensions, measures\).  
  
-   **Tabular Mode** \- Implement in\-memory relational data modeling constructs \(model, tables, columns\).  
  
     Tabular models can be created at the default compatibility level 1200; using the latest functionality, or at the older 1103 compatibility level. There are significant differences between  compatibility levels. See [Compatibility Level for Tabular models in Analysis Services](../../Topics\TopicNameNotContainA/Compatibility-Level-for-Tabular-models-in-Analysis-Services.md)for information on how the levels compare.  
  
-   **Power Pivot Mode** \- Implement [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] and Excel data models in SharePoint \([!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] for SharePoint is a middle\-tier data engine that loads, queries, and refreshes data models hosted in SharePoint\).  
  
 A single instance can be configured with only one mode,  and cannot be changed later.  You can install multiple instances with different modes on the same server, but you'll need to run Setup and specify configuration settings for each instance.  
  
 [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] features vary by edition. For more information, see [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
## Authoring solutions  
 To create a model, you use SQL Server Data Tools \(see [Tools and applications used in Analysis Services](../../Topics\TopicNameNotContainA/Tools-and-applications-used-in-Analysis-Services.md)\), choosing either a Tabular or Multidimensional and Data Mining project template. The project template contains folders for all of the objects needed in a model. Wizards help create many of the basic elements, such as data sources, data source views, dimensions, cubes, and roles.  
  
## Documentation by area  
Documentation for Analysis Services is organized into sections that correspond to the type of project you are building. Choose from the following links to learn more about each mode or feature area.  
   
 ![Small File Folder Icon](../../Images\Image\ImageNotContaina/filefolder_small.png "filefolder_small") [What's New](../../Topics\TopicNameNotContainA/What-s-New-in-Analysis-Services.md)  
  
 ![Small File Folder Icon](../../Images\Image\ImageNotContaina/filefolder_small.png "filefolder_small") [Comparing Tabular and Multidimensional Solutions](../Topic/Comparing%20Tabular%20and%20Multidimensional%20Solutions%20\(SSAS\).md)  
  
 ![Small File Folder Icon](../../Images\Image\ImageNotContaina/filefolder_small.png "filefolder_small") [Tabular Models](../Topic/Tabular%20Models%20\(SSAS\).md)  
  
 ![Small File Folder Icon](../../Images\Image\ImageNotContaina/filefolder_small.png "filefolder_small") [Multidimensional Models](../Topic/Multidimensional%20Models%20\(SSAS\).md)  
  
 ![Small File Folder Icon](../../Images\Image\ImageNotContaina/filefolder_small.png "filefolder_small") [Data Mining](../Topic/Data%20Mining%20\(SSAS\).md)  
  
 ![Small File Folder Icon](../../Images\Image\ImageNotContaina/filefolder_small.png "filefolder_small") [Power Pivot for SharePoint](../Topic/Power%20Pivot%20for%20SharePoint%20\(SSAS\).md)  
  
 ![Small File Folder Icon](../../Images\Image\ImageNotContaina/filefolder_small.png "filefolder_small") [Analysis Services Instance Management](../../Topics\TopicNameNotContainA/Analysis-Services-Instance-Management.md)  
   
 ![Small File Folder Icon](../../Images\Image\ImageNotContaina/filefolder_small.png "filefolder_small") [Analysis Services Tutorials](Analysis%20Services%20Tutorials%20\(SSAS\).md)  
  
![Small File Folder Icon](../../Images\Image\ImageNotContaina/filefolder_small.png "filefolder_small") [Analysis Services Developer Documentation](https://msdn.microsoft.com/library/bb500153(SQL.130).aspx)  
 
![Small File Folder Icon](../../Images\Image\ImageNotContaina/filefolder_small.png "filefolder_small") [Technical Reference (SSAS)](Technical%20Reference%20\(SSAS\).md)