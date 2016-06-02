---
title: Transfer Logins Task Editor (Logins Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bf244c24-bd45-4ece-b66b-78b488f35c5b
---
# Transfer Logins Task Editor (Logins Page)
  Use the **Logins** page of the **Transfer Logins Task Editor** dialog box to specify properties for copying one or more [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] logins from one instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to another. For more information about this task, see [Transfer Logins Task](../../Topics\TopicNameNotContainA/Transfer-Logins-Task.md).  
  
> [!IMPORTANT]  
>  When the Transfer Logins task is executed, logins are created on the destination server with random passwords and the passwords are disabled. To use these logins, a member of the **sysadmin** fixed server role must change the passwords and then enable them. The **sa** login cannot be transferred.  
  
## Options  
 **SourceConnection**  
 Select a SMO connection manager in the list, or click **\<New connection...\>** to create a new connection to the source server.  
  
 **DestinationConnection**  
 Select a SMO connection manager in the list, or click **\<New connection...\>** to create a new connection to the destination server.  
  
 **LoginsToTransfer**  
 Select the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] logins to copy from the source to the destination server. This property has the options listed in the following table:  
  
|Value|Description|  
|-----------|-----------------|  
|**AllLogins**|All [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] logins on the source server will be copied to the destination server.|  
|**SelectedLogins**|Only logins specified with **LoginsList** will be copied to the destination server.|  
|**AllLoginsFromSelectedDatabases**|All logins from the databases specified with **DatabasesList** will be copied to the destination server.|  
  
 **LoginsList**  
 Select the logins on the source server to be copied to the destination server. This option is only available when **SelectedLogins** is selected for **LoginsToTransfer**.  
  
 **DatabasesList**  
 Select the databases on the source server that contain logins to be copied to the destination server. This option is only available when **AllLoginsFromSelectedDatabases** is selected for **LoginsToTransfer**.  
  
 **IfObjectExists**  
 Select how the task should handle logins of the same name that already exist on the destination server.  
  
 This property has the options listed in the following table:  
  
|Value|Description|  
|-----------|-----------------|  
|**FailTask**|Task fails if logins of the same name already exist on the destination server.|  
|**Overwrite**|Task overwrites logins of the same name on the destination server.|  
|**Skip**|Task skips logins of the same name that exist on the destination server.|  
  
 **CopySids**  
 Select whether the security identifiers associated with the logins should be copied to the destination server. **CopySids** must be set to **True** if the Transfer Logins task is used along with the Transfer Database task. Otherwise, the copied logins will not be recognized by the transferred database.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Integration Services Tasks](../../Topics\TopicNameNotContainA/Integration-Services-Tasks.md)   
 [Transfer Logins Task Editor &#40;General Page&#41;](../Topic/Transfer%20Logins%20Task%20Editor%20\(General%20Page\).md)   
 [Expressions Page](../../Topics\TopicNameNotContainA/Expressions-Page.md)   
 [SMO Connection Manager](../../Topics\TopicNameNotContainA/SMO-Connection-Manager.md)   
 [Strong Passwords](../../Topics\TopicNameNotContainA/Strong-Passwords.md)   
 [Security Considerations for a SQL Server Installation](../../Topics\TopicNameContainA/Security-Considerations-for-a-SQL-Server-Installation.md)  
  
  