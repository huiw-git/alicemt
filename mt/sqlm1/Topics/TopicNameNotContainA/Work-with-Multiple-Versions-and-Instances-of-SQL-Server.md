---
title: Work with Multiple Versions and Instances of SQL Server
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 93acefa8-bb41-4ccc-b763-7801f51134e0
---
# Work with Multiple Versions and Instances of SQL Server
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] supports multiple instances of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], and [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] on the same computer. You can also upgrade earlier versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], or install [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] on a computer where earlier [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] versions are already installed. For supported upgrade scenarios, see [Supported Version and Edition Upgrades](../../Topics\TopicNameNotContainA/Supported-Version-and-Edition-Upgrades.md).  
  
## Version Components and Numbering  
 The following concepts are useful in understanding the behavior of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] for side\-by\-side instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
 The standard product version format for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is MM.nn.bbbb.rr where each segment is defined as:  
  
 MM \- Major version  
  
 nn \- Minor version  
  
 bbbb \- Build number  
  
 rr \- Build revision number  
  
 In each major or minor release of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], there is an increment to the version number to differentiate it from earlier versions. This change to the version is used for many purposes. This includes displaying version information in the user interface, controlling how files are replaced during upgrade, applying service packs, and also as a mechanism for functional differentiation between the successive versions.  
  
### Components shared by all versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]  
 Certain components are shared by all instances of all installed versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. When you install different versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] side\-by\-side on the same machine, these components are automatically upgraded to the latest version. Such components are usually uninstalled automatically when the last instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is uninstalled.  
  
 Examples: [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser and Microsoft [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] VSS Writer.  
  
### Components shared across all instances of the same major version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] versions that have the same major version share some components across all instances. If the shared components are selected during upgrade, the existing components are upgraded to the latest version.  
  
 Examples: [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)], [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online.  
  
### Components shared across minor versions  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] versions that have the same major.minor version shared components.  
  
 Example: Setup support files.  
  
### Components specific to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]  
 Some [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] components or services are specific to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. These are also known as instance\-aware. They share the same version as the instance that hosts them, and are used exclusively for that instance.  
  
 Examples: [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], and [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)].  
  
### Components that are independent of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] versions  
 Certain components are installed during [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup, but are independent of the versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. They may be shared across major versions or by all [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] versions.  
  
 Examples: Microsoft Sync Framework, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact.  
  
 For more information about [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact installation, see [Install SQL Server 2016 from the Installation Wizard &#40;Setup&#41;](../Topic/Install%20SQL%20Server%202016%20from%20the%20Installation%20Wizard%20\(Setup\).md). For more information about how to uninstall [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact, see [Uninstall an Existing Instance of SQL Server &#40;Setup&#41;](../Topic/Uninstall%20an%20Existing%20Instance%20of%20SQL%20Server%20\(Setup\).md).  
  
## Using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Side\-By\-Side with Previous Versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]  
 You can install [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] on a computer that is already running instances of an earlier [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] version. If a default instance already exists on the computer, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] must be installed as a named instance.  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] SysPrep does not support side by side installation of prepared instances of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] with earlier versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] on the same computer. For example, you cannot prepare a [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] instance side by side with a prepared instance of [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)]. However, you can install multiple prepared instances of the same major version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] side by side on the same computer. For more information, see [Considerations for Installing SQL Server Using SysPrep](../../Topics\TopicNameNotContainA/Considerations-for-Installing-SQL-Server-Using-SysPrep.md).  
>   
>  [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] cannot be installed side\-by\-side with earlier versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] on a computer that is running Windows Server 2008 R2 Server Core SP1. For more information on Server Core installations, see [Install SQL Server 2016 on Server Core](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-on-Server-Core.md).  
  
 The following table shows side\-by\-side support for [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]:  
  
|Existing instance of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]|Side\-by\-side support|  
|--------------------------------------------------|----------------------------|  
|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] \(64\-bit\) [!INCLUDE[vcprx64](../../Token\Other/vcprx64_md.md)]|[!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] \(32\-bit\)<br /><br /> [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] \(64\-bit\) [!INCLUDE[vcprx64](../../Token\Other/vcprx64_md.md)]<br /><br /> [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] \(32\-bit\)<br /><br /> [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] \(64\-bit\) [!INCLUDE[vcprx64](../../Token\Other/vcprx64_md.md)]<br /><br /> [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] \(32\-bit\)<br /><br /> [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] \(64\-bit\) [!INCLUDE[vcprx64](../../Token\Other/vcprx64_md.md)]<br /><br /> [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] \(32\-bit\)<br /><br /> [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] \(64\-bit\) [!INCLUDE[vcprx64](../../Token\Other/vcprx64_md.md)]<br /><br /> [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] \(32\-bit\)<br /><br /> [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] \(64\-bit\) [!INCLUDE[vcprx64](../../Token\Other/vcprx64_md.md)]|  
  
## Preventing IP Address Conflicts  
 When a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Failover Cluster Instance is installed side\-by\-side with a standalone instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], take care to avoid TCP port number conflicts on the IP addresses. Conflicts usually occur when two instances of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] are both configured to use the default TCP port \(1433\). To avoid conflicts, configure one instance to use a non\-default fixed port. Configuring a fixed port is usually easiest on the standalone instance. Configuring the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] to use different ports will prevent an unexpected IP Address\/TCP port conflict that blocks an instance startup when a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Failover Cluster Instance fails to the standby node  
  
## See Also  
 [Hardware and Software Requirements for Installing SQL Server 2016](../../Topics\TopicNameNotContainA/Hardware-and-Software-Requirements-for-Installing-SQL-Server-2016.md)   
 [Install SQL Server 2016 from the Installation Wizard &#40;Setup&#41;](../Topic/Install%20SQL%20Server%202016%20from%20the%20Installation%20Wizard%20\(Setup\).md)   
 [Supported Version and Edition Upgrades](../../Topics\TopicNameNotContainA/Supported-Version-and-Edition-Upgrades.md)   
 [Upgrade to SQL Server 2016](../../Topics\TopicNameNotContainA/Upgrade-to-SQL-Server-2016.md)   
 [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md)   
 [Backward Compatibility_deleted](../Topic/Backward%20Compatibility_deleted.md)  
  
  