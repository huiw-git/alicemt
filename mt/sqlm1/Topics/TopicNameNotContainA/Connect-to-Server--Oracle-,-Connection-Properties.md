---
title: Connect to Server (Oracle), Connection Properties
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
---
# Connect to Server (Oracle), Connection Properties
  Use the **Connection Properties** tab of the **Connect to Server** dialog box to specify a publishing option of **Gateway** or **Complete**. After a Publisher is identified, this option cannot be changed without dropping and reconfiguring the Publisher. For more information, see [Configure an Oracle Publisher](../../Topics\TopicNameNotContainA/Configure-an-Oracle-Publisher.md).  
  
## Options  
 **Publisher type**  
 Select **Gateway** or **Complete**. The **Complete** option is designed to provide snapshot and transactional publications with the complete set of supported features for Oracle publishing. The **Gateway** option provides specific design optimizations to improve performance for cases where replication serves as a gateway between systems. The **Gateway** option cannot be used if you plan to publish the same table in multiple transactional publications. A table can appear in at most one transactional publication and any number of snapshot publications if you select **Gateway**.  
  
 **Timeouts**  
 Specify how long the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Distributor should attempt to connect to the Oracle Publisher before a timeout error occurs.  
  
## See Also  
 [Glossary of Terms for Oracle Publishing](../../Topics\TopicNameNotContainA/Glossary-of-Terms-for-Oracle-Publishing.md)   
 [Performance Tuning for Oracle Publishers](../../Topics\TopicNameNotContainA/Performance-Tuning-for-Oracle-Publishers.md)  
  
  