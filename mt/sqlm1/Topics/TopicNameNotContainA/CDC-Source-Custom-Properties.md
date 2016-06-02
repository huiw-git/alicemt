---
title: CDC Source Custom Properties
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 744e9357-94a9-4202-abe8-1d3d202697e9
---
# CDC Source Custom Properties
  The following table describes the custom properties of the CDC source. All properties are read\/write.  
  
|Property name|Data Type|Description|  
|-------------------|---------------|-----------------|  
|Connection|ADO.Net Connection|An ADO.NET connection to the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] CDC database for access to the change tables.|  
|StateVariable|String|An SSIS string package variable that maintains the CDC state of the current CDC run.|  
|CdcProcessingMode|Integer \(enumeration\)|This mode determines how processing is handled. The possible options are **All**, **All with old values**, **Net**, **Net with update mask**, and **Net with merge**.<br /><br /> Modes that start with All return all changes and modes that start with Net return net changes only.<br /><br /> Tables without a primary key can take the ALL values only.<br /><br /> **Net with Update Mask** adds boolean columns with the name pattern **\_\_$\<column\-name\>\_\_Changed** that indicate changed columns in the current change row.<br /><br /> For additional information about the values for this property, see [CDC Source Editor &#40;Connection Manager Page&#41;](../Topic/CDC%20Source%20Editor%20\(Connection%20Manager%20Page\).md).|  
|CaptureInstance|String|The name of the CDC capture instance with the CDC table to be read. A captured source table can have one or two captured instances to handle seamless transitioning of table definition through schema changes. If more than one capture instance is defined for the source table being captured, select the capture instance you want to use here. The default capture instance name for a table \[schema\].\[table\] is \<schema\>\_\<table\> but that actual capture instance names in use may be different. The actual table that is read from is the CDC table **cdc .\<capture\-instance\>\_CT**.|  
|ReprocessingIndicator|Boolean|A value that specifies whether to add the **\_\_$reprocessing** column. This special output column lets the SSIS developer handle consistency errors differently when working on the Initial Processing Range.<br /><br /> If **true**, the  **\_\_$reprocessing** column is added.<br /><br /> This column value is **true** when the CDC processing range overlaps with the initial processing range \(the range of LSNs corresponding to the period of initial load\) or when a CDC processing range is reprocessed following an error in a previous run. This indicator column lets the SSIS developer handle errors differently when reprocessing changes \(for example, actions such as a delete of a non\-existing row and an insert that failed on a duplicate key can be ignored\).<br /><br /> The default value is **false**.|  
|CommandTimeout|Integer|This value indicates the timeout \(in seconds\) to use when communicating with the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] database. This value is used where the response time from the database is very slow and the default value\(30 seconds\) is not enough.|  
  
 For more information about the CDC source, see [CDC Source](../../Topics\TopicNameNotContainA/CDC-Source.md).  
  
  