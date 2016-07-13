---
title: getUser Method (SQLServerDataSource)
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
  - SQLServerDataSource.getUser
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 3513dd7f-6ae5-4010-bde0-454ac4365bce
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
# getUser Method (SQLServerDataSource)
  Returns the user name that is used to connect the data source.  
  
## Syntax  
  
```  
  
public java.lang.String getUser()  
```  
  
## Return Value  
 A **String** that contains the user name.  
  
## Remarks  
 The [setUser](../content/setUser-Method--SQLServerDataSource-.md) method sets the user name that will be used when connecting to the instance of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]. If user name value is not set, the getUser method returns the default value of null.  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  