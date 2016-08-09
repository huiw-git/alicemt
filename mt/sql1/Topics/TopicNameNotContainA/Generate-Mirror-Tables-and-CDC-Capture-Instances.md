---
title: "Generate Mirror Tables and CDC Capture Instances"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 260c1617-eecc-4007-a84d-3c5778ce46b6
caps.latest.revision: 6
manager: jhubbard
---
# Generate Mirror Tables and CDC Capture Instances
Use the Generate Mirror Tables page to generate the mirror tables for the tables you included in the CDC instance  
  
 Click **Run** to create the mirror tables. The progress for the creation of each table is displayed and a message is displayed to let you know whether each mirror table is completed successfully or with errors. If any errors occur, click **Details** to see a dialog box with an explanation of the error.  
  
 If any of the tables fail to be created, you can choose to continue or delete any tables that failed before continuing. After you finish running the wizard, you can decide whether to fix the table in the Oracle source database or not use it in the CDC instance. If you fix the table, you can add it when you [Edit Tables](../../Topics/TopicNameNotContainA/Edit-Tables.md).  
  
 Click **Next** to open the [Finish](../../Topics/TopicNameNotContainA/Finish.md) page.  
  
## See Also  
 [How to Create the SQL Server Change Database Instance](../../Topics/TopicNameNotContainA/How-to-Create-the-SQL-Server-Change-Database-Instance.md)