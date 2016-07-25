---
title: "acceptsURL Method (SQLServerDriver)"
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
  - SQLServerDriver.acceptsURL
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: fc744566-7191-4b15-9f76-b4b8087fb14a
caps.latest.revision: 7
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
# acceptsURL Method (SQLServerDriver)
  Checks if the given URL is valid.  
  
## Syntax  
  
```  
  
public boolean acceptsURL(java.lang.String url)  
```  
  
#### Parameters  
 *url*  
  
 A **String** value containing the URL used to connect to the database.  
  
## Return Value  
 **true** if the given URL is valid. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This acceptsURL method is specified by the acceptsURL method in the java.sql.Driver interface.  
  
## See Also  
 [SQLServerDriver Methods](../content/SQLServerDriver-Methods.md)   
 [SQLServerDriver Members](../content/SQLServerDriver-Members.md)   
 [SQLServerDriver Class](../content/SQLServerDriver-Class.md)  
  
  