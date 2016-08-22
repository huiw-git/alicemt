---
title: "Upgrade on-premises infrastructure that supports System Center Configuration Manager"
ms.custom: na
ms.date: 2016-03-11
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 8ca970dd-e71c-404f-9435-d36e773a0db2
caps.latest.revision: 7
caps.handback.revision: 0
---
# Upgrade on-premises infrastructure that supports System Center Configuration Manager
Use the following information to help you upgrade infrastructure that runs [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].  
  
-   [Upgrade site operating system of site systems](#BKMK_SupConfigUpgradeSiteSrv)  
  
-   [Upgrade the operating system of clients](#BKMK_SupConfigUpgradeClient)  
  
-   [Upgrade SQL Server on the site database server](#BKMK_SupConfigUpgradeDBSrv)  
  
##  <a name="BKMK_SupConfigUpgradeSiteSrv"></a> Upgrade site operating system of site systems  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports an in-place upgrade of the operating system of the site server  in the following situations:  
  
-   In-place upgrade to a higher Windows Server service pack as long as the resulting service pack level remains supported by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
-   In-place upgrade from Windows Server 2012 to Windows Server 2012 R2.  
  
-   Configuration Manager sites that run version 1602 or later  support the in-place upgrade of the site servers operating system from  Windows Server 2008 R2 to Windows Server 2012 R2.  
  
    > [!WARNING]  
    >  Before you upgrade to Windows Server 2012 R2, **you must uninstall WSUS 3.2** from the server.  
    >   
    >  For information about this critical step, see the New and changed functionality section  in [Windows Server Update Services Overview](https://technet.microsoft.com/library/hh852345.aspx) in the Windows Server documentation.  
  
     To upgrade a server, you use the Windows Server 2012 R2 upgrade procedures and do not need to run a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site server restore after the upgrade.  For upgrade procedures, see [Upgrade Options for Windows Server 2012 R2](https://technet.microsoft.com/library/dn303416.aspx) in the Windows Server documentation.  
  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not support the following Windows Server upgrade scenarios.  
  
-   Windows Server 2008 to Windows Server 2012 or later.  
  
-   Windows Server 2008 R2 to Windows Server 2012.  
  
##  <a name="BKMK_SupConfigUpgradeClient"></a> Upgrade the operating system of clients  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports an in-place upgrade of the operating system for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients in the following situations:  
  
-   In-place upgrade to a higher Windows service pack as long as the resulting service pack level remains supported by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
-   In-place upgrade of Windows from a supported version to Windows 10. See [Upgrade Windows to the latest version with System Center Configuration Manager](../System Center Configuration Manager/Upgrade-Windows-to-the-latest-version-with-System-Center-Configuration-Manager.md) for more information.  
  
-   Build-to-build servicing upgrades of Windows 10.  See [Manage Windows as a service using System Center Configuration Manager](../System Center Configuration Manager/Manage-Windows-as-a-service-using-System-Center-Configuration-Manager.md) for more information.  
  
##  <a name="BKMK_SupConfigUpgradeDBSrv"></a> Upgrade SQL Server on the site database server  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports an in-place upgrade of SQL Server from a supported version of SQL on the site database server. The following table provides details about the upgrade scenarios supported by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and any requirements for each scenario.  
  
 For information about which versions of SQL Server are supported by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [Support for SQL Server versions for System Center Configuration Manager](../System Center Configuration Manager/Support-for-SQL-Server-versions-for-System-Center-Configuration-Manager.md) .  
  
 For information about which versions of SQL Server are supported for upgrade by SQL Server, see the SQL Server documentation on TechNet:  
  
-   [Upgrade to SQL Server 2014](http://technet.microsoft.com/library/ms143393\(v=sql.120\).aspx)  
  
-   [Upgrade to SQL Server 2012](http://technet.microsoft.com/library/ms143393\(v=sql.110\).aspx)  
  
|Upgrade scenario|More information|  
|----------------------|----------------------|  
|Upgrade the service pack version of SQL Server|[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports the in-place upgrade of SQL Server to a higher service pack as long as the resulting SQL Server service pack level remains supported by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].<br /><br /> When you have multiple [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] sites in a hierarchy, each site can run a different service pack version of SQL Server, and there is no limitation to the order in which sites upgrade the service pack version of SQL Server that is used for the site database.|  
|Upgrade to SQL Server 2012|[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports the in-place upgrade of SQL Server to SQL Server 2012 with the following limitations:<br /><br /> When you upgrade the version of SQL Server that hosts the site database at each site to SQL Server 2012, you must upgrade the SQL Server at sites in the following order:<br /><br /> 1. Upgrade SQL Server at the central administration site first.<br /><br /> 2. Upgrade secondary sites before you upgrade a secondary sites parent primary site.<br /><br /> 3. Upgrade parent primary sites last. This includes both child primary sites that report to a central administration site, and stand-alone primary sites that are the top-level site of a hierarchy.|  
|Upgrade to SQL Server 2014|[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]supports the in-place upgrade of SQL Server to SQL Server 2014 with the following limitations:<br /><br /> When you upgrade the version of SQL Server that hosts the site database at each site to SQL Server 2014, you must upgrade the SQL Server version that is used at sites in the following order:<br /><br /> 1. Upgrade SQL Server at the central administration site first.<br /><br /> 2. Upgrade secondary sites before you upgrade a secondary sites parent primary site.<br /><br /> 3. Upgrade parent primary sites last. This includes both child primary sites that report to a central administration site, and stand-alone primary sites that are the top-level site of a hierarchy.|  
  
### To upgrade SQL Server on the site database server  
  
1.  Stop all [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] services at the site.  
  
2.  Upgrade SQL Server to a supported version.  
  
3.  Restart the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] services.  
  
> [!NOTE]  
>  When you change the SQL Server edition in use at the central administration site from a Standard edition to either a Datacenter or Enterprise edition, the database partition that limits the number of clients the hierarchy supports does not change.