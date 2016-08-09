---
title: "Database Element for Workload (DTA)"
ms.custom: na
ms.date: 06/29/2016
ms.devlang: 
  - XML
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 112fca2a-37e5-4162-b2e7-b56eb8ab0c6f
caps.latest.revision: 13
manager: jhubbard
---
# Database Element for Workload (DTA)
Specifies the database where the workload trace table is located.  
  
## Syntax  
  
```  
  
<Workload>  
  <Database>  
   ...code removed here...  
  </Database>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|None.|  
|**Default value**|None.|  
|**Occurrence**|Required once if no other type of workload is specified. You must specify an **EventString**, a **File**, or a **Database** child element for the **Workload** parent, but only one type can be used. For example, if you specify a workload with the **Database** element, you cannot also specify a workload with the **File** element in the same XML input file.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[Workload Element (DTA)](../../Topics/TopicNameNotContainA/Workload-Element--DTA-.md)|  
|**Child elements**|[Name Element for Database (DTA)](../../Topics/TopicNameNotContainA/Name-Element-for-Database--DTA-.md)<br /><br /> [Schema Element for Database (DTA)](../../Topics/TopicNameNotContainA/Schema-Element-for-Database--DTA-.md)|  
  
## Remarks  
 This element is of the **DatabaseDetailsTypecomplexType** name in the Database Engine Tuning Advisor XML schema. Do not confuse this **Database** element with the one whose root parent is the **Configuration** element. (See [Database Element for Configuration (DTA)](../../Topics/TopicNameNotContainA/Database-Element-for-Configuration--DTA-.md).)  
  
## Example  
 For a usage example of this **Database** element, see the code example in [Workload Element (DTA)](../../Topics/TopicNameNotContainA/Workload-Element--DTA-.md).  
  
## See Also  
 [XML Input File Reference (Database Engine Tuning Advisor)](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)