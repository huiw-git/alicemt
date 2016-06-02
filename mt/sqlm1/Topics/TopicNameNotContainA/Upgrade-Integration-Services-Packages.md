---
title: Upgrade Integration Services Packages
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68dbdf81-032c-4a73-99f6-41420e053980
---
# Upgrade Integration Services Packages
  When you upgrade an instance of [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] to the current release of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], your existing [!INCLUDE[ssISversion10](../../Token\Other/ssISversion10_md.md)] packages are not automatically upgraded to the package format that the current release [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)][!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] uses. You will have to select an upgrade method and manually upgrade your packages.  
  
 For information on upgrading packages when you convert a project to the project deployment model, see [Deploy Projects to Integration Services Server](../../Topics\TopicNameNotContainA/Deploy-Projects-to-Integration-Services-Server.md).  
  
## Selecting an Upgrade Method  
 You can use various methods to upgrade [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] packages. For some of these methods, the upgrade is only temporary. For others, the upgrade is permanent. The following table describes each of these methods and whether the upgrade is temporary or permanent.  
  
> [!NOTE]  
>  When you run a [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] package using the **dtexec** utility \(dtexec.exe\) that is installed with the current release of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], the temporary package upgrade increases the execution time. The rate of increase in package execution time varies depending on the size of the package. To avoid an increase in the execution time, it is recommended that you upgrade the package before running it.  
  
|Upgrade Method|Type of Upgrade|  
|--------------------|---------------------|  
|Use the **dtexec** utility \(dtexec.exe\) that is installed with the current release of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to run a [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] package.<br /><br /> For more information, see [dtexec Utility](../../Topics\TopicNameNotContainA/dtexec-Utility.md).|The package upgrade is temporary.<br /><br /> The changes cannot be saved.|  
|Open a [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] package file in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)].|The package upgrade is permanent if you save the package; otherwise, it is temporary if you do not save the package.|  
|Add a [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] package to an existing project in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)].|The package upgrade is permanent.|  
|Open a [!INCLUDE[ssISversion10](../../Token\Other/ssISversion10_md.md)] or later project file in [!INCLUDE[vsprvs](../../Token\Other/vsprvs_md.md)], and then use the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Upgrade Wizard to upgrade multiple packages in the project.<br /><br /> For more information, see [Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard](../../Topics\TopicNameNotContainA/Upgrade-Integration-Services-Packages-Using-the-SSIS-Package-Upgrade-Wizard.md) and [SSIS Package Upgrade Wizard F1 Help](../../Topics\TopicNameNotContainA/SSIS-Package-Upgrade-Wizard-F1-Help.md).|The package upgrade is permanent.|  
|Use the [Upgrade](assetId:///M:Microsoft.SqlServer.Dts.Runtime.Application.Upgrade(System.Collections.Generic.IEnumerable{Microsoft.SqlServer.Dts.Runtime.UpgradePackageInfo},Microsoft.SqlServer.Dts.Runtime.StorageInfo,Microsoft.SqlServer.Dts.Runtime.StorageInfo,Microsoft.SqlServer.Dts.Runtime.BatchUpgradeOptions,Microsoft.SqlServer.Dts.Runtime.IDTSEvents)) method to upgrade one or more [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages.|The package upgrade is permanent.|  
  
## Custom Applications and Custom Components  
 [!INCLUDE[ssISversion2005](../../Token\Other/ssISversion2005_md.md)] custom components will not work with the current release of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)][!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)].  
  
 You can use the current release of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)][!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] tools to run and manage packages that include [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)][!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] custom components. We added four binding redirection rules to the following files to help redirect the runtime assemblies from version 10.0.0.0 \([!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)]\), version 11.0.0.0 \([!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)]\), or version 12.0.0.0 \([!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)]\) to version 13.0.0.0 \([!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]\).  
  
-   DTExec.exe.config  
  
-   dtshost.exe.config  
  
-   DTSWizard.exe.config  
  
-   DTUtil.exe.config  
  
-   DTExecUI.exe.config  
  
 To use [!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)] to design packages that include [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] custom components, you need to modify the devenv.exe.config file that is located at *\<drive\>*:\\Program Files\\Microsoft Visual Studio 10.0\\Common7\\IDE.  
  
 To use these packages with customer applications that are built with the runtime for [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], include redirection rules in the configuration section of the \*.exe.config file for the executable. The rules redirect the runtime assemblies to version 13.0.0.0 \([!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]\). For more information about assembly version redirection, see [\<assemblyBinding\> Element for \<runtime\>](http://msdn.microsoft.com/library/twy1dw1e.aspx).  
  
### Locating the Assemblies  
 In [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] assemblies were upgraded to .NET 4.0. There is a separate global assembly cache for .NET 4, located in *\<drive\>*:\\Windows\\Microsoft.NET\\assembly. You can find all of the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] assemblies under this path, usually in the GAC\_MSIL folder.  
  
 As in previous versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], the core [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] extensibility .dll files are also located at *\<drive\>*:\\Program Files\\Microsoft SQL Server\\130\\SDK\\Assemblies.  
  
## Understanding SQL Server Package Upgrade Results  
 During the package upgrade process, most components and features in [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] packages convert seamlessly to their counterparts in the current release of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. However, there are several components and features that either will not be upgraded or have upgrade results of which you should be aware. The following table identifies these components and features.  
  
> [!NOTE]  
>  To identify which packages have the issues listed in this table, run Upgrade Advisor.  
  
|Component or Feature|Upgrade Results|  
|--------------------------|---------------------|  
|Connection strings|For [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] packages, the names of certain providers have changed and require different values in the connection strings. To update the connection strings, use one of the following procedures:<br /><br /> Use the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Upgrade Wizard to upgrade the package, and select the **Update connection strings to use new provider names** option.<br /><br /> In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], on the General page of the Options dialog box, select the **Update connection strings to use new provider names** option. For more information about this option, see [General Page](../../Topics\TopicNameNotContainA/General-Page.md).<br /><br /> In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the package and manually change the text of the ConnectionString property.<br /><br /> Note: You cannot use the previous procedures to update a connection string when the connection string is stored in either a configuration file or a data source file, or when an expression sets the **ConnectionString** property. To update the connection string in these cases, you must manually update the file or the expression.<br /><br /> For more information about data sources, see [Data Sources](../../Topics\TopicNameNotContainA/Data-Sources.md).|  
  
### Scripts that Depend on ADODB.dll  
 Script Task and Script Component scripts that explicitly reference ADODB.dll may not upgrade or run on machines without [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] installed. In order to upgrade these Script Task or Script Component scripts, it is recommended that you remove the dependency on ADODB.dll.  Ado.Net is the recommended alternative for managed code such as VB and C\# scripts.  
  
  