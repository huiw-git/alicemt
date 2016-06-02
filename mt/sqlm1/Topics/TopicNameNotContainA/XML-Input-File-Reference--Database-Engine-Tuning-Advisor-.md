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
  [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Tuning Advisor can use an XML input file to tune a database. This XML file designates which databases, tables, workload files or tables, and tuning options to use for the tuning session. You can also use this file to specify a user\-specified configuration to perform "what\-if" analysis.  
  
 A [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Tuning Advisor XML input file contains a hierarchy of XML elements, each containing text or other elements that specify the tuning session settings. The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Tuning Advisor XML input file must conform to the standards for well\-formed XML, so all element names are case sensitive. Elements are specified using Pascal case, which means that the first character is uppercase and the first letter of any subsequent concatenated word is uppercase.  
  
 All element values must conform to XML naming conventions. For more information about these conventions, see [XML Textual Content](http://go.microsoft.com/fwlink/?LinkId=7614) in the MSDN Library.  
  
 Note that this reference is not comprehensive. For information about all the elements you can use to define XML input, refer to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Tuning Advisor XML schema, DTASchema.xsd.  
  
## XML Declaration  
  
-   [XML Data &#40;SQL Server&#41;](../Topic/XML%20Data%20\(SQL%20Server\).md)  
  
## DTAXML Root Element  
  
-   [DTAXML Element &#40;DTA&#41;](../Topic/DTAXML%20Element%20\(DTA\).md)  
  
## DTAInput Elements  
  
-   [DTAInput Element &#40;DTA&#41;](../Topic/DTAInput%20Element%20\(DTA\).md)  
  
-   [Server Element &#40;DTA&#41;](../Topic/Server%20Element%20\(DTA\).md)  
  
-   [Workload Element &#40;DTA&#41;](../Topic/Workload%20Element%20\(DTA\).md)  
  
-   [TuningOptions Element &#40;DTA&#41;](../Topic/TuningOptions%20Element%20\(DTA\).md)  
  
-   [Configuration Element &#40;DTA&#41;](../Topic/Configuration%20Element%20\(DTA\).md)  
  
## Server Elements  
  
-   [Name Element for Server &#40;DTA&#41;](../Topic/Name%20Element%20for%20Server%20\(DTA\).md)  
  
-   [Database Element for Server &#40;DTA&#41;](../Topic/Database%20Element%20for%20Server%20\(DTA\).md)  
  
## Workload Elements  
  
-   [File Element &#40;DTA&#41;](../Topic/File%20Element%20\(DTA\).md)  
  
-   [Database Element for Workload &#40;DTA&#41;](../Topic/Database%20Element%20for%20Workload%20\(DTA\).md)  
  
-   [EventString Element &#40;DTA&#41;](../Topic/EventString%20Element%20\(DTA\).md)  
  
## Tuning Options Elements  
  
-   [TuningTimeInMin Element &#40;DTA&#41;](../Topic/TuningTimeInMin%20Element%20\(DTA\).md)  
  
-   [StorageBoundInMB Element &#40;DTA&#41;](../Topic/StorageBoundInMB%20Element%20\(DTA\).md)  
  
-   [TestServer Element &#40;DTA&#41;](../Topic/TestServer%20Element%20\(DTA\).md)  
  
-   [FeatureSet Element &#40;DTA&#41;](../Topic/FeatureSet%20Element%20\(DTA\).md)  
  
-   [Partitioning Element &#40;DTA&#41;](../Topic/Partitioning%20Element%20\(DTA\).md)  
  
-   [DropOnlyMode Element &#40;DTA&#41;](../Topic/DropOnlyMode%20Element%20\(DTA\).md)  
  
-   [KeepExisting Element &#40;DTA&#41;](../Topic/KeepExisting%20Element%20\(DTA\).md)  
  
-   [OnlineIndexOperation Element &#40;DTA&#41;](../Topic/OnlineIndexOperation%20Element%20\(DTA\).md)  
  
-   [DatabaseToConnect Element &#40;DTA&#41;](../Topic/DatabaseToConnect%20Element%20\(DTA\).md)  
  
## Configuration Elements  
  
-   [Server Element for Configuration &#40;DTA&#41;](../Topic/Server%20Element%20for%20Configuration%20\(DTA\).md)  
  
-   [Database Element for Configuration &#40;DTA&#41;](../Topic/Database%20Element%20for%20Configuration%20\(DTA\).md)  
  
-   [Recommendation Element &#40;DTA&#41;](../Topic/Recommendation%20Element%20\(DTA\).md)  
  
-   [Create Element &#40;DTA&#41;](../Topic/Create%20Element%20\(DTA\).md)  
  
-   [Index Element &#40;DTA&#41;](../Topic/Index%20Element%20\(DTA\).md)  
  
-   [Name Element for Index &#40;DTA&#41;](../Topic/Name%20Element%20for%20Index%20\(DTA\).md)  
  
-   [Column Element for Index &#40;DTA&#41;](../Topic/Column%20Element%20for%20Index%20\(DTA\).md)  
  
-   [Name Element for Column &#40;DTA&#41;](../Topic/Name%20Element%20for%20Column%20\(DTA\).md)  
  
-   [Filegroup Element for Index &#40;DTA&#41;](../Topic/Filegroup%20Element%20for%20Index%20\(DTA\).md)  
  
## Database Elements  
  
-   [Name Element for Database &#40;DTA&#41;](../Topic/Name%20Element%20for%20Database%20\(DTA\).md)  
  
-   [Schema Element for Database &#40;DTA&#41;](../Topic/Schema%20Element%20for%20Database%20\(DTA\).md)  
  
-   [Name Element for Schema &#40;DTA&#41;](../Topic/Name%20Element%20for%20Schema%20\(DTA\).md)  
  
-   [Table Element for Schema &#40;DTA&#41;](../Topic/Table%20Element%20for%20Schema%20\(DTA\).md)  
  
-   [Name Element for Table &#40;DTA&#41;](../Topic/Name%20Element%20for%20Table%20\(DTA\).md)  
  
## See Also  
 [Database Engine Tuning Advisor](../../Topics\TopicNameNotContainA/Database-Engine-Tuning-Advisor.md)  
  
  