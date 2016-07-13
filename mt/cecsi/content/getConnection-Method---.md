---
title: getConnection Method ()
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
  - SQLServerDataSource.getConnection ()
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 7f520e96-5313-468f-b987-535ddaea027e
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
# getConnection Method ()
  Tries to establish a connection with the data source that this [SQLServerDataSource](../content/SQLServerDataSource-Class.md) object represents.  
  
## Syntax  
  
```  
  
public java.sql.Connection getConnection()  
```  
  
## Return Value  
 A [SQLServerConnection](../content/SQLServerConnection-Class.md) object.  
  
## Exceptions  
 java.sql.SQLException  
  
## Remarks  
 This getConnection method is specified by the getConnection method in the javax.sql.DataSource interface.  
  
## See Also  
 [getConnection Method &#40;SQLServerDataSource&#41;](../content/getConnection-Method--SQLServerDataSource-.md)   
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  