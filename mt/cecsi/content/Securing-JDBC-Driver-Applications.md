---
title: Securing JDBC Driver Applications
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 90724ec6-a9cb-43ef-903e-793f89410bc0
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
# Securing JDBC Driver Applications
  Enhancing the security of a [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] application involves more than avoiding common coding pitfalls. An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data. It is important to understand all aspects of security, from the process of threat modeling during the design phase of your application to its eventual deployment, and continuing through its ongoing maintenance.  
  
 The topics in this section describe some common security concerns including connection strings, validating user input, and general application security.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Securing Connection Strings](../content/Securing-Connection-Strings.md)|Describes techniques to help protect information used to connect to a data source.|  
|[Validating User Input](../content/Validating-User-Input.md)|Describes techniques to validate user input.|  
|[Application Security](../content/Application-Security.md)|Describes how to use Java policy permissions to help secure a JDBC driver application.|  
|[Using SSL Encryption](../content/Using-SSL-Encryption.md)|Describes how to establish a secure communication channel with a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database using Secure Sockets Layer \(SSL\).|  
  
## See Also  
 [Overview of the JDBC Driver](../content/Overview-of-the-JDBC-Driver.md)  
  
  