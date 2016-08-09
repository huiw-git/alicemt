---
title: "SQL Server Connector, Appendix"
ms.custom: na
ms.date: 2016-05-18
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7f5b73fc-e699-49ac-a22d-f4adcfae62b1
caps.latest.revision: 16
---
# SQL Server Connector, Appendix
Supplemental information about the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector is provided in this topic. For more information about the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] connector, see [Extensible Key Management Using Azure Key Vault (SQL Server)](../../Topics/TopicNameNotContainA/Extensible-Key-Management-Using-Azure-Key-Vault--SQL-Server-.md), [Setup Steps for Extensible Key Management Using the Azure Key Vault](../../Topics/TopicNameNotContainA/Setup-Steps-for-Extensible-Key-Management-Using-the-Azure-Key-Vault.md),  and [Use SQL Server Connector with SQL Encryption Features](../../Topics/TopicNameNotContainA/Use-SQL-Server-Connector-with-SQL-Encryption-Features.md).  
  
##  <a name="AppendixA"></a> A. Error Code Explanations for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector  
 **Provider Error Codes:**  
  
|Provider Error Code|Explanation|  
|-------------------------|-----------------|  
|2050|Run time failure due to unhandled exception.|  
|2053|Web request failed. A generic vault error to represent unexpected failures.<br /><br /> Users receiving the error “Cannot export public key from the provider. Provider error code: 2053.” Should check their `get`, `list`, `wrapKey`, and `unwrapKey` permissions in the key vault.|  
|2055|Error creating key in the vault because it already exists.|  
  
 If you don’t receive an error code in this table, one of the following errors might apply:  
  
-   You may not have Internet access and cannot access your Azure Key Vault – please check your Internet connection.  
  
-   The Azure Key Vault service may be down. Please try again at another time.  
  
