---
title: Stretch 8 disable
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0f7d9e58-f720-4eef-9cd1-39a05fb0c00c
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
# Stretch 8 disable
  To disable Stretch Database for a table, select **Stretch** for a table in SQL Server Management Studio. Then select one of the following options.

-   **Disable | Bring data back from Azure**. Copy the remote data for the table from Azure back to SQL Server, then disable Stretch Database for the table. This operation incurs data transfer costs, and it can't be canceled.

-   **Disable | Leave data in Azure**. Disable Stretch Database for the table.  Abandon the remote data for the table in Azure.

 After you disable Stretch Database for a table, data migration stops and query results no longer include results from the remote table.

 You can also use Transact\-SQL to disable Stretch Database for a table or for a database.

 If you simply want to pause data migration, see [Pause and resume Stretch Database](assetId:///65d6a990-b295-41b2-97f9-7b6bf3000e4d).

## Disable Stretch Database for a table

### Use SQL Server Management Studio to disable Stretch Database for a table

1.  In SQL Server Management Studio, in Object Explorer, select the table for which you want to disable Stretch Database.

2.  Right\-click and select **Stretch**, and then select one of the following options.

    -   **Disable | Bring data back from Azure**. Copy the remote data for the table from Azure back to SQL Server, then disable Stretch Database for the table. This command can't be canceled.

         This operation incurs data transfer costs. For more info, see [Data Transfers Pricing Details](https://azure.microsoft.com/en-us/pricing/details/data-transfers/).

         After all the remote data has been copied from Azure back to SQL Server, Stretch is disabled for the table.

    -   **Disable | Leave data in Azure**. Disable Stretch Database for the table.  Abandon the remote data for the table in Azure.

         Abandoning the remote data and disabling Stretch does not remove the remote data. If you want to delete the remote data, you have to drop the remote table by using the Azure management portal.

### Use Transact\-SQL to disable Stretch Database for a table

-   To disable Stretch for a table and copy the remote data for the table from Azure SQL Database back to SQL Server, run the following command. This command can't be canceled.

    ```tsql
    ALTER TABLE <table name>
       SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = OUTBOUND ) ) ;
    ```

     This operation incurs data transfer costs. For more info, see [Data Transfers Pricing Details](https://azure.microsoft.com/en-us/pricing/details/data-transfers/).

     After all the remote data has been copied from Azure back to SQL Server, Stretch is disabled for the table.

-   To disable Stretch for a table and abandon the remote data, run the following command.

    ```tsql
    ALTER TABLE <table_name>
       SET ( REMOTE_DATA_ARCHIVE = OFF_WITHOUT_DATA_RECOVERY ( MIGRATION_STATE = PAUSED ) ) ;
    ```

     Abandoning the remote data and disabling Stretch does not remove the remote data. If you want to delete the remote data, you have to drop the remote table by using the Azure management portal.

## Disable Stretch Database for a database
 Before you can disable Stretch Database for a database, you have to disable Stretch Database on the individual Stretch\-enabled tables in the database.

### Use SQL Server Management Studio to disable Stretch Database for a database

1.  In SQL Server Management Studio, in Object Explorer, select the database for which you want to disable Stretch Database.

2.  Right\-click and select **Tasks**, and then select **Stretch**, and then select **Disable**.

### Use Transact\-SQL to disable Stretch Database for a database
 Run the following command.

```tsql
ALTER DATABASE <database name>
    SET REMOTE_DATA_ARCHIVE = OFF ;

```

## Drop a Stretch\-enabled database
 Dropping a database that was enabled for Stretch Database drops the local database but does not remove the remote data. If you want to delete the remote data, you have to drop the remote database by using the Azure management portal.

## See Also
 [ALTER DATABASE SET Options \(Transact\-SQL\)](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc) 
 [Pause and resume Stretch Database](assetId:///65d6a990-b295-41b2-97f9-7b6bf3000e4d)

  