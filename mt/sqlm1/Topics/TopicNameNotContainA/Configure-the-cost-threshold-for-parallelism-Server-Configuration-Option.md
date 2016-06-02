---
title: Configure the cost threshold for parallelism Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dad21bee-fe28-41f6-9d2f-e6ababfaf9db
---
# Configure the cost threshold for parallelism Server Configuration Option
  This topic describes how to configure the **cost threshold for parallelism** server configuration option in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. The **cost threshold for parallelism** option specifies the threshold at which [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] creates and runs parallel plans for queries. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] creates and runs a parallel plan for a query only when the estimated cost to run a serial plan for the same query is higher than the value set in **cost threshold for parallelism**. The cost refers to an estimated elapsed time in seconds required to run the serial plan on a specific hardware configuration. The **cost threshold for parallelism** option can be set to any value from 0 through 32767. The default value is 5.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To configure the cost threshold for parallelism option, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After you configure the cost threshold for parallelism option](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   The cost refers to an estimated elapsed time in seconds required to run the serial plan on a specific hardware configuration. Only set **cost threshold for parallelism** on symmetric multiprocessors.  
  
-   [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] ignores the **cost threshold for parallelism** value under the following conditions:  
  
    -   Your computer has only one logical processor.  
  
    -   Only a single logical processor is available to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] because of the **affinity mask** configuration option.  
  
    -   The **max degree of parallelism** option is set to 1.  
  
 A logical processor is the basic unit of processor hardware that allows the operating system to dispatch a task or execute a thread context. Each logical processor can execute only one thread context at a time. The processor core is the circuitry that provides ability to decode and execute instructions. A processor core may contain one or more logical processors. The following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] query can be used for obtaining CPU information for the system.  
  
```  
SELECT (cpu_count / hyperthread_ratio) AS PhysicalCPUs,   
cpu_count AS logicalCPUs   
FROM sys.dm_os_sys_info  
```  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] technician.  
  
-   In certain cases, a parallel plan may be chosen even though the query's cost plan is less than the current **cost threshold for parallelism** value. This can happen because the decision to use a parallel or serial plan is based on a cost estimate provided before the full optimization is complete.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Execute permissions on **sp\_configure** with no parameters or with only the first parameter are granted to all users by default. To execute **sp\_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server\-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To configure the cost threshold for parallelism option  
  
1.  In Object Explorer, right\-click a server and select **Properties**.  
  
2.  Click the **Advanced** node.  
  
3.  Under **Parallelism**, change the **CostThresholdForParallelism** option to the value you want. Type or select a value from 0 to 32767.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To configure the cost threshold for parallelism option  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp\_configure](../Topic/sp_configure%20\(Transact-SQL\).md) to set the value of the `cost threshold for parallelism` option to `10`.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'cost threshold for parallelism', 10 ;  
GO  
RECONFIGURE  
GO  
```  
  
 For more information, see [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md).  
  
##  <a name="FollowUp"></a> Follow Up: After you configure the cost threshold for parallelism option  
 The setting takes effect immediately without restarting the server.  
  
## See Also  
 [Configure Parallel Index Operations](../../Topics\TopicNameNotContainA/Configure-Parallel-Index-Operations.md)   
 [Query Hints &#40;Transact-SQL&#41;](../Topic/Query%20Hints%20\(Transact-SQL\).md)   
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../Topic/ALTER%20WORKLOAD%20GROUP%20\(Transact-SQL\).md)   
 [affinity mask Server Configuration Option](../../Topics\TopicNameNotContainA/affinity-mask-Server-Configuration-Option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)   
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)   
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)  
  
  