-   You may have dropped the asymmetric key from Azure Key Vault or [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. Please restore the key.  
  
##  <a name="AppendixB"></a> B. Configuration Settings for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector  
 **Configuration AppConfig Settings:**  
  
 The **appSettings** are in the **Microsoft.ManagedEKM.Service.exe** configuration file in the directory where the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector for Microsoft Azure Key Vault program files are installed on your computer.  
  
|Setting|Details|Values|  
|-------------|-------------|------------|  
|LogLevel|The Azure Key Vault SQL Connector windows service writes to the Application event log.  The service can be configured to write events at the various levels which controls the type of events logged and in term determines the verbosity of logging.|Verbose, Trace, Error, Critical<br /><br /> Default is Error|  
|Use SoftKeys|Controls whether the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector creates a software controlled key or a HSM controlled key when a new asymmetric key is created in the Key Vault EKM using  `CREATE ASYMMETRIC KEY`.|true, false<br /><br /> Default is true|  
|Disable Cache|The S[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector caches decrypted Data Encryption Keys it gets back from the Key vault.  This helps minimize latencies in fetching a key for the column level encryption scenario.   The Disable Cache setting lets you disable any caching of results.|true, false<br /><br /> Default is false<br /><br /> If the value is set to true, the Cache Duration setting has no effect.|  
|Cache Duration|The duration for which the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector caches the decrypted data encryption keys from the vault.|.NET timespan:<br /><br /> 1:00:00 represents a one hour expiration<br /><br /> 30:00 represents 30 minutes<br /><br /> Default is 30 minutes|  
  
##  <a name="AppendixC"></a> C. Maintenance Instructions for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector  
  
### Key Rollover  
  
> [!IMPORTANT]  
>  The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector requires the key name to only use the characters “a-z”, “A-Z”, “0-9”, and “-“, with a 26-character limit.   
> Different key versions under the same key name in Azure Key Vault will not work with [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector. To rotate an Azure Key Vault key that’s being used by [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], a new key with a new key name must be created.  
  
 Typically  server asymmetric keys for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] encryption  need to be versioned every 1-2 years. It's important to note that although the Key Vault allows keys to be versioned, customers should not use that feature to implement versioning. The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector cannot deal with changes in Key Vault key version. To implement key versioning, the customer must create a new key in the Key Vault and then re-encrypt the data encryption key in [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)].  
  
 For TDE, this is how this would be achieved:  
  
-   **In PowerShell:** Create a new asymmetric key (with a different name from your current TDE asymmetric key) in the Key Vault.  
  
    ```powershell  
    Add-AzureRmKeyVaultKey -VaultName 'ContosoDevKeyVault' `  
      -Name 'Key2' -Destination 'Software'  
    ```  
  
-   **Using [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)] or sqlcmd.exe:** Use the following statements as shown in Step 3, section 3.  
  
     Import the new asymmetric key.  
  
    ```tsql  
    USE master  
    CREATE ASYMMETRIC KEY [MASTER_KEY2]   
    FROM PROVIDER [EKM]   
    WITH PROVIDER_KEY_NAME = 'Key2',   
    CREATION_DISPOSITION = OPEN_EXISTING   
    GO  
    ```  
  
     Create a new login to be associated with the new asymmetric key (as shown under the TDE instructions).  
  
    ```tsql  
    USE master  
    CREATE LOGIN TDE_Login2   
    FROM ASYMMETRIC KEY [MASTER_KEY2]  
    GO  
    ```  
  
     Create a new credential to be mapped to the login.  
  
    ```tsql  
    CREATE CREDENTIAL Azure_EKM_TDE_cred2  
        WITH IDENTITY = 'ContosoDevKeyVault',   
       SECRET = 'EF5C8E094D2A4A769998D93440D8115DAADsEcReT123456789=’   
    FOR CRYPTOGRAPHIC PROVIDER EKM;  
  
    ALTER LOGIN TDE_Login2  
    ADD CREDENTIAL Azure_EKM_TDE_cred2;  
    GO  
    ```  
  
     Choose the database whose database encryption key you would like to re-encrypt.  
  
    ```tsql  
    USE [database]  
    GO  
    ```  
  
     Re-encrypt the database encryption key.  
  
    ```tsql  
    ALTER DATABASE ENCRYPTION KEY   
    ENCRYPTION BY SERVER ASYMMETRIC KEY [MASTER_KEY2];  
    GO  
    ```  
  
### Upgrade of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector  
  
1.  Stop the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
2.  Stop the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector service.  
  
3.  Uninstall the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector using the Windows Programs and Features feature.  
  
     (Alternatively, you can rename the folder that the DLL file is in. The default name of the folder is  “[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] for Microsoft Azure Key Vault”.  
  
4.  Install the newest version of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector from the Microsoft Download Center.  
  
5.  Restart the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
6.  Run the following statement to alter the EKM Provider to start using the newest version of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector. Make sure that the file path is pointing to where you downloaded the newest version.  
  
    ```tsql  
    ALTER CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov   
    FROM FILE =   
    'C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault\Microsoft.AzureKeyVaultService.EKM.dll';  
    GO  
    ```  
  
7.  Check that the databases using TDE are accessible.  
  
8.  After validating that the update works, you may delete the old [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector folder (if you chose to rename it instead of uninstalling in Step 3.)  
  
### Rolling the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Service Principal  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] uses Service Principals created in Azure Active Directory as credentials to access the Key Vault.  Service Principal has a Client ID and Authentication Key.  A [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] credential is set up with the **VaultName**, **Client ID**, and **Authentication Key**.  The **Authentication Key** is valid for a certain period of time (1 or 2 years).   Before the time period expires a new key must be generated in Azure AD for the Service Principal.  Then the credential has to be changed in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].    [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)] maintains a cache for the credential in the current session, so when a credential is changed, [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)] should be restarted.  
  
### Key Backup and Recovery  
 The Key vault should be regularly backed up. If an asymmetric key in the vault is lost, it can be restored from backup.  The key must be restored using the same name as before.  
  
 If the vault has been lost, you will need to recreate a vault and restore the asymmetric key to the vault using the same name as before.  The vault name can be different (or the same as before).   You must also set the access permissions on the new vault to grant to the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] service principal the access that is needed for the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] encryption scenarios and then adjust the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] credential so that the new vault name is reflected.  
  
 In summary, here are the steps:  
  
-   Backup the vault key (using the `Backup-AzureKeyVaultKey Powershell` cmdlet).  
  
-   In the case of vault failure, create a new vault in the same region.  The user creating this should be in the same default directory as the service principal setup for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
-   Restore the key to the new vault (using the `Restore-AzureKeyVaultKey` Powershell cmdlet – this restores the key using the same name as before).  
  
-   Grant permissions to the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] service principal to use this new vault.  
  
-   Modify the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] credential used by the Database Engine to reflect the new vault name (if needed).  
  
##  <a name="AppendixD"></a> D. Frequently Asked Questions  
 On Azure Key Vault  
  
How do key operations work with Azure Key Vault?  
 The asymmetric key in the key vault is used to protect [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] encryption keys. Only the public portion of the asymmetric key ever leaves the vault; the private portion is never exported by the vault. All cryptographic operations using the asymmetric key are done within the Azure Key Vault service, and are protected by the service’s security.  
  
 What is a Key URI?  
 Every key in Azure Key Vault has a Uniform Resource Identifier (URI), which you can use to reference the key in your application. Use the format **https://ContosoKeyVault.vault.azure.net/keys/ContosoFirstKey** to get the current version, and use the format **https://ContosoKeyVault.vault.azure.net/keys/ContosoFirstKey/cgacf4f763ar42ffb0a1gca546aygd87** to get a specific version.  
  
 On Configuring [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]  
  
 What are the minimum permission levels required for each configuration step in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]?  
 Though you could perform all the configuration steps as a member of the sysadmin fixed server role, [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] encourages you to minimize the permissions you use. The following list defines the minimum permission level for each action.  
  
-   To create a cryptographic provider, requires `CONTROL SERVER` permission or membership in the **sysadmin** fixed server role.  
  
-   To change a configuration option and run the `RECONFIGURE` statement, you must be granted the `ALTER SETTINGS` server-level permission. The `ALTER SETTINGS` permission is implicitly held by the sysadmin and **serveradmin** fixed server roles.  
  
-   To create a credential, requires `ALTER ANY CREDENTIAL` permission.  
  
-   To add a credential to a login, requires `ALTER ANY LOGIN` permission.  
  
-   To create an asymmetric key, requires `CREATE ASYMMETRIC KEY` permission.  
  
## Additional References  
 More About Extensible Key Management  
  
-   [Extensible Key Management (EKM)](../../Topics/TopicNameNotContainA/Extensible-Key-Management--EKM-.md)  
  
 SQL Encryptions supporting EKM  
  
-   [Enable TDE on SQL Server Using EKM](../../Topics/TopicNameNotContainA/Enable-TDE-on-SQL-Server-Using-EKM.md)  
  
     [Backup Encryption](../../Topics/TopicNameNotContainA/Backup-Encryption.md)  
  
     [Create an Encrypted Backup](../../Topics/TopicNameNotContainA/Create-an-Encrypted-Backup.md)  
  
 Related [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] Commands  
  
-   [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)  
  
     [CREATE CRYPTOGRAPHIC PROVIDER (Transact-SQL)](assetId:///059a39a6-9d32-4d3f-965b-0a1ce75229c7)  
  
     [CREATE CREDENTIAL (Transact-SQL)](assetId:///d5e9ae69-41d9-4e46-b13d-404b88a32d9d)  
  
     [CREATE ASYMMETRIC KEY (Transact-SQL)](assetId:///141bc976-7631-49f6-82bd-a235028645b1)  
  
     [CREATE SYMMETRIC KEY (Transact-SQL)](assetId:///b5d23572-b79d-4cf1-9eef-d648fa3b1358)  
  
     [CREATE LOGIN (Transact-SQL)](assetId:///eb737149-7c92-4552-946b-91085d8b1b01)  
  
     [ALTER LOGIN (Transact-SQL)](assetId:///e247b84e-c99e-4af8-8b50-57586e1cb1c5)  
  
 Azure Key Vault documentation  
  
-   [What is Azure Key Vault?](https://azure.microsoft.com/documentation/articles/key-vault-whatis/)  
  
-   [Get Started with Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)  
  
-   PowerShell [Azure Key Vault Cmdlets](https://msdn.microsoft.com/library/dn868052.aspx) reference  
  
## See Also  
 [Extensible Key Management Using Azure Key Vault (Proposed)](../../Topics/TopicNameNotContainA/Extensible-Key-Management-Using-Azure-Key-Vault--Proposed-.md)   
 [Use SQL Server Connector with SQL Encryption Features](../../Topics/TopicNameNotContainA/Use-SQL-Server-Connector-with-SQL-Encryption-Features.md)   
 [EKM provider enabled Server Configuration Option](../../Topics/TopicNameNotContainA/EKM-provider-enabled-Server-Configuration-Option.md)   
 [Setup Steps for Extensible Key Management Using the Azure Key Vault](../../Topics/TopicNameNotContainA/Setup-Steps-for-Extensible-Key-Management-Using-the-Azure-Key-Vault.md)