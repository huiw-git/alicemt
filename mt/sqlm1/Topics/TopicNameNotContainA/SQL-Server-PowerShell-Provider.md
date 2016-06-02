---
title: SQL Server PowerShell Provider
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b97acc43-fcd2-4ae5-b218-e183bab916f9
---
# SQL Server PowerShell Provider
  The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provider for Windows PowerShell exposes the hierarchy of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] objects in paths similar to file system paths. You can use the paths to locate an object, and then use methods from the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Management Object \(SMO\) models to perform actions on the objects.  
  
## Benefits of the SQL Server PowerShell Provider  
 The paths implemented by the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provider enable easily and interactively reviewing all of the objects in an instance of SQL Server. You can navigate the paths using Windows PowerShell aliases similar to the commands you typically use to navigate file system paths.  
  
## The SQL Server PowerShell Hierarchy  
 Products whose data or object models can be represented in a hierarchy use Windows PowerShell providers to expose the hierarchies. The hierarchy is exposed by using a drive and path structure similar to what the Windows file system uses.  
  
 Each Windows PowerShell provider implements one or more drives. Each drive is the root node of a hierarchy of related objects. The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provider implements a SQLSERVER: drive. The provider also defines a set of primary folders for the SQLSERVER: drive. Each folder and its subfolders represent the set of objects that can be accessed by using a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] management object model. When you are focused on a subfolder in a path that starts with one of these primary folders, you can use the methods from the associated object model to perform actions on the object that is represented by the node. The Windows PowerShell folders implemented by the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] provider are listed in the following table.  
  
|Folder|SQL Server object model namespace|Objects|  
|------------|---------------------------------------|-------------|  
|SQLSERVER:\\SQL|[Microsoft.SqlServer.Management.Smo](assetId:///N:Microsoft.SqlServer.Management.Smo)<br /><br /> [Microsoft.SqlServer.Management.Smo.Agent](assetId:///N:Microsoft.SqlServer.Management.Smo.Agent)<br /><br /> [Microsoft.SqlServer.Management.Smo.Broker](assetId:///N:Microsoft.SqlServer.Management.Smo.Broker)<br /><br /> [Microsoft.SqlServer.Management.Smo.Mail](assetId:///N:Microsoft.SqlServer.Management.Smo.Mail)|Database objects, such as tables, views, and stored procedures.|  
|SQLSERVER:\\SQLPolicy|[Microsoft.SqlServer.Management.Dmf](assetId:///N:Microsoft.SqlServer.Management.Dmf)<br /><br /> [Microsoft.SqlServer.Management.Facets](assetId:///N:Microsoft.SqlServer.Management.Facets)|Policy\-based management objects, such as policies and facets.|  
|SQLSERVER:\\SQLRegistration|[Microsoft.SqlServer.Management.RegisteredServers](assetId:///N:Microsoft.SqlServer.Management.RegisteredServers)<br /><br /> [Microsoft.SqlServer.Management.Smo.RegSvrEnum](assetId:///N:Microsoft.SqlServer.Management.Smo.RegSvrEnum)|Registered server objects, such as server groups and registered servers.|  
|SQLSERVER:\\Utility|[Microsoft.SqlServer.Management.Utility](assetId:///N:Microsoft.SqlServer.Management.Utility)|Utility objects, such as managed instances of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].|  
|SQLSERVER:\\DAC|[N:Microsoft.SqlServer.Management.DAC](assetId:///N:Microsoft.SqlServer.Management.DAC)|Data\-tier application objects such as DAC packages, and operations such as deploying a DAC.|  
|SQLSERVER:\\DataCollection|[Microsoft.SqlServer.Management.Collector](assetId:///N:Microsoft.SqlServer.Management.Collector)|Data collector objects, such as collection sets and configuration stores.|  
|SQLSERVER:\\IntegrationServices|[Microsoft.SqlServer.Management.IntegrationServices](assetId:///N:Microsoft.SqlServer.Management.IntegrationServices)|[!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] objects such as projects, packages, and environments.|  
|SQLSERVER:\\SQLAS|[Microsoft.AnalysisServices](assetId:///N:Microsoft.AnalysisServices)|[!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] objects such as cubes, aggregations, and dimensions.|  
  
 For example, you can use the SQLSERVER:\\SQL folder to start paths that can represent any object that is supported by the SMO object model. The leading part of a SQLSERVER:\\SQL path is SQLSERVER:\\SQL\\*ComputerName*\\*InstanceName*. The nodes after the instance name alternate between object collections \(such as *Databases* or *Views*\) and object names \(such as AdventureWorks2012\). Schemas are not represented as object classes. When you specify the node for a top\-level object in a schema, such as a table or view, you must specify the object name in the format *SchemaName.ObjectName*.  
  
 This is the path of the Vendor table in the Purchasing schema of the AdventureWorks2012 database in a default instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] on the local computer:  
  
```  
SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012\Tables\Purchasing.Vendor  
```  
  
 For more information about the SMO object model hierarchy, see [SMO Object Model Diagram](../Topic/SMO%20Object%20Model%20Diagram.md).  
  
 Collection nodes in a path are associated with a collection class in the associated object model. Object name nodes are associated with an object class in the associated object model, as in the following table.  
  
|Path|SMO class|  
|----------|---------------|  
|SQLSERVER:\\SQL\\MyComputer\\DEFAULT\\Databases|[DatabaseCollection](assetId:///T:Microsoft.SqlServer.Management.Smo.DatabaseCollection)|  
|SQLSERVER:\\SQL\\MyComputer\\DEFAULT\\Databases\\AdventureWorks2012|[Database](assetId:///T:Microsoft.SqlServer.Management.Smo.Database)|  
  
## SQL Server Provider Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Describes how to use Windows PowerShell cmdlets to navigate through the nodes in a path, and at each node get a list of the objects at that node.|[Navigate SQL Server PowerShell Paths](../../Topics\TopicNameNotContainA/Navigate-SQL-Server-PowerShell-Paths.md)|  
|Describes how to use the SMO methods and properties to report on and perform work on the object represented by a node in a path. Also describes how to get a list of the SMO methods and properties for that node.|[Work With SQL Server PowerShell Paths](../../Topics\TopicNameNotContainA/Work-With-SQL-Server-PowerShell-Paths.md)|  
|Describes how to convert a SMO Uniform Resource Name \(URN\) to a SQL Server provider path.|[Convert URNs to SQL Server Provider Paths](../../Topics\TopicNameNotContainA/Convert-URNs-to-SQL-Server-Provider-Paths.md)|  
|Describes how to open SQL Server Authentication connections by using the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provider. By default, the provider uses Windows Authentication connections made using the credentials of the Windows account running the Windows PowerShell session.|[Manage Authentication in Database Engine PowerShell](../../Topics\TopicNameNotContainA/Manage-Authentication-in-Database-Engine-PowerShell.md)|  
  
## See Also  
 [SQL Server PowerShell](../../Topics\TopicNameNotContainA/SQL-Server-PowerShell.md)  
  
  