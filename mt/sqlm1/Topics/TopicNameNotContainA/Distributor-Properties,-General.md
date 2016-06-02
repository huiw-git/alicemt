---
title: Distributor Properties, General
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab4120ec-e524-4c0c-8b48-f2f40adb1a3b
---
# Distributor Properties, General
  The **General** page of the **Distributor Properties** dialog box allows you to add and delete distribution databases and set distribution database properties.  
  
 The distribution database stores metadata and history data for all types of replication, and transactions for transactional replication. In many cases, a single distribution database is sufficient. But if multiple Publishers use a single Distributor, consider creating a distribution database for each Publisher. Doing so ensures that the data flowing through each distribution database is distinct.  
  
## Options  
 **Databases**  
 The **Databases** property grid shows the name and retention properties of the distribution databases on the Distributor. **Transaction Retention** is the length of time transactions are stored for transactional replication \(transaction retention is also known as distribution retention\). **History Retention** is the length of time history metadata is stored for all types of replication. For more information about distribution retention, see [Subscription Expiration and Deactivation](../../Topics\TopicNameNotContainA/Subscription-Expiration-and-Deactivation.md).  
  
 Click the properties button \(**...**\) in the **Databases** property grid to launch the **Distribution Database Properties** dialog box.  
  
 **New**  
 Click to create a new distribution database.  
  
 **Delete**  
 Select an existing distribution database in the **Databases** property grid, and click **Delete** to delete the database. You cannot delete the distribution database if there is only one such database; each Distributor must have at least one distribution database. To delete all distribution databases, you must disable distribution on the computer. For more information, see [Disable Publishing and Distribution](../../Topics\TopicNameNotContainA/Disable-Publishing-and-Distribution.md).  
  
 **Profile Defaults**  
 Click to access replication agent profiles in the **Agent Profiles** dialog box. For more information about profiles, see [Replication Agent Profiles](../../Topics\TopicNameNotContainA/Replication-Agent-Profiles.md).  
  
## See Also  
 [Configure Distribution](../../Topics\TopicNameNotContainA/Configure-Distribution.md)   
 [View and Modify Distributor and Publisher Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Distributor-and-Publisher-Properties.md)  
  
  