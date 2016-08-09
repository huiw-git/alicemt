---
title: "Use Dynamic Management Views (DMVs) to Monitor Analysis Services"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 22b82b2d-867f-4ebf-9288-79d1cdd62f18
caps.latest.revision: 16
manager: mblythe
---
# Use Dynamic Management Views (DMVs) to Monitor Analysis Services
Analysis Services Dynamic Management Views (DMV) are query structures that expose information about local server operations and server health. The query structure is an interface to schema rowsets that return metadata and monitoring information about an Analysis Services instance.  
  
 For most DMV queries, you use a **SELECT** statement and the **$System** schema with an XML/A schema rowset.  
  
```  
SELECT * FROM $System.<schemaRowset>  
```  
  
 DMV queries return information about server state that is current at the time the query was run. To monitor operations in real time, use tracing instead. For more information, see [Use SQL Server Profiler to Monitor Analysis Services](../../Topics/TopicNameNotContainA/Use-SQL-Server-Profiler-to-Monitor-Analysis-Services.md).  
  
 This topic includes the following sections:  
  
 [Benefits of Using DMV Queries](#bkmk_ben)  
  
 [Examples and Scenarios](#bkmk_ex)  
  
 [Query Syntax](#bkmk_syn)  
  
 [Tools and Permissions](#bkmk_tools)  
  
 [DMV Reference](#bkmk_ref)  
  
##  <a name="bkmk_ben"></a> Benefits of Using DMV Queries  
 DMV queries return information about operations and resource consumption that are not available through other means.  
  
 DMV queries are an alternative to running XML/A Discover commands. For most administrators, writing a DMV query is simpler because the query syntax is based on SQL. In addition, the result set is returned in a tabular format that is easier to read and copy from.  
  
##  <a name="bkmk_ex"></a> Examples and Scenarios  
 A DMV query can help you answer questions about active sessions and connections, and which objects are consuming the most CPU or memory at a specific point in time. This section provides examples for scenarios where DMV queries are most commonly used. You can also review the [SQL Server 2008 R2 Analysis Services Operations Guide](http://go.microsoft.com/fwlink/?LinkID=225539&clcid=0x409) for additional insights into using DMV queries to monitor a server instance.  
  
 `Select * from $System.discover_object_activity` /** This query reports on object activity since the service last started. For example queries based on this DMV, see [New System.Discover_Object_Activity](http://go.microsoft.com/fwlink/?linkid=221322).  
  
 `Select * from $System.discover_object_memory_usage` /** This query reports on memory consumption by object.  
  
 `Select * from $System.discover_sessions` /** This query reports on active sessions, including session user and duration.  
  
 `Select * from $System.discover_locks` /** This query returns a snapshot of the locks used at a specific point in time.  
  
##  <a name="bkmk_syn"></a> Query Syntax  
 The query engine for DMVs is the Data Mining parser. The DMV query syntax is based on the [SELECT (DMX)](assetId:///32d9e8fd-796b-4e1c-ae59-73cd6f645485) statement.  
  
 Although DMV query syntax is based on a SQL SELECT statement, it does not support the full syntax of a SELECT statement. Notably, JOIN, GROUP BY, LIKE, CAST, and CONVERT are not supported.  
  
```  
SELECT [DISTINCT] [TOP <n>] <select list>  
FROM $System.<schemaRowset>  
[WHERE <condition expression>]  
[ORDER BY <expression>[DESC|ASC]]  
```  
  
 The following example for DISCOVER_CALC_DEPENDENCY illustrates the use of the WHERE clause for supplying a parameter to the query:  
  
```  
SELECT * FROM $System.DISCOVER_CALC_DEPENDENCY  
WHERE OBJECT_TYPE = 'ACTIVE_RELATIONSHIP'  
```  
  
 Alternatively, for schema rowsets that have restrictions, the query must include the SYSTEMRESTRICTSCHEMA function. The following example returns CSDL metadata about tabular models running on a tabular mode server. Note that CATALOG_NAME is case-sensitive:  
  
```  
Select * from SYSTEMRESTRICTSCHEMA ($System.Discover_csdl_metadata, [CATALOG_NAME] = 'Adventure Works DW')  
```  
  
##  <a name="bkmk_tools"></a> Tools and Permissions  
 You must have system administrator permissions on the Analysis Services instance to query a DMV.  
  
 You can use any client application that supports MDX or DMX queries, including SQL Server Management Studio, a Reporting Services report, or a PerformancePoint Dashboard.  
  
 To run a DMV query from Management Studio, connect to the instance you want to query, click **New Query**. You can run a query from an MDX or a DMX query window.  
  
##  <a name="bkmk_ref"></a> DMV Reference  
 Not all schema rowsets have a DMV interface. To return a list of all the schema rowsets that can be queried using DMV, run the following query.  
  
```  
SELECT * FROM $System.DBSchema_Tables   
WHERE TABLE_TYPE = 'SCHEMA'   
ORDER BY TABLE_NAME ASC  
```  
  
> [!NOTE]  
>  If a DMV is not available for a given rowset, the server returns the following error: “The <schemarowset\> request type was not recognized by the server". All other errors point to problems with the syntax.  
  
|Rowset|Description|  
|------------|-----------------|  
|[DBSCHEMA_CATALOGS Rowset](assetId:///f02dc75d-5442-4eea-b33a-567dc816be7a)|Returns a list of the Analysis Services databases on the current connection.|  
|[DBSCHEMA_COLUMNS Rowset](assetId:///653bdd07-a533-4a99-8b6a-6e5c7322e1f3)|Returns a list of all the columns in the current database. You can use this list to construct a DMV query.|  
|[DBSCHEMA_PROVIDER_TYPES Rowset](assetId:///255e01ba-53a9-478d-9b86-45faba76710e)|Returns properties about the base data types supported by the OLE DB data provider.|  
|[DBSCHEMA_TABLES Rowset](assetId:///14c16e6b-0aff-4ad1-b98f-cdb7df0f8d73)|Returns a list of all the tables in the current database. You can use this list to construct a DMV query.|  
|[DISCOVER_CALC_DEPENDENCY Rowset](assetId:///f39dde72-fa5c-4c82-8b4e-88358aa2e422)|Returns a list of the columns and tables used in a model that have dependencies on other columns and tables.|  
|[DISCOVER_COMMAND_OBJECTS Rowset](assetId:///325114ee-3a50-4504-9782-dbf7c1a44778)|Provides resource usage and activity information about objects in use by the referenced command.|  
|[DISCOVER_COMMANDS Rowset](assetId:///d228f265-05d9-4d2c-a622-44c73eab7a71)|Provides resource usage and activity information about currently executing command.|  
|[DISCOVER_CONNECTIONS Rowset](assetId:///e4703970-c31d-448c-ab68-503303c91aa4)|Provides resource usage and activity information about open connections to Analysis Services.|  
|[DISCOVER_CSDL_METADATA Rowset](assetId:///a2d3cffd-a2c4-411c-b244-9e41ebe30939)|Returns information about a tabular model.<br /><br /> Requires the addition of SYSTEMRESTRICTSCHEMA and additional parameters.|  
|[DISCOVER_DB_CONNECTIONS Rowset](assetId:///12a51a4e-5f3d-4449-9d94-7836fea1bc8b)|Provides resource usage and activity information about open connections from Analysis Services to external data sources, for example during processing or importing.|  
|[DISCOVER_DIMENSION_STAT Rowset](assetId:///639f8cd7-3b43-40d5-8b84-552daf60d484)|Returns the attributes in a dimension or columns in a table, depending on the model type.|  
|[DISCOVER_ENUMERATORS Rowset](assetId:///ddc7b13c-3135-4419-8166-eddd459167da)|Returns metadata about the enumerators supported for a specific data source.|  
|[DISCOVER_INSTANCES Rowset](assetId:///e0842e63-089d-468d-869f-634da343d9fb)|Returns information about the specified instance.<br /><br /> Requires the addition of SYSTEMRESTRICTSCHEMA and additional parameters.|  
|[DISCOVER_JOBS Rowset](assetId:///b4d83bb6-aed3-4513-b516-cefadf95dad2)|Returns information about current jobs.|  
|[DISCOVER_KEYWORDS Rowset (XMLA)](assetId:///99945e53-3a1b-4d7b-9aff-712977db8b2d)|Returns the list of reserved keywords.|  
|[DISCOVER_LITERALS Rowset](assetId:///1bf0a2e2-a419-4c25-b271-37dfa44de2ea)|Returns the list of literals, including data types and values, supported by XMLA.|  
|[DISCOVER_LOCKS Rowset](assetId:///dea48167-212c-40b7-a416-434042a1b697)|Returns a snapshot of the locks used at a specific point in time.|  
|[DISCOVER_MEMORYGRANT Rowset](assetId:///d254e42d-9918-47ce-b6df-47f1f0b432dd)|Returns information about memory allocated by Analysis Services at start up.|  
|[DISCOVER_MEMORYUSAGE Rowset](assetId:///e416ea61-9615-468c-a96f-bbf731f803b1)|Shows memory usage by specific objects.|  
|[DISCOVER_OBJECT_ACTIVITY Rowset](assetId:///100f7de1-ad5c-4973-b863-3c10df1245c4)|Reports on object activity since the service last started.|  
|[DISCOVER_OBJECT_MEMORY_USAGE Rowset](assetId:///211cfa04-7bd6-43fe-8bd5-bfbff78bdafb)|Reports on memory consumption by object.|  
|[DISCOVER_PARTITION_DIMENSION_STAT Rowset](assetId:///bf4626b3-4d6b-4795-bb01-df335fb9c09a)|Provides information about the attributes in a dimension.<br /><br /> Requires the addition of SYSTEMRESTRICTSCHEMA and additional parameters.|  
|[DISCOVER_PARTITION_STAT Rowset](assetId:///20d339e2-f47f-437f-94d5-5b00b400356a)|Provides information about the partitions in a dimension, table, or measure group.<br /><br /> Requires the addition of SYSTEMRESTRICTSCHEMA and additional parameters.|  
|[DISCOVER_PERFORMANCE_COUNTERS Rowset](assetId:///62b1e967-af67-4915-a305-727bffd61fe4)|Lists the columns used in a performance counter.<br /><br /> Requires the addition of SYSTEMRESTRICTSCHEMA and additional parameters.|  
|[DISCOVER_PROPERTIES Rowset](assetId:///3e2b50e2-3855-4091-8b02-4968e8e57d4c)|Returns information about properties supported by XMLA for the specified data source.|  
|[DISCOVER_SCHEMA_ROWSETS Rowset](assetId:///e5012aa0-6ef8-497f-96c1-2772e2394f62)|Returns names, restrictions, description and other information for all enumeration values supported by XMLA.|  
|[DISCOVER_SESSIONS Rowset](assetId:///47a79542-3142-4e62-a66f-6c4dbfe0f5c0)|Reports on active sessions, including session user and duration.|  
|[DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS Rowset](assetId:///3e514715-9fe6-4e6a-accb-4149ffd7e0bf)|Provides information at the column and segment level about storage tables used by an Analysis Services database running in Tabular or SharePoint mode.|  
|[DISCOVER_STORAGE_TABLE_COLUMNS Rowset](assetId:///24abb88e-33a9-4ae2-829d-cdef0ff22ec1)|Allows the client to determine the assignment of columns to storage tables used by an Analysis Services database running in Tabular or SharePoint mode.|  
|[DISCOVER_STORAGE_TABLES Rowset](assetId:///13df6f10-8efe-4fe9-83a6-96d108809ed1)|Returns information about the tables used for storage of models in a Tabular model database.|  
|[DISCOVER_TRACE_COLUMNS Rowset](assetId:///02baf401-52b0-4a73-8a7b-3b5b5e568626)|Returns an XML description of the columns available in a trace.|  
|[DISCOVER_TRACE_DEFINITION_PROVIDERINFO Rowset](assetId:///8dda2ef7-202a-454b-93f9-a2b29c2d277c)|Returns name and version information of the provider.|  
|[DISCOVER_TRACE_EVENT_CATEGORIES Rowset](assetId:///1ad74fd2-4740-469d-85b5-abf0171737fd)|Returns a list of available categories.|  
|[DISCOVER_TRACES Rowset](assetId:///1be6a035-ffc9-489e-9d4d-7391b3e384e2)|Returns a list of traces actively running on the current connection.|  
|[DISCOVER_TRANSACTIONS Rowset](assetId:///85789177-c5df-4336-a90c-c20d69277ab4)|Returns a list of transactions actively running on the current connection.|  
|[DISCOVER_XEVENT_TRACE_DEFINITION Rowset](assetId:///e1ce2d2d-f994-4318-801a-ee0385aecd84)|Returns a list of xevent traces actively running on the current connection.|  
|[DMSCHEMA_MINING_COLUMNS Rowset](assetId:///ae35ccde-4438-46f4-8611-40b2b1a42fce)|Lists the individual columns of all mining models available on the current connection.|  
|[DMSCHEMA_MINING_FUNCTIONS Rowset](assetId:///9ace7493-a7b1-45ca-93de-3cb2f3597017)|Returns a list of functions supported by the data mining algorithms on the server.|  
|[DMSCHEMA_MINING_MODEL_CONTENT Rowset](assetId:///1e85d9e7-3b74-42ac-b94e-f52f76d8a25d)|Returns a rowset consisting of columns that describe the current model.|  
|[DMSCHEMA_MINING_MODEL_CONTENT_PMML Rowset](assetId:///fa05bb08-a955-4c8d-b57f-ffcd82470220)|Returns a rowset consisting of columns that describe the current model in PMML format.|  
|[DMSCHEMA_MINING_MODEL_XML Rowset](assetId:///f58b00e9-3f72-4cff-b448-21a9fb529772)|Returns a rowset consisting of columns that describe the current model in PMML format.|  
|[DMSCHEMA_MINING_MODELS Rowset](assetId:///1636f4cf-b342-4e2e-93b4-04136e2d41ef)|Returns a list of the mining models in the current database.|  
|[DMSCHEMA_MINING_SERVICE_PARAMETERS Rowset](assetId:///5994e66b-84d0-4279-9f50-d92fd829dd83)|Returns a list of the parameters for the algorithms on the server.|  
|[DMSCHEMA_MINING_SERVICES Rowset](assetId:///4a672f2f-d637-4def-a572-c18556f83d34)|Provides a list of the data mining algorithms available on the server.|  
|[DMSCHEMA_MINING_STRUCTURE_COLUMNS Rowset](assetId:///81f25502-ac90-42f1-8ddf-7b0f9752ebfd)|Returns a list of all of the columns from all of the mining models available in the current connection.|  
|[DMSCHEMA_MINING_STRUCTURES Rowset](assetId:///6224556b-08a0-496e-bd7c-632c3e833e26)|Lists the mining structures available in the current connection.|  
|[MDSCHEMA_CUBES Rowset](assetId:///5f1b63d4-aa3f-48c6-b866-7ffd91675044)|Returns information about the cubes that are defined in the current database.|  
|[MDSCHEMA_DIMENSIONS Rowset](assetId:///a0fd94bb-359a-4df6-93a6-d60d50223944)|Returns information about the dimensions that are defined in the current database.|  
|[MDSCHEMA_FUNCTIONS Rowset](assetId:///5253fa8c-b1ce-4504-aff6-a246b5e675c7)|Returns a list of functions available to client applications connected to the database.|  
|[MDSCHEMA_HIERARCHIES Rowset](assetId:///2e5b2a81-366e-4d5b-af1e-1d372bf596d9)|Returns information about the hierarchies that are defined in the current database.|  
|[MDSCHEMA_INPUT_DATASOURCES Rowset](assetId:///12482fd5-16e3-4171-9cb0-76d0d4f5308e)|Returns information about the data source objects that are defined in the current database.|  
|[MDSCHEMA_KPIS Rowset](assetId:///40fb5112-6a90-4455-82b3-8b6322490222)|Returns information about the KPIs that are defined in the current database.|  
|[MDSCHEMA_LEVELS Rowset](assetId:///4313e268-33f4-4e99-96d7-2ec26775c580)|Returns information about the levels within the hierarchies that are defined in the current database.|  
|[MDSCHEMA_MEASUREGROUP_DIMENSIONS](assetId:///c731c06a-7382-4e50-ba0e-d8cee3ab4f28)|Lists the dimension of measure groups.|  
|[MDSCHEMA_MEASUREGROUPS Rowset](assetId:///bab1bbd0-421b-4fad-9aee-e6511e0e1f1b)|Returns a list of measure groups in the current connection.|  
|[MDSCHEMA_MEASURES Rowset](assetId:///6ff5bd1a-aad0-49b8-9f8d-7df2637caacf)|Returns a list of measures in the current connection.|  
|[MDSCHEMA_MEMBERS Rowset](assetId:///0b1aada0-67f8-4ef6-81b2-0100b65e0c2f)|Returns a list of all members in the current connection, listed by database, cube, and dimension.|  
|[MDSCHEMA_PROPERTIES Rowset](assetId:///95c480f7-c525-44ba-a59b-cd36f5855a4f)|Returns a fully qualified name of each property, along with property type, data type, and other metadata.|  
|[MDSCHEMA_SETS Rowset](assetId:///abb00dc0-2b83-48d6-b2ba-6615c1488d06)|Returns a list of set that are defined in the current connection.|  
  
## See Also  
 [SQL Server 2008 R2 Analysis Services Operations Guide](http://go.microsoft.com/fwlink/?LinkID=225539&clcid=0x409)   
 [New System.Discover_Object_Activity](http://go.microsoft.com/fwlink/?linkid=221322)   
 [New SYSTEMRESTRICTEDSCHEMA Function for Restricted Rowsets and DMVs](http://go.microsoft.com/fwlink/?LinkId=231885)