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
|**Parent element**|[DTAInput Element &#40;DTA&#41;](../Topic/DTAInput%20Element%20\(DTA\).md)|  
|**Child elements**|[Name Element for Server &#40;DTA&#41;](../Topic/Name%20Element%20for%20Server%20\(DTA\).md)<br /><br /> [Database Element for Server &#40;DTA&#41;](../Topic/Database%20Element%20for%20Server%20\(DTA\).md)|  
  
## Remarks  
 You can specify only one **Server** element for the **DTAInput** element. This element is of the **ServerDetailsTypecomplexType** name in the DTA XML schema. Do not confuse this **Server** element with the one that is the child of the **Configuration** element. For more information, see [Server Element for Configuration &#40;DTA&#41;](../Topic/Server%20Element%20for%20Configuration%20\(DTA\).md).  
  
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
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../Topic/XML%20Input%20File%20Reference%20\(Database%20Engine%20Tuning%20Advisor\).md)  
  
  