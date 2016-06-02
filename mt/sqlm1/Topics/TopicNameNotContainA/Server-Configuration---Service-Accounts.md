---
title: Server Configuration - Service Accounts
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c283702d-ab20-4bfa-9272-f0c53c31cb9f
---
# Server Configuration - Service Accounts
  Use the Server Configuration page of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Installation Wizard to assign login accounts to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] services. The actual services configured on this page depend on the features you have selected to install.  
  
 Startup accounts used to start and run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] can be  domain user accounts, local user accounts, managed service accounts, virtual accounts, or built\-in system accounts.  
  
## Options  
 You can assign the same login account to all [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] services, or you can configure each service account individually. You can also specify whether services start automatically, are started manually, or are disabled. The default account is recommended for most installations.  
  
 On Windows 7 and [!INCLUDE[nextref_longhorn](../../Token\Other/nextref_longhorn_md.md)] R2 most accounts default to a virtual account.  
  
 If you configure services to use domain accounts, [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] recommends that you configure service accounts individually to provide least privileges for each service, where [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] services are granted the minimum permissions they need to complete their tasks. For more information including descriptions of the types of accounts, see [Configure Windows Service Accounts and Permissions](../../Topics\TopicNameNotContainA/Configure-Windows-Service-Accounts-and-Permissions.md).  
  
 **Configure [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service accounts individually \(recommended\)**  
 Use the grid to provision each [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service with a logon user name and password, and to set the startup type for the service. You can use built\-in system accounts, a local account, local group, domain group, or domain user accounts for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] services.  
  
 Select any of the following services to customize its settings.  
  
|Select this service|To configure authentication settings for|Details|  
|-------------------------|----------------------------------------------|-------------|  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent|The service that executes jobs, monitors, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], and allows automation of administrative tasks.|There is no default logon account for this service.<br /><br /> The default startup type is Manual.|  
|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]||The default startup type is Automatic.|  
|[!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]|For SharePoint integrated mode, you must specify a Windows domain user account. The account you specify is used for the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] service. The account you specify for the current instance must also be used for any additional [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instances that you subsequently add to the same farm.|The default startup type is Automatic.|  
|[!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]|Service accounts are used to configure a report server database connection. Choose the built\-in network service if you want to use default authentication settings. If you specify a domain user account, be sure to register a service principle name \(SPN\) for it if you are using Windows Authentication on the report server. For more information, see [Configure Windows Authentication on the Report Server](../../Topics\TopicNameNotContainA/Configure-Windows-Authentication-on-the-Report-Server.md).|The default startup type is Automatic.|  
|[!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]|[!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] is a set of graphical tools and programmable objects for moving, copying, and transforming data.|The default startup type is Automatic.|  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Distributed Replay Client|The service account used for the Distributed Replay client service.<br /><br /> Provide an account in which to run the Distributed Replay client service. This account should be different from the account that you use for the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service.|The default startup type is Manual.|  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Distributed Replay Controller|The service account used for the Distributed Replay controller service.<br /><br /> Provide an account in which to run the Distributed Replay controller service. This account should be different from the account that you use for the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service.|The default startup type is Manual.|  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Full\-text Filter Daemon Launcher|The service that creates the fdhost.exe processes. This is required to host the word breakers and filters that process textual data for full\-text indexing.|If you provide a domain account in which to run the FDHOST Launcher service, we highly recommend that you use a low privilege account. This account should be different from the account that you use for the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service.|  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser is the name resolution service that provides [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] connection information to client computers. This service is shared across multiple [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] instances.<br /><br /> The default logon account is NT Authority\\Local service and cannot be changed during [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup. You can change the account after the setup has been completed.|If the startup type is not specified during setup, it is determined as follows:<br /><br /> [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser is set to Automatic and running in the installation scenarios described below:<br /><br /> \-<br />                            [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster instance<br /><br /> \-Named instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] where TCP or NP is enabled<br /><br /> \-Named instance of Analysis Server and is not clustered<br /><br /> If none of the above scenarios apply, and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser is already installed, the current state of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser will be maintained.<br /><br /> The startup type is set to Disabled and stopped if there is not an existing instance of an older [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] version prior to the installation.|  
  
 Select the **Grant Perform Volume Maintenance Task privilege to SQL Server Database Engine Service** check box to enable instant file initialization for SQL Server data files. For security and performance considerations see [Database Instant File Initialization](../../Topics\TopicNameNotContainA/Database-Instant-File-Initialization.md).  
  
## See Also  
 [Security Considerations for a SQL Server Installation](../../Topics\TopicNameContainA/Security-Considerations-for-a-SQL-Server-Installation.md)  
  
  