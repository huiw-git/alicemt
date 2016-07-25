---
title: "setApplicationName Method (SQLServerDataSource)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDataSource.setApplicationName
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 24d6e48d-53c4-4da2-a6de-1cdff463c9cd
caps.latest.revision: 12
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
# setApplicationName Method (SQLServerDataSource)
  Sets the application name.  
  
## Syntax  
  
```  
  
public void setApplicationName(java.lang.String applicationName)  
```  
  
#### Parameters  
 *applicationName*  
  
 A **String** that contains the name of the application.  
  
## Remarks  
 The application name is used to identify the specific application in various [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] profiling and logging tools. If the application name is not set, the getApplicationName method returns the non-localized string "[!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]".  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  