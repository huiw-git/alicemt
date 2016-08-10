---
title: "XML Input File Reference (Database Engine Tuning Advisor)"
ms.custom: na
ms.date: 08/09/2016
ms.devlang: 
  - XML
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 05e5e5f0-d6df-4336-b18e-e9bc2835a766
caps.latest.revision: 27
manager: jhubbard
---
# XML Input File Reference (Database Engine Tuning Advisor)
[!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] Tuning Advisor can use an XML input file to tune a database. This XML file designates which databases, tables, workload files or tables, and tuning options to use for the tuning session. You can also use this file to specify a user-specified configuration to perform "what-if" analysis.  
  
 A [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] Tuning Advisor XML input file contains a hierarchy of XML elements, each containing text or other elements that specify the tuning session settings. The [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] Tuning Advisor XML input file must conform to the standards for well-formed XML, so all element names are case sensitive. Elements are specified using Pascal case, which means that the first character is uppercase and the first letter of any subsequent concatenated word is uppercase.  
  
 All element values must conform to XML naming conventions. For more information about these conventions, see [XML Textual Content](http://go.microsoft.com/fwlink/?LinkId=7614) in the MSDN Library.  
  
 Note that this reference is not comprehensive. For information about all the elements you can use to define XML input, refer to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] Tuning Advisor XML schema, DTASchema.xsd.  
  
## XML Declaration  
  
-   [XML Data (SQL Server)](../../Topics/TopicNameNotContainA/XML-Data--SQL-Server-.md)  
  
## DTAXML Root Element  
  
-   [DTAXML Element (DTA)](../../Topics/TopicNameNotContainA/DTAXML-Element--DTA-.md)  
  
## DTAInput Elements  
  
-   [DTAInput Element (DTA)](../../Topics/TopicNameNotContainA/DTAInput-Element--DTA-.md)  
  
-   [Server Element (DTA)](../../Topics/TopicNameNotContainA/Server-Element--DTA-.md)  
  
-   [Workload Element (DTA)](../../Topics/TopicNameNotContainA/Workload-Element--DTA-.md)  
  
-   [TuningOptions Element (DTA)](../../Topics/TopicNameNotContainA/TuningOptions-Element--DTA-.md)  
  
-   [Configuration Element (DTA)](../../Topics/TopicNameNotContainA/Configuration-Element--DTA-.md)  
  
## Server Elements  
  
-   [Name Element for Server (DTA)](../../Topics/TopicNameNotContainA/Name-Element-for-Server--DTA-.md)  
  
-   [Database Element for Server (DTA)](../../Topics/TopicNameNotContainA/Database-Element-for-Server--DTA-.md)  
  
## Workload Elements  
  
-   [File Element (DTA)](../../Topics/TopicNameNotContainA/File-Element--DTA-.md)  
  
-   [Database Element for Workload (DTA)](../../Topics/TopicNameNotContainA/Database-Element-for-Workload--DTA-.md)  
  
-   [EventString Element (DTA)](../../Topics/TopicNameNotContainA/EventString-Element--DTA-.md)  
  
## Tuning Options Elements  
  
-   [TuningTimeInMin Element (DTA)](../../Topics/TopicNameNotContainA/TuningTimeInMin-Element--DTA-.md)  
  
-   [StorageBoundInMB Element (DTA)](../../Topics/TopicNameNotContainA/StorageBoundInMB-Element--DTA-.md)  
  
-   [TestServer Element (DTA)](../../Topics/TopicNameNotContainA/TestServer-Element--DTA-.md)  
  
-   [FeatureSet Element (DTA)](../../Topics/TopicNameNotContainA/FeatureSet-Element--DTA-.md)  
  
-   [Partitioning Element (DTA)](../../Topics/TopicNameNotContainA/Partitioning-Element--DTA-.md)  
  
-   [DropOnlyMode Element (DTA)](../../Topics/TopicNameNotContainA/DropOnlyMode-Element--DTA-.md)  
  
-   [KeepExisting Element (DTA)](../../Topics/TopicNameNotContainA/KeepExisting-Element--DTA-.md)  
  
-   [OnlineIndexOperation Element (DTA)](../../Topics/TopicNameNotContainA/OnlineIndexOperation-Element--DTA-.md)  
  
-   [DatabaseToConnect Element (DTA)](../../Topics/TopicNameNotContainA/DatabaseToConnect-Element--DTA-.md)  
  
## Configuration Elements  
  
-   [Server Element for Configuration (DTA)](../../Topics/TopicNameNotContainA/Server-Element-for-Configuration--DTA-.md)  
  
-   [Database Element for Configuration (DTA)](../../Topics/TopicNameNotContainA/Database-Element-for-Configuration--DTA-.md)  
  
-   [Recommendation Element (DTA)](../../Topics/TopicNameNotContainA/Recommendation-Element--DTA-.md)  
  
-   [Create Element (DTA)](../../Topics/TopicNameNotContainA/Create-Element--DTA-.md)  
  
-   [Index Element (DTA)](../../Topics/TopicNameNotContainA/Index-Element--DTA-.md)  
  
-   [Name Element for Index (DTA)](../../Topics/TopicNameNotContainA/Name-Element-for-Index--DTA-.md)  
  
-   [Column Element for Index (DTA)](../../Topics/TopicNameNotContainA/Column-Element-for-Index--DTA-.md)  
  
-   [Name Element for Column (DTA)](../../Topics/TopicNameNotContainA/Name-Element-for-Column--DTA-.md)  
  
-   [Filegroup Element for Index (DTA)](../../Topics/TopicNameNotContainA/Filegroup-Element-for-Index--DTA-.md)  
  
## Database Elements  
  
-   [Name Element for Database (DTA)](../../Topics/TopicNameNotContainA/Name-Element-for-Database--DTA-.md)  
  
-   [Schema Element for Database (DTA)](../../Topics/TopicNameNotContainA/Schema-Element-for-Database--DTA-.md)  
  
-   [Name Element for Schema (DTA)](../../Topics/TopicNameNotContainA/Name-Element-for-Schema--DTA-.md)  
  
-   [Table Element for Schema (DTA)](../../Topics/TopicNameNotContainA/Table-Element-for-Schema--DTA-.md)  
  
-   [Name Element for Table (DTA)](../../Topics/TopicNameNotContainA/Name-Element-for-Table--DTA-.md)  
  
## See Also  
 [Database Engine Tuning Advisor](../../Topics/TopicNameNotContainA/Database-Engine-Tuning-Advisor.md)