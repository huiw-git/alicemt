---
title: Pause and resume data migration (Stretch Database)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.service: sql-server-stretch-database
ms.suite: na
ms.technology: 
  - dbe-stretch
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 65d6a990-b295-41b2-97f9-7b6bf3000e4d
---
# Pause and resume data migration (Stretch Database)
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
 [ALTER TABLE &#40;Transact-SQL&#41;](../Topic/ALTER%20TABLE%20\(Transact-SQL\).md)  
  
  