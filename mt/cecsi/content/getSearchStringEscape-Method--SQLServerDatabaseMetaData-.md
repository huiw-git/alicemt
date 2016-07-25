---
title: "getSearchStringEscape Method (SQLServerDatabaseMetaData)"
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
  - SQLServerDatabaseMetaData.getSearchStringEscape
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: ea0f95d0-0238-4dc8-9f26-7ff9b65f30c3
caps.latest.revision: 8
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
# getSearchStringEscape Method (SQLServerDatabaseMetaData)
  Retrieves the **String** that can be used to escape wildcard characters.  
  
## Syntax  
  
```  
  
public java.lang.String getSearchStringEscape()  
```  
  
## Return Value  
 A **String** that contains the escape wildcard character String.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getSearchStringEscape method is specified by the getSearchStringEscape method in the java.sql.DatabaseMetaData interface.  
  
 This method is used only for metadata pattern searches. It returns "\\". A **String** search pattern can escape wildcards ("%" and "_") and provide them as literals by prepending a backslash. This translates "\\%" to "[%]" and "\\\_" to "[\_]".  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  