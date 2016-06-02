---
title: Options (Query Results/Dependency Services Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dd7f6c31-7d7f-4972-854a-1419a2826dca
---
# Options (Query Results/Dependency Services Page)
  Use this page to specify the server to connect for Dependency Services. Dependency Services enables you to extract information about dependencies between [!INCLUDE[ssISnoversion](../../../Token\Other/ssISnoversion_md.md)] and [!INCLUDE[ssNoVersion](../../../Token\Other/ssNoVersion_md.md)] objects stored on different servers. You view object dependencies by using the **Object Dependencies** dialog box in [!INCLUDE[ssNoVersion](../../../Token\Other/ssNoVersion_md.md)][!INCLUDE[ssManStudio](../../../Token\Other/ssManStudio_md.md)].  
  
 **What do you want to do?**  
  
1.  [Open the Options (Query Results/Dependency Services Page) Dialog Box](#open_dialog)  
  
2.  [Configure the Options](#options)  
  
##  <a name="open_dialog"></a> Open the Options \(Query Results\/Dependency Services Page\) Dialog Box  
  
1.  In [!INCLUDE[ssNoVersion](../../../Token\Other/ssNoVersion_md.md)][!INCLUDE[ssManStudio](../../../Token\Other/ssManStudio_md.md)], click **Options** on the **Tools** menu.  
  
2.  Expand **Query Results**, and then click **Dependency Services**.  
  
##  <a name="options"></a> Configure the Options  
  
### Options  
 **Dependency Services server**  
 Specify the server that Dependency Services is installed on.  
  
 **Authentication**  
 Select Windows Authentication to log on using a Microsoft Windows user account, or select SQL Server Authentication.  
  
 When a user connects with a specified login name and password from a non\-trusted connection, SQL Server performs the authentication by checking to see if a SQL Server login account has been set up and if the specified password matches the one previously recorded. If SQL Server cannot find the login account, authentication fails, and the user receives an error message.  
  
 **User name**  
 If using SQL Server Authentication, provide a user name.  
  
 **Password**  
 If using SQL Server Authentication, provide a password.  
  
 **Test**  
 Click to test the connection.  
  
  