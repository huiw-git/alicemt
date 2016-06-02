---
title: View the Properties and Contents of a Logical Backup Device (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3a309074-e816-454d-b6c3-fcfdde0cbf74
---
# View the Properties and Contents of a Logical Backup Device (SQL Server)
  This topic describes how to view the properties and contents of a logical backup device in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To view the properties and contents of a logical backup device, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
 For information about security, see [RESTORE LABELONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20LABELONLY%20\(Transact-SQL\).md).  
  
####  <a name="Permissions"></a> Permissions  
 In [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] and later versions, obtaining information about a backup set or backup device requires CREATE DATABASE permission. For more information, see [GRANT Database Permissions &#40;Transact-SQL&#41;](../Topic/GRANT%20Database%20Permissions%20\(Transact-SQL\).md).  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To view the properties and contents of a logical backup device  
  
1.  After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], in Object Explorer, click the server name to expand the server tree.  
  
2.  Expand **Server Objects**, and expand **Backup Devices**.  
  
3.  Click the device and right\-click **Properties**, which opens the **Backup Device** dialog box.  
  
4.  The **General** page displays the device name and destination, which is either a tape device or file path.  
  
5.  In the **Select a Page** pane, click **Media Contents**.  
  
6.  The right\-hand pane displays in the following properties panels:  
  
    -   **Media**  
  
         Media sequence information \(the media sequence number, the family sequence number, and the mirror identifier, if any\) and the media creation date and time.  
  
    -   **Media set**  
  
         Media set information: the media set name and description, if any, and the number of families in the media set.  
  
7.  The **Backup sets** grid displays information about the contents of the media set.  
  
> [!NOTE]  
>  For more information, see [Media Contents Page](../Topic/Backup%20Device%20\(Media%20Contents%20Page\).md).  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To view the properties and contents of a logical backup device  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Use the [RESTORE LABELONLY](../Topic/RESTORE%20LABELONLY%20\(Transact-SQL\).md) statement. This example returns information about the `AdvWrks2008R2Backup` logical backup device.  
  
```tsql  
USE AdventureWorks2012 ;  
RESTORE LABELONLY  
   FROM AdvWrks2008R2Backup ;  
GO  
  
```  
  
## See Also  
 [backupfilegroup &#40;Transact-SQL&#41;](../Topic/backupfilegroup%20\(Transact-SQL\).md)   
 [backupfile &#40;Transact-SQL&#41;](../Topic/backupfile%20\(Transact-SQL\).md)   
 [backupset &#40;Transact-SQL&#41;](../Topic/backupset%20\(Transact-SQL\).md)   
 [backupmediaset &#40;Transact-SQL&#41;](../Topic/backupmediaset%20\(Transact-SQL\).md)   
 [backupmediafamily &#40;Transact-SQL&#41;](../Topic/backupmediafamily%20\(Transact-SQL\).md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../Topic/sp_addumpdevice%20\(Transact-SQL\).md)   
 [Backup Devices &#40;SQL Server&#41;](../Topic/Backup%20Devices%20\(SQL%20Server\).md)  
  
  