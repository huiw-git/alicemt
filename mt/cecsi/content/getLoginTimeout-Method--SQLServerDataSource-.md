---
title: getLoginTimeout Method (SQLServerDataSource)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDataSource.getLoginTimeout
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 316f067c-9e08-456a-af19-b80b0bbd4a5c
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
# getLoginTimeout Method (SQLServerDataSource)
  Returns the number of seconds that this [SQLServerDataSource](../content/SQLServerDataSource-Class.md) object will wait while trying to make a connection.  
  
## Syntax  
  
```  
  
public int getLoginTimeout()  
```  
  
## Return Value  
 An **int** value that represents the number of seconds to wait.  
  
## Remarks  
 If the application does not specify a timeout value explicitly, this method returns a default value of 15 seconds.  
  
 This getLoginTimeout method is specified by the getLoginTimeout method in the javax.sql.DataSource interface.  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  