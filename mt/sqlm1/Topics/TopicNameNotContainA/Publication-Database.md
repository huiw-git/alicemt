---
title: Publication Database
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
---
# Publication Database
  The publication database is the database on the Publisher that is the source of data and database objects to be replicated. Each publication database used in replication must be enabled. The database is enabled when a member of the **sysadmin** fixed server role:  
  
-   Creates a publication on that database using the New Publication Wizard.  
  
-   Selects the database in the **Publisher Properties** dialog box.  
  
-   Executes **sp\_replicationdboption** and sets the option **publish** \(for snapshot or transactional publications\) or **merge publish** \(for merge publications\) to **True**.  
  
## Options  
 **Databases**  
 Select the name of the database that contains the data and database objects that you want to publish.  
  
## See Also  
 [Publish Data and Database Objects](../../Topics\TopicNameNotContainA/Publish-Data-and-Database-Objects.md)   
 [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md)   
 [View and Modify Distributor and Publisher Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Distributor-and-Publisher-Properties.md)   
 [sp_replicationdboption &#40;Transact-SQL&#41;](../Topic/sp_replicationdboption%20\(Transact-SQL\).md)  
  
  