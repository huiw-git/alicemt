---
title: "getEncrypt Method (SQLServerDataSource)"
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
  - getEncrypt Method (SQLServerDataSource)
apilocation: 
  - getEncrypt Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 1cdb12dd-6e6f-4bbd-8f5f-9e630f3ee2c9
caps.latest.revision: 19
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
# getEncrypt Method (SQLServerDataSource)
  Returns a **Boolean** value that indicates if the encrypt property is enabled.  
  
## Syntax  
  
```  
  
public boolean getEncypt()  
```  
  
## Return Value  
 **true** if encrypt is enabled. Otherwise, **false**.  
  
## Remarks  
 If the encrypt property is set to **true**, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] ensures that [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] uses SSL encryption for all data sent between the client and the server if the server has a certificate installed.  
  
 If the encrypt property is unspecified or set to **false**, the driver will not enforce the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] to support SSL encryption. If the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] instance is not configured to force the SSL encryption, a connection is established without any encryption. If the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] instance is configured to force the SSL encryption, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] will automatically enable SSL encryption when running on properly configured Java Virtual Machine (JVM), or else the connection is terminated and the driver will raise an error. If the encryption property is not set, the [getEncrypt](../content/getEncrypt-Method--SQLServerDataSource-.md) method returns the default value of **false**.  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  