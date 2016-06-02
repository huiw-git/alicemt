---
title: Publisher Properties - Publisher, Publication Databases
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 574ea2e7-4e7b-4733-ab52-429ca93c7b0a
---
# Publisher Properties - Publisher, Publication Databases
  The **Publication Databases** page of the **Publisher Properties** dialog box allows a user in the **sysadmin** fixed server role to enable databases for replication. Enabling a database does not publish that database; rather, it allows any user in the **db\_owner** fixed database role for that database to create one or more publications on the database.  
  
## Options  
 **Transactional**  
 Select this check box to allow users in the **db\_owner** fixed database role to create snapshot publications or transactional publications in the database.  
  
 **Merge**  
 Select this check box to allow users in the **db\_owner** fixed database role to create merge publications in the database.  
  
## See Also  
 [View and Modify Distributor and Publisher Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Distributor-and-Publisher-Properties.md)   
 [Properties Reference &#40;Replication&#41;](../Topic/Properties%20Reference%20\(Replication\).md)  
  
  