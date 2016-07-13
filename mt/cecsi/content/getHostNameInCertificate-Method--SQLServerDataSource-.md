---
title: getHostNameInCertificate Method (SQLServerDataSource)
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
  - getHostNameInCertificate Method (SQLServerDataSource)
apilocation: 
  - getHostNameInCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 45ea04e2-9ea5-4171-9136-d09f8a95e128
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
# getHostNameInCertificate Method (SQLServerDataSource)
  Returns the host name used in validating the SQL Server Secure Sockets Layer \(SSL\) certificate.  
  
## Syntax  
  
```  
  
public java.lang.String getHostNameInCertificate()  
```  
  
## Return Value  
 A **String** that contains the host name, or null if no value is set.  
  
## Remarks  
 The host name is used to validate the SQL Server SSL certificate value when the communication layer is encrypted using SSL.  
  
 If the host name is not set, the [getHostNameInCertificate](../content/getHostNameInCertificate-Method--SQLServerDataSource-.md) method returns null.  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  