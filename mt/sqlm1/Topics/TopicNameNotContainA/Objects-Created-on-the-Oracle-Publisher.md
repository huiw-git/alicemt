---
title: Objects Created on the Oracle Publisher
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c58a124b-4da7-46e2-9292-af8ce9e6664b
---
# Objects Created on the Oracle Publisher
  [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] replication installs database objects on the Oracle Publisher to enable change tracking and forwarding \([!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] does not install any binary files on the Oracle Publisher\). The following table lists the objects that are created at the Oracle Publisher when it is identified as a Publisher at the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Distributor. The object descriptions are provided for informational purposes only. These objects should not be modified.  
  
|Object Name|Object Type|Description|  
|-----------------|-----------------|-----------------|  
|HREPL\_ArticleNlog\_V|Table|Change tracking table used to store information as changes are made to the published table. A change tracking table is created for each published table.|  
|HREPL\_Changes|Table|Table used internally by the Xactset Job to determine the number of changes waiting to be assigned to a transaction set. For more information about this job, see [Performance Tuning for Oracle Publishers](../../Topics\TopicNameNotContainA/Performance-Tuning-for-Oracle-Publishers.md).|  
|HREPL\_Distributor|Table|Distributor status table used to maintain information about the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Distributor associated with the Oracle Publisher.|  
|HREPL\_Event|Table|Event table used for synchronizing snapshots and row count requests.|  
|HREPL\_Mutex|Table|Table used to ensure that the Oracle package procedure PopulatePollTable is not executed concurrently by both the Log Reader Agent and the database job.|  
|HREPL\_Poll|Table|Table used to identify log table entries associated with sets of changes to published tables.|  
|HREPL\_PublishedTables|Table|Table containing an entry for each article in a transactional publication.|  
|HREPL\_Publisher|Table|Publisher status table used for maintaining Publisher specific information.|  
|HREPL\_SchemaFilter|Table|Table containing schemas that are not displayed when publishing through the New Publication Wizard.|  
|HREPL\_XactsetCreateTimes|Table|Table identifying the create time associated with each transaction set.|  
|HREPL\_XactsetJob|Table|Table with current parameter settings for the Xactset Job.|  
|HREPL\_Pollid|Sequence|Sequence used to generate poll IDs.|  
|HREPL\_Seq|Sequence|Sequence used to order change commands.|  
|HREPL\_Stmt|Sequence|Sequence used to generate statement IDs.|  
|HREPL|Package and Package Body|Package of Publisher support code that is created at the Publisher.|  
|MSSQLSERVERDISTRIBUTOR|Public Synonym|Public synonym for the HREPL\_Distributor table. If you configure a Distributor to use with an Oracle Publisher, and this synonym already exists in the database, it is dropped and recreated.<br /><br /> Dropping the public synonym and the configured Oracle replication user with the CASCADE option removes all replication objects from the Oracle Publisher.|  
|HREPL\_Len\_I\_J\_K|Function|Function defined outside the Oracle publishing package code, used to query for the length of a LONG column \(used when generating parameterized commands for tables with published LONG columns\). A function is created for each published table with a LONG column.|  
|HREPL\_DropPublisher|Procedure|Procedure defined outside the Oracle publishing package code, used to drop the Oracle Publisher.|  
|HREPL\_ExecuteCommand|Procedure|Procedure defined outside the Oracle publishing package code, used to execute a command at the Publisher.|  
|HREPL\_ArticleN\_Trigger\_Row|Trigger|Trigger generated for each published table, used to track row changes.|  
|HREPL\_ArticleN\_Trigger\_Stmt|Trigger|Trigger generated for each published table, used to track statement level changes.|  
|HREPL\_Article\_I\_J|View|View created for each published table, used to query the published table.|  
|HREPL\_Log\_I\_J\_K|View|View created for each published table, used to query the change tracking table.|  
  
## See Also  
 [Configure an Oracle Publisher](../../Topics\TopicNameNotContainA/Configure-an-Oracle-Publisher.md)   
 [Glossary of Terms for Oracle Publishing](../../Topics\TopicNameNotContainA/Glossary-of-Terms-for-Oracle-Publishing.md)   
 [Oracle Publishing Overview](../../Topics\TopicNameNotContainA/Oracle-Publishing-Overview.md)  
  
  