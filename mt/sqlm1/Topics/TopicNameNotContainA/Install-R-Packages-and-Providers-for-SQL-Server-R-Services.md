---
title: Install R Packages and Providers for SQL Server R Services
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 81134591-e5a1-47c1-8260-8540bace03cf
robots: noindex,nofollow
---
# Install R Packages and Providers for SQL Server R Services
  To use [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] RC0 or earlier, you must install the following R components after you have installed [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]:  
  
-   **Microsoft R Open**  
  
     A distribution of the open\-source R language that works with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. This distribution includes a recent release of the R runtime and core packages and is required for using [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)].  
  
-   **Revolution R Enterprise**  
  
     This download includes the SQL connectivity tools and enhanced R packages provided by Revolution Analytics. The download includes connectivity optimizations for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
## Requirements  
  
-   [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] requires [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] CTP3 or later.  
  
-   [!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)] has been especially designed to work with [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] and [!INCLUDE[rsql_rre-noversion](../../Token\Other/rsql_rre-noversion_md.md)]. You **cannot** use a different distribution of R 3.2.2; you  must  download and install the distribution provided by [!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)].  
  
-   If you previously installed any other versions of the Revolution Analytics tools, you must uninstall them first and then install these components.  
  
     Be sure to uninstall [!INCLUDE[rsql_rre-noversion](../../Token\Other/rsql_rre-noversion_md.md)]**before** uninstalling [!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)] \(the opposite of installation order\).  
  
-   You must be logged in with administrative privileges to run the installers for [!INCLUDE[rsql_rre-noversion](../../Token\Other/rsql_rre-noversion_md.md)] and [!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)].  
  
-   Approximately 450MB free disk space is required for a full install of [!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)] and [!INCLUDE[rsql_rre-noversion](../../Token\Other/rsql_rre-noversion_md.md)].  
  
-   We recommend that you have at least 4GB of RAM.  
  
-   You must install to a local drive on the computer. Installing to a network drive is not supported.  
  
-   Before running these installers, close any other programs running on the system. You might need to temporarily disable any antivirus software you may have running.  
  
## 1. Install Microsoft R Open  
 **[!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)]**  includes a distribution of the R runtime, together with several open source R packages that are commonly used for data science tasks.  
  
1.  Determine the version of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] where you are installing R, or the version on the server to which you will be connecting.  
  
2.  Refer to the [Compatibility Chart](#bkmk_CompatibilityChart) to get the link to the appropriate release of [!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)].  
  
3.  Follow the on\-screen prompts to install [!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)], as well as any additional components that are required by [!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)].  
  
