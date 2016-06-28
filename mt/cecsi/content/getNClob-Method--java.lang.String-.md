---
title: getNClob Method (java.lang.String)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: be01ce56-8f13-437b-8de6-246cda5f7830
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
# getNClob Method (java.lang.String)
  Retrieves the value of a JDBC **NCLOB** parameter as a NClob object in the Java programming language.  
  
## Syntax  
  
```  
  
public java.sql.NClob getNClob(java.lang.String parameterName)  
```  
  
#### Parameters  
 *parameterName*  
  
 A **String** that contains the parameter name.  
  
## Return Value  
 ANClobobject.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getNClob method is specified by the getNClob method in the java.sql.CallableStatement interface.  
  
 This method only supports retrieving **NCHAR**, **NVARCHAR**, **NTEXT**, and **XML** parameters. Calling these methods on other data type parameters will cause an exception.  
  
## See Also  
 [getNClob Method &#40;SQLServerCallableStatement&#41;](../content/getNClob-Method--SQLServerCallableStatement-.md)   
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)  
  
  