---
title: getServerName Method (SQLServerDataSource)
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
  - SQLServerDataSource.getServerName
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 3004ed22-5d69-4dd0-8761-d39f0b7dde13
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
# getServerName Method (SQLServerDataSource)
  Returns the name of the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] instance.  
  
## Syntax  
  
```  
  
public java.lang.String getServerName()  
```  
  
## Return Value  
 A **String** that contains the server name or null if no value is set.  
  
## Remarks  
 The server name is the host name of the target computer that is running [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]. If the getServerName property is not set, getServerName returns the default value of null.  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  