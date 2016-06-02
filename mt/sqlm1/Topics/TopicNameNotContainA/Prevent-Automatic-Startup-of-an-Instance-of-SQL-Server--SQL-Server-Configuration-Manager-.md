---
title: Prevent Automatic Startup of an Instance of SQL Server (SQL Server Configuration Manager)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 782663cf-f3d7-4cc6-b621-21e4550f0322
---
# Prevent Automatic Startup of an Instance of SQL Server (SQL Server Configuration Manager)
  This topic describes how prevent an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] from starting automatically in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using SQL Server Configuration Manager. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is normally configured to start automatically. You can change that by setting the start mode for the instance to manual.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Configuration Manager  
  
#### To prevent automatic startup of an instance of SQL Server  
  
1.  On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../Token\Other/ssCurrentUI_md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.  
  
    > [!NOTE]  
    >  Because [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager is a snap\-in for the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Management Console program and not a stand\-alone program, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager does not appear as an application in newer versions of Windows.  
    >   
    >  -   **Windows 10**:  
    >          To open [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, on the **Start Page**, type SQLServerManager13.msc \(for [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)]\). For previous versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] replace 13 with a smaller number. Clicking SQLServerManager13.msc opens the Configuration Manager. To pin the Configuration Manager to the Start Page or Task Bar, right\-click SQLServerManager13.msc, and then click **Open file location**. In the Windows File Explorer, right\-click SQLServerManager13.msc, and then click **Pin to Start** or **Pin to taskbar**.  
    > -   **Windows 8**:  
    >          To open [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager\<version\>.msc** such as **SQLServerManager13.msc**, and then press **Enter**.  
  
2.  In SQL Server Configuration Manager, expand **Services**, and then click **SQL Server**.  
  
3.  In the details pane, right\-click **MSSQLServer**, and then click **Properties.**  
  
4.  In the **SQL Server \<***instancename***\> Properties** dialog box, in the **Properties** box, set the value of **Start Mode** to **Manual**.  
  
5.  Click **OK** to close the **SQL Server \<***instancename***\> Properties** dialog box, and then close [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager.  
  
## See Also  
 [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../Topics\TopicNameNotContainA/Start,-Stop,-Pause,-Resume,-Restart-the-Database-Engine,-SQL-Server-Agent,-or-SQL-Server-Browser-Service.md)  
  
  