---
title: rowUpdated Method (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.rowUpdated
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 29303550-294e-4d43-b892-312b42e21271
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
# rowUpdated Method (SQLServerResultSet)
  Retrieves whether the current row has been updated.  
  
## Syntax  
  
```  
  
public boolean rowUpdated()  
```  
  
## Return Value  
 **true** if both the row has been visibly updated by the owner or another user, and updates are detected. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This rowUpdated method is specified by the rowUpdated method in the java.sql.ResultSet interface.  
  
 The value that is returned depends on whether or not the result set can detect updates.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] does not detect updated rows for any cursor type.  
  
## See Also  
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  