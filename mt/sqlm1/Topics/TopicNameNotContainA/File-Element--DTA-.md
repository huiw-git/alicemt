---
title: File Element (DTA)
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
ms.assetid: 73dce835-9a80-4aef-8e0f-9dcf07dd5b80
---
# File Element (DTA)
  Specifies the workload file. A workload is a set of [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements that execute against a database or databases that you want to tune. Workload files can be [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] scripts \(.sql\) or trace files \(.trc\). For more information, see[Start and Use the Database Engine Tuning Advisor](../../Topics\TopicNameNotContainA/Start-and-Use-the-Database-Engine-Tuning-Advisor.md).  
  
## Syntax  
  
```  
  
<DTAInput>  
  <Server>...</Server>  
  <Workload>  
    <File>...</File>  
  </Workload>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|Use the **string** data type to specify the directory path to your workload file. For example:<br /><br /> `<File>C:\Tuning\tun.sql</File>`<br /><br /> Note that length limit is enforced by the server.|  
|**Default value**|None.|  
|**Occurrence**|Required once if no other type of workload is specified. You must specify an **EventString**, a **File**, or a **Database** child element for the **Workload** parent, but only one type can be used. For example, if you specify a workload with the **File** element, then you cannot also specify a workload with the **Database** element in the same XML input file.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[Workload Element &#40;DTA&#41;](../Topic/Workload%20Element%20\(DTA\).md)|  
|**Child elements**|None.|  
  
## Example  
 For a usage example of this element, see [Simple XML Input File Sample &#40;DTA&#41;](../Topic/Simple%20XML%20Input%20File%20Sample%20\(DTA\).md).  
  
## See Also  
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../Topic/XML%20Input%20File%20Reference%20\(Database%20Engine%20Tuning%20Advisor\).md)  
  
  