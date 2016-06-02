---
title: Run SQL Server With or Without a Network
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 54eac961-5c7a-4481-982d-f93a64b5c2f4
---
# Run SQL Server With or Without a Network
  [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] can run on a network, or it can function without a network.  
  
## Running SQL Server on a Network  
 For [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to communicate over a network, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service must be running. By default, [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows automatically starts the built\-in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service. To find out whether the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service has been started, at the command prompt, type the following:  
  
 **net start**  
  
 If the services associated with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] have been started, the following services will appear in the **net start** output:  
  
-   Analysis Services \(MSSQLSERVER\)  
  
-   SQL Server \(MSSQLSERVER\)  
  
-   SQL Server Agent \(MSSQLSERVER\)  
  
## Running SQL Server Without a Network  
 When running an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] without a network, you do not need to start the built\-in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service. Because [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], SQL Server Configuration Manager, and the **net start** and **net stop** commands are functional even without a network, the procedures for starting and stopping an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] are identical for a network or stand\-alone operation.  
  
 When connecting to an instance of a stand\-alone [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] from a local client such as **sqlcmd**, you bypass the network and connect directly to the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] by using a local pipe. The difference between a local pipe and a network pipe is whether you are using a network. Both local and network pipes establish a connection with an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] by using the standard pipe \(\\\\.\\pipe\\sql\\query\), unless otherwise directed.  
  
 When you connect to an instance of a local [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] without specifying a server name, you are using a local pipe. When you connect to an instance of a local [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and specify a server name explicitly, you are using either a network pipe or another network interprocess communication \(IPC\) mechanism, such as Internetwork Packet Exchange\/Sequenced Packet Exchange \(IPX\/SPX\) \(assuming you have configured [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to use multiple networks\). Because a stand\-alone [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] does not support network pipes, you must omit the unnecessary **\/***\<Server\_name\>* argument when connecting to the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] from a client. For example, to connect to a stand\-alone instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] from **osql**, type:  
  
 **osql \/Usa \/P** *\<saPassword\>*  
  
  