---
title: XML Input File Reference (Database Engine Tuning Advisor)
ms.custom: na
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
---
# XML Input File Reference (Database Engine Tuning Advisor)
  [!INCLUDE[ssDE](../../Topics/TopicNameContainA/includes/ssDE_md.md)] Tuning Advisor can use an XML input file to tune a database. This XML file designates which databases, tables, workload files or tables, and tuning options to use for the tuning session. You can also use this file to specify a user-specified configuration to perform "what-if" analysis.  
  
 A [!INCLUDE[ssDE](../../Topics/TopicNameContainA/includes/ssDE_md.md)] Tuning Advisor XML input file contains a hierarchy of XML elements, each containing text or other elements that specify the tuning session settings. The [!INCLUDE[ssDE](../../Topics/TopicNameContainA/includes/ssDE_md.md)] Tuning Advisor XML input file must conform to the standards for well-formed XML, so all element names are case sensitive. Elements are specified using Pascal case, which means that the first character is uppercase and the first letter of any subsequent concatenated word is uppercase.  
  
 All element values must conform to XML naming conventions. For more information about these conventions, see [XML Textual Content](http://go.microsoft.com/fwlink/?LinkId=7614) in the MSDN Library.  
  
 Note that this reference is not comprehensive. For information about all the elements you can use to define XML input, refer to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/includes/ssDE_md.md)] Tuning Advisor XML schema, DTASchema.xsd.  
  
## XML Declaration  
  
-   [XML Data &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/XML-Data--SQL-Server-.md)  
  
## DTAXML Root Element  
  
-   [DTAXML Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/DTAXML-Element--DTA-.md)  
  
## DTAInput Elements  
  
-   [DTAInput Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/DTAInput-Element--DTA-.md)  
  
-   [Server Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Server-Element--DTA-.md)  
  
-   [Workload Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Workload-Element--DTA-.md)  
  
-   [TuningOptions Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/TuningOptions-Element--DTA-.md)  
  
-   [Configuration Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Configuration-Element--DTA-.md)  
  
## Server Elements  
  
-   [Name Element for Server &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Name-Element-for-Server--DTA-.md)  
  
-   [Database Element for Server &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Database-Element-for-Server--DTA-.md)  
  
## Workload Elements  
  
-   [File Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/File-Element--DTA-.md)  
  
-   [Database Element for Workload &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Database-Element-for-Workload--DTA-.md)  
  
-   [EventString Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/EventString-Element--DTA-.md)  
  
## Tuning Options Elements  
  
-   [TuningTimeInMin Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/TuningTimeInMin-Element--DTA-.md)  
  
-   [StorageBoundInMB Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/StorageBoundInMB-Element--DTA-.md)  
  
-   [TestServer Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/TestServer-Element--DTA-.md)  
  
-   [FeatureSet Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/FeatureSet-Element--DTA-.md)  
  
-   [Partitioning Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Partitioning-Element--DTA-.md)  
  
-   [DropOnlyMode Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/DropOnlyMode-Element--DTA-.md)  
  
-   [KeepExisting Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/KeepExisting-Element--DTA-.md)  
  
-   [OnlineIndexOperation Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/OnlineIndexOperation-Element--DTA-.md)  
  
-   [DatabaseToConnect Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/DatabaseToConnect-Element--DTA-.md)  
  
## Configuration Elements  
  
-   [Server Element for Configuration &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Server-Element-for-Configuration--DTA-.md)  
  
-   [Database Element for Configuration &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Database-Element-for-Configuration--DTA-.md)  
  
-   [Recommendation Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Recommendation-Element--DTA-.md)  
  
-   [Create Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Create-Element--DTA-.md)  
  
-   [Index Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Index-Element--DTA-.md)  
  
-   [Name Element for Index &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Name-Element-for-Index--DTA-.md)  
  
-   [Column Element for Index &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Column-Element-for-Index--DTA-.md)  
  
-   [Name Element for Column &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Name-Element-for-Column--DTA-.md)  
  
-   [Filegroup Element for Index &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Filegroup-Element-for-Index--DTA-.md)  
  
## Database Elements  
  
-   [Name Element for Database &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Name-Element-for-Database--DTA-.md)  
  
-   [Schema Element for Database &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Schema-Element-for-Database--DTA-.md)  
  
-   [Name Element for Schema &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Name-Element-for-Schema--DTA-.md)  
  
-   [Table Element for Schema &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Table-Element-for-Schema--DTA-.md)  
  
-   [Name Element for Table &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Name-Element-for-Table--DTA-.md)  
  
## See Also  
 [Database Engine Tuning Advisor](../../Topics/TopicNameNotContainA/Database-Engine-Tuning-Advisor.md)  
  
  