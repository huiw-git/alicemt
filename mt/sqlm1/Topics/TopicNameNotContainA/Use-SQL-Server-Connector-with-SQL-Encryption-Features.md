---
title: Use SQL Server Connector with SQL Encryption Features
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58fc869e-00f1-4d7c-a49b-c0136c9add89
---
# Use SQL Server Connector with SQL Encryption Features
  Common [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] encryption activities using an asymmetric key protected by the Azure Key Vault include the following three areas.  
  
-   Transparent Data Encryption by using an Asymmetric Key from Azure Key Vault  
  
-   Encrypting Backups by Using an Asymmetric Key from the Key Vault  
  
-   Column Level Encryption by Using an Asymmetric Key from the Key Vault  
  
 Complete parts I through IV of the topic [Setup Steps for Extensible Key Management Using the Azure Key Vault](../../Topics\TopicNameNotContainA/Setup-Steps-for-Extensible-Key-Management-Using-the-Azure-Key-Vault.md), before following the steps on this topic.  
  
## Transparent Data Encryption by using an Asymmetric Key from Azure Key Vault  
 After completing Parts I through IV of the topic Setup Steps for Extensible Key Management Using the Azure Key Vault, use the Azure Key Vault key to encrypt the database encryption key using TDE.  
You will need to create a credential and a login, and create a database encryption key which will encrypt the data and logs in the database. To encrypt a database requires **CONTROL** permission on the database. The following graphic shows the hierarchy of the encryption key when using the Azure Key Vault.  
  
 ![ekm&#45;key&#45;hierarchy&#45;with&#45;akv](../../Images\Image\ImageNotContaina/ekm-key-hierarchy-with-akv.jpg "ekm\-key\-hierarchy\-with\-akv")  
  
1.  **Create a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] credential for the Database Engine to use for TDE**  
  
     The Database Engine uses the credential to access the Key Vault during database load. We recommend creating another Azure Active Directory **Client ID** and **Secret** in Part I for the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], to limit the Key Vault permissions that are granted.  
  
     Modify the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] script below in the following ways:  
  
    -   Replace the `IDENTITY` argument \(`ContosoDevKeyVault`\) with the name of your Azure Key Vault from Part II.  
  
    -   Replace the first part of the `SECRET` argument with the Azure Active Directory **Client ID** from Part I. In this example, the **Client ID** is `EF5C8E094D2A4A769998D93440D8115D`.  
  
        > [!IMPORTANT]  
        >  You must remove the hyphens from the **Client ID**.  
  
    -   Complete the second part of the `SECRET` argument with **Secret** from Part I.  In this example the **Secret** from Part 1 is `AADsecret123456789=`. The final string for the `SECRET` argument will be a long sequence of letters and numbers.  
  
    ```tsql  
    USE master;  
    CREATE CREDENTIAL Azure_EKM_TDE_cred   
        WITH IDENTITY = 'ContosoDevKeyVault',   
        SECRET =   
    'EF5C8E094D2A4A769998D93440D8115DAADsecret123456789='  
        FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov;  
    ```  
  
2.  **Create a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login for the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] for TDE**  
  
     Create a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login and add the credential from Step 1 to it. This [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] example uses the same key that was imported earlier.  
  
    ```tsql  
    USE master;  
    -- Create a SQL Server login associated with the asymmetric key   
    -- for the Database engine to use when it loads a database   
    -- encrypted by TDE.  
    CREATE LOGIN TDE_Login   
    FROM ASYMMETRIC KEY ContosoRSAKey0;  
    GO   
  
    -- Alter the TDE Login to add the credential for use by the   
    -- Database Engine to access the key vault  
    ALTER LOGIN TDE_Login   
    ADD CREDENTIAL Azure_EKM_TDE_cred ;  
    GO  
    ```  
  
3.  **Create the Database Encryption Key \(DEK\)**  
  
     The DEK will encrypt your data and log files in the database instance, and in turn be encrypted by the Azure Key Vault asymmetric key. The DEK can be created using any [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] supported algorithm or key length.  
  
    ```tsql  
    USE ContosoDatabase;  
    GO  
  
    CREATE DATABASE ENCRYPTION KEY   
    WITH ALGORITHM = AES_256   
    ENCRYPTION BY SERVER ASYMMETRIC KEY CONTOSO_KEY;  
    GO  
    ```  
  
