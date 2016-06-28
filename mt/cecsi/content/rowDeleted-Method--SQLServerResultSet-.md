---
title: rowDeleted Method (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.rowDeleted
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 9c6db315-e614-4604-b020-41af6a214cc1
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
# rowDeleted Method (SQLServerResultSet)
  Retrieves whether a row has been deleted.  
  
## Syntax  
  
```  
  
public boolean rowDeleted()  
```  
  
## Return Value  
 **true** if a row was deleted and deletions are detected. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This rowDeleted method is specified by the rowDeleted method in the java.sql.ResultSet interface.  
  
 A deleted row might leave a visible hole in a result set. This method can be used to detect holes in a result set. The value that is returned depends on whether this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object can detect deletions.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] detects deleted rows for all updatable cursor types, though the detection is transient for forward and dynamic cursors.  
  
## See Also  
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  