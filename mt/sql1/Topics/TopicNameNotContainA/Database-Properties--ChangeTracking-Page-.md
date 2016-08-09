---
title: "Database Properties (ChangeTracking Page)"
ms.custom: na
ms.date: 2016-01-07
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b929640-bc62-449b-9b06-b5a77b8cf372
caps.latest.revision: 14
caps.handback.revision: 0
manager: jhubbard
---
# Database Properties (ChangeTracking Page)
Use this page to view or modify change tracking settings for the selected database. For more information about the options available on this page, see [Enable and Disable Change Tracking (SQL Server)](../../Topics/TopicNameNotContainA/Enable-and-Disable-Change-Tracking--SQL-Server-.md).  
  
## Options  
 **Change Tracking**  
 Use to enable or disable change tracking for the database.  
  
 To enable change tracking, you must have permission to modify the database.  
  
 Setting the value to **True** sets a database option that allows change tracking to be enabled on individual tables.  
  
 You can also configure change tracking by using [ALTER DATABASE](assetId:///15f8affd-8f39-4021-b092-0379fc6983da).  
  
 **Retention Period**  
 Specifies the minimum period for keeping change track information in the database. Data is removed only if the **Auto Clean-Up**value is **True**.  
  
 The default value is 2.  
  
 **Retention Period Units**  
 Specifies the units for the Retention Period value. You can select **Days**, **Hours**, or **Minutes**. The default value is **Days**.  
  
 The minimum retention period is 1 minute. There is no maximum retention period.  
  
 **Auto Clean-Up**  
 Indicates whether change tracking information is automatically removed after the specified retention period.  
  
 Enabling **Auto Clean-Up** resets any previous custom retention period to the default retention period of 2 days.  
  
## See Also  
 [ALTER DATABASE (Transact-SQL)](assetId:///15f8affd-8f39-4021-b092-0379fc6983da)   
 [CREATE DATABASE (Transact-SQL)](assetId:///29ddac46-7a0f-4151-bd94-75c1908c89f8)