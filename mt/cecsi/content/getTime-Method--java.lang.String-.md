---
title: getTime Method (java.lang.String)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerCallableStatement.getTime (java.lang.String)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: ca0a3b29-30d1-4d20-bc8d-d3d9ed19ff50
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
# getTime Method (java.lang.String)
  Retrieves the value of the designated parameter as a java.sql.Time object in the Java programming language given the parameter name.  
  
## Syntax  
  
```  
  
public java.sql.Time getTime(java.lang.String sCol)  
```  
  
#### Parameters  
 *sCol*  
  
 A **String** that contains the parameter name.  
  
## Return Value  
 A Time object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getTime method is specified by the getTime method in the java.sql.CallableStatement interface.  
  
 See the chart titled "Getter Method Conversions" in [Understanding Data Type Conversions](../content/Understanding-Data-Type-Conversions.md) to see which [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data types can be retrieved with this method.  
  
## See Also  
 [getTime Method &#40;SQLServerCallableStatement&#41;](../content/getTime-Method--SQLServerCallableStatement-.md)   
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)   
 [SQLServerCallableStatement Class](../content/SQLServerCallableStatement-Class.md)  
  
  