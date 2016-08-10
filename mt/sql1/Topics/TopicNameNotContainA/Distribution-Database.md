---
title: "Distribution Database"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5b42a083-7a11-41d8-9e3f-320c7c907237
caps.latest.revision: 27
caps.handback.revision: 0
manager: jhubbard
---
# Distribution Database
The distribution database stores metadata and history data for all types of replication, and transactions for transactional replication.  
  
 In many cases, a single distribution database is sufficient. However, if multiple Publishers use a single Distributor, consider creating a distribution database for each Publisher. Doing so ensures that the data flowing through each distribution database is distinct. You can specify one distribution database for the Distributor using the Configure Distribution Wizard. If necessary, specify additional distribution databases in the **Distributor Properties** dialog box.  
  
## Options  
 **Distribution database name**  
 Enter a name for the distribution database. The default name for the distribution database is 'distribution'. If you specify a name, the name can be a maximum of 128 characters, must be unique within an instance of [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], and must conform to the rules for identifiers. For more information, see [Database Identifiers](../../Topics/TopicNameNotContainA/Database-Identifiers.md).  
  
 **Folder for the distribution database file** and **Folder for the distribution database log file**  
 Enter the path for the distribution database and log files. Paths must refer to disks that are local to the Distributor and begin with a local drive letter and colon (for example, C:). Mapped drive letters and network paths are not valid.  
  
> [!NOTE]  
>  You can decrease the time it takes to write transactions and improve the performance of replication by placing the distribution database log on a separate disk drive from the distribution database.  
  
## See Also  
 [Configure Distribution](../../Topics/TopicNameNotContainA/Configure-Distribution.md)   
 [Configure Publishing and Distribution](../../Topics/TopicNameNotContainA/Configure-Publishing-and-Distribution.md)   
 [View and Modify Distributor and Publisher Properties](../../Topics/TopicNameNotContainA/View-and-Modify-Distributor-and-Publisher-Properties.md)