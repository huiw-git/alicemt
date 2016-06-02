---
title: Publisher Properties - Distributor
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab6ada76-0f99-43fe-b524-baac7b1bc483
---
# Publisher Properties - Distributor
  The **Publisher Properties** dialog box allows you to view and modify properties associated with the relationship between the Publisher and its Distributor.  
  
## Options  
 **Agent Connection to the Publisher**  
 Specify the context under which the following agents make connections from the Distributor to the Publisher:  
  
-   The Queue Reader Agent for transactional publications that allow queued updating subscriptions.  
  
-   The Snapshot Agent and Log Reader Agent for Oracle publications.  
  
 Select **Impersonate agent process account** to make connections to the Publisher using the context of the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows account under which these agents run, or specify **SQL Server Authentication**, and then enter a value for **Login** and **Password**. It is recommended that you select **Impersonate agent process account**. For more information on agent security, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
 The Windows accounts under which these agents run are specified in the New Publication Wizard. These accounts can be changed:  
  
-   In the **Distributor Properties** dialog box for the Queue Reader Agent.  
  
-   In the **Publication Properties** dialog box for the Snapshot Agent and Log Reader Agent.  
  
 **Miscellaneous**  
 The properties **Publisher Type** and **Distribution Database Name** are read\-only. The property **Default Snapshot Folder** can be changed. For more information about the snapshot folder, see [Secure the Snapshot Folder](../../Topics\TopicNameNotContainA/Secure-the-Snapshot-Folder.md).  
  
## See Also  
 [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md)   
 [View and Modify Distributor and Publisher Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Distributor-and-Publisher-Properties.md)   
 [Properties Reference &#40;Replication&#41;](../Topic/Properties%20Reference%20\(Replication\).md)  
  
  