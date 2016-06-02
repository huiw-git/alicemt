---
title: Select a Package
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92b47a2b-21b5-460a-885d-6cc4bb567249
---
# Select a Package
  Use the **Select a Package** dialog box to specify the package from which the Message Queue task can receive messages.  
  
## Static Options  
 **Location**  
 Specify the location of the package. This property has the options listed in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]|Set the location to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Selecting this value displays the dynamic options, **Server**, **Use Windows Authentication**, **Use SQL Server Authentication**, **User name**, and **Password**.|  
|DTSX file|Set the location to a DTSX file. Selecting this value displays the dynamic option, **File name**.|  
  
## Location Dynamic Options  
  
### Location \= SQL Server  
 **Package name**  
 Select a package that is stored on the specified server.  
  
 **Server**  
 Provide a server name or select a server from the list.  
  
 **Use Windows Authentication**  
 Click to use Windows Authentication.  
  
 **Use SQL Server Authentication**  
 Click to use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication.  
  
 **User name**  
 If using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication, provide a user name to use when logging on to the server.  
  
 **Password**  
 If using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication, provide a password.  
  
### Location \= DTSX file  
 **File name**  
 Provide the path of a package or click the browse button **\(…\)** and locate the package.  
  
## See Also  
 [Message Queue Task](../../Topics\TopicNameNotContainA/Message-Queue-Task.md)  
  
  