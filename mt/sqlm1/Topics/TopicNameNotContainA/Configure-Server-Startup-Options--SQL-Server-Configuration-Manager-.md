---
title: Configure Server Startup Options (SQL Server Configuration Manager)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7a94643c-6460-4baf-bb31-0cb99eaf970d
---
# Configure Server Startup Options (SQL Server Configuration Manager)
  This topic describes how to to configure startup options that will be used every time the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] starts in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager. For a list of startup options, see [Database Engine Service Startup Options](../../Topics\TopicNameNotContainA/Database-Engine-Service-Startup-Options.md).  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
### Limitations and Restrictions  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager writes startup parameters to the registry. They take effect upon the next startup of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
 On a cluster, changes must be made on the active server when [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is online, and will take effect when the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] is restarted. The registry update of the startup options on the other node will occur upon the next failover.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Configuring server startup options is restricted to users who can change the related entries in the registry. This includes the following users.  
  
-   Members of the local administrators group.  
  
-   The domain account that is used by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], if the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] is configured to run under a domain account.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Configuration Manager  
  
#### To configure startup options  
  
1.  Click the **Start** button, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../Token\Other/ssCurrentUI_md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.  
  
    > [!NOTE]  
    >  Because [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager is a snap\-in for the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Management Console program and not a stand\-alone program, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager does not appear as an application in newer versions of Windows.  
    >   
    >  -   **Windows 10**:  
    >          To open [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, on the **Start Page**, type SQLServerManager13.msc \(for [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)]\). For previous versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] replace 13 with a smaller number. Clicking SQLServerManager13.msc opens the Configuration Manager. To pin the Configuration Manager to the Start Page or Task Bar, right\-click SQLServerManager13.msc, and then click **Open file location**. In the Windows File Explorer, right\-click SQLServerManager13.msc, and then click **Pin to Start** or **Pin to taskbar**.  
    > -   **Windows 8**:  
    >          To open [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager\<version\>.msc** such as **SQLServerManager13.msc**, and then press **Enter**.  
  
2.  In [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, click **SQL Server Services**.  
  
3.  In the right pane, right\-click **SQL Server \(***\<instance\_name\>***\)**, and then click **Properties**.  
  
4.  On the **Startup Parameters** tab, in the **Specify a startup parameter** box, type the parameter, and then click **Add**.  
  
     For example, to start in single\-user mode, type **\-m** in the **Specify a startup parameter** box and then click **Add**. \(When you restart [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in single\-user mode, stop the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent. Otherwise, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent might connect first and prevent you from connecting as a second user.\)  
  
5.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
6.  Restart the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
    > [!WARNING]  
    >  After you are finished using single\-user mode, in the Startup Parameters box, select the **\-m** parameter in the **Existing Parameters** box, and then click **Remove**. Restart the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] to restore [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to the typical multi\-user mode.  
  
## See Also  
 [Start SQL Server in Single-User Mode](../../Topics\TopicNameNotContainA/Start-SQL-Server-in-Single-User-Mode.md)   
 [Connect to SQL Server When System Administrators Are Locked Out](../../Topics\TopicNameNotContainA/Connect-to-SQL-Server-When-System-Administrators-Are-Locked-Out.md)   
 [Start, Stop, or Pause the SQL Server Agent Service](../Topic/Start,%20Stop,%20or%20Pause%20the%20SQL%20Server%20Agent%20Service.md)  
  
  