4.  **Turn On TDE**  
  
    ```tsql  
    -- Alter the database to enable transparent data encryption.  
    ALTER DATABASE ContosoDatabase   
    SET ENCRYPTION ON;  
    GO  
    ```  
  
     Using [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)],  verify that TDE has been turned on by connecting to your database with Object Explorer. Right\-click your database, point to **Tasks**, and then click **Manage Database Encryption**.  
  
     ![ekm&#45;tde&#45;object&#45;explorer](../../Images\Image\ImageNotContaina/ekm-tde-object-explorer.png "ekm\-tde\-object\-explorer")  
  
     In the **Manage Database Encryption** dialog box, confirm that TDE is on, and what asymmetric key is encrypting the DEK.  
  
     ![ekm&#45;tde&#45;dialog&#45;box](../../Images\Image\ImageNotContaina/ekm-tde-dialog-box.png "ekm\-tde\-dialog\-box")  
  
     Alternatively, you can execute the following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] script. An encryption state of 3 indicates an encrypted database.  
  
    ```tsql  
    USE MASTER  
    SELECT * FROM sys.asymmetric_keys  
  
    -- Check which databases are encrypted using TDE  
    SELECT d.name, dek.encryption_state   
    FROM sys.dm_database_encryption_keys AS dek  
    JOIN sys.databases AS d  
         ON dek.database_id = d.database_id;  
    ```  
  
    > [!NOTE]  
    >  The `tempdb` database is automatically encrypted whenever any database enables TDE.  
  
## Encrypting Backups by Using an Asymmetric Key from the Key Vault  
 Encrypted backups are supported starting with [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)]. The following example creates and restores a backup encrypted a data encryption key protected by the asymmetric key in the key vault.  
The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] needs the credential when accessing the Key Vault during database load. We recommend creating another Azure Active Directory Client ID and Secret in Part I for the Database Engine, to limit the Key Vault permissions that are granted.  
  
1.  **Create a SQL Server credential for the Database Engine to use for Backup Encryption**  
  
     Modify the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] script below in the following ways:  
  
    -   Replace the `IDENTITY` argument \(`ContosoDevKeyVault`\) with the name of your Azure Key Vault from Part II.  
  
    -   Replace the first part of the `SECRET` argument with the Azure Active Directory **Client ID** from Part I. In this example, the **Client ID** is `EF5C8E094D2A4A769998D93440D8115D`.  
  
        > [!IMPORTANT]  
        >  You must remove the hyphens from the **Client ID**.  
  
    -   Complete the second part of the `SECRET` argument with **Secret** from Part I.  In this example the **Secret** from Part 1 is `AADsecret123456789=`. The final string for the `SECRET` argument will be a long sequence of letters and numbers.  
  
        ```tsql  
        USE master;  
  
        CREATE CREDENTIAL Azure_EKM_Backup_cred   
            WITH IDENTITY = 'ContosoDevKeyVault',   
            SECRET =   
        'EF5C8E094D2A4A769998D93440D8115DAADsecret123456789='   
            FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov;  
        ```  
  
2.  **Create a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login for the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] for Backup Encryption**  
  
     Create a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login to be used by the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]e for encryption backups, and add the credential from Step 1 to it. This [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] example uses the same key that was imported earlier.  
  
    > [!IMPORTANT]  
    >  You cannot use the same asymmetric key for backup encryption if you’ve already used that key for TDE \(the above example\) or column level Encryption \(the following example\).  
  
     This example uses the `CONTOSO_KEY_BACKUP` asymmetric key stored in the key vault, which can be imported or created earlier for the master database, as Part IV, Step 5 earlier.  
  
    ```tsql  
    USE master;  
  
    -- Create a SQL Server login associated with the asymmetric key   
    -- for the Database engine to use when it is encrypting the backup.  
    CREATE LOGIN Backup_Login   
    FROM ASYMMETRIC KEY CONTOSO_KEY_BACKUP;  
    GO   
  
    -- Alter the Encrypted Backup Login to add the credential for use by   
    -- the Database Engine to access the key vault  
    ALTER LOGIN Backup_Login   
    ADD CREDENTIAL Azure_EKM_Backup_cred ;  
    GO  
    ```  
  
