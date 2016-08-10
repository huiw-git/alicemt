---
title: "Install Client Tools on a SQL Server Failover Cluster"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c82d510-9798-46be-bebb-cac9bef56936
caps.latest.revision: 10
caps.handback.revision: 0
manager: jhubbard
---
# Install Client Tools on a SQL Server Failover Cluster
Client tools such as [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] are shared features common across all instances on the same machine. They are backward compatible, with supported [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] versions that can be installed side by side. Only one version of the client tool exists on a node at a time.  
  
 If the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] client tools are installed during setup on first node of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] cluster, they are automatically added to any nodes that may be added later to the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] using Add Node.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Books Online is not automatically added to the additional nodes added to the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] cluster using Add Node. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Books Online can be installed manually on the nodes that you wish to have a local copy of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Books Online.  
  
 If you do not install the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] client tools during the initial installation of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] cluster, you can install it later as described in the procedures below.  
  
## Installation procedures  
  
#### Installing [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Client Tools Using the Setup User Interface  
  
1.  Insert the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] installation media. From the root installation folder, double click Setup.exe. To install from the network share, locate the root folder on the share, and then double-click Setup.exe.  
  
2.  On the **Installation** page, click **New [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] stand-alone installation or add Features to an existing installation**. Do not click **New [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] failover cluster installation**.  
  
3.  The system configuration checker verifies the system state of your computer before Setup will continue.  
  
4.  On the **Installation Type** page, click **Perform a new installation of [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)]**.  
  
5.  On the **Feature Selection** page, select the tools that you want to install and follow through the rest of the steps of the Setup process.  
  
#### Installing [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] client tools at the command prompt  
  
1.  To install [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] client tools and [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Books Online, run the following command: Setup.exe/q/Action=Install /Features=Tools  
  
2.  To install only the basic [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Management tools run the following command: Setup.exe/q/Action=Install Features=SSMS. This will install [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)] support for [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)], [!INCLUDE[ssExpress](../../Topics/TopicNameContainA/tokens/ssExpress_md.md)], sqlcmd utility, and the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Powershell provider.  
  
3.  To install the complete [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Management tools, run the following command: Setup.exe/q/Action=Install /Features=ADV_SSMS. For more information about parameter values for the features, see [Install SQL Server 2016 from the Command Prompt](../../Topics/TopicNameNotContainA/Install-SQL-Server-2016-from-the-Command-Prompt.md).  
  
### Uninstalling [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Client Tools  
 They appear in Add or Remove programs in Control Panel as **[!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)][!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)]**, and can be removed from there. When you use Remove Node to uninstall an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] from the failover cluster, the client components are not uninstalled at the same time.  
  
## See Also  
 [View and Read SQL Server Setup Log Files](../../Topics/TopicNameNotContainA/View-and-Read-SQL-Server-Setup-Log-Files.md)