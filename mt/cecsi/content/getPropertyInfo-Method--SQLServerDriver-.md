---
title: getPropertyInfo Method (SQLServerDriver)
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
  - SQLServerDriver.getPropertyInfo
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: b5eaad8a-31ef-44ac-af11-d5caa13ac3e2
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
# getPropertyInfo Method (SQLServerDriver)
  Used to discover the properties needed to connect to a database.  
  
## Syntax  
  
```  
  
public java.sql.DriverPropertyInfo[] getPropertyInfo(java.lang.String Url,  
                                                     java.util.Properties Info)  
```  
  
#### Parameters  
 *Url*  
  
 A **String** value that contains the URL that is used to connect to the database.  
  
 *Info*  
  
 A list of property value pairs, null on first use.  
  
## Return Value  
 An array of DriverPropertyInfo objects.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getPropertyInfo method is specified by the getPropertyInfo method in the java.sql.Driver interface.  
  
## See Also  
 [SQLServerDriver Methods](../content/SQLServerDriver-Methods.md)   
 [SQLServerDriver Members](../content/SQLServerDriver-Members.md)   
 [SQLServerDriver Class](../content/SQLServerDriver-Class.md)  
  
  