---
title: setUser Method (SQLServerDataSource)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDataSource.setUser
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: d2ea7906-2d10-438d-aa51-f576eea923c7
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
# setUser Method (SQLServerDataSource)
  Sets the user name that is used to connect the data source.  
  
## Syntax  
  
```  
  
public void setUser(java.lang.String user)  
```  
  
#### Parameters  
 *user*  
  
 A **String** that contains the user name.  
  
## Remarks  
 The setUser method sets the user name that will be used to connect to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]. If user name value is not set, the [getUser](../content/getUser-Method--SQLServerDataSource-.md) method returns the default value of null.  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  