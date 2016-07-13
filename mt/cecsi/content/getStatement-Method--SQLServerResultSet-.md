---
title: getStatement Method (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.getStatement
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 7dea981b-b4fd-4f8d-954f-e686124627e2
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
# getStatement Method (SQLServerResultSet)
  Retrieves the [SQLServerStatement](../content/SQLServerStatement-Class.md) object that produced this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Syntax  
  
```  
  
public java.sql.Statement getStatement()  
```  
  
## Return Value  
 A SQLServerStatement object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getStatement method is specified by the getStatement method in the java.sql.ResultSet interface.  
  
 If the result set was generated some other way, such as by a [SQLServerDatabaseMetaData](../content/SQLServerDatabaseMetaData-Class.md) method, this method returns null.  
  
## See Also  
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  