---
title: "FTP Connection Manager"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c4f43455-29ca-44ba-ac7f-ea729b1daf93
caps.latest.revision: 41
caps.handback.revision: 0
manager: jhubbard
---
# FTP Connection Manager
  An FTP connection manager enables a package to connect to a File Transfer Protocol (FTP) server. The FTP task that [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] includes uses this connection manager.  
  
 When you add an FTP connection manager to a package, [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] creates a connection manager that can be resolved as an FTP connection at run time, sets the connection manager properties, and adds the connection manager to the **Connections** collection on the package.  
  
 The **ConnectionManagerType** property of the connection manager is set to **FTP**.  
  
 You can configure the FTP connection manager in the following ways:  
  
-   Specify a server name and server port.  
  
-   Specify anonymous access, or provide a user name and a password for basic authentication.  
  
    > [!IMPORTANT]  
    >  The FTP connection manager supports only anonymous authentication and basic authentication. It does not support Windows Authentication.  
  
-   Set the time-out, number of retries, and the amount of data to copy at a time.  
  
-   Indicate whether the FTP connection manager uses passive or active mode.  
  
 Depending on the configuration of the FTP site to which the FTP connection manager connects, you may need to change the following default values of the connection manager:  
  
-   The server port is set to 21. You should specify the port that the FTP site listens to.  
  
-   The user name is set to "anonymous". You should provide the credentials that the FTP site requires.  
  
## Active/Passive Modes  
 An FTP connection manager can send and receive files using either active mode or passive mode. In active mode, the server initiates the data connection, and in passive mode, the client initiates the data connection.  
  
## Configuration of the FTP Connection Manager  
 You can set properties through [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer or programmatically.  
  
 For information about the properties that you can set in [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer, see [FTP Connection Manager Editor](../../Topics/TopicNameNotContainA/FTP-Connection-Manager-Editor.md).  
  
 For information about configuring a connection manager programmatically, see [ConnectionManager](assetId:///T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager) and [Adding Connections Programmatically](../Topic/Adding%20Connections%20Programmatically.md).  
  
## See Also  
 [FTP Task](../../Topics/TopicNameNotContainA/FTP-Task.md)   
 [Integration Services &#40;SSIS&#41; Connections](../../Topics/TopicNameNotContainA/Integration-Services--SSIS--Connections.md)  
  
  