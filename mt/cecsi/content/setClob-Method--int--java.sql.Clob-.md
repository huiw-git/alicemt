---
title: setClob Method (int, java.sql.Clob)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerPreparedStatement.setClob
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 68d49f2c-fd8d-4abb-bfdc-e7b0fbd9a9da
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
# setClob Method (int, java.sql.Clob)
  Sets the designated parameter to the given Clob object.  
  
## Syntax  
  
```  
  
public final void setClob(int parameterIndex,  
                          java.sql.Clob clobValue)  
```  
  
#### Parameters  
 *parameterIndex*  
  
 An **int** that indicates the parameter number.  
  
 *clobValue*  
  
 A Clob object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setClob method is specified by the setClob method in the java.sql.PreparedStatement interface.  
  
## See Also  
 [SQLServerPreparedStatement Methods](../content/SQLServerPreparedStatement-Methods.md)   
 [SQLServerPreparedStatement Class](../content/SQLServerPreparedStatement-Class.md)  
  
  