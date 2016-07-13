---
title: getBytes Method (java.lang.String)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerCallableStatement.getBytes (java.lang.String)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 4d0dac7f-7f39-47a2-953e-80ab03688d82
manager: jhubbard
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
# getBytes Method (java.lang.String)
  Retrieves the value of the designated parameter as an array of bytes value given the parameter name.  
  
## Syntax  
  
```  
  
public byte[] getBytes(java.lang.String sCol)  
```  
  
#### Parameters  
 *sCol*  
  
 A **String** that contains the parameter name.  
  
## Return Value  
 An array of **byte** values.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 In a previous version of [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)], you could use SQLServerCallableStatement.getBytes to convert values between byte arrays and [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data type **date**, **time**, **datetime2**, or **datetimeoffset**. Now, using this method with those data types will cause an exception indicating that the conversion is not supported.  
  
 This getBytes method is specified by the getBytes method in the java.sql.CallableStatement interface.  
  
## See Also  
 [getBytes Method &#40;SQLServerCallableStatement&#41;](../content/getBytes-Method--SQLServerCallableStatement-.md)   
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)   
 [SQLServerCallableStatement Class](../content/SQLServerCallableStatement-Class.md)  
  
  