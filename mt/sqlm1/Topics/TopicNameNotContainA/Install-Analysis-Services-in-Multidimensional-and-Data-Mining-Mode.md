---
title: Install Analysis Services in Multidimensional and Data Mining Mode
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8a1f33e8-2bd6-4fb8-bd46-c86f2a067f60
robots: noindex,nofollow
---
# Install Analysis Services in Multidimensional and Data Mining Mode
  [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] provides online analytical processing \(OLAP\) and data mining functionality for business intelligence applications. In this release, support for OLAP databases and data mining models is available when you install [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] in *Multidimensional mode*. Multidimensional mode is one of three server modes that [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] runs in. It is the default mode. If you install [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] using default values, you will get an instance that runs multidimensional databases and data mining models.  
  
 [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] is a multi\-instance feature, which means that you can install more than one instance [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] on a single computer, or run a new instance of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] side\-by\-side an earlier version. Server mode is specific to an instance. Using other modes requires that you install additional instances of the server.  
  
 You can install [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] by itself or with other components. If you install just [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], the following features are installed when you select **Analysis Services** on the Feature Selection page of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Installation Wizard:  
  
-   [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] server for running [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] databases and data mining models  
  
-   Data providers used for [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] data access to source databases  
  
-   SQL Server Configuration Manager  
  
## Choosing additional features  
 Analysis Services OLAP and data warehouse solutions will require the installation of additional [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] components to enable the development, deployment, and administration of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] databases. The following additional features are options for many typical user scenarios:  
  
-   [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], used to create and view Analysis Services data structures and data mining models.  
  
-   Client tools connectivity components, used for communication between clients and servers, including network libraries for DB\-Library, ODBC, and OLE DB.  
  
-   [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)], a set of graphical and programmable objects for moving, copying, and transforming data.  
  
-   Management tools, including [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)], and Replication Monitor.  
  
## Installation Tasks  
 Installation tasks include the following:  
  
|Links|Tasks|  
|-----------|-----------|  
|[Hardware and Software Requirements for Installing SQL Server 2016](../../Topics\TopicNameNotContainA/Hardware-and-Software-Requirements-for-Installing-SQL-Server-2016.md) and [Configure Windows Service Accounts and Permissions](../../Topics\TopicNameNotContainA/Configure-Windows-Service-Accounts-and-Permissions.md).|Before you run Setup, check prerequisites for installing [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] and determine which account you will use to provision the server.|  
|[Install SQL Server 2016 from the Installation Wizard &#40;Setup&#41;](../Topic/Install%20SQL%20Server%202016%20from%20the%20Installation%20Wizard%20\(Setup\).md).|Run SQL Server Setup to install the software.|  
|[Configure the Windows Firewall to Allow Analysis Services Access](../../Topics\TopicNameNotContainA/Configure-the-Windows-Firewall-to-Allow-Analysis-Services-Access.md)|After Setup is finished, you must configure firewall settings to allow remote connections to the server.|  
|[Authorizing access to objects and operations &#40;Analysis Services&#41;](../Topic/Authorizing%20access%20to%20objects%20and%20operations%20\(Analysis%20Services\).md)|Users who access Analysis Services databases must have Read permission on at least one database on the server.|  
  
## Related Content  
 Additional setup content can be found in the following topics:  
  
 [Install Analysis Services](../../Topics\TopicNameNotContainA/Install-Analysis-Services.md)  
  
 [Power Pivot for SharePoint 2010 Installation](assetId:///8d47dde7-c941-4280-a934-e2fe3f9a938f)  
  
 [Determine the Server Mode of an Analysis Services Instance](../../Topics\TopicNameNotContainA/Determine-the-Server-Mode-of-an-Analysis-Services-Instance.md)  
  
 [SQL Server Data Mining Add\-ins](http://go.microsoft.com/fwlink/?LinkId=197091)  
  
 By default, sample databases, sample code, and client application add\-ins are not installed as part of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup. To install sample databases and sample code, see the [CodePlex Web site](http://go.microsoft.com/fwlink/?LinkId=87843).  
  
## See Also  
 [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md)   
 [Languages and Collations &#40;Analysis Services&#41;](../Topic/Languages%20and%20Collations%20\(Analysis%20Services\).md)   
 [Upgrade Analysis Services](../../Topics\TopicNameNotContainA/Upgrade-Analysis-Services.md)  
  
  