---
title: Resource Governor Classifier Function
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 64c25012-7068-476f-afa2-0b4f3adde9a4
---
# Resource Governor Classifier Function
  The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] resource governor classification process assigns incoming sessions to a workload group based on the characteristics of the session. You can tailor the classification logic by writing a user\-defined function, called a classifier function.  
  
## Classification  
 Resource Governor supports the classification of incoming sessions. Classification is based on a set of user\-written criteria contained in a function. The results of the function logic enable Resource Governor to classify sessions into existing workload groups.  
  
> [!NOTE]  
>  The internal workload group is populated with requests that are for internal use only. You cannot change the criteria used for routing these requests and you cannot classify requests into the internal workload group.  
  
 You can write a scalar function that contains the logic that is used to assign incoming sessions to a workload group. Before you can use this function, you must complete the following actions:  
  
-   Create and register the function using the ALTER RESOURCE GOVERNOR statement. For more information, see [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../Topic/ALTER%20RESOURCE%20GOVERNOR%20\(Transact-SQL\).md).  
  
-   Update the Resource Governor configuration using the ALTER RESOURCE GOVERNOR statement with the RECONFIGURE parameter.  
  
 After you create the function and apply the configuration changes, the Resource Governor classifier will use the workload group name returned by the function to send a new request to the appropriate workload group.  
  
> [!IMPORTANT]  
>  The client session may time out if the classification function does not complete within the specified time\-out for the login. Login time\-out is a client property and as such, the server is unaware of a time\-out. A long\-running classifier function can leave the server with orphaned connections for long periods. It is important that you create classifier functions that finish executing before a connection time\-out.  
  
 The user\-defined function has the following characteristics and behaviors:  
  
-   The user\-defined function is evaluated for every new session, even when connection pooling is enabled.  
  
-   The user\-defined function gives workload group context for the session. After group membership is determined, the session is bound to the workload group for the lifetime of the session.  
  
-   If the user\-defined function returns NULL, default, or the name of non\-existent group the session is given the default workload group context. The session is also given the default context if the function fails for any reason.  
  
-   The function should be defined with server scope \(master database\).  
  
-   The classifier user\-defined function designation only takes effect after ALTER RESOURCE GOVERNOR RECONFIGURE is executed.  
  
-   Only one user\-defined function can be designated as a classifier at a time.  
  
-   The classifier user\-defined function cannot be dropped or altered unless its classifier status is removed.  
  
-   In the absence of a classifier user\-defined function, all sessions are classified into the default group.  
  
-   The workload group returned by the classifier function is outside the scope of the schema\-binding restriction. For example, you cannot drop a table, but you can drop a workload group.  
  
> [!IMPORTANT]  
>  We recommend enabling the Dedicated Administrator Connection \(DAC\) on the server. The DAC is not subject to Resource Governor classification and can be used to monitor and troubleshoot a classifier function. For more information, see [Diagnostic Connection for Database Administrators](../../Topics\TopicNameNotContainA/Diagnostic-Connection-for-Database-Administrators.md). If a DAC is not available for troubleshooting, the other option is to restart the system in single user mode. Although single user mode is not subject to classification, it does not give you the ability to diagnose Resource Governor classification while it is running.  
  
### Classification Process  
 In the context of Resource Governor, the login process for a session consists of the following steps:  
  
1.  Login authentication  
  
2.  LOGON trigger execution  
  
3.  Classification  
  
 When classification starts, Resource Governor executes the classifier function and uses the value returned by the function to send requests to the appropriate workload group.  
  
> [!NOTE]  
>  Information about the execution of the classifier function and LOGON triggers is exposed in [sys.dm\_exec\_sessions](../Topic/sys.dm_exec_sessions%20\(Transact-SQL\).md) and [sys.dm\_exec\_requests](../Topic/sys.dm_exec_requests%20\(Transact-SQL\).md).  
  
## Classification Function Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Describes how to create and test a classifier user\-defined function.|[Create and Test a Classifier User-Defined Function](../../Topics\TopicNameContainA/Create-and-Test-a-Classifier-User-Defined-Function.md)|  
  
## See Also  
 [Resource Governor](../../Topics\TopicNameNotContainA/Resource-Governor.md)   
 [Enable Resource Governor](../../Topics\TopicNameNotContainA/Enable-Resource-Governor.md)   
 [Resource Governor Resource Pool](../../Topics\TopicNameNotContainA/Resource-Governor-Resource-Pool.md)   
 [Resource Governor Workload Group](../../Topics\TopicNameNotContainA/Resource-Governor-Workload-Group.md)   
 [Configure Resource Governor Using a Template](../../Topics\TopicNameContainA/Configure-Resource-Governor-Using-a-Template.md)   
 [View Resource Governor Properties](../../Topics\TopicNameNotContainA/View-Resource-Governor-Properties.md)  
  
  