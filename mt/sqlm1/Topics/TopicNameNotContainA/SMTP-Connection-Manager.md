---
title: SMTP Connection Manager
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3795d442-714b-4bbb-9acd-75bf277a468a
---
# SMTP Connection Manager
  An SMTP connection manager enables a package to connect to a Simple Mail Transfer Protocol \(SMTP\) server. The Send Mail task that [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes uses an SMTP connection manager.  
  
 When using Microsoft Exchange as the SMTP server, you may need to configure the SMTP connection manager to use Windows Authentication. Exchange servers may be configured to not allow unauthenticated SMTP connections.  
  
## Configuration the SMTP Connection Manager  
 When you add an SMTP connection manager to a package, [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] creates a connection manager that will resolve to an SMTP connection at run time, sets the connection manager properties, and adds the connection manager to the **Connections** collection on the package. The **ConnectionManagerType** property of the connection manager is set to **SMTP**.  
  
 You can configure an SMTP connection manager in the following ways:  
  
-   Provide a connection string.  
  
-   Specify the name of an SMTP server.  
  
-   Specify the authentication method to use.  
  
    > [!IMPORTANT]  
    >  The SMTP connection manager supports only anonymous authentication and Windows Authentication. It does not support basic authentication.  
  
-   Specify whether to encrypt communication using Secure Sockets Layer \(SSL\) when sending e\-mail messages.  
  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, see [SMTP Connection Manager Editor](../../Topics\TopicNameNotContainA/SMTP-Connection-Manager-Editor.md).  
  
 For information about configuring a connection manager programmatically, see [ConnectionManager](assetId:///T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager) and [Adding Connections Programmatically](../Topic/Adding%20Connections%20Programmatically.md).  
  
  