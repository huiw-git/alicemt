---
title: Stretch 10 pause
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4e78b97-37a7-41f3-ae96-91f7ddda3950
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Stretch 10 pause
To pause or resume data migration to Azure, select **Stretch** for a table in SQL Server Management Studio, and then select **Pause** to pause data migration or **Resume** to resume data migration. You can also use Transact\-SQL to pause or resume data migration.  
  
 Pause data migration on individual tables when you want to troubleshoot problems on the local server or to maximize the available network bandwidth.  
  
## Pause data migration  
  
### Use SQL Server Management Studio to pause data migration  
  
1.  In SQL Server Management Studio, in Object Explorer, select the Stretch\-enabled table for which you want to pause data migration.  
  
2.  Right\-click and select **Stretch**, and then select **Pause**.  
  
### Use Transact\-SQL to pause data migration  
 Run the following command.  
  
```tsql  
ALTER TABLE <table name>  
    SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = PAUSED ) ) ;  
GO;  
  
```  
  
## Resume data migration  
  
### Use SQL Server Management Studio to resume data migration  
  
1.  In SQL Server Management Studio, in Object Explorer, select the Stretch\-enabled table for which you want to resume data migration.  
  
2.  Right\-click and select **Stretch**, and then select **Resume**.  
  
### Use Transact\-SQL to resume data migration  
 Run the following command.  
  
```tsql  
ALTER TABLE <table name>  
    SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = OUTBOUND ) ) ;  
  
```  
  
## See Also  
 [ALTER TABLE \(Transact\-SQL\)](assetId:///f1745145-182d-4301-a334-18f799d361d1)