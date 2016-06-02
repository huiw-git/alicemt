---
title: Example: Retrieving Binary Data
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-xml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5cea5d49-58ac-403a-a933-c4fd91de400b
---
# Example: Retrieving Binary Data
  The following query returns the product photo stored in a **varbinary\(max\)** type column. The `BINARY BASE64` option is specified in the query to return the binary data in base64\-encoded format.  
  
## Example  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductPhotoID, ThumbNailPhoto  
FROM Production.ProductPhoto  
WHERE ProductPhotoID=1  
FOR XML RAW, BINARY BASE64 ;  
GO  
```  
  
 This is the result:  
  
```  
<row ProductModelID="1" ThumbNailPhoto="base64 encoded binary data"/>  
```  
  
## See Also  
 [Use RAW Mode with FOR XML](../../Topics\TopicNameNotContainA/Use-RAW-Mode-with-FOR-XML.md)  
  
  