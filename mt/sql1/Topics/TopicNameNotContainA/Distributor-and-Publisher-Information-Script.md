---
title: "Distributor and Publisher Information Script"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8622db47-c223-48fa-87ff-0b4362cd069a
caps.latest.revision: 13
caps.handback.revision: 0
manager: jhubbard
---
# Distributor and Publisher Information Script
This script uses system tables and replication stored procedures to answer questions commonly asked about objects at the Distributor and Publisher. The script can be used "as-is" and can also provide the basis for customized scripts. The script might require two modifications to run in your environment:  
  
-   Change the line `use AdventureWorks2012` to use the name of your publication database.  
  
-   Remove the comments (`--`) from the line `exec sp_helparticle @publication='<PublicationName>'` and replace <PublicationName\> with the name of a publication.  
  
```  
--********** Execute at the Distributor in the master database **********--  
  
USE master;  
go  
  
--Is the current server a Distributor?  
--Is the distribution database installed?  
--Are there other Publishers using this Distributor?  
EXEC sp_get_distributor  
  
--Is the current server a Distributor?  
SELECT is_distributor FROM sys.servers WHERE name='repl_distributor' AND data_source=@@servername;  
  
--Which databases on the Distributor are distribution databases?  
SELECT name FROM sys.databases WHERE is_distributor = 1  
  
--What are the Distributor and distribution database properties?  
EXEC sp_helpdistributor;  
EXEC sp_helpdistributiondb;  
EXEC sp_helpdistpublisher;  
  
--********** Execute at the Publisher in the master database **********--  
  
--Which databases are published for replication and what type of replication?  
EXEC sp_helpreplicationdboption;  
  
--Which databases are published using snapshot replication or transactional replication?  
SELECT name as tran_published_db FROM sys.databases WHERE is_published = 1;  
--Which databases are published using merge replication?  
SELECT name as merge_published_db FROM sys.databases WHERE is_merge_published = 1;  
  
--What are the properties for Subscribers that subscribe to publications at this Publisher?  
EXEC sp_helpsubscriberinfo;  
  
--********** Execute at the Publisher in the publication database **********--  
  
USE AdventureWorks2012;  
go  
  
--What are the snapshot and transactional publications in this database?   
EXEC sp_helppublication;  
--What are the articles in snapshot and transactional publications in this database?  
--REMOVE COMMENTS FROM NEXT LINE AND REPLACE <PublicationName> with the name of a publication  
--EXEC sp_helparticle @publication='<PublicationName>';  
  
--What are the merge publications in this database?   
EXEC sp_helpmergepublication;  
--What are the articles in merge publications in this database?  
EXEC sp_helpmergearticle; -- to return information on articles for a single publication, specify @publication='<PublicationName>'  
  
--Which objects in the database are published?  
SELECT name AS published_object, schema_id, is_published AS is_tran_published, is_merge_published, is_schema_published  
FROM sys.tables WHERE is_published = 1 or is_merge_published = 1 or is_schema_published = 1  
UNION  
SELECT name AS published_object, schema_id, 0, 0, is_schema_published  
FROM sys.procedures WHERE is_schema_published = 1  
UNION  
SELECT name AS published_object, schema_id, 0, 0, is_schema_published  
FROM sys.views WHERE is_schema_published = 1;  
  
--Which columns are published in snapshot or transactional publications in this database?  
SELECT object_name(object_id) AS tran_published_table, name AS published_column FROM sys.columns WHERE is_replicated = 1;  
  
--Which columns are published in merge publications in this database?  
SELECT object_name(object_id) AS merge_published_table, name AS published_column FROM sys.columns WHERE is_merge_published = 1;  
```  
  
## See Also  
 [Frequently Asked Questions for Replication Administrators](../../Topics/TopicNameNotContainA/Frequently-Asked-Questions-for-Replication-Administrators.md)   
 [sp_get_distributor (Transact-SQL)](assetId:///f0134448-bc17-4f2f-bd81-619351ce56ac)   
 [sp_helparticle (Transact-SQL)](assetId:///9c4a1a88-56f1-45a0-890c-941b8e0f0799)   
 [sp_helpdistributiondb (Transact-SQL)](assetId:///a2917020-26d1-4011-99f8-9212d120fd2d)   
 [sp_helpdistpublisher (Transact-SQL)](assetId:///f207c22d-8fb2-4756-8a9d-6c51d6cd3470)   
 [sp_helpdistributor (Transact-SQL)](assetId:///37b0983e-3b69-4f0f-977e-20efce0a0b97)   
 [sp_helpmergearticle (Transact-SQL)](assetId:///0fb9986a-3c33-46ef-87bb-297396ea5a6a)   
 [sp_helpmergepublication (Transact-SQL)](assetId:///dfe1e1e1-9a65-406a-aced-6385a078e135)   
 [sp_helppublication (Transact-SQL)](assetId:///e801c3f0-dcbd-4b4a-b254-949a05f63518)   
 [sp_helpreplicationdboption (Transact-SQL)](assetId:///143ce689-108b-49d7-9892-fd3a86897f38)   
 [sp_helpsubscriberinfo (Transact-SQL)](assetId:///fbabe1ec-57cf-425c-bae7-af7f5d3198fd)   
 [sys.columns (Transact-SQL)](assetId:///323ac9ea-fc52-4b8c-8a7e-e0e44f8ed86c)   
 [sys.databases (Transact-SQL)](assetId:///46c288c1-3410-4d68-a027-3bbf33239289)   
 [sys.procedures (Transact-SQL)](assetId:///d17af274-b2dd-464e-9523-ee1f43e1455b)   
 [sys.servers (Transact-SQL)](assetId:///4e774ed9-4e83-4726-9f1d-8efde8f9feff)   
 [sys.tables (Transact-SQL)](assetId:///8c42eba1-c19f-4045-ac82-b97a5e994090)   
 [sys.views (Transact-SQL)](assetId:///f8a8ea39-5a09-4662-801e-b43519467def)