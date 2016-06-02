---
title: Complete the Database Engine Upgrade
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3f08087e-e532-416c-8caa-e0ec88c57596
---
# Complete the Database Engine Upgrade
  After the upgrade to SQL Server 2016 is complete, there are a number of additional steps that you may need to take. These include the following:  
  
 After upgrading the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], complete the following tasks:  
  
-   **Backup your databases:** Perform a full backup of each upgraded database.  
  
-   **Enable new features:** In SQL Server 2016, some changes are only enabled once the DATABASE\_COMPATIBILITY level for a database has been changed to 130.  For more information and for the recommended workflow, see [Change the Database Compatibility Mode and Use the Query Store](../../Topics\TopicNameNotContainA/Change-the-Database-Compatibility-Mode-and-Use-the-Query-Store.md).  
  
-   **Integration Services:**  
  
     Migrate Integration Services packages to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] format. For more information, see [Upgrade Integration Services Packages](../../Topics\TopicNameNotContainA/Upgrade-Integration-Services-Packages.md).  
  
-   **Reporting Services:** For a new installation upgrade, restore the Reporting Services  encryption Keys. For more information, see [Back Up and Restore Reporting Services Encryption Keys](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-Reporting-Services-Encryption-Keys.md).  
  
-   **Master Data Services:**  Upgrade the MDS database schema and create the SQL Server 2016 web application. For more information, see [Upgrade Master Data Services](../../Topics\TopicNameNotContainA/Upgrade-Master-Data-Services.md).  
  
-   **Data Quality Services:** Upgrade the DQS databases schema and verify the DQS databases schema upgrade. For more information, see [Upgrade Data Quality Services](../../Topics\TopicNameNotContainA/Upgrade-Data-Quality-Services.md).  
  
-   **Full Text Search:** Re\-populate full\-text catalogs to ensure semantic consistency in query results. For more information, see [Populate Full-Text Indexes](../../Topics\TopicNameNotContainA/Populate-Full-Text-Indexes.md).  
  
## Did this Article Help You? We’re Listening  
 What information are you looking for, and did you find it? We’re listening to your feedback to improve the content. Please submit your comments to [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Complete%20the%20Database%20Engine%20Upgrade%20page)  
  
  