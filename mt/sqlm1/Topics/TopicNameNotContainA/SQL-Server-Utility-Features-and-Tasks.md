---
title: SQL Server Utility Features and Tasks
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e6cbd25-6b1c-4e21-9ade-4584e243fd8f
---
# SQL Server Utility Features and Tasks
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] customers have a requirement to manage their [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] environment as a whole, addressed in this release through the concept of application and multiserver management in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Utility.  
  
## Benefits of the SQL Server Utility  
 The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Utility models an organization’s [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\-related entities in a unified view. Utility Explorer and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Utility viewpoints in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] \(SSMS\) provide administrators a holistic view of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] resource health through an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that serves as a utility control point \(UCP\). The combination of summary and detailed data presented in the UCP for both underutilization and overutilization policies, and for a variety of key parameters, enables resource consolidation opportunities and resource overutilization to be identified with ease. Health policies are configurable, and can be adjusted to change either upper or lower resource utilization thresholds. You can change global monitoring policies, or configure individual monitoring policies for each entity managed in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Utility.  
  
##  <a name="typical_scenarios"></a> Getting Started with SQL Server Utility  
 The typical user scenario begins with creation of a utility control point which establishes the central reasoning point for the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Utility. The UCP provides a consolidated view of resource health collected from managed instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Utility. After the UCP is created, you enroll instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] into the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Utility so that they can be managed by the UCP.  
  
 Each instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and data\-tier application managed by the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Utility can be monitored based on global policy definitions or based on individual policy definitions.  
  
## Related Tasks  
 Use the following topics to get started with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] utility.  
  
|||  
|-|-|  
|**Description**|**Topic**|  
|Describes considerations to configure a server to run utility and non\-utility collection sets on the same instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|[Considerations for Running Utility and non-Utility Collection Sets on the Same Instance of SQL Server](../../Topics\TopicNameNotContainA/Considerations-for-Running-Utility-and-non-Utility-Collection-Sets-on-the-Same-Instance-of-SQL-Server.md)|  
|Describes how to create a SQL Server utility control point.|[Create a SQL Server Utility Control Point &#40;SQL Server Utility&#41;](../Topic/Create%20a%20SQL%20Server%20Utility%20Control%20Point%20\(SQL%20Server%20Utility\).md)|  
|Describes how to connect to a SQL Server Utility.|[Connect to a SQL Server Utility](../../Topics\TopicNameContainA/Connect-to-a-SQL-Server-Utility.md)|  
|Describes how to enroll an instance of SQL Server with a Utility Control Point.|[Enroll an Instance of SQL Server &#40;SQL Server Utility&#41;](../Topic/Enroll%20an%20Instance%20of%20SQL%20Server%20\(SQL%20Server%20Utility\).md)|  
|Describes how to use Utility Explorer to manage the SQL Server utility.|[Use Utility Explorer to Manage the SQL Server Utility](../../Topics\TopicNameNotContainA/Use-Utility-Explorer-to-Manage-the-SQL-Server-Utility.md)|  
|Describes how to monitor instances of SQL Server in the SQL Server Utility.|[Monitor Instances of SQL Server in the SQL Server Utility](../../Topics\TopicNameNotContainA/Monitor-Instances-of-SQL-Server-in-the-SQL-Server-Utility.md)|  
|Describes how to view resource health policy results.|[View Resource Health Policy Results &#40;SQL Server Utility&#41;](../Topic/View%20Resource%20Health%20Policy%20Results%20\(SQL%20Server%20Utility\).md)|  
|Describes how to modify a resource health policy definition.|[Modify a Resource Health Policy Definition &#40;SQL Server Utility&#41;](../Topic/Modify%20a%20Resource%20Health%20Policy%20Definition%20\(SQL%20Server%20Utility\).md)|  
|Describes how to configure your UCP data warehouse.|[Configure Your Utility Control Point Data Warehouse &#40;SQL Server Utility&#41;](../Topic/Configure%20Your%20Utility%20Control%20Point%20Data%20Warehouse%20\(SQL%20Server%20Utility\).md)|  
|Describes how to configure utility health policies.|[Configure Health Policies &#40;SQL Server Utility&#41;](../Topic/Configure%20Health%20Policies%20\(SQL%20Server%20Utility\).md)|  
|Describes how to adjust attenuation in CPU utilization policies.|[Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](../Topic/Reduce%20Noise%20in%20CPU%20Utilization%20Policies%20\(SQL%20Server%20Utility\).md)|  
|Describes how to remove an instance of SQL Server from a UCP.|[Remove an Instance of SQL Server from the SQL Server Utility](../../Topics\TopicNameNotContainA/Remove-an-Instance-of-SQL-Server-from-the-SQL-Server-Utility.md)|  
|Describes how to change the proxy account for the utility data collector on a managed instance of SQL Server.|[Change the Proxy Account for the Utility Collection Set on a Managed Instance of SQL Server &#40;SQL Server Utility&#41;](../Topic/Change%20the%20Proxy%20Account%20for%20the%20Utility%20Collection%20Set%20on%20a%20Managed%20Instance%20of%20SQL%20Server%20\(SQL%20Server%20Utility\).md)|  
|Describes how to move a UCP from one instance of SQL Server to another.|[Move a UCP from One Instance of SQL Server to Another &#40;SQL Server Utility&#41;](../Topic/Move%20a%20UCP%20from%20One%20Instance%20of%20SQL%20Server%20to%20Another%20\(SQL%20Server%20Utility\).md)|  
|Describes how to remove a UCP.|[Remove a Utility Control Point &#40;SQL Server Utility&#41;](../Topic/Remove%20a%20Utility%20Control%20Point%20\(SQL%20Server%20Utility\).md)|  
|Describes how to troubleshoot the SQL server utility.|[Troubleshoot the SQL Server Utility](../../Topics\TopicNameNotContainA/Troubleshoot-the-SQL-Server-Utility.md)|  
|Describes how to troubleshoot SQL Server resource health.|[Troubleshoot SQL Server Resource Health &#40;SQL Server Utility&#41;](../Topic/Troubleshoot%20SQL%20Server%20Resource%20Health%20\(SQL%20Server%20Utility\).md)|  
|Links to UtilityExplorer F1 Help topics.|[Utility Explorer F1 Help](../../Topics\TopicNameNotContainA/Utility-Explorer-F1-Help.md)|  
  
  