---
title: setReadOnly Method (SQLServerConnection)
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
  - SQLServerConnection.setReadOnly
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: bd11fd50-f092-43a0-a6bc-c63e70cff8da
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
# setReadOnly Method (SQLServerConnection)
  Puts this [SQLServerConnection](../content/SQLServerConnection-Class.md) object in read\-only mode as a hint to the JDBC driver to enable database optimizations.  
  
> [!NOTE]  
>  This method is not supported by the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)].  
  
## Syntax  
  
```  
  
public void setReadOnly(boolean readOnly)  
```  
  
#### Parameters  
 *readOnly*  
  
 **true** if the connection is to be read\-only. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setReadOnly method is specified by the setReadOnly method in the java.sql.Connection interface.  
  
## See Also  
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  