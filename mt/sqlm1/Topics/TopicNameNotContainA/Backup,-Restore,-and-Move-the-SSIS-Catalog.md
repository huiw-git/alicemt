---
title: Backup, Restore, and Move the SSIS Catalog
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bf806aef-8556-48ab-aed5-e95de9a2204e
---
# Backup, Restore, and Move the SSIS Catalog
  [!INCLUDE[ssISCurrent](../../Token\Other/ssISCurrent_md.md)] includes the SSISDB database. You query views in the SSISDB database to inspect objects, settings, and operational data that are stored in the **SSISDB** catalog. This topic provides instructions for backing up and restoring the database.  
  
 The **SSISDB** catalog stores the packages that you’ve deployed to the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] server. For more information about the catalog, see [SSIS Catalog](../../Topics\TopicNameNotContainA/SSIS-Catalog.md).  
  
##  <a name="backup"></a> To Back up the SSIS Database  
  
1.  Open [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] and connect to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
2.  Back up the master key for the SSISDB database, by using the BACKUP MASTER KEY Transact\-SQL statement. The key is stored in a file that you specify. Use a password to encrypt the master key in the file.  
  
     For more information about the statement, see [BACKUP MASTER KEY &#40;Transact-SQL&#41;](../Topic/BACKUP%20MASTER%20KEY%20\(Transact-SQL\).md).  
  
     In the following example, the master key is exported to the `c:\temp directory\RCTestInstKey` file. The `LS2Setup!` password is used to encrypt the master key.  
  
    ```  
    backup master key to file = 'c:\temp\RCTestInstKey'  
           encryption by password = 'LS2Setup!'  
  
    ```  
  
3.  Back up the SSISDB database by using the **Backup Database** dialog box in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. For more information, see [How to: Back Up a Database \(SQL Server Management Studio\)](http://go.microsoft.com/fwlink/?LinkId=231812).  
  
4.  Generate the CREATE LOGIN script for \#\#MS\_SSISServerCleanupJobLogin\#\#, by doing the following. For more information, see [CREATE LOGIN &#40;Transact-SQL&#41;](../Topic/CREATE%20LOGIN%20\(Transact-SQL\).md).  
  
    1.  In Object Explorer in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], expand the **Security** node and then expand the **Logins** node.  
  
    2.  Right\-click **\#\#MS\_SSISServerCleanupJobLogin\#\#**, and then click **Script Login as** \> **CREATE To** \> **New Query Editor Window**.  
  
5.  If you will be restoring the SSISDB database to an [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance where the SSISDB catalog was never created, generate the CREATE PROCEDURE script for sp\_ssis\_startup, by doing the following. For more information, see [CREATE PROCEDURE &#40;Transact-SQL&#41;](../Topic/CREATE%20PROCEDURE%20\(Transact-SQL\).md).  
  
    1.  In Object Explorer, expand the **Databases** node and then expand the **master** \> **Programmability** \> **Stored Procedures** node.  
  
    2.  Right click **dbo.sp\_ssis\_startup**, and then click **Script Stored Procedure as** \> **CREATE To** \> **New Query Editor Window**.  
  
6.  Confirm that SQL Server Agent has been started  
  
7.  If you will be restoring the SSISDB database to an [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance where the SSISDB catalog was never created, generate a script for the SSIS Server Maintenance Job by doing the following. The script is created in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent automatically when the SSISDB catalog is created. The job helps clean up cleanup operation logs outside the retention window and remove older versions of projects.  
  
    1.  In Object Explorer, expand the **SQL Server Agent** node and then expand the **Jobs** node.  
  
    2.  Right click SSIS Server Maintenance Job, and then click **Script Job as** \> **CREATE To** \> **New Query Editor Window**.  
  
### To Restore the SSIS Database  
  
1.  If you are restoring the SSISDB database to an [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance where the SSISDB catalog was never created, enable common language runtime \(clr\) by running the sp\_configure stored procedure. For more information, see [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md) and [clr enabled Option](http://go.microsoft.com/fwlink/?LinkId=231855).  
  
    ```  
    use master   
           sp_configure 'clr enabled', 1  
           reconfigure  
  
    ```  
  
2.  If you are restoring the SSISDB database to an [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance where the SSISDB catalog was never created, create the asymmetric key and the login from the asymmetric key, and grant UNSAFE permission to the login.  
  
    ```  
    Create Asymmetric key MS_SQLEnableSystemAssemblyLoadingKey  
           FROM Executable File = 'C:\Program Files\Microsoft SQL Server\110\DTS\Binn\Microsoft.SqlServer.IntegrationServices.Server.dll'  
  
    ```  
  
     [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] CLR stored procedures require UNSAFE permissions to be granted to the login because the login requires additional access to restricted resources, such as the Microsoft Win32 API. For more information about the UNSAFE code permission, see [Creating an Assembly](../Topic/Creating%20an%20Assembly.md).  
  
    ```  
    Create Login MS_SQLEnableSystemAssemblyLoadingUser  
           FROM Asymmetric key MS_SQLEnableSystemAssemblyLoadingKey   
  
           Grant unsafe Assembly to MS_SQLEnableSystemAssemblyLoadingUser  
  
    ```  
  
3.  Restore the SSISDB database from the backup by using the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. For more information, see the following topics.  
  
    -   [Restore Database &#40;General Page&#41;](../Topic/Restore%20Database%20\(General%20Page\).md)  
  
    -   [Restore Database &#40;Files Page&#41;](../Topic/Restore%20Database%20\(Files%20Page\).md)  
  
    -   [Restore Database &#40;Options Page&#41;](../Topic/Restore%20Database%20\(Options%20Page\).md)  
  
4.  Execute the scripts that you created in the [To Back up the SSIS Database](#backup) for \#\#MS\_SSISServerCleanupJobLogin\#\#, sp\_ssis\_startup, and SSIS Server Maintenance Job. Confirm that SQL Server Agent has been started.  
  
5.  Run the following statement to set the sp\_ssis\_startup prodecure for autoexecution. For more information, see [sp_procoption &#40;Transact-SQL&#41;](../Topic/sp_procoption%20\(Transact-SQL\).md).  
  
    ```  
    EXEC sp_procoption N'sp_ssis_startup','startup','on'  
    ```  
  
6.  Map the SSISDB user \#\#MS\_SSISServerCleanupJobUser\#\# \(SSISDB database\) to \#\#MS\_SSISServerCleanupJobLogin\#\#, by using the **Login Properties** dialog box in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
7.  Restore the master key by using one of the following methods. For more information about encryption, see [Encryption Hierarchy](../../Topics\TopicNameNotContainA/Encryption-Hierarchy.md).  
  
    -   **Method 1**  
  
         Use this method if you’ve already performed a backup of the database master key, and you have the password used to encrypt the master key.  
  
        ```  
               Restore master key from file = 'c:\temp\RCTestInstKey'  
               Decryption by password = 'LS2Setup!' -- 'Password used to encrypt the master key during SSISDB backup'  
               Encryption by password = 'LS3Setup!' -- 'New Password'  
               Force  
  
        ```  
  
        > [!NOTE]  
        >  Confirm that the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service account has permissions to read the backup key file.  
  
        > [!NOTE]  
        >  You will see the following warning message displayed in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] if the database master key has not yet been encrypted by the service master key. Ignore the warning message.  
        >   
        >  **The current master key cannot be decrypted. The error was ignored because the FORCE option was specified.**  
        >   
        >  The FORCE argument specifies that the restore process should continue even if the current database master key is not open. For the SSISDB catalog, because the database master key has not been opened on the instance where you are restoring the database, you will see this message.  
  
    -   **Method 2**  
  
         Use this method if you have the original password that was used to create SSISDB.  
  
        ```  
        open master key decryption by password = 'LS1Setup!' --'Password used when creating SSISDB'  
               Alter Master Key Add encryption by Service Master Key  
        ```  
  
8.  Determine whether the SSISDB catalog schema and the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] binaries \(ISServerExec and SQLCLR assembly\) are compatible, by running [catalog.check_schema_version](../Topic/catalog.check_schema_version.md).  
  
9. To confirm that the SSISDB database has been restored successfully, perform operations against the SSISDB catalog such as running packages that have been deployed to the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] server. For more information, see [Run a Package on the SSIS Server Using SQL Server Management Studio](../../Topics\TopicNameContainA/Run-a-Package-on-the-SSIS-Server-Using-SQL-Server-Management-Studio.md).  
  
### To Move the SSIS Database  
  
-   Follow the instructions for moving user databases. For more information, see [Move User Databases](../../Topics\TopicNameNotContainA/Move-User-Databases.md).  
  
     Ensure that you back up the master key for the SSISDB database and protect the backup file. For more information, see [To Back up the SSIS Database](#backup).  
  
     Ensure that the Integration Services \(SSIS\) relevant objects are created in the new [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance where the SSISDB catalog has not yet been created.  
  
  