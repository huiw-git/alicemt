---
title: Install Reporting Services at the Command Prompt
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 048169b3-512c-41e4-895a-0416eff41268
---
# Install Reporting Services at the Command Prompt
  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] supports a command\-line installation from the SQL Server setup program. This topic contains several examples of command\-line installations that are specific to [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]. For a complete description of the command\-line options available for all SQL Server components, see [Install SQL Server 2016 from the Command Prompt](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-from-the-Command-Prompt.md). This topic does not describe command\-line options for the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] add\-in for SharePoint products. For information on command installation of the add\-in, see [Install the add-in using the installation file rsSharePoint.msi](../../Topics\TopicNameNotContainA/Install-or-Uninstall-the-Reporting-Services-Add-in-for-SharePoint.md).  
  
 **[!INCLUDE[applies](../../Token\Other/applies_md.md)]**  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint mode | [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native mode  
  
##  <a name="bkmk_native_mode"></a> Native mode Reporting Services  
  
### RSINSTALLMODE \(Native Mode\)  
 The primary input setting for installing [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] is the **\/RSINSTALLMODE** input setting. The setting has two options: **DefaultNativeMode** and **FilesOnlyMode**  
  
 If the installation includes the SQL Server Database engine, the default RSINSTALLMODE is DefaultNativeMode.If the installation does not include the SQL Server Database engine, the default RSINSTALLMODE is FilesOnlyMode.If you choose DefaultNativeMode but the installation does not include the SQL Server Database engine, the installation automatically changes the RSINSTALLMODE to FilesOnlyMode. For more information on the input settings, see [Install SQL Server 2016 from the Command Prompt](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-from-the-Command-Prompt.md).  
  
### Examples of Native Mode Installation  
 The following example installs the following and configures the accounts for :  
  
-   [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] in native mode.  
  
-   The [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)].  
  
-   SQL Server Agent, which is needed for the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] subscriptions features.  
  
-   [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
```  
Setup.exe /q /IACCEPTSQLSERVERLICENSETERMS /ACTION="install" /ERRORREPORTING=1 /UPDATEENABLED="False" /INSTANCENAME="MSSQLSERVER" /FEATURES="SQLEngine,Adv_SSMS,RS" /RSINSTALLMODE="DefaultNativeMode" /SQLSVCACCOUNT="redmond\sqlcl01" /SQLSVCPASSWORD="Things4everAnother1#GoneAway!1" /AGTSVCACCOUNT="redmond\sqlcl01" /AGTSVCPASSWORD="Things4everAnother1#GoneAway!1" /SQLSYSADMINACCOUNTS="redmond\craigg"  
```  
  
##  <a name="bkmk_sharepoint_mode"></a> SharePoint mode Reporting Services  
  
### RSSHPINSTALLMODE \(SharePoint Mode\)  
 The input setting to install [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] in SharePoint mode is **\/RSSHPINSTALLMODE**. The input setting has one option: SharePointFilesOnlyMode. The option installs all the files needed for SharePoint mode but, configuration is required following installation. The additional configuration steps are completed using SharePoint Central Administration. For more information, see [Install Reporting Services SharePoint Mode for SharePoint 2010](assetId:///47efa72e-1735-4387-8485-f8994fb08c8c).  
  
### Examples of SharePoint Mode Installation  
 The following example installs SQL Server the database engine service and [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] in SharePoint mode as well as the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] add\-in for SharePoint \(RS\_SHPWFE\).  
  
```  
setup /q /ACTION=install /FEATURES=SQL, RS_SHP, RS_SHPWFE,TOOLS /INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /SQLSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /AGTSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE"  
```  
  
 The following example installs only [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint mode.  
  
```  
Setup.exe /q /ACTION="Install" /IACCEPTSQLSERVERLICENSETERMS /FEATURES="RS_SHP" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SECURITYMODE="SQL" /SAPWD="*****" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Name]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="[Account Name]" /UPDATEENABLED="False"  
  
```  
  
### Examples of SharePoint Mode Upgrade  
 The following example upgrades [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint mode. **RSUPGRADEPASSWORD** is the password of the existing Report Server service account. RSUPGRADEPASSWORD is a required field in an upgrade scenario unless the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] service account is a built\-in account.  
  
```  
Setup.exe /q /ACTION="Upgrade" /INSTANCENAME="MSSQLSERVER" /PID="[PID value]" /FTSVCACCOUNT="[DOMAIN\ACCOUNT]" /FTSVCPASSWORD="[ACCOUNTPASSSWORD]" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSUPGRADEPASSWORD="******"  
```  
  
 The following example can be used to upgrade a SharePoint Mode installation that is based on the SharePoint shared service architecture. The example uses switch ALLOWUPGRADEFORSSRSSHAREPOINTMODE. The switch is not needed for upgrading older versions that are not based on the shared service architecture:  
  
-   [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)]  
  
-   [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)]  
  
```  
Setup.exe /q /ACTION="Upgrade" /INSTANCENAME="MSSQLSERVER" /PID="[Your PID Value]" /FTSVCACCOUNT="[ACCOUNT Name]" /FTSVCPASSWORD="****" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /ALLOWUPGRADEFORSSRSSHAREPOINTMODE="True"  
```  
  
## See Also  
 [Install SQL Server 2016 from the Command Prompt](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-from-the-Command-Prompt.md)   
 [SysPrep Parameters](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-from-the-Command-Prompt.md)   
 [Install Power Pivot from the Command Prompt](assetId:///7f1f2b28-c9f5-49ad-934b-02f2fa6b9328)  
  
  