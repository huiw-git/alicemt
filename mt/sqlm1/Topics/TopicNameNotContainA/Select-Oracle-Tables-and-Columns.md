---
title: Select Oracle Tables and Columns
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bf73f80e-a954-4c5f-874e-17fdd4082715
---
# Select Oracle Tables and Columns
  Use the Select Oracle Tables and Columns page to select the tables from the Oracle source database where changes are captured. This page has the following elements:  
  
## Options  
 **Table list**  
 The table list has three columns:  
  
-   **Oracle Table Name**: The name of the table, including the table schema.  
  
-   **Capture Instance**: The name of the capture instance used to name instance\-specific change data capture objects. The capture instance cannot be NULL.  
  
     If not specified, the name is derived from the source schema name plus the source table name in the format `<schema-name>_<table-name>`. The capture instance name cannot exceed 100 characters and must be unique within the database.  
  
     You can click in any cell in this column to manually edit the **capture\_instance**.  
  
-   **Security Role**: The name of the database gating role used to control access to change data.  
  
     You can click in any cell in this column to manually edit the **security\_role**.  
  
 **Add Tables**  
 Click **Add Tables** to open the Table Selection dialog box where you can [Select Oracle Tables for Capturing Changes](../../Topics\TopicNameNotContainA/Select-Oracle-Tables-for-Capturing-Changes.md).  
  
 **Edit**  
 Select a table from the list and select **Edit** to open the **Properties** dialog box for that table where you can [Make Changes to the Tables Selected for Capturing Changes](../../Topics\TopicNameNotContainA/Make-Changes-to-the-Tables-Selected-for-Capturing-Changes.md).  
  
 **Remove**  
 Select a table from the list and click **Remove** to remove the table from the CDC instance.  
  
 After you [Select Oracle Tables for Capturing Changes](../../Topics\TopicNameNotContainA/Select-Oracle-Tables-for-Capturing-Changes.md) and\/or [Make Changes to the Tables Selected for Capturing Changes](../../Topics\TopicNameNotContainA/Make-Changes-to-the-Tables-Selected-for-Capturing-Changes.md) using the correct dialog boxes, click **Next** to [Generate and Run the Supplemental Logging Script](../../Topics\TopicNameNotContainA/Generate-and-Run-the-Supplemental-Logging-Script.md).  
  
## See Also  
 [How to Create the SQL Server Change Database Instance](../../Topics\TopicNameNotContainA/How-to-Create-the-SQL-Server-Change-Database-Instance.md)   
 [Edit Tables](../../Topics\TopicNameNotContainA/Edit-Tables.md)   
 [Add Tables to a CDC Instance](../../Topics\TopicNameContainA/Add-Tables-to-a-CDC-Instance.md)   
 [Edit the Table Properties](../../Topics\TopicNameNotContainA/Edit-the-Table-Properties.md)  
  
  