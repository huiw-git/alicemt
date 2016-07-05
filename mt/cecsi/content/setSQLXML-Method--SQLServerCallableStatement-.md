---
title: setSQLXML Method (SQLServerCallableStatement)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: de095cb3-1111-4154-8996-3c2e529e3000
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
# setSQLXML Method (SQLServerCallableStatement)
  Sets the designated parameter to the specified SQLXML object.  
  
## Syntax  
  
```  
  
public final void setSQLXML(java.lang.String parameterName,  
                            java.sql.SQLXML xmlObject)  
```  
  
#### Parameters  
 *parameterName*  
  
 An **String** that indicates the parameter name.  
  
 *xmlObject*  
  
 A SQLXML object that contains the parameter value.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setSQLXML method is specified by the setSQLXML method in the java.sql.CallableStatement interface.  
  
## See Also  
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)  
  
  