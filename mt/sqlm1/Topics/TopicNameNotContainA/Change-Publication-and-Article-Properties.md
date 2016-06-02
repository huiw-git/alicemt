---
title: Change Publication and Article Properties
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7df51ef-c088-4efc-b247-f91fb2c6ff32
---
# Change Publication and Article Properties
  After a publication has been created, most publication and article properties can be changed, but some require that the snapshot be regenerated and\/or subscriptions be reinitialized. This topic provides information about all properties that require one or both of these actions if they are changed.  
  
## Publication Properties for Snapshot and Transactional Replication  
  
|Description|Stored procedure|Properties|Requirements|  
|-----------------|----------------------|----------------|------------------|  
|Change snapshot format.|**sp\_changepublication**|**sync\_method**|New snapshot.|  
|Change snapshot location.|**sp\_changepublication**|**alt\_snapshot\_folder**<br /><br /> **snapshot\_in\_defaultfolder**|New snapshot.|  
|Change snapshot location.|**sp\_changedistpublisher**|**working\_directory**|New snapshot.|  
|Change snapshot compression.|**sp\_changepublication**|**compress\_snapshot**|New snapshot.|  
|Change any File Transfer Protocol \(FTP\) snapshot options.|**sp\_changepublication**|**enabled\_for\_internet**<br /><br /> **ftp\_address**<br /><br /> **ftp\_login**<br /><br /> **ftp\_password**<br /><br /> **ftp\_port**<br /><br /> **ftp\_subdirectory**|New snapshot.|  
|Change pre\- or post\-snapshot script location.|**sp\_changepublication**|**pre\_snapshot\_script**<br /><br /> **post\_snapshot\_script**|New snapshot \(also required if you change the script contents\).<br /><br /> Reinitialization is required to apply the new script to the Subscriber.|  
|Enable or disable support for non\-[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Subscribers.|**sp\_changepublication**|**is\_enabled\_for\_het\_sub**|New snapshot.|  
|Change conflict reporting for queued updating subscriptions|**sp\_changepublication**|**centralized\_conflicts**|Can only be changed if there are no active subscriptions.|  
|Change conflict resolution policy for queued updating subscriptions.|**sp\_changepublication**|**conflict\_policy**|Can only be changed if there are no active subscriptions.|  
  
## Article Properties for Snapshot and Transactional Replication  
  
|Description|Stored procedure|Properties|Requirements|  
|-----------------|----------------------|----------------|------------------|  
|Drop an article|**sp\_droparticle**|All parameters.|Articles can be dropped prior to subscriptions being created. Using stored procedures, it is possible to drop a subscription to an article; using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], the entire subscription must be dropped, recreated, and synchronized. For more information, see [Add Articles to and Drop Articles from Existing Publications](../../Topics\TopicNameNotContainA/Add-Articles-to-and-Drop-Articles-from-Existing-Publications.md).|  
|Change a column filter.|**sp\_articlecolumn**|**@column**<br /><br /> **@operation**|New snapshot.<br /><br /> Reinitialize subscriptions.|  
|Add a row filter.|**sp\_articlefilter**|All parameters.|New snapshot.<br /><br /> Reinitialize subscriptions.|  
|Drop a row filter.|**sp\_articlefilter**|**@article**|New snapshot.<br /><br /> Reinitialize subscriptions.|  
|Change a row filter.|**sp\_articlefilter**|**@filter\_clause**|New snapshot.<br /><br /> Reinitialize subscriptions.|  
|Change a row filter.|**sp\_changearticle**|**filter**|New snapshot.<br /><br /> Reinitialize subscriptions.|  
|Change schema options.|**sp\_changearticle**|**schema\_option**|New snapshot.|  
|Change how tables at the Subscriber are handled prior to applying the snapshot.|**sp\_changearticle**|**pre\_creation\_cmd**|New snapshot.|  
|Change article status|**sp\_changearticle**|**status**|New snapshot.|  
|Change INSERT, UPDATE or DELETE commands.|**sp\_changearticle**|**ins\_cmd**<br /><br /> **upd\_cmd**<br /><br /> **del\_cmd**|New snapshot.<br /><br /> Reinitialize subscriptions.|  
|Change destination table name|**sp\_changearticle**|**dest\_table**|New snapshot.<br /><br /> Reinitialize subscriptions.|  
|Change destination table owner \(schema\).|**sp\_changearticle**|**destination\_owner**|New snapshot.<br /><br /> Reinitialize subscriptions.|  
|Change data type mappings \(applies to Oracle publishing only\).|**sp\_changearticlecolumndatatype**|**@type**<br /><br /> **@length**<br /><br /> **@precision**<br /><br /> **@scale**|New snapshot.<br /><br /> Reinitialize subscriptions.|  
  
