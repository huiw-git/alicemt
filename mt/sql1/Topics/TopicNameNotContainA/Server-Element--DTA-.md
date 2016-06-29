---
title: Server Element (DTA)
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
ms.assetid: 9fe0bfb4-3aa6-4eb2-a83e-c0d0e7d4e9f6
---
# Server Element (DTA)
  Contains the identifying information for the server on which the databases reside that you want to tune.  
  
## Syntax  
  
```  
  
<DTAInput>  
    <Server>  
    ...code removed here...  
    </Server>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|None.|  
|**Default value**|None.|  
|**Occurrence**|Required once per **DTAInput** element.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[DTAInput Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/DTAInput-Element--DTA-.md)|  
|**Child elements**|[Name Element for Server &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Name-Element-for-Server--DTA-.md)<br /><br /> [Database Element for Server &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Database-Element-for-Server--DTA-.md)|  
  
## Remarks  
 You can specify only one **Server** element for the **DTAInput** element. This element is of the **ServerDetailsTypecomplexType** name in the DTA XML schema. Do not confuse this **Server** element with the one that is the child of the **Configuration** element. For more information, see [Server Element for Configuration &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Server-Element-for-Configuration--DTA-.md).  
  
## Example  
 The following example shows how to specify the **Sales.SalesPerson** table in the **AdventureWorks** database on SERVER001:  
  
```xml  
<Server>  
  <Name>SERVER001</Name>  
  <Database>  
    <Name>AdventureWorks</Name>  
    <Schema>  
      <Name>Sales</Name>  
      <Table>  
        <Name>SalesPerson</Name>  
      </Table>  
    </Schema>  
  </Database>  
</Server  
```  
  
## See Also  
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)  
  
  