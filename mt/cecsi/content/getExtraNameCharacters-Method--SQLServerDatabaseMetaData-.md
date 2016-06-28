---
title: getExtraNameCharacters Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.getExtraNameCharacters
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: a22becfe-0f07-4a15-8d11-06d4054b2369
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
# getExtraNameCharacters Method (SQLServerDatabaseMetaData)
  Retrieves all the extra characters that can be used in unquoted identifier names, such as those beyond a\-z, A\-Z, 0\-9, and \_.  
  
## Syntax  
  
```  
  
public java.lang.String getExtraNameCharacters()  
```  
  
## Return Value  
 A **String** that contains the extra characters.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getExtraNameCharacters method is specified by the getExtraNameCharacters method in the java.sql.DatabaseMetaData interface.  
  
 When using the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] with a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database, this method returns the $, \#, and @ extra characters.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  