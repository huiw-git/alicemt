---
title: setAuthenticationScheme (SQLServerDataSource)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b942f78e-7ce1-44ef-923d-a7c3d7c76b83
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
# setAuthenticationScheme (SQLServerDataSource)
  Indicates the kind of integrated security you want your application to use.  
  
## Syntax  
  
```vb  
public void setAuthenticationScheme(String authenticationScheme);  
```  
  
#### Parameters  
 *authenticationScheme*  
  
 Values are **"JavaKerberos"** and the default **"NativeAuthentication"**. For more information, see [Using Kerberos Integrated Authentication to Connect to SQL Server](../content/Using-Kerberos-Integrated-Authentication-to-Connect-to-SQL-Server.md).  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  