---
title: "Use a SQL Server cluster for the System Center Configuration Manager site database"
ms.custom: na
ms.date: 2016-07-22
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: d09a82c6-bbd1-49ca-8ffe-e3ce87b85d33
caps.latest.revision: 10
caps.handback.revision: 0
---
# Use a SQL Server cluster for the System Center Configuration Manager site database

 You can use a SQL Server cluster to host the [!INCLUDE[cm6long_md](../System Center Configuration Manager/itokens/cm6long_md.md)] site database. The site database is the only site system role supported on a Server cluster.  
  
> [!NOTE]  
>  Successful configuration and SQL Server clusters requires you to be comfortable with configuring SQL Server clusters, and relies on documentation and procedures provided in the SQL Server documentation library.  
  
 Use of a cluster can provide failover support and improve the reliability of the site database. However, use of a clustered site database does not provide additional processing or load balancing benefits. In fact, degradation in performance can occur because the site server must find the active node of the SQL Server cluster before it connects to the site database.  
  
 Before you install [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], you must prepare the SQL Server cluster to support [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. (See the prerequisites later in this section).  
  
 During [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Setup, the Volume Shadow Copy Service (VSS) writer installs on each physical computer node of the Microsoft Windows Server cluster to support the **Backup Site Server** maintenance task.  
  
 After the site installs, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] checks for changes to the cluster node each hour and automatically manages any changes that are found that affect [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] component installations (like a node failover or the addition of a new node to the SQL Server cluster).  
  
 ## Supported options for using a SQL Server failover cluster
  
-   Single instance cluster  
  
-   Multiple instance configuration  
  
-   Multiple active nodes  
  
-   Both a named or default instance is supported  
  
 **Prerequisites:**  
  
-   The site database must be remote from the site server. (The cluster cannot include the site system server.)  
  
-   You must add the computer account of the site server to the Local Administrators group of each Server in the cluster.  
  
-   To support Kerberos authentication, **TCP/IP** network communication protocol must be enabled for the network connection of each SQL Server cluster node. **Named pipes** is not required, but can be used to troubleshoot Kerberos authentication issues. The network protocol settings are configured in **SQL Server Configuration Manager** under **SQL Server Network Configuration**.  
  
-   If you use a PKI, see <PKI Certificate Requirements for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]> for specific certificate requirements when you use a SQL Server cluster for the site database.  
  
 **Limitations to consider:**  
  
-   **Installation and configuration:**  
  
    -   Secondary sites cannot use a SQL Server cluster.  
  
    -   The option to specify non-default file locations for the site database is not available when you specify a SQL Server cluster.  
  
-   **SMS Provider:**  
  
    -   It is not supported to install an instance of the SMS Provider on a SQL Server cluster or a computer that runs as a clustered SQL Server node.  
  
-   **Data replication options:**  
  
    -   If you will use **Distributed Views**, you cannot use a SQL Server Cluster to host the site database.  
  
-   **Backup and recovery:**  
  
    -   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not support DPM backup for a SQL Server cluster that uses a named instance, but does support DPM backup on a SQL Server cluster that uses the default instance of SQL Server.  
  
## To prepare a clustered SQL Server instance for the site database  
  
-   Create the virtual SQL Server cluster to host the site database on an existing Windows Server cluster environment. For specific steps to install and configure a SQL Server cluster, see the documentation specific to your version of SQL Server. For example, if you are using SQL Server 2008 R2, see  [Installing a SQL Server 2008 R2 Failover Cluster](http://go.microsoft.com/fwlink/p/?LinkId=240231). If you are using SQL Server 2014, see [SQL Server Failover Cluster Installation](https://technet.microsoft.com/library/hh231721\(v=sql.120\).aspx).  
  
-   On each computer in the SQL Server cluster you can place a file with the name **NO_SMS_ON_DRIVE.SMS** in the root folder of each drive where you do not want [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to install site components. By default,  [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] installs some components on each physical node to support operations such as backup.  
  
-   Add the computer account of the site server to the **Local Administrators** group of each Windows Server cluster node computer.  
  
-   In the virtual SQL Server instance, assign the **sysadmin** SQL Server role to the user account that will run [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Setup.  
  
### To install a new site using a clustered SQL Server  
 To install a site that uses a clustered site database, run [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Setup following your normal process for installing a site with the following alteration:  
  
-   On the **Database Information** page, specify the name of the virtual SQL Server cluster instance that will host the site database.  The virtual instance replaces the name of the computer that runs SQL Server.  
  
    > [!IMPORTANT]  
    >  When you enter the name of the virtual SQL Server cluster instance, do not enter the virtual Windows Server name created by the Windows Server cluster. If you use the virtual Windows Server name the site database installs on the local hard drive of the active Windows Server cluster node. This prevents successful failover if that node fails.  
  

  
## See Also   
[Configure sites and hierarchies](../System Center Configuration Manager/Configure-sites-and-hierarchies-for-System-Center-Configuration-Manager.md)