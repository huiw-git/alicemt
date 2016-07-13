---
title: setTrustServerCertificate Method (SQLServerDataSource)
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
  - setTrustServerCertificate Method (SQLServerDataSource)
apilocation: 
  - setTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 6c37b518-147e-4cd9-9eff-b48a3f5888c6
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
# setTrustServerCertificate Method (SQLServerDataSource)
  Sets a **Boolean** value that indicates if the trustServerCertificate property is enabled.  
  
## Syntax  
  
```  
  
public void setTrustServerCertificate(boolean trustServerCertificate)  
```  
  
#### Parameters  
 *trustServerCertificate*  
  
 **true** if the server Secure Sockets Layer \(SSL\) certificate should be automatically trusted when the communication layer is encrypted using SSL. Otherwise, **false**.  
  
## Remarks  
 If the trustServerCertificate property is set to **true**, the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] SSL certificate is automatically trusted when the communication layer is encrypted using SSL. In other words, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] will not validate the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] SSL certificate. The default value is **false**.  
  
 If the trustServerCertificate property is set to **false**, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] will validate the server SSL certificate.  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  