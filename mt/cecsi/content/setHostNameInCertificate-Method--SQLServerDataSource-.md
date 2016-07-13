---
title: setHostNameInCertificate Method (SQLServerDataSource)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - setHostNameInCertificate Method (SQLServerDataSource)
apilocation: 
  - setHostNameInCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 2bcf4f2e-a103-4374-abc4-ffad4ce8e3c0
manager:jhubbard
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
# setHostNameInCertificate Method (SQLServerDataSource)
  Sets the host name to be used in validating the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Secure Sockets Layer \(SSL\) certificate.  
  
## Syntax  
  
```  
  
public void setHostNameInCertificate(java.lang.String hostNameInCertificate)  
```  
  
#### Parameters  
 *hostNameInCertificate*  
  
 A **String** that contains the host name.  
  
## Remarks  
 The hostNameInCertificate value is used to validate the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] SSL certificate when the communication layer is encrypted by using SSL. The default value is null.  
  
 If the hostNameInCertificate property is set to null or unspecified, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] will use the serverName property value to validate against the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] SSL certificate. If the hostNameInCertificate property is set to a string or an empty string "", the driver will use that value to validate the server SSL certificate.  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  