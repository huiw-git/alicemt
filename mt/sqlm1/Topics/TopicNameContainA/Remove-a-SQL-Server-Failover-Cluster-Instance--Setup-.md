---
title: Remove a SQL Server Failover Cluster Instance (Setup)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bf63353b-69cf-4c5c-98ea-7b151e36537f
---
# Remove a SQL Server Failover Cluster Instance (Setup)
  Use this procedure to uninstall a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover clustered instance.  
  
> [!IMPORTANT]  
>  To update or remove a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster, you must be a local administrator with permission to login as a service on all nodes of the failover cluster.  
  
 **Before you begin**  
  
 Consider the following important points before you uninstall a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster:  
  
-   If [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Native Client is uninstalled by accident, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] resources will fail to start. To reinstall [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Native Client, run the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup program to install [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] prerequisites.  
  
-   If you uninstall a failover cluster that has more than one SQL IP cluster resource, you must remove the additional SQL IP resources using cluster administrator.  
  
 For information about command prompt syntax, see [Install SQL Server 2016 from the Command Prompt](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-from-the-Command-Prompt.md).  
  
### To uninstall a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster  
  
1.  To uninstall a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster, use the Remove Node functionality provided by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup to remove each node individually. For more information, see [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](../Topic/Add%20or%20Remove%20Nodes%20in%20a%20SQL%20Server%20Failover%20Cluster%20\(Setup\).md).  
  
## See Also  
 [View and Read SQL Server Setup Log Files](../../Topics\TopicNameNotContainA/View-and-Read-SQL-Server-Setup-Log-Files.md)  
  
  