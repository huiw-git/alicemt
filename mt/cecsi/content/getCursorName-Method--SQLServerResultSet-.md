---
title: getCursorName Method (SQLServerResultSet)
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
  - SQLServerResultSet.getCursorName
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: e5b3af67-423a-4551-a4c6-a4bc076bd504
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
# getCursorName Method (SQLServerResultSet)
  Retrieves the name of the SQL cursor that is used by this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
> [!NOTE]  
>  This method is not currently supported by the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]. If called, an exception will be thrown.  
  
## Syntax  
  
```  
  
public java.lang.String getCursorName()  
```  
  
## Return Value  
 A **String** that contains the cursor name.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getCursorName method is specified by the getCursorName method in the java.sql.ResultSet interface.  
  
## See Also  
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  