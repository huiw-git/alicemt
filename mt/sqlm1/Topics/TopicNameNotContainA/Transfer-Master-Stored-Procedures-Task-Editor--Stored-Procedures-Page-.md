---
title: Transfer Master Stored Procedures Task Editor (Stored Procedures Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5fcf171e-cc0b-4c24-8eb5-3a4b4775e64a
---
# Transfer Master Stored Procedures Task Editor (Stored Procedures Page)
  Use the **Stored Procedures** page of the **Transfer Master Stored Procedures Task Editor** dialog box to specify properties for copying one or more user\-defined stored procedures from the **master** database in one instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance to a **master** database in another instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For more information about this task, see [Transfer Master Stored Procedures Task](../../Topics\TopicNameNotContainA/Transfer-Master-Stored-Procedures-Task.md).  
  
> [!NOTE]  
>  This task transfers only user\-defined stored procedures owned by **dbo** from a **master** database on the source server to a **master** database on the destination server. Users must be granted the CREATE PROCEDURE permission in the **master** database on the destination server or be members of the **sysadmin** fixed server role on the destination server to create stored procedures there.  
  
## Options  
 **SourceConnection**  
 Select a SMO connection manager in the list, or click **\<New connection...\>** to create a new connection to the source server.  
  
 **DestinationConnection**  
 Select a SMO connection manager in the list, or click **\<New connection...\>** to create a new connection to the destination server.  
  
 **IfObjectExists**  
 Select how the task should handle user\-defined stored procedures of the same name that already exist in the **master** database on the destination server.  
  
 This property has the options listed in the following table:  
  
|Value|Description|  
|-----------|-----------------|  
|**FailTask**|Task fails if stored procedures of the same name already exist in the **master** database on the destination server.|  
|**Overwrite**|Task overwrites stored procedures of the same name in the **master** database on the destination server.|  
|**Skip**|Task skips stored procedures of the same name that exist in the **master** database on the destination server.|  
  
 **TransferAllStoredProcedures**  
 Select whether all user\-defined stored procedures in the **master** database on the source server should be copied to the destination server.  
  
|Value|Description|  
|-----------|-----------------|  
|**True**|Copy all user\-defined stored procedures in the **master** database.|  
|**False**|Copy only the specified stored procedures.|  
  
 **StoredProceduresList**  
 Select which user\-defined stored procedures in the **master** database on the source server should be copied to the destination **master** database. This option is only available when **TransferAllStoredProcedures** is set to **False**.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Integration Services Tasks](../../Topics\TopicNameNotContainA/Integration-Services-Tasks.md)   
 [Transfer Master Stored Procedures Task Editor &#40;General Page&#41;](../Topic/Transfer%20Master%20Stored%20Procedures%20Task%20Editor%20\(General%20Page\).md)   
 [Expressions Page](../../Topics\TopicNameNotContainA/Expressions-Page.md)   
 [SMO Connection Manager](../../Topics\TopicNameNotContainA/SMO-Connection-Manager.md)  
  
  