---
title: Installing Previous Versions of SQL Server R Services
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 48380645-9e72-4744-bebb-1c1fd8a18c43
robots: noindex,nofollow
---
# Installing Previous Versions of SQL Server R Services
    
> [!IMPORTANT]  
>  This page is provided only for backward compatibility, to support customers who are still using earlier releases of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. **We strongly recommend that you install [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Release Candidate 2 or higher**.   For setup instructions, see [Set up SQL Server R Services &#40;In-Database&#41;](../Topic/Set%20up%20SQL%20Server%20R%20Services%20\(In-Database\).md).  
>   
>  RC2 offers an easy, integrated setup experience for all R components., as well as improvements in performance and resource governance for R Services.  
  
 If you have one of the following older versions of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] and want to install [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)], use the instructions in this section.  
  
-   [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] CTP 3.0 through CTP 3.3  
  
-   [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Release Candidate 0 \(RC0\)  
  
 If you installed [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] before CTP 3.0, you must upgrade to at least CTP 3.0 and preferably to Release Candidate 1 \(RC1\).  
  
## I need to set up a server to deploy R solutions and support data scientists  
  
1.  Install **[!INCLUDE[rsql_extensions](../../Token\Other/rsql_extensions_md.md)]**, a new feature in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] that lets the R runtime be called from [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
     You must install this feature on the server to operationalize predictive models. You do **not** need it on a client workstation.  
  
     Instructions: [Install Advanced Analytics Extensions](../../Topics\TopicNameNotContainA/Install-Advanced-Analytics-Extensions.md)  
  
     For other [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] requirements, see [Hardware and Software Requirements for Installing SQL Server 2016](../../Topics\TopicNameNotContainA/Hardware-and-Software-Requirements-for-Installing-SQL-Server-2016.md).  
  
2.  Download and install [!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)]. This download contains a distribution of R provided under the General Public License \(GPL\) that includes the open source R runtime and several core package libraries.  
  
     This distribution is required for using R in [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)]. All client workstations that connect to the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] instance must use the same version of [!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)] to ensure compatibility with [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
     Instructions and download links: [Install R Packages and Providers for SQL Server R Services](../../Topics\TopicNameNotContainA/Install-R-Packages-and-Providers-for-SQL-Server-R-Services.md)  
  
3.  Download and install [!INCLUDE[rsql_rre-noversion](../../Token\Other/rsql_rre-noversion_md.md)].  This download contains a set of enhanced R packages and providers that support high\-performance analytics with [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] and with other data sources.  
  
     These tools are required for using [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)]. All client workstations that connect to the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] instance must use the same version of [!INCLUDE[rsql_rre-noversion](../../Token\Other/rsql_rre-noversion_md.md)] to ensure compatibility with [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
     Instructions and download links: [Install R Packages and Providers for SQL Server R Services](../../Topics\TopicNameNotContainA/Install-R-Packages-and-Providers-for-SQL-Server-R-Services.md)  
  
4.  Run the post\-installation configuration steps.  
  
     Instructions: [Post-Installation Server Configuration &#40;SQL Server R Services&#41;](../Topic/Post-Installation%20Server%20Configuration%20\(SQL%20Server%20R%20Services\).md)  
  
> [!TIP]  
>  Installing on an Azure virtual machine? Some additional steps are required because the [!INCLUDE[rsql_extensions](../../Token\Other/rsql_extensions_md.md)] feature is not enabled by default. For details, see [Upgrade and Installation FAQ &#40;SQL Server R Services&#41;](../Topic/Upgrade%20and%20Installation%20FAQ%20\(SQL%20Server%20R%20Services\).md).  
  
## I need to create a data science workstation  
  
> [!IMPORTANT]  
>  If you intend to connect to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to run R code in the context of the server, or use the RevoScaleR functions from a remote workstation, you must install the version of [!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)] and [!INCLUDE[rsql_rre-noversion](../../Token\Other/rsql_rre-noversion_md.md)] that is compatible with the build of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] that is installed on the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] computer.  
  
1.  Download and install**[!INCLUDE[rsql_rro-noversion](../../Token\Other/rsql_rro-noversion_md.md)]**, a distribution of R provided under the General Public License \(GPL\) that includes the open source R runtime and other libraries. This distribution is required for using R in [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)].  
  
     Instructions and download links: [Install R Packages and Providers for SQL Server R Services](../../Topics\TopicNameNotContainA/Install-R-Packages-and-Providers-for-SQL-Server-R-Services.md)  
  
2.  Download and install **[!INCLUDE[rsql_rre-noversion](../../Token\Other/rsql_rre-noversion_md.md)]**, a set of enhanced R packages and providers that support high\-performance analytics with [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] and with other data sources. These tools are required for using [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)].  
  
     Instructions  and download links: [Install R Packages and Providers for SQL Server R Services](../../Topics\TopicNameNotContainA/Install-R-Packages-and-Providers-for-SQL-Server-R-Services.md)  
  
3.  If you will be using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] as a compute context,  talk to your database administrator about enabling the [!INCLUDE[rsql_extensions](../../Token\Other/rsql_extensions_md.md)] and providing you with access to the instance and any needed databases.  
  
     You can then develop R solutions on the workstation and send the R code to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] as described in [Data Exploration and Predictive Modeling &#40;Tutorial: SQL Server R Services&#41;](../Topic/Data%20Exploration%20and%20Predictive%20Modeling%20\(Tutorial:%20SQL%20Server%20R%20Services\).md).  
  
> [!TIP]  
>  For examples of how you can develop R code and deploy it to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [Data Exploration and Predictive Modeling &#40;Tutorial: SQL Server R Services&#41;](../Topic/Data%20Exploration%20and%20Predictive%20Modeling%20\(Tutorial:%20SQL%20Server%20R%20Services\).md) or [Data Science Deep Dive: Overview &#40;SQL Server R Services&#41;deleted](../Topic/Data%20Science%20Deep%20Dive:%20Overview%20\(SQL%20Server%20R%20Services\)deleted.md).  
  
##  <a name="bkmk_Requirements"></a> Requirements  
 .NET 3.5 is a prerequisite for both client and server installation.   Note that .NET 3.5  is not installed as part of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup.  
  
#### To verify or install .NET 3.5  
  
1.  Open **Control Panel**, select **Programs** \(or **Programs and Features**\), and then click **Turn Windows features on or off**.  
  
2.  Expand the list item for **.NET Framework 3.5** \(which includes .NET 2.0 and 3.0\) and make sure that both of the WCF components are selected. [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
## See Also  
 [Post-Installation Server Configuration &#40;SQL Server R Services&#41;](../Topic/Post-Installation%20Server%20Configuration%20\(SQL%20Server%20R%20Services\).md)  
  
  