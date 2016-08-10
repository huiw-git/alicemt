---
title: "View the Properties and Contents of a Logical Backup Device (SQL Server)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3a309074-e816-454d-b6c3-fcfdde0cbf74
caps.latest.revision: 23
caps.handback.revision: 0
manager: jhubbard
---
# View the Properties and Contents of a Logical Backup Device (SQL Server)
This topic describes how to view the properties and contents of a logical backup device in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To view the properties and contents of a logical backup device, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
 For information about security, see [RESTORE LABELONLY (Transact-SQL)](assetId:///7cf0641e-0d55-4ffb-9500-ecd6ede85ae5).  
  
####  <a name="Permissions"></a> Permissions  
 In [!INCLUDE[ssKatmai](../../Topics/TopicNameContainA/tokens/ssKatmai_md.md)] and later versions, obtaining information about a backup set or backup device requires CREATE DATABASE permission. For more information, see [GRANT Database Permissions (Transact-SQL)](assetId:///499e5ed6-945c-4791-ab45-68dec0b9c289).  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To view the properties and contents of a logical backup device  
  
1.  After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)], in Object Explorer, click the server name to expand the server tree.  
  
2.  Expand **Server Objects**, and expand **Backup Devices**.  
  
3.  Click the device and right-click **Properties**, which opens the **Backup Device** dialog box.  
  
4.  The **General** page displays the device name and destination, which is either a tape device or file path.  
  
5.  In the **Select a Page** pane, click **Media Contents**.  
  
6.  The right-hand pane displays in the following properties panels:  
  
    -   **Media**  
  
         Media sequence information (the media sequence number, the family sequence number, and the mirror identifier, if any) and the media creation date and time.  
  
    -   **Media set**  
  
         Media set information: the media set name and description, if any, and the number of families in the media set.  
  
7.  The **Backup sets** grid displays information about the contents of the media set.  
  
> [!NOTE]  
>  For more information, see [Media Contents Page](../../Topics/TopicNameNotContainA/Backup-Device--Media-Contents-Page-.md).  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To view the properties and contents of a logical backup device  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Use the [RESTORE LABELONLY](assetId:///7cf0641e-0d55-4ffb-9500-ecd6ede85ae5) statement. This example returns information about the `AdvWrks2008R2Backup` logical backup device.  
  
```tsql  
USE AdventureWorks2012 ;  
RESTORE LABELONLY  
   FROM AdvWrks2008R2Backup ;  
GO  
  
```  
  
## See Also  
 [backupfilegroup (Transact-SQL)](assetId:///d26e8fbe-f5c5-4e10-b2bd-0d8e16ea21f9)   
 [backupfile (Transact-SQL)](assetId:///f1a7fc0a-f4b4-47eb-9138-eebf930dc9ac)   
 [backupset (Transact-SQL)](assetId:///6ff79bbf-4acf-4f75-926f-38637ca8a943)   
 [backupmediaset (Transact-SQL)](assetId:///d9c18a93-cab9-4db8-ae09-c6bd8145ab8f)   
 [backupmediafamily (Transact-SQL)](assetId:///ee16de24-3d95-4b2e-a094-78df2514d18a)   
 [sp_addumpdevice (Transact-SQL)](assetId:///c2d2ae49-0808-46d8-8444-db69a69d0ec3)   
 [Backup Devices (SQL Server)](../../Topics/TopicNameNotContainA/Backup-Devices--SQL-Server-.md)