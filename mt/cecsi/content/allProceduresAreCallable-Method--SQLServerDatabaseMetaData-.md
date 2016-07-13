---
title: allProceduresAreCallable Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.allProceduresAreCallable
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 8886137d-455e-497c-afea-4b326eda52f1
manager:jhubbard
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
# allProceduresAreCallable Method (SQLServerDatabaseMetaData)
  Retrieves whether the current user has permissions to call all the procedures that are returned by the [getProcedures](../content/getProcedures-Method--SQLServerDatabaseMetaData-.md) method.  
  
## Syntax  
  
```  
  
public boolean allProceduresAreCallable()  
```  
  
## Return Value  
 **true** if the user has permissions to call all the procedures. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This allProceduresAreCallable method is specified by the allProceduresAreCallable method in the java.sql.DatabaseMetaData interface.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  