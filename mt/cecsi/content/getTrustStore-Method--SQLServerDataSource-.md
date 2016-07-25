---
title: "getTrustStore Method (SQLServerDataSource)"
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
  - getTrustStore Method (SQLServerDataSource)
apilocation: 
  - getTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 8f5850e4-8627-49a8-ba0e-b1f4014322a5
caps.latest.revision: 12
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
# getTrustStore Method (SQLServerDataSource)
  Returns the path (including file name) to the certificate trustStore file.  
  
## Syntax  
  
```  
  
public java.lang.String getTrustStore()  
```  
  
## Return Value  
 A **String** that contains the path (including file name) to the certificate trustStore file, or null if no value is set.  
  
## Remarks  
 If the trustStore property is not set, the [getTrustStore](../content/getTrustStore-Method--SQLServerDataSource-.md) method returns null.  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  