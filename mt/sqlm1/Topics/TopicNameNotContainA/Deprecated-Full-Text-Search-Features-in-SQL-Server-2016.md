---
title: Deprecated Full-Text Search Features in SQL Server 2016
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab0d799c-ba79-4459-837b-c4862730dafd
---
# Deprecated Full-Text Search Features in SQL Server 2016
  This topic describes the deprecated full\-text search features that are still available in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. These features are scheduled to be removed in a future release of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Deprecated features should not be used in new applications.  
  
 You can monitor the use of deprecated features by using the **SQL Server:Deprecated Features** object performance counter and trace events. For more information, see [Use SQL Server Objects](../../Topics\TopicNameNotContainA/Use-SQL-Server-Objects.md).  
  
## Features Not Supported in the Next Version of SQL Server  
 The following full\-text search features will not be supported in the next release of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
|Deprecated feature|Replacement|Feature name|Feature ID|  
|------------------------|-----------------|------------------|----------------|  
|FULLTEXTCATALOGPROPERTY property: LogSize|None.|FULLTEXTCATALOGPROPERTY**\('LogSize'\)**|211|  
|FULLTEXTSERVICEPROPERTY property:<br /><br /> ConnectTimeout<br /><br /> DataTimeout|None.|FULLTEXTSERVICEPROPERTY**\('ConnectTimeout'\)**<br /><br /> FULLTEXTSERVICEPROPERTY**\('DataTimeout'**\)|210<br /><br /> 209|  
|sp\_fulltext\_catalog|CREATE FULL CATALOG<br /><br /> ALTER FULLTEXT CATALOG<br /><br /> DROP FULLTEXT CATALOG|sp\_fulltext\_catalog|84|  
|sp\_fulltext\_column<br /><br /> sp\_fulltext\_database<br /><br /> sp\_fulltext\_table|CREATE FULL INDEX<br /><br /> ALTER FULLTEXT INDEX<br /><br /> DROP FULLTEXT INDEX|sp\_fulltext\_column<br /><br /> sp\_fulltext\_database<br /><br /> sp\_fulltext\_table|86<br /><br /> 87<br /><br /> 85|  
|sp\_help\_fulltext\_catalogs<br /><br /> sp\_help\_fulltext\_catalog\_components<br /><br /> sp\_help\_fulltext\_catalogs\_cursor<br /><br /> sp\_help\_fulltext\_columns<br /><br /> sp\_help\_fulltext\_columns\_cursor<br /><br /> sp\_help\_fulltext\_tables<br /><br /> sp\_help\_fulltext\_tables\_cursor|sys.fulltext\_catalogs<br /><br /> sys.fulltext\_index\_columns<br /><br /> sys.fulltext\_indexes|sp\_help\_fulltext\_catalogs<br /><br /> sp\_help\_fulltext\_catalog\_components<br /><br /> sp\_help\_fulltext\_catalogs\_cursor<br /><br /> sp\_help\_fulltext\_columns<br /><br /> sp\_help\_fulltext\_columns\_cursor<br /><br /> sp\_help\_fulltext\_table<br /><br /> sp\_help\_fulltext\_tables\_cursor|88<br /><br /> 203<br /><br /> 90<br /><br /> 92<br /><br /> 93<br /><br /> 91<br /><br /> 89|  
|sp\_fulltext\_service action values: clean\_up, connect\_timeout, and data\_timeout return zero|None|sp\_fulltext\_service @action\=clean\_up<br /><br /> sp\_fulltext\_service @action\=connect\_timeout<br /><br /> sp\_fulltext\_service @action\=data\_timeout|116<br /><br /> 117<br /><br /> 118|  
|sys.dm\_fts\_active\_catalogs columns:<br /><br /> is\_paused<br /><br /> previous\_status<br /><br /> previous\_status\_description<br /><br /> row\_count\_in\_thousands<br /><br /> status<br /><br /> status\_description<br /><br /> worker\_count|None.|dm\_fts\_active\_catalogs.is\_paused<br /><br /> dm\_fts\_active\_catalogs.previous\_status<br /><br /> dm\_fts\_active\_catalogs.previous\_status\_description<br /><br /> dm\_fts\_active\_catalogs.row\_count\_in\_thousands<br /><br /> dm\_fts\_active\_catalogs.status<br /><br /> dm\_fts\_active\_catalogs.status\_description<br /><br /> dm\_fts\_active\_catalogs.worker\_count|218<br /><br /> 221<br /><br /> 222<br /><br /> 224<br /><br /> 219<br /><br /> 220<br /><br /> 223|  
|sys.dm\_fts\_memory\_buffers column:<br /><br /> row\_count|None.|dm\_fts\_memory\_buffers.row\_count|225|  
|sys.fulltext\_catalogs columns:<br /><br /> path<br /><br /> data\_space\_id<br /><br /> file\_id columns|None.|fulltext\_catalogs.path<br /><br /> fulltext\_catalogs.data\_space\_id<br /><br /> fulltext\_catalogs.file\_id|215<br /><br /> 216<br /><br /> 217|  
  
