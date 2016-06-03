---
title: Change the Service Startup Account for SQL Server (SQL Server Configuration Manager)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d721c796-0397-46a7-901b-1a9a3c3fb385
---
# Change the Service Startup Account for SQL Server (SQL Server Configuration Manager)
  This topic describes how to Use the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager to change the start up options of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] services and to change the service accounts that are used by the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]. in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or PowerShell. For more information about how to select an appropriate service account, see [Configure Windows Service Accounts and Permissions](../../Topics\TopicNameNotContainA/Configure-Windows-Service-Accounts-and-Permissions.md).  
  
> [!IMPORTANT]  
>  When you change the service startup account for the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service \(the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]\) must be restarted for the change to take effect. When the service is restarted, all databases associated with that instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] will be unavailable until the service successfully restarts. If you have to change the service startup account of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent, make sure that you do so during regularly scheduled maintenance or when the databases can be taken offline without interrupting daily operations.  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   Clustered servers  
  
     Changing the service account that is used by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent must be performed from the active node of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cluster.  
  
     When running on Windows Server 2008 \(in a non\-default configuration using Domain groups\), changing the service account that is used by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent requires [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager to stop [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] by taking the resource groups offline.  
  
-   SKU Upgrade \([!INCLUDE[ssExpress](../../Token\Other/ssExpress_md.md)] to non\-Express SKU\)  
  
     During [!INCLUDE[ssExpress](../../Token\Other/ssExpress_md.md)] installation, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service is configured to use the Network Service account but disabled. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager can change the account assigned for the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service   but the service cannot be enabled or started. After SKU upgrade from [!INCLUDE[ssExpress](../../Token\Other/ssExpress_md.md)] to non\-Express, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service is not automatically enabled, but can be enabled when needed by using the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager and changing the service start mode to Manual or Automatic.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Configuration Manager  
  
#### To change the SQL Server service startup account  
  
1.  On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../Token\Other/ssCurrentUI_md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.  
  
    > [!NOTE]  
    >  Because [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager is a snap\-in for the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Management Console program and not a stand\-alone program, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager does not appear as an application in newer versions of Windows.  
    >   
    >  -   **Windows 10**:  
    >          To open [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, on the **Start Page**, type SQLServerManager13.msc \(for [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)]\). For previous versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] replace 13 with a smaller number. Clicking SQLServerManager13.msc opens the Configuration Manager. To pin the Configuration Manager to the Start Page or Task Bar, right\-click SQLServerManager13.msc, and then click **Open file location**. In the Windows File Explorer, right\-click SQLServerManager13.msc, and then click **Pin to Start** or **Pin to taskbar**.  
    > -   **Windows 8**:  
    >          To open [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager\<version\>.msc** such as **SQLServerManager13.msc**, and then press **Enter**.  
  
2.  In [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, click **SQL Server Services**.  
  
3.  In the details pane, right\-click the name of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance for which you want to change the service startup account, and then click **Properties**.  
  
4.  In the **SQL Server \<***instancename***\> Properties** dialog box, click the **Log On** tab, and select a **Log on as** account type.  
  
5.  After selecting the new service startup account, click **OK**.  
  
     A message box asks whether you want to restart the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service.  
  
6.  Click **Yes**, and then close [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager.  
  
## See Also  
 [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../Topics\TopicNameNotContainA/Start,-Stop,-Pause,-Resume,-Restart-the-Database-Engine,-SQL-Server-Agent,-or-SQL-Server-Browser-Service.md)   
 [Configure WMI to Show Server Status in SQL Server Tools](../Topic/Configure%20WMI%20to%20Show%20Server%20Status%20in%20SQL%20Server%20Tools.md)  
  
  