---
title: updateBytes Method (java.lang.String, byte)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.updateBytes (java.lang.String, byte[])
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 4fb9de2b-61bc-4c96-89a5-c07cd7ee201a
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
# updateBytes Method (java.lang.String, byte)
  Updates the designated column with an array of **byte** values given the column name.  
  
## Syntax  
  
```  
  
public void updateBytes(java.lang.String columnName,  
                        byte[] x)  
```  
  
#### Parameters  
 *columnName*  
  
 A **String** that contains the column name.  
  
 *x*  
  
 An array of **byte** values.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This updateBytes method is specified by the updateBytes method in the java.sql.ResultSet interface.  
  
 In a previous version of [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)], you could use SQLServerResultSet.updateBytes to convert values between byte arrays and [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data type **date**, **time**, **datetime2**, or **datetimeoffset**. Now, using this method with those data types will cause an exception indicating that the conversion is not supported.  
  
## See Also  
 [updateBytes Method &#40;SQLServerResultSet&#41;](../content/updateBytes-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  