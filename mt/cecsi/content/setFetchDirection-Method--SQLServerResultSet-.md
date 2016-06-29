---
title: setFetchDirection Method (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.setFetchDirection
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 4ee82290-508d-4bff-a5c5-8a56338deef8
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
# setFetchDirection Method (SQLServerResultSet)
  Gives a hint as to the direction in which the rows in this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object will be processed.  
  
> [!NOTE]  
>  This method is not currently supported by the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]. If you use this method, the JDBC driver remembers the setting, but currently does not act on it.  
  
## Syntax  
  
```  
  
public void setFetchDirection(int direction)  
```  
  
#### Parameters  
 *direction*  
  
 An **int** that indicates the suggested fetch direction. Can be one of the following values:  
  
 ResultSet.FETCH\_FORWARD  
  
 ResultSet.FETCH\_REVERSE  
  
 ResultSet.FETCH\_UNKNOWN  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setFetchDirection method is specified by the setFetchDirection method in the java.sql.ResultSet interface.  
  
 The initial value of this method is determined by the [SQLServerStatement](../content/SQLServerStatement-Class.md) object that produced this SQLServerResultSet object. The fetch direction can be changed at any time.  
  
> [!NOTE]  
>  Using this method when the cursor type is forward\-only has no effect.  
  
## See Also  
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  