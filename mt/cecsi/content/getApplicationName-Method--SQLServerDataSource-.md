---
title: getApplicationName Method (SQLServerDataSource)
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
  - SQLServerDataSource.getApplicationName
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: f71e501c-ccd7-4a1e-b6ea-4d47a81c18c6
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
# getApplicationName Method (SQLServerDataSource)
  Returns the application name.  
  
## Syntax  
  
```  
  
public java.lang.String getApplicationName()  
```  
  
## Return Value  
 A **String** that contains the application name, or "[!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]" if no value is set.  
  
## Remarks  
 The application name is used to identify the specific application in various [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] profiling and logging tools. If the application name is not set, the getApplicationName method returns the non\-localized string "[!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]".  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  