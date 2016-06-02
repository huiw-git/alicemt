---
title: Example: Retrieving Product Model Information as XML
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-xml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3828b4ca-3ab2-444f-9c58-8be6e7f064a6
---
# Example: Retrieving Product Model Information as XML
  The following query returns product model information. `RAW` mode is specified in the `FOR XML` clause.  
  
## Example  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW;  
GO  
```  
  
 This is the partial result:  
  
 `<row ProductModelID="122" Name="All-Purpose Bike Stand" />`  
  
 `<row ProductModelID="119" Name="Bike Wash" />`  
  
 You can retrieve element\-centric XML by specifying the `ELEMENTS` directive.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, ELEMENTS;  
GO  
```  
  
 This is the result:  
  
```  
<row>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</row>  
<row>  
  <ProductModelID>119</ProductModelID>  
  <Name>Bike Wash</Name>  
</row>  
```  
  
 You can optionally specify the `TYPE` directive to retrieve the results as **xml** type. The `TYPE` directive does not change the content of the results. Only the data type of the results is affected.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, TYPE ;  
GO  
```  
  
## See Also  
 [Use RAW Mode with FOR XML](../../Topics\TopicNameNotContainA/Use-RAW-Mode-with-FOR-XML.md)  
  
  