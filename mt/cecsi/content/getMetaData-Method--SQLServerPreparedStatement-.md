---
title: getMetaData Method (SQLServerPreparedStatement)
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
  - SQLServerPreparedStatement.getMetaData
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 5ed49a53-ed61-4e95-ad67-45957aaabb6a
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
# getMetaData Method (SQLServerPreparedStatement)
  Retrieves a [SQLServerResultSetMetaData Class](../content/SQLServerResultSetMetaData-Class.md) object that contains information about the columns of the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object that will be returned when this [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md) object is run.  
  
## Syntax  
  
```  
  
public final java.sql.ResultSetMetaData getMetaData()  
```  
  
## Return Value  
 A ResultSetMetaData object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getMetaData method is specified by the getMetaData method in the java.sql.PreparedStatement interface.  
  
## See Also  
 [SQLServerPreparedStatement Members](../content/SQLServerPreparedStatement-Members.md)   
 [SQLServerPreparedStatement Class](../content/SQLServerPreparedStatement-Class.md)  
  
  