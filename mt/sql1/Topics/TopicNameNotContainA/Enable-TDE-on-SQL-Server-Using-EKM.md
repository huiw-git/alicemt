---
title: "Enable TDE on SQL Server Using EKM"
ms.custom: na
ms.date: 2016-04-15
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b892e7a7-95bd-4903-bf54-55ce08e225af
caps.latest.revision: 26
caps.handback.revision: 0
manager: jhubbard
---
# Enable TDE on SQL Server Using EKM
This topic describes how to enable transparent data encryption (TDE) in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] to protect a database encryption key by using an asymmetric key stored in an extensible key management (EKM) module with [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 TDE encrypts the storage of an entire database by using a symmetric key called the database encryption key. The database encryption key can also be protected using a certificate which is protected by the database master key of the master database. For more information about protecting the database encryption key by using the database master key, see [Transparent Data Encryption (TDE)](../../Topics/TopicNameNotContainA/Transparent-Data-Encryption--TDE-.md). For information about configuring TDE when [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is running on an Azure VM, see [Extensible Key Management Using Azure Key Vault (SQL Server)](../../Topics/TopicNameNotContainA/Extensible-Key-Management-Using-Azure-Key-Vault--SQL-Server-.md).  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   [To enable TDE using EKM, using Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   You must be a high privileged user (such as a system administrator) to create a database encryption key and encrypt a database. That user must be able to be authenticated by the EKM module.  
  
-   Upon start up the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] must open the database. To do this, you should create a credential that will be authenticated by the EKM, and add it to a login that is based on an asymmetric key. Users cannot login using that login, but the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] will be able to authenticate itself with the EKM device.  
  
-   If the asymmetric key stored in the EKM module is lost, the database will not be able to be opened by [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. If the EKM provider lets you back up the asymmetric key, you should create a back up and store it in a secure location.  
  
-   The options and parameters required by your EKM provider can differ from what is provided in the code example below. For more information, see your EKM provider.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 This topic uses the following permissions:  
  
-   To change a configuration option and run the RECONFIGURE statement, you must be granted the ALTER SETTINGS server-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
-   Requires ALTER ANY CREDENTIAL permission.  
  
-   Requires ALTER ANY LOGIN permission.  
  
-   Requires CREATE ASYMMETRIC KEY permission.  
  
-   Requires CONTROL permission on the database to encrypt the database.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To enable TDE using EKM  
  
1.  Copy the files supplied by the EKM provider to an appropriate location on the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] computer. In this example, we use the **C:\EKM** folder.  
  
2.  Install certificates to the computer as required by your EKM provider.  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] does not supply an EKM provider. Each EKM provider can have different procedures for installing, configuring and authorizing users.  Consult your EKM provider documentation to complete this step.  
  
3.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
4.  On the Standard bar, click **New Query**.  
  
5.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    -- Enable advanced options.  
    sp_configure 'show advanced options', 1 ;  
    GO  
    RECONFIGURE ;  
    GO  
    -- Enable EKM provider  
    sp_configure 'EKM provider enabled', 1 ;  
    GO  
    RECONFIGURE ;  
    GO  
    -- Create a cryptographic provider, which we have chosen to call "EKM_Prov," based on an EKM provider  
  
    CREATE CRYPTOGRAPHIC PROVIDER EKM_Prov   
    FROM FILE = 'C:\EKM_Files\KeyProvFile.dll' ;  
    GO  
  
    -- Create a credential that will be used by system administrators.  
    CREATE CREDENTIAL sa_ekm_tde_cred   
    WITH IDENTITY = 'Identity1',   
    SECRET = 'q*gtev$0u#D1v'   
    FOR CRYPTOGRAPHIC PROVIDER EKM_Prov ;  
    GO  
  
    -- Add the credential to a high privileged user such as your   
    -- own domain login in the format [DOMAIN\login].  
    ALTER LOGIN Contoso\Mary  
    ADD CREDENTIAL sa_ekm_tde_cred ;  
    GO  
    -- create an asymmetric key stored inside the EKM provider  
    USE master ;  
    GO  
    CREATE ASYMMETRIC KEY ekm_login_key   
    FROM PROVIDER [EKM_Prov]  
    WITH ALGORITHM = RSA_512,  
    PROVIDER_KEY_NAME = 'SQL_Server_Key' ;  
    GO  
  
    -- Create a credential that will be used by the Database Engine.  
    CREATE CREDENTIAL ekm_tde_cred   
    WITH IDENTITY = 'Identity2'   
    , SECRET = 'jeksi84&sLksi01@s'   
    FOR CRYPTOGRAPHIC PROVIDER EKM_Prov ;  
  
    -- Add a login used by TDE, and add the new credential to the login.  
    CREATE LOGIN EKM_Login   
    FROM ASYMMETRIC KEY ekm_login_key ;  
    GO  
    ALTER LOGIN EKM_Login   
    ADD CREDENTIAL ekm_tde_cred ;  
    GO  
  
    -- Create the database encryption key that will be used for TDE.  
    USE AdventureWorks2012 ;  
    GO  
    CREATE DATABASE ENCRYPTION KEY  
    WITH ALGORITHM  = AES_128  
    ENCRYPTION BY SERVER ASYMMETRIC KEY ekm_login_key ;  
    GO  
  
    -- Alter the database to enable transparent data encryption.  
    ALTER DATABASE AdventureWorks2012   
    SET ENCRYPTION ON ;  
    GO  
    ```  
  
 For more information, see the following:  
  
-   [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)  
  
-   [CREATE CRYPTOGRAPHIC PROVIDER (Transact-SQL)](assetId:///059a39a6-9d32-4d3f-965b-0a1ce75229c7)  
  
-   [CREATE CREDENTIAL (Transact-SQL)](assetId:///d5e9ae69-41d9-4e46-b13d-404b88a32d9d)  
  
-   [CREATE ASYMMETRIC KEY (Transact-SQL)](assetId:///141bc976-7631-49f6-82bd-a235028645b1)  
  
-   [CREATE LOGIN (Transact-SQL)](assetId:///eb737149-7c92-4552-946b-91085d8b1b01)  
  
-   [CREATE DATABASE ENCRYPTION KEY (Transact-SQL)](assetId:///2ee95a32-5140-41bd-9ab3-a947b9990688)  
  
-   [ALTER LOGIN (Transact-SQL)](assetId:///e247b84e-c99e-4af8-8b50-57586e1cb1c5)  
  
-   [ALTER DATABASE (Transact-SQL)](assetId:///15f8affd-8f39-4021-b092-0379fc6983da)  
  
## See Also  
 [Transparent Data Encryption with Azure SQL Database](../../Topics/TopicNameNotContainA/Transparent-Data-Encryption-with-Azure-SQL-Database.md)