## Features Not Supported in a Future Version of SQL Server  
 The following full\-text search features are supported in the next version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], but will be removed in a later version. The specific version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] has not been determined.  
  
 The **Feature name** value appears in trace events as the ObjectName and in performance counters and sys.dm\_os\_performance\_counters as the instance name. The **Feature ID** value appears in trace events as the ObjectId.  
  
|Deprecated feature|Replacement|Feature name|Feature ID|  
|------------------------|-----------------|------------------|----------------|  
|CONTAINS and CONTAINSTABLE generic NEAR operator:<br /><br /> {\<simple\_term\> &#124; \<prefix\_term\>}<br /><br /> {<br /><br /> { { NEAR &#124; ~ }    {\<simple\_term\> &#124; \<prefix\_term\>} } \[...*n*\]<br /><br /> }|The custom NEAR operator:<br /><br /> NEAR\(<br /><br /> {   {\<simple\_term\> &#124; \<prefix\_term\>} \[ ,…*n* \]<br /><br /> &#124; \( {\<simple\_term\> &#124; \<prefix\_term\>} \[,…*n*\] \)<br /><br /> \[,\<distance\> \[,\<order\>\] \]<br /><br /> }<br /><br /> \)<br /><br /> \<distance\> ::\= {*integer* &#124; **MAX**}<br /><br /> \<order\> ::\= {TRUE &#124; **FALSE**}|FULLTEXT\_OLD\_NEAR\_SYNTAX|247|  
|CREATE FULLTEXT CATALOG option:<br /><br /> IN PATH '*rootpath*'<br /><br /> ON FILEGROUP *filegroup*|None.|CREATE FULLTEXT CATLOG IN PATH<br /><br /> None.<sup>*</sup>|237<br /><br /> None.\*|  
|DATABASEPROPERTYEX property: IsFullTextEnabled|None.|DATABASEPROPERTYEX**\('IsFullTextEnabled'\)**|202|  
|sp\_detach\_db option:<br /><br /> \[ @keepfulltextindexfile \= \] '*KeepFulltextIndexFile*'|None.|sp\_detach\_db @keepfulltextindexfile|226|  
|sp\_fulltext\_service action values: resource\_usage has no function.|None|sp\_fulltext\_service @action\=resource\_usage|200|  
  
 \*The **SQL Server:Deprecated Features** object does not monitor occurrences of CREATE FULLTEXT CATLOG ON FILEGROUP *filegroup*.  
  
## See Also  
 [SQL Server, Deprecated Features Object](../../Topics\TopicNameNotContainA/SQL-Server,-Deprecated-Features-Object.md)   
 [Breaking Changes to Full-Text Search](../../Topics\TopicNameNotContainA/Breaking-Changes-to-Full-Text-Search.md)   
 [Deprecated Database Engine Features in SQL Server 2016](../../Topics\TopicNameNotContainA/Deprecated-Database-Engine-Features-in-SQL-Server-2016.md)  
  
  