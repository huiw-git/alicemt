---
title: Database Engine Instances (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: af9ae643-9866-4014-b36f-11ab556a773e
---
# Database Engine Instances (SQL Server)
  An instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] is a copy of the **sqlservr.exe** executable that runs as an operating system service. Each instance manages several system databases and one or more user databases. Each computer can run multiple instances of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]. Applications connect to the instance in order to perform work in a database managed by the instance.  
  
## Instances  
 An instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] operates as a service that handles all application requests to work with the data in any of the databases managed by that instance. It is the target of the connection requests \(logins\) from applications. The connection runs through a network connection if the application and instance are on separate computers. If the application and instance are on the same computer, the SQL Server connection can run as either a network connection or an in\-memory connection. When a connection has been completed, an application sends [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements across the connection to the instance. The instance resolves the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements into operations against the data and objects in the databases, and if the required permissions have been granted to the login credentials, performs the work. Any data retrieved is returned to the application, along with any messages such as errors.  
  
 You can run multiple instances of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] on a computer. One instance can be the default instance. The default instance has no name. If a connection request specifies only the name of the computer, the connection is made to the default instance. A named instance is one where you specify an instance name when installing the instance. A connection request must specify both the computer name and instance name in order to connect to the instance. There is no requirement to install a default instance; all of the instances running on a computer can be named instances.  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Describes how to configure the properties of an instance. Configure defaults such as file locations and date formats, or how the instance uses operating system resources, such as memory or threads.|[Configure Database Engine Instances &#40;SQL Server&#41;](../Topic/Configure%20Database%20Engine%20Instances%20\(SQL%20Server\).md)|  
|Describes how to manage the collation for an instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]. Collations define the bit patterns used to represent characters, and associated behaviors such as sorting, and case or accent sensitivity in comparison operations.|[Collation and Unicode Support](../../Topics\TopicNameNotContainA/Collation-and-Unicode-Support.md)|  
|Describes how to configure linked server definitions, which allow [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements run in an instance to work with data stored in separate OLE DB data sources.|[Linked Servers &#40;Database Engine&#41;](../Topic/Linked%20Servers%20\(Database%20Engine\).md)|  
|Describes how to create a logon trigger, which specifies actions to be taken after a logon attempt has been validated, but before it starts working with resources in the instance. Logon triggers support actions such as logging connection activity, or restricting logins based on logic in addition to the credential authentication performed by Windows and SQL Server.|[Logon Triggers](../../Topics\TopicNameNotContainA/Logon-Triggers.md)|  
|Describes how to manage the service associated with an instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]. This includes actions such as starting and stopping the service, or configuring startup options.|[Manage the Database Engine Services](../../Topics\TopicNameNotContainA/Manage-the-Database-Engine-Services.md)|  
|Describes how to perform server network configuration tasks such as enabling protocols, modifying the port or pipe used by a protocol, configuring encryption, configuring the SQL Server Browser service, exposing or hiding the SQL Server Database Engine on the network, and registering the Server Principal Name.|[Server Network Configuration](../../Topics\TopicNameNotContainA/Server-Network-Configuration.md)|  
|Describes how to perform client network configuration tasks such as configuring client protocols and creating or deleting a Server Alias.|[Client Network Configuration](../../Topics\TopicNameNotContainA/Client-Network-Configuration.md)|  
|Describes the [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] editors that can be used to design, debug, and run scripts such as [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] scripts. Also describes how to code Windows PowerShell scripts to work with SQL Server components.|[Database Engine Scripting](../../Topics\TopicNameNotContainA/Database-Engine-Scripting.md)|  
|Describes how to use maintenance plans to specify a workflow of common administration tasks for an instance. Workflows include tasks such as backing up databases and updating statistics to improve performance.|[Maintenance Plans](../../Topics\TopicNameNotContainA/Maintenance-Plans.md)|  
|Describes how to use the resource governor to manage resource consumption and workloads by specifying limits to the amount of CPU and memory that application requests can use.|[Resource Governor](../../Topics\TopicNameNotContainA/Resource-Governor.md)|  
|Describes how database applications can use database mail to send e\-mail messages from the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].|[Database Mail](../../Topics\TopicNameNotContainA/Database-Mail.md)|  
|Describes how to use extended events to capture performance data can be used to build performance baselines or to diagnose performance problems. Extended events are a light\-weight, highly scalable system for gathering performance data.|[Extended Events](../../Topics\TopicNameNotContainA/Extended-Events.md)|  
|Describes how to use SQL Trace to build a customized system for capturing and recording events in the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].|[SQL Trace](../../Topics\TopicNameNotContainA/SQL-Trace.md)|  
|Describes how to use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Profiler to capture traces of application requests coming in to an instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]. These traces can later be replayed for activities such as performance testing or problem diagnosis.|[SQL Server Profiler](../../Topics\TopicNameNotContainA/SQL-Server-Profiler.md)|  
|Describes the Change Data Capture \(CDC\) and Change Tracking features and describes how to use these features to track changes to data in a database.|[Track Data Changes &#40;SQL Server&#41;](../Topic/Track%20Data%20Changes%20\(SQL%20Server\).md)|  
|Describes how to use the Log File viewer to find and view [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] errors and messages in various logs, such as the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] job history, the SQL Server logs, and Windows event logs.|[Log File Viewer](../../Topics\TopicNameNotContainA/Log-File-Viewer.md)|  
|Describes how to use the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Tuning Advisor to analyze databases and make recommendations for addressing potential performance problems.|[Database Engine Tuning Advisor](../../Topics\TopicNameNotContainA/Database-Engine-Tuning-Advisor.md)|  
|Describes how the production database administrators can make a diagnostic connection to instances when standard connections are not being accepted.|[Diagnostic Connection for Database Administrators](../../Topics\TopicNameNotContainA/Diagnostic-Connection-for-Database-Administrators.md)|  
|Describes how to use the deprecated remote servers feature to enable access from one instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] to another. The preferred mechanism for this functionality is a linked server.|[Remote Servers](../../Topics\TopicNameNotContainA/Remote-Servers.md)|  
|Describes the capabilities of Service Broker for messaging and queueing applications and provides pointers to the Service Broker documentation.|[Service Broker](../../Topics\TopicNameNotContainA/SQL-Server-Service-Broker.md)|  
|Describes how the buffer pool extension can be used to provide seamless integration of nonvolatile random access storage \(solid\-state drives\) to the Database Engine buffer pool to significantly improve I\/O throughput.|[Buffer Pool Extension File](../../Topics\TopicNameNotContainA/Buffer-Pool-Extension.md)|  
  
## See Also  
 [sqlservr Application](../../Topics\TopicNameNotContainA/sqlservr-Application.md)   
 [Database Features](../../Topics\TopicNameNotContainA/Database-Features.md)   
 [Database Engine Cross-Instance Features](../../Topics\TopicNameNotContainA/Database-Engine-Cross-Instance-Features.md)  
  
  