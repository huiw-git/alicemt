---
title: "Transfer Master Stored Procedures Task Editor (General Page)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fa1abd4c-e2be-427f-be53-860e49c97227
caps.latest.revision: 26
caps.handback.revision: 0
manager: jhubbard
---
# Transfer Master Stored Procedures Task Editor (General Page)
Use the **General** page of the **Transfer Master Stored Procedures Task Editor** dialog box to name and describe the Transfer Master Stored Procedures task. For more information about this task, see [Transfer Master Stored Procedures Task](../../Topics/TopicNameNotContainA/Transfer-Master-Stored-Procedures-Task.md).  
  
> [!NOTE]  
>  This task transfers only user-defined stored procedures owned by **dbo** from a **master** database on the source server to a **master** database on the destination server. Users must be granted the CREATE PROCEDURE permission in the **master** database on the destination server or be members of the **sysadmin** fixed server role on the destination server to create stored procedures there.  
  
## Options  
 **Name**  
 Type a unique name for the Transfer Master Stored Procedures task. This name is used as the label in the task icon.  
  
> [!NOTE]  
>  Task names must be unique within a package.  
  
 **Description**  
 Type a description of the Transfer Master Stored Procedures task.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics/TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Integration Services Tasks](../../Topics/TopicNameNotContainA/Integration-Services-Tasks.md)   
 [Transfer Master Stored Procedures Task Editor (Stored Procedures Page)](../../Topics/TopicNameNotContainA/Transfer-Master-Stored-Procedures-Task-Editor--Stored-Procedures-Page-.md)   
 [Expressions Page](../../Topics/TopicNameNotContainA/Expressions-Page.md)