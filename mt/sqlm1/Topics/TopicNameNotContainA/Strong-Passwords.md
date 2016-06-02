---
title: Strong Passwords
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 338548f4-c4d8-47ca-b597-5c9c0f2fa205
---
# Strong Passwords
  Passwords can be the weakest link in a server security deployment. You should always take great care when you select a password. A strong password has the following characteristics:  
  
-   Is at least 8 characters long.  
  
-   Combines letters, numbers, and symbol characters within the password.  
  
-   Is not found in a dictionary.  
  
-   Is not the name of a command.  
  
-   Is not the name of a person.  
  
-   Is not the name of a user.  
  
-   Is not the name of a computer.  
  
-   Is changed regularly.  
  
-   Is significantly different from previous passwords.  
  
 [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] passwords can contain up to 128 characters, including letters, symbols, and digits. Because logins, user names, roles, and passwords are frequently used in [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements, certain symbols must be enclosed by double quotation marks \("\) or square brackets \(\[ \]\). Use these delimiters in [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements when the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login, user, role, or password has the following characteristics:  
  
-   Contains or starts with a space character.  
  
-   Starts with the $ or @ character.  
  
 If used in an OLE DB or ODBC connection string, a login or password must not contain the following characters: \[\] {}\(\) , ; ? \* \! @. These characters are used to either initialize a connection or separate connection values.  
  
## Related Content  
 [Password Policy](../../Topics\TopicNameNotContainA/Password-Policy.md)  
  
  