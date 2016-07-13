---
title: createClob Method (SQLServerConnection)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58b0865a-1cde-4046-9761-51e471294023
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
# createClob Method (SQLServerConnection)
  Creates a Clob object without any data.  
  
## Syntax  
  
```  
  
public java.sql.Clob createClob()  
```  
  
## Return Value  
 A Clob object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This createClob method is specified by the createClob method in the java.sql.Connection interface.  
  
 This method replaces the need for [SQLServerClob Constructor &#40;SQLServerConnection, java.lang.String&#41;](../content/SQLServerClob-Constructor--SQLServerConnection--java.lang.String-.md).  
  
## See Also  
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  