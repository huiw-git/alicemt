---
title: setCatalog Method (SQLServerConnection)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerConnection.setCatalog
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 553c0603-c07d-436a-86eb-3ba6b51bd696
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
# setCatalog Method (SQLServerConnection)
  Sets the given catalog name to select a subspace of this [SQLServerConnection](../content/SQLServerConnection-Class.md) object's database in which to work.  
  
## Syntax  
  
```  
  
public void setCatalog(java.lang.String catalog)  
```  
  
#### Parameters  
 *catalog*  
  
 A **String** that contains the catalog name.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setCatalog method is specified by the setCatalog method in the java.sql.Connection interface.  
  
 The *catalog* argument is escaped by the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] automatically. Using this method sets the catalog property for the Connection object. It is not set implicitly in any other way.  
  
## See Also  
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  