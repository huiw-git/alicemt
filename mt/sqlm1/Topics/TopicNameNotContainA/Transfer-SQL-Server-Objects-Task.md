---
title: Transfer SQL Server Objects Task
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fe86d6e5-e415-406c-88f3-dc3ef71bd5f0
---
# Transfer SQL Server Objects Task
  The Transfer [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Objects task transfers one or more types of objects in a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database between instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For example, the task can copy tables and stored procedures. Depending on the version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that is used as a source, different types of objects are available to copy. For example, only a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database includes schemas and user\-defined aggregates.  
  
## Objects to Transfer  
 Server roles, roles, and users from the specified database can be copied, as well as the permissions for the transferred objects. By copying the associated users, roles, and permissions together with the objects, you can make the transferred objects immediately operable on the destination server.  
  
 The following table lists the type of objects that can be copied.  
  
|Object|  
|------------|  
|Tables|  
|Views|  
|Stored Procedures|  
|User\-Defined Functions|  
|Defaults|  
|User\-Defined Data Types|  
|Partition Functions|  
|Partition Schemes|  
|Schemas|  
|Assemblies|  
|User\-Defined Aggregates|  
|User\-Defined Types|  
|XML Schema Collection|  
  
 User\-defined types \(UDTs\) that were created in an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] have dependencies on common language runtime \(CLR\) assemblies. If you use the Transfer [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Objects task to transfer UDTs, you must also configure the task to transfer dependent objects. To transfer dependent objects, set the **IncludeDependentObjects** property to **True**.  
  
### Table Options  
 When copying tables, you can indicate the types of table\-related items to include in the copy process. The following types of items can be copied together with the related table:  
  
-   Indexes  
  
-   Triggers  
  
-   Full\-text indexes  
  
-   Primary keys  
  
-   Foreign keys  
  
 You can also indicate whether the script that the task generates is in Unicode format.  
  
## Destination Options  
 You can configure the Transfer [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Objects task to include schema names, data, extended properties of transferred objects, and dependent objects in the transfer. If data is copied, it can replace or append existing data.  
  
 Some options apply only to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For example, only [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] supports schemas.  
  
## Security Options  
 The Transfer [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Objects task can include [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database\-level users and roles from the source, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] logins, and the permissions for transferred objects. For example, the transfer can include the permissions on the transferred tables.  
  
## Transfer Objects Between Instances of SQL Server  
 The Transfer [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Objects task supports a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] source and destination.  
  
## Events  
 The task raises an information event that reports the object transferred and a warning event when an object is overwritten. An information event is also raised for actions such as the truncation of database tables.  
  
 The Transfer [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Objects task does not report incremental progress of the object transfer; it reports only 0% and 100 % completion.  
  
## Execution Value  
 The execution value, stored in the **ExecutionValue** property of the task, returns the number of objects transferred. By assigning a user\-defined variable to the **ExecValueVariable** property of the Transfer SQL Server Objects task, information about the object transfer can be made available to other objects in the package. For more information, see [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md) and [Use Variables in Packages](../../Topics\TopicNameNotContainA/Use-Variables-in-Packages.md).  
  
## Log Entries  
 The Transfer SQL Server Objects task includes the following custom log entries:  
  
-   TransferSqlServerObjectsTaskStartTransferringObjects   This log entry reports that the transfer has started. The log entry includes the start time.  
  
-   TransferSqlServerObjectsTaskFinishedTransferringObjects    This log entry reports that the transfer has completed. The log entry includes the end time.  
  
 In addition, a log entry for an **OnInformation** event reports the number of objects of the object types that have been selected for transfer, the number of objects that were transferred, and actions such as the truncation of tables when data is transferred with tables. A log entry for the **OnWarning** event is written for each object on the destination that is overwritten.  
  
## Security and Permissions  
 The user must have permission to browse objects on the source server, and must have permission to drop and create objects on the destination server; moreover, the user must have access to the specified database and database objects.  
  
## Configuration of the Transfer SQL Server Objects Task  
 The Transfer [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Objects task can be configured to transfer all objects, all objects of a type, or only specified objects of a type. For example, you can choose to copy only selected tables in the AdventureWorks database.  
  
 If the Transfer [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Objects task transfers tables, you can specify the types of table\-related objects to copy with the tables. For example, you can specify that primary keys are copied with tables.  
  
 To further enhance functionality of transferred objects, you can configure the Transfer [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Objects task to include schema names, data, extended properties of transferred objects, and dependent objects in the transfer. When copying data, you can specify whether to replace or append existing data.  
  
 At run time, the Transfer [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Objects task connects to the source and destination servers by using two SMO connection managers. The SMO connection managers are configured separately from the Transfer [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Objects task, and then referenced in the Transfer [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Objects task. The SMO connection managers specify the server and the authentication mode to use when accessing the server. For more information, see [SMO Connection Manager](../../Topics\TopicNameNotContainA/SMO-Connection-Manager.md).  
  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click one of the following topics:  
  
-   [Transfer SQL Server Objects Task Editor &#40;General Page&#41;](../Topic/Transfer%20SQL%20Server%20Objects%20Task%20Editor%20\(General%20Page\).md)  
  
-   [Transfer SQL Server Objects Task Editor &#40;Objects Page&#41;](../Topic/Transfer%20SQL%20Server%20Objects%20Task%20Editor%20\(Objects%20Page\).md)  
  
-   [Expressions Page](../../Topics\TopicNameNotContainA/Expressions-Page.md)  
  
 For more information about how to set these properties in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the following topic:  
  
-   [Set the Properties of a Task or Container](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md)  
  
## Programmatic Configuration of the Transfer SQL Server Objects Task  
 For more information about programmatically setting these properties, click the following topic:  
  
-   [TransferSqlServerObjectsTask](assetId:///T:Microsoft.SqlServer.Dts.Tasks.TransferSqlServerObjectsTask.TransferSqlServerObjectsTask)  
  
  