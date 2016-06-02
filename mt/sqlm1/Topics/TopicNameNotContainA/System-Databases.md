---
title: System Databases
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 30468a7c-4225-4d35-aa4a-ffa7da4f1282
---
# System Databases
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] includes the following system databases.  
  
|System database|Description|  
|---------------------|-----------------|  
|[master Database](../../Topics\TopicNameNotContainA/master-Database.md)|Records all the system\-level information for an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|  
|[msdb Database](../../Topics\TopicNameNotContainA/msdb-Database.md)|Is used by SQL Server Agent for scheduling alerts and jobs.|  
|[model Database](../../Topics\TopicNameNotContainA/model-Database.md)|Is used as the template for all databases created on the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Modifications made to the **model** database, such as database size, collation, recovery model, and other database options, are applied to any databases created afterward.|  
|[Resource Database](../../Topics\TopicNameNotContainA/Resource-Database.md)|Is a read\-only database that contains system objects that are included with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. System objects are physically persisted in the **Resource** database, but they logically appear in the **sys** schema of every database.|  
|[tempdb Database](../../Topics\TopicNameNotContainA/tempdb-Database.md)|Is a workspace for holding temporary objects or intermediate result sets.|  
  
## Modifying System Data  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] does not support users directly updating the information in system objects such as system tables, system stored procedures, and catalog views. Instead, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides a complete set of administrative tools that let users fully administer their system and manage all users and objects in a database. These include the following:  
  
-   Administration utilities, such as [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
-   SQL\-SMO API. This lets programmers include complete functionality for administering [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in their applications.  
  
-   [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] scripts and stored procedures. These can use system stored procedures and [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] DDL statements.  
  
 These tools shield applications from changes in the system objects. For example, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] sometimes has to change the system tables in new versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to support new functionality that is being added in that version. Applications issuing SELECT statements that directly reference system tables are frequently dependent on the old format of the system tables. Sites may not be able to upgrade to a new version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] until they have rewritten applications that are selecting from system tables. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] considers the system stored procedures, DDL, and SQL\-SMO published interfaces, and works to maintain the backward compatibility of these interfaces.  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] does not support triggers defined on the system tables, because they might modify the operation of the system.  
  
> [!NOTE]  
>  System databases cannot reside on UNC share directories.  
  
## Viewing System Database Data  
 You should not code [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements that directly query the system tables, unless that is the only way to obtain the information that is required by the application. Instead, applications should obtain catalog and system information by using the following:  
  
-   System catalog views  
  
-   SQL\-SMO  
  
-   Windows Management Instrumentation \(WMI\) interface  
  
-   Catalog functions, methods, attributes, or properties of the data API used in the application, such as ADO, OLE DB, or ODBC.  
  
-   [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] system stored procedures and built\-in functions.  
  
## Related Tasks  
 [Back Up and Restore of System Databases &#40;SQL Server&#41;](../Topic/Back%20Up%20and%20Restore%20of%20System%20Databases%20\(SQL%20Server\).md)  
  
 [Hide System Objects in Object Explorer](../Topic/Hide%20System%20Objects%20in%20Object%20Explorer.md)  
  
## Related Content  
 [Catalog Views &#40;Transact-SQL&#41;](../Topic/Catalog%20Views%20\(Transact-SQL\).md)  
  
 [Databases](../../Topics\TopicNameNotContainA/Databases.md)  
  
  