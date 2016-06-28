---
title: getTime Method (int, java.util.Calendar)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerCallableStatement.getTime (int, java.util.Calendar)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 87b7fbaf-7149-494f-b3b2-16b468a8ebf1
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
# getTime Method (int, java.util.Calendar)
  Retrieves the value of the designated parameter as a java.sql.Time object in the Java programming language, given the parameter index, by using the given Calendar object.  
  
## Syntax  
  
```  
  
public java.sql.Time getTime(int index,  
                             java.util.Calendar cal)  
```  
  
#### Parameters  
 *index*  
  
 An **int** that indicates the parameter index.  
  
 *cal*  
  
 A Calendar object.  
  
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
  
  