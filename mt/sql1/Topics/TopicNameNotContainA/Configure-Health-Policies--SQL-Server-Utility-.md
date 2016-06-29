---
title: Configure Health Policies (SQL Server Utility)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 030aac3b-8901-4c41-91ed-aba96420276c
---
# Configure Health Policies (SQL Server Utility)
  Use the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Utility dashboard in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/includes/ssManStudioFull_md.md)] to view [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Utility resource parameters for managed instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] and data-tier applications. For more information, see [SQL Server Utility Features and Tasks](../../Topics/TopicNameNotContainA/SQL-Server-Utility-Features-and-Tasks.md).  
  
 To view [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Utility health policy results, connect to a utility control point from [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/includes/ssManStudio_md.md)]. For more information, see [Use Utility Explorer to Manage the SQL Server Utility](../../Topics/TopicNameNotContainA/Use-Utility-Explorer-to-Manage-the-SQL-Server-Utility.md).  
  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Utility health policies can be configured for data-tier applications and managed instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)]. Health policies can be defined globally for all data-tier applications and managed instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] in the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Utility, or they can be defined individually for each data-tier application and for each managed instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] in the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Utility.  
  
## Monitoring Policies for Data-tier Applications  
 Overutilization and underutilization policies for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] data-tier applications are as follows:  
  
-   Data-tier application processor utilization.  
  
-   Data-tier application file space for database files.  
  
-   Data-tier application file space for storage volumes.  
  
-   Computer processor utilization.  
  
> [!NOTE]  
>  Storage volume and processor utilization are read-only policies for data-tier applications.  
  
 For more information about viewing or changing global monitoring policies for data-tier applications, see [Utility Administration &#40;SQL Server Utility&#41;](../../Topics/TopicNameNotContainA/Utility-Administration--SQL-Server-Utility-.md).  
  
 For more information about viewing or changing monitoring policies for individual data-tier applications, see [Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../Topics/TopicNameNotContainA/Deployed-Data-tier-Application-Details--SQL-Server-Utility-.md).  
  
## Monitoring Policies for Managed Instances of SQL Server  
 Overutilization and underutilization policies for managed instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] are as follows:  
  
-   [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] instance processor utilization.  
  
-   [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] instance file space for database files.  
  
-   [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] instance file space for storage volumes.  
  
-   Computer processor utilization.  
  
 For more information about viewing or changing global monitoring policies for managed instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)], see [Utility Administration &#40;SQL Server Utility&#41;](../../Topics/TopicNameNotContainA/Utility-Administration--SQL-Server-Utility-.md).  
  
 For more information about viewing or changing monitoring policies for individual managed instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)], see [Managed Instance Details &#40;SQL Server Utility&#41;](../../Topics/TopicNameNotContainA/Managed-Instance-Details--SQL-Server-Utility-.md).  
  
## See Also  
 [SQL Server Utility Features and Tasks](../../Topics/TopicNameNotContainA/SQL-Server-Utility-Features-and-Tasks.md)   
 [Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../../Topics/TopicNameNotContainA/Reduce-Noise-in-CPU-Utilization-Policies--SQL-Server-Utility-.md)  
  
  