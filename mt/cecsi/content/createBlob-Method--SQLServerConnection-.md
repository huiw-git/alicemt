---
title: createBlob Method (SQLServerConnection)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 630a93b0-6e3c-4255-a007-1097ce0ee243
manager:jhubbard
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - sv-se
  - zh-cn
  - zh-tw
---
# createBlob Method (SQLServerConnection)
  Creates a Blob object without any data.  
  
## Syntax  
  
```  
  
public java.sql.Blob createBlob()  
```  
  
## Return Value  
 A Blob object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This createBlob method is specified by the createBlob method in the java.sql.Connection interface.  
  
 This method replaces the need for [SQLServerBlob Constructor &#40;SQLServerConnection, byte&#41;](../content/SQLServerBlob-Constructor--SQLServerConnection--byte-.md).  
  
## See Also  
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  