3.  **Backup the Database**  
  
     Backup the database specifying encryption with the symmetric key stored in the key vault.  
  
    ```tsql  
    USE master;  
  
    BACKUP DATABASE [DATABASE_TO_BACKUP]  
    TO DISK = N'[PATH TO BACKUP FILE]'   
    WITH FORMAT, INIT, SKIP, NOREWIND, NOUNLOAD,   
    ENCRYPTION(ALGORITHM = AES_256,   
    SERVER ASYMMETRIC KEY = [CONTOSO_KEY_BACKUP]);  
    GO  
    ```  
  
     Sample restore code:  
  
    ```tsql  
    RESTORE DATABASE [DATABASE_TO_BACKUP]  
    FROM DISK = N'[PATH TO BACKUP FILE]'   
        WITH FILE = 1, NOUNLOAD, REPLACE;  
    GO  
    ```  
  
     For more information about backup options, see [BACKUP \(Transact\-SQL\)](../Topic/BACKUP%20\(Transact-SQL\).md).  
  
## Column Level Encryption by Using an Asymmetric Key from the Key Vault  
 The following example creates a symmetric key protected by the asymmetric key in the key vault. Then the symmetric key is used to encrypt data in the database.  
  
> [!IMPORTANT]  
>  You cannot use the same asymmetric key for backup encryption if you’ve already used that key for TDE or backup encryption \(the preceding examples\).  
  
 This example uses the `CONTOSO_KEY_COLUMNS` asymmetric key stored in the key vault, which can be imported or created earlier, as described in Step 3, section 3 of [Setup Steps for Extensible Key Management Using the Azure Key Vault](../../Topics\TopicNameNotContainA/Setup-Steps-for-Extensible-Key-Management-Using-the-Azure-Key-Vault.md). To use this asymmetric key in the `ContosoDatabase` database, you must execute the `CREATE ASYMMETRIC KEY` statement again, to provide the `ContosoDatabase` database with a reference to the key.  
  
```tsql  
USE [ContosoDatabase];  
GO  
  
-- Create a reference to the key in the key vault  
CREATE ASYMMETRIC KEY CONTOSO_KEY_COLUMNS   
FROM PROVIDER [AzureKeyVault_EKM_Prov]  
WITH PROVIDER_KEY_NAME = 'ContosoDevRSAKey2',  
CREATION_DISPOSITION = OPEN_EXISTING;  
  
-- Create the data encryption key.  
-- The data encryption key can be created using any SQL Server   
-- supported algorithm or key length.  
-- The DEK will be protected by the asymmetric key in the key vault  
  
CREATE SYMMETRIC KEY DATA_ENCRYPTION_KEY  
    WITH ALGORITHM=AES_256  
    ENCRYPTION BY ASYMMETRIC KEY CONTOSO_KEY_COLUMNS;  
  
DECLARE @DATA VARBINARY(MAX);  
  
--Open the symmetric key for use in this session  
OPEN SYMMETRIC KEY DATA_ENCRYPTION_KEY   
DECRYPTION BY ASYMMETRIC KEY CONTOSO_KEY_COLUMNS;  
  
--Encrypt syntax  
SELECT @DATA = ENCRYPTBYKEY  
    (  
    KEY_GUID('DATA_ENCRYPTION_KEY'),   
    CONVERT(VARBINARY,'Plain text data to encrypt')  
    );  
  
-- Decrypt syntax  
SELECT CONVERT(VARCHAR, DECRYPTBYKEY(@DATA));  
  
--Close the symmetric key  
CLOSE SYMMETRIC KEY DATA_ENCRYPTION_KEY;  
```  
  
## See Also  
 [Setup Steps for Extensible Key Management Using the Azure Key Vault](../../Topics\TopicNameNotContainA/Setup-Steps-for-Extensible-Key-Management-Using-the-Azure-Key-Vault.md)   
 [Extensible Key Management Using Azure Key Vault](Extensible%20Key%20Management%20Using%20Azure%20Key%20Vault%20\(SQL%20Server\).md)  
 [EKM provider enabled Server Configuration Option](../../Topics\TopicNameNotContainA/EKM-provider-enabled-Server-Configuration-Option.md)   
 [SQL Server Connector, Appendix](../../Topics\TopicNameNotContainA/SQL-Server-Connector,-Appendix.md)  
  
  