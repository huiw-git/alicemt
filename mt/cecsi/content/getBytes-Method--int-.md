---
title: getBytes Method (int)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerCallableStatement.getBytes (int)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 8c2973e6-d57f-4f64-b812-350ce4098ce6
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
# getBytes Method (int)
  Retrieves the value of the designated parameter as an array of bytes value given the parameter index.  
  
## Syntax  
  
```  
  
public byte[] getBytes(int index)  
```  
  
#### Parameters  
 *index*  
  
 An **int** that indicates the parameter index.  
  
## Return Value  
 An array of **byte** values.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 In a previous version of [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)], you could use SQLServerCallableStatement.getBytes to convert values between byte arrays and [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data type **date**, **time**, **datetime2**, or **datetimeoffset**. Now, using this method with those data types will cause an exception indicating that the conversion is not supported.  
  
 This getBytes method is specified by the getBytes method in the java.sql.CallableStatement interface.  
  
## See Also  
 [getBytes Method &#40;SQLServerCallableStatement&#41;](../content/getBytes-Method--SQLServerCallableStatement-.md)   
 [SQLServerCallableStatement Class](../content/SQLServerCallableStatement-Class.md)  
  
  