4.  Optionally, you can download the modified GPL\/LGPL  source code \([rre\-gpl\-src.7.5.0.tar.gz](http://go.microsoft.com/fwlink/?LinkId=690702), approximately  131.4MB\) from the repository on GitHub. This is made available in compliance with the GNU General Public License, but is not required to install or use [!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)] or [!INCLUDE[rsql_rre-noversion](../../Token\Other/rsql_rre-noversion_md.md)].  
  
## 2. Install Revolution Enterprise  
 [!INCLUDE[rsql_rre-noversion](../../Token\Other/rsql_rre-noversion_md.md)] is a platform for scaling R in the enterprise that includes enhanced R packages and R functions. [!INCLUDE[rsql_rre-noversion](../../Token\Other/rsql_rre-noversion_md.md)] also includes the Intel Math Libraries, and  libraries for building your own parallel machine learning algorithms in R.  
  
 You must install these components on the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance that will be running R jobs, and on each data science workstation that you use to connect to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance.  
  
> [!NOTE]  
>  If you previously installed any other versions of the Revolution Analytics tools, you must uninstall them first and then install these components.  
  
1.  Refer to the [Compatibility Chart](#bkmk_CompatibilityChart) to get the link to the appropriate release of [!INCLUDE[rsql_rre-noversion](../../Token\Other/rsql_rre-noversion_md.md)].  
  
     For CTP 3.0, 3.1, 3.2 and 3.3, two downloads of [!INCLUDE[rsql_rre-noversion](../../Token\Other/rsql_rre-noversion_md.md)] were provided  
  
    -   The  full version included all connectivity components and the Revolution Enterprise development tools.  
  
    -   The lightweight version does not include tools and is recommended for installation on the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] computer.  
  
     If in doubt, install the lightweight version.  
  
2.  When download is complete, run the setup wizard and follow the on\-screen prompts. The setup wizard will install additional required components as needed.  
  
> [!NOTE]  
>  To enable the use of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] on [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], you must perform some additional configuration of the server by running a script.  
>   
>  For more information, see [Post-Installation Server Configuration &#40;SQL Server R Services&#41;](../Topic/Post-Installation%20Server%20Configuration%20\(SQL%20Server%20R%20Services\).md).  
  
##  <a name="bkmk_CompatibilityChart"></a> Compatibility Chart  
 The version of [!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)] and [!INCLUDE[rsql_rre-noversion](../../Token\Other/rsql_rre-noversion_md.md)] that you install must be compatible with the version of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] that you will connect to.  
  
 For example, if you installed [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] CTP 3.0, to enable use of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)], you must install a version of [!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)] and [!INCLUDE[rsql_rre-noversion](../../Token\Other/rsql_rre-noversion_md.md)] that is compatible with the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] build. Moreover, you must ensure that all data science clients that connect to the  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance also install  the compatible  versions of [!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)] and [!INCLUDE[rsql_rre-noversion](../../Token\Other/rsql_rre-noversion_md.md)].  
  
||||  
|-|-|-|  
|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]|[!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)]|[!INCLUDE[rsql_rre-noversion](../../Token\Other/rsql_rre-noversion_md.md)]|  
|CTP 3.0<br /><br /> CTP 3.1<br /><br /> CTP 3.2<br /><br /> CTP 3.3|**File name:** RRO\-3.2.2\-for\-RRE\-7.5.0\-Windows.exe<br /><br /> Download page with instructions: [Revolution R Open 3.2.2 for Revolution R Enterprise 7.5.0](https://www.microsoft.com/download/details.aspx?id=49525).|**Server**<br /><br /> File name: Revolution\-R\-Enterprise\-Node\-SQL\-7.5.0\-Windows.exe<br /><br /> Download page with instructions: [Revolution R Enterprise 7.5.0 Server \(RRE\-7.5.0\)](https://www.microsoft.com/download/details.aspx?id=49505)<br /><br /> **Client**<br /><br /> File name: Revolution\-R\-Enterprise\-SQL\-7.5.0\-Windows.exe<br /><br /> Download page with instructions:  [Revolution R Enterprise 7.5.0 Client \(RRE\-7.5.0\)](https://www.microsoft.com/download/details.aspx?id=50351)|  
|RC0<br /><br /> \(13.0.1100.288\)|Continue to use previous version|Continue to use previous version|  
|RC1<br /><br /> \(13.0.1100.242\)|Download page with instructions: [Microsoft R Open 3.2.2 for Revolution R Enterprise 8.0.1](http://go.microsoft.com/fwlink/?LinkID=723836&clcid=0x409)|Download page with instructions: [Revolution R Enterprise 8.0 \(RRE\-8.0.1\)](http://go.microsoft.com/fwlink/?LinkID=724391&clcid=0x409)|  
  
## Next Step  
 [Post-Installation Server Configuration &#40;SQL Server R Services&#41;](../Topic/Post-Installation%20Server%20Configuration%20\(SQL%20Server%20R%20Services\).md)  
  
## See Also  
 [Installing Previous Versions of SQL Server R Services](../../Topics\TopicNameNotContainA/Installing-Previous-Versions-of-SQL-Server-R-Services.md)   
 [SQL Server R Services Features and Tasks](../../Topics\TopicNameNotContainA/SQL-Server-R-Services-Features-and-Tasks.md)  
  
  