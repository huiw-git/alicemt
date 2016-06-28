---
title: setLastUpdateCount Method (SQLServerDataSource)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDataSource.setLastUpdateCount
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 5487631a-1107-4169-84ca-b77fd09bea66
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
# setLastUpdateCount Method (SQLServerDataSource)
  Sets a **Boolean** value that indicates if the lastUpdateCount property is enabled.  
  
## Syntax  
  
```  
  
public void setLastUpdateCount(boolean lastUpdateCount)  
```  
  
#### Parameters  
 *lastUpdateCount*  
  
 **true** if lastUpdateCount is enabled. Otherwise, **false**.  
  
## Remarks  
 If the lastUpdateCount property is set to **true**, [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] will return only the last update count from from an SQL statement passed to the server. If the lastUpdateCount property is set to **false**, the driver will return all update counts including those returned by any triggers that may have fired. If the lastUpdateCount property is not set, the [getLastUpdateCount](../content/getLastUpdateCount-Method--SQLServerDataSource-.md) method returns the default value of **true**.  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  