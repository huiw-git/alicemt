---
title: Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (Always On Availability Groups)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1ed564b4-9835-4245-ae35-9ba67419a4ce
---
# Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (Always On Availability Groups)
  This topic describes how to configure the flexible failover policy for an Always On availability group by using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] or PowerShell in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. A flexible failover policy provides granular control over the conditions that cause automatic failover for an availability group. By changing the failure conditions that trigger an automatic failover and the frequency of health checks, you can increase or decrease the likelihood of an automatic failover to support your SLA for high availability.  
  
-   **Before you begin:**  
  
     [Limitations on Automatic Failovers](#Limitations)  
  
     [Prerequisites](#Prerequisites)  
  
     [Security](#Security)  
  
-   **To configure the flexible failover policy, using:**  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
    > [!NOTE]  
    >  The flexible failover policy of an availability group cannot be configured by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Limitations"></a> Limitations on Automatic Failovers  
  
-   For an automatic failover to occur, the current primary replica and one secondary replica must be configured for synchronous\-commit availability mode with automatic failover and the secondary replica must be synchronized with the primary replica.  
  
-   Only three replicas are supported for automatic failover.  
  
-   If an availability group exceeds its WSFC failure threshold, the WSFC cluster will not attempt an automatic failover for the availability group. Furthermore, the WSFC resource group of the availability group remains in a failed state until either the cluster administrator manually brings the failed resource group online or the database administrator performs a manual failover of the availability group. The *WSFC failure threshold* is defined as the maximum number of failures supported for the availability group during a given time period. The default time period is six hours, and the default value for the maximum number of failures during this period is *n*\-1, where *n* is the number of WSFC nodes. To change the failure\-threshold values for a given availability group, use the WSFC Failover Manager Console.  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   You must be connected to the server instance that hosts the primary replica.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
  
|Task|Permissions|  
|----------|-----------------|  
|To configure the flexible failover policy for a new availability group|Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.|  
|To modify the policy of an existing availability group|Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.|  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To configure the flexible failover policy**  
  
1.  Connect to the server instance that hosts the primary replica.  
  
2.  For a new availability group, use the [CREATE AVAILABILITY GROUP](../Topic/CREATE%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md)[!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement. If you are modifying an existing availability group, use the [ALTER AVAILABILITY GROUP](../Topic/ALTER%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md)[!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement.  
  
    -   To set the failover condition level, use the FAILURE\_CONDITION\_LEVEL \= *n* option, where, *n* is an integer from 1 to 5.  
  
         For example, the following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement changes the failure\-condition level of an existing availability group, `AG1`, to level one:  
  
        ```  
  
        ALTER AVAILABILITY GROUP AG1 SET (FAILURE_CONDITION_LEVEL = 1);  
        ```  
  
         The relationship of these integer values to the failure condition levels is as follows:  
  
        |[!INCLUDE[tsql](../../Token\Other/tsql_md.md)] Value|Level|Automatic Is Failover Initiated When…|  
        |------------------------------|-----------|-------------------------------------------|  
        |1|One|On server down. The SQL Server service stops because of a failover or restart.|  
        |2|Two|On server unresponsive. Any condition of lower value is satisfied, the SQL Server service is connected to the cluster and the health check timeout threshold is exceeded, or the current primary replica is in a failed state.|  
        |3|Three|On critical server error. Any condition of lower value is satisfied or an internal critical server error occurs.<br /><br /> This is the default level.|  
        |4|Four|On moderate server error. Any condition of lower value is satisfied or a moderate Server error occurs.|  
        |5|Five|On any qualified failure conditions. Any condition of lower value is satisfied or a qualifying failure condition occurs.|  
  
         For more information about the failover condition levels, see [Flexible Failover Policy for Automatic Failover of an Availability Group &#40;SQL Server&#41;](../Topic/Flexible%20Failover%20Policy%20for%20Automatic%20Failover%20of%20an%20Availability%20Group%20\(SQL%20Server\).md).  
  
    -   To configure the health check timeout threshold, use the HEALTH\_CHECK\_TIMEOUT \= *n* option, where, *n* is an integer from 15000 milliseconds \(15 seconds\) to 4294967295 milliseconds. The default value is 30000 milliseconds \(30 seconds\)  
  
         For example, the following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement changes the health\-check timeout threshold of an existing availability group, `AG1`, to 60,000 milliseconds \(one minute\).  
  
        ```  
  
        ALTER AVAILABILITY GROUP AG1 SET (HEALTH_CHECK_TIMEOUT = 60000);  
        ```  
  
##  <a name="PowerShellProcedure"></a> Using PowerShell  
 **To configure the flexible failover policy**  
  
1.  Set default \(**cd**\) to the server instance that hosts the primary replica.  
  
2.  When adding an availability replica to an availability group, use the **New\-SqlAvailabilityGroup** cmdlet. When modifying an existing availability replica, use the **Set\-SqlAvailabilityGroup** cmdlet.  
  
    -   To set the failover condition level, use the **FailureConditionLevel***level* parameter, where, *level* is one of the following values:  
  
        |Value|Level|Automatic Is Failover Initiated When…|  
        |-----------|-----------|-------------------------------------------|  
        |**OnServerDown**|One|On server down. The SQL Server service stops because of a failover or restart.|  
        |**OnServerUnresponsive**|Two|On server unresponsive. Any condition of lower value is satisfied, the SQL Server service is connected to the cluster and the health check timeout threshold is exceeded, or the current primary replica is in a failed state.|  
        |**OnCriticalServerError**|Three|On critical server error. Any condition of lower value is satisfied or an internal critical server error occurs.<br /><br /> This is the default level.|  
        |**OnModerateServerError**|Four|On moderate server error. Any condition of lower value is satisfied or a moderate Server error occurs.|  
        |**OnAnyQualifiedFailureConditions**|Five|On any qualified failure conditions. Any condition of lower value is satisfied or a qualifying failure condition occurs.|  
  
         For more information about the failover condition levels, see [Flexible Failover Policy for Automatic Failover of an Availability Group &#40;SQL Server&#41;](../Topic/Flexible%20Failover%20Policy%20for%20Automatic%20Failover%20of%20an%20Availability%20Group%20\(SQL%20Server\).md).  
  
         For example, the following command changes the failure\-condition level of an existing availability group, `AG1`, to level one.  
  
        ```  
        Set-SqlAvailabilityGroup `   
        -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg `   
        -FailureConditionLevel OnServerDown  
        ```  
  
    -   To set the health check timeout threshold, use the **HealthCheckTimeout***n* parameter, where, *n* is an integer from 15000 milliseconds \(15 seconds\) to 4294967295 milliseconds. The default value is 30000 milliseconds \(30 seconds\).  
  
         For example, the following command changes the health\-check timeout threshold of an existing availability group, `AG1`, to 120,000 milliseconds \(two minutes\).  
  
        ```  
        Set-SqlAvailabilityGroup `   
        -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAG `   
        -HealthCheckTimeout 120000  
        ```  
  
> [!NOTE]  
>  To view the syntax of a cmdlet, use the **Get\-Help** cmdlet in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell environment. For more information, see [Get Help SQL Server PowerShell](../../Topics\TopicNameNotContainA/Get-Help-SQL-Server-PowerShell.md).  
  
 **To set up and use the SQL Server PowerShell provider**  
  
-   [SQL Server PowerShell Provider](../../Topics\TopicNameNotContainA/SQL-Server-PowerShell-Provider.md)  
  
-   [Get Help SQL Server PowerShell](../../Topics\TopicNameNotContainA/Get-Help-SQL-Server-PowerShell.md)  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Availability Modes &#40;Always On Availability Groups&#41;](../Topic/Availability%20Modes%20\(Always%20On%20Availability%20Groups\).md)   
 [Failover and Failover Modes &#40;Always On Availability Groups&#41;](../Topic/Failover%20and%20Failover%20Modes%20\(Always%20On%20Availability%20Groups\).md)   
 [Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../Topic/Windows%20Server%20Failover%20Clustering%20\(WSFC\)%20with%20SQL%20Server.md)   
 [Failover Policy for Failover Cluster Instances](../../Topics\TopicNameNotContainA/Failover-Policy-for-Failover-Cluster-Instances.md)   
 [sp_server_diagnostics &#40;Transact-SQL&#41;](../Topic/sp_server_diagnostics%20\(Transact-SQL\).md)  
  
  