## Publication Properties for Merge Replication  
  
|Description|Stored procedure|Properties|Requirements|  
|-----------------|----------------------|----------------|------------------|  
|Change snapshot format|**sp\_changemergepublication**|**sync\_mode**|New snapshot.|  
|Change snapshot location.|**sp\_changemergepublication**|**alt\_snapshot\_folder**<br /><br /> **snapshot\_in\_defaultfolder**|New snapshot.|  
|Change snapshot location.|**sp\_changedistpublisher**|**working\_directory**|New snapshot.|  
|Change snapshot compression|**sp\_changemergepublication**|**compress\_snapshot**|New snapshot.|  
|Change any FTP snapshot options|**sp\_changemergepublication**|**enabled\_for\_internet**<br /><br /> **ftp\_address**<br /><br /> **ftp\_login**<br /><br /> **ftp\_password**<br /><br /> **ftp\_port**<br /><br /> **ftp\_subdirectory**|New snapshot.|  
|Change pre\- or post\-snapshot scripts.|**sp\_changemergepublication**|**pre\_snapshot\_script**<br /><br /> **post\_snapshot\_script**|New snapshot \(also required if you change the script contents\).<br /><br /> Reinitialization is required to apply the new script to the Subscriber.|  
|Add a join filter or logical record.|**sp\_addmergefilter**|All parameters.|New snapshot.<br /><br /> Reinitialize subscriptions.|  
|Drop a join filter or logical record.|**sp\_dropmergefilter**|All parameters.|New snapshot.<br /><br /> Reinitialize subscriptions.|  
|Change a join filter or logical record.|**sp\_changemergefilter**|**@property**<br /><br /> **@value**|New snapshot<br /><br /> Reinitialize subscriptions.|  
|Disable the use of parameterized filters \(enabling parameterized filters does not require any special actions\).|**sp\_changemergepublication**|A value of **false** for **dynamic\_filters**|New snapshot.<br /><br /> Reinitialize subscriptions.|  
|Enable or disable the use of precomputed partitions.|**sp\_changemergepublication**|**use\_partition\_groups**|New snapshot.|  
|Enable or disable [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssVersion2000](../../Token\Other/ssVersion2000_md.md)] partition optimization.|**sp\_changemergepublication**|**keep\_partition\_changes**|Reinitialize subscriptions.|  
|Enable or disable Subscriber partition validation.|**sp\_changemergepublication**|**validate\_subscriber\_info**|Reinitialize subscriptions.|  
|Change the publication compatibility level to 80sp3 or lower.|**sp\_changemergepublication**|**publication\_compatibility\_level**|New snapshot.|  
  
## Article Properties for Merge Replication  
  
|Description|Stored Procedure|Properties|Requirements|  
|-----------------|----------------------|----------------|------------------|  
|Drop an article, where the article has the last parameterized filter in the publication.|**sp\_dropmergearticle**|All parameters|New snapshot.<br /><br /> Reinitialize subscriptions.|  
|Drop an article, where the article is a parent in a join filter or logical record \(this has the side effect of dropping the join\).|**sp\_dropmergearticle**|All parameters|New snapshot.<br /><br /> Reinitialize subscriptions.|  
|Drop an article, all other circumstances.|**sp\_dropmergearticle**|All parameters|New snapshot.|  
|Include a column filter that was previously unpublished.|**sp\_mergearticlecolumn**|**@column**<br /><br /> **@operation**|New snapshot.<br /><br /> Reinitialize subscriptions.|  
|Add, drop, or change a row filter.|**sp\_changemergearticle**|**subset\_filterclause**|New snapshot.<br /><br /> Reinitialize subscriptions.<br /><br /> If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization. If you want to upload pending changes, synchronize all subscriptions before changing the filter.<br /><br /> If an article is not involved in any join filters, you can drop the article and add it again with a different row filter, which does not require the entire subscription to be reinitialized. For more information about adding and dropping articles, see [Add Articles to and Drop Articles from Existing Publications](../../Topics\TopicNameNotContainA/Add-Articles-to-and-Drop-Articles-from-Existing-Publications.md).|  
|Change schema options.|**sp\_changemergearticle**|**schema\_option**|New snapshot.|  
|Change tracking from column\-level to row\-level \(changing from row\-level tracking to column\-level tracking does not require any special actions\).|**sp\_changemergearticle**|A value of **false** for **column\_tracking**|New snapshot.<br /><br /> Reinitialize subscriptions.|  
|Change whether permissions are checked before statements made at the Subscriber are applied at the Publisher.|**sp\_changemergearticle**|**check\_permissions**|New snapshot.<br /><br /> Reinitialize subscriptions.|  
|Enable or disable download\-only subscriptions \(changing to or from other upload options does not require any special actions\).|**sp\_changemergearticle**|Change to or from a value of **2** for **subscriber\_upload\_options**|Reinitialize subscriptions.|  
|Change destination table owner.|**sp\_changemergearticle**|**destination\_owner**|New snapshot.<br /><br /> Reinitialize subscriptions.|  
  
## See Also  
 [Administration &#40;Replication&#41;](../Topic/Administration%20\(Replication\).md)   
 [Create and Apply the Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Snapshot.md)   
 [Reinitialize Subscriptions](../../Topics\TopicNameNotContainA/Reinitialize-Subscriptions.md)   
 [sp_addmergefilter &#40;Transact-SQL&#41;](../Topic/sp_addmergefilter%20\(Transact-SQL\).md)   
 [sp_articlecolumn &#40;Transact-SQL&#41;](../Topic/sp_articlecolumn%20\(Transact-SQL\).md)   
 [sp_articlefilter &#40;Transact-SQL&#41;](../Topic/sp_articlefilter%20\(Transact-SQL\).md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../Topic/sp_changearticle%20\(Transact-SQL\).md)   
 [sp_changearticlecolumndatatype &#40;Transact-SQL&#41;](../Topic/sp_changearticlecolumndatatype%20\(Transact-SQL\).md)   
 [sp_changedistpublisher &#40;Transact-SQL&#41;](../Topic/sp_changedistpublisher%20\(Transact-SQL\).md)   
 [sp_changemergearticle &#40;Transact-SQL&#41;](../Topic/sp_changemergearticle%20\(Transact-SQL\).md)   
 [sp_changemergefilter &#40;Transact-SQL&#41;](../Topic/sp_changemergefilter%20\(Transact-SQL\).md)   
 [sp_changemergepublication &#40;Transact-SQL&#41;](../Topic/sp_changemergepublication%20\(Transact-SQL\).md)   
 [sp_changepublication &#40;Transact-SQL&#41;](../Topic/sp_changepublication%20\(Transact-SQL\).md)   
 [sp_droparticle &#40;Transact-SQL&#41;](../Topic/sp_droparticle%20\(Transact-SQL\).md)   
 [sp_dropmergearticle &#40;Transact-SQL&#41;](../Topic/sp_dropmergearticle%20\(Transact-SQL\).md)   
 [sp_dropmergefilter &#40;Transact-SQL&#41;](../Topic/sp_dropmergefilter%20\(Transact-SQL\).md)   
 [sp_mergearticlecolumn &#40;Transact-SQL&#41;](../Topic/sp_mergearticlecolumn%20\(Transact-SQL\).md)  
  
  