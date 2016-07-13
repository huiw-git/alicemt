---
title: Validating User Input
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8aa867b0-e6f0-49eb-93d3-817ae2ed8f77
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
# Validating User Input
  When you construct an application that accesses data, you should assume all user input to be malicious until proven otherwise. Failure to do this can leave your application vulnerable to attack. One type of attack that can occur is called SQL injection, where malicious code is added to strings that are later passed to an instance of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] to be parsed and run. To avoid this type of attack, you should use stored procedures with parameters where possible, and always validate user input.  
  
 Validating user input in client code is important so that you do not waste round trips to the server. It is equally important to validate parameters to stored procedures on the server to catch input that is not valid and that bypasses client\-side validation.  
  
 For more information about SQL injection and how to avoid it, see "SQL Injection" in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Books Online. For more information about validating stored procedure parameters, see "Stored Procedures \([!INCLUDE[ssDE](../content/includes/ssDE_md.md)]\)" and subordinate topics in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Books Online.  
  
## See Also  
 [Securing JDBC Driver Applications](../content/Securing-JDBC-Driver-Applications.md)  
  
  