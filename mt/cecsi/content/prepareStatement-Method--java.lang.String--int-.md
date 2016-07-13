---
title: prepareStatement Method (java.lang.String, int)
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
  - SQLServerConnection.prepareStatement (java.lang.String, int)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 4504cd55-81fd-4783-bcb0-1efb1938fdd5
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
# prepareStatement Method (java.lang.String, int)
  Creates a [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md) object for sending parameterized SQL statements to the database, and has the capability to retrieve auto\-generated keys.  
  
## Syntax  
  
```  
  
public java.sql.PreparedStatement prepareStatement(java.lang.String sql,  
                                                   int flag)  
```  
  
#### Parameters  
 *sql*  
  
 A **String** containing an SQL statement.  
  
 *flag*  
  
 An **int** that indicates if auto\-generated keys will be available.  
  
## Return Value  
 A PreparedStatement object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This prepareStatement method is specified by the prepareStatement method in the java.sql.Connection interface.  
  
## See Also  
 [prepareStatement Method &#40;SQLServerConnection&#41;](../content/prepareStatement-Method--SQLServerConnection-.md)   
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  