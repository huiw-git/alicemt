---
title: "getSchemaTerm Method (SQLServerDatabaseMetaData)"
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
  - SQLServerDatabaseMetaData.getSchemaTerm
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 3e4a400f-0859-4ac3-983e-c25633b33683
caps.latest.revision: 10
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
# getSchemaTerm Method (SQLServerDatabaseMetaData)
  Retrieves the preferred term for "schema" in this database.  
  
## Syntax  
  
```  
  
public java.lang.String getSchemaTerm()  
```  
  
## Return Value  
 A **String** that contains the preferred term.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getSchemaTerm method is specified by the getSchemaTerm method in the java.sql.DatabaseMetaData interface.  
  
 When using the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] with a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database, this method returns "schema" as the preferred term.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  