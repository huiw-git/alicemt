---
title: SQL Server Connector, Appendix
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7f5b73fc-e699-49ac-a22d-f4adcfae62b1
---
# SQL Server Connector, Appendix
  Supplemental information about the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Connector is provided in this topic. For more information about the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] connector, see [Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;](../Topic/Extensible%20Key%20Management%20Using%20Azure%20Key%20Vault%20\(SQL%20Server\).md), [Setup Steps for Extensible Key Management Using the Azure Key Vault](../../Topics\TopicNameNotContainA/Setup-Steps-for-Extensible-Key-Management-Using-the-Azure-Key-Vault.md),  and [Use SQL Server Connector with SQL Encryption Features](../../Topics\TopicNameNotContainA/Use-SQL-Server-Connector-with-SQL-Encryption-Features.md).  
  
  
##  <a name="AppendixA"></a> A. Maintenance Instructions for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Connector  
  
### Key Rollover  
  
> [!IMPORTANT]  
>  The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Connector requires the key name to only use the characters “a\-z”, “A\-Z”, “0\-9”, and “\-“, with a 26\-character limit.   
> Different key versions under the same key name in Azure Key Vault will not work with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Connector. To rotate an Azure Key Vault key that’s being used by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], a new key with a new key name must be created.  
  
 Typically  server asymmetric keys for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] encryption  need to be versioned every 1\-2 years. It's important to note that although the Key Vault allows keys to be versioned, customers should not use that feature to implement versioning. The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Connector cannot deal with changes in Key Vault key version. To implement key versioning, the customer must create a new key in the Key Vault and then re\-encrypt the data encryption key in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)].  
  
 For TDE, this is how this would be achieved:  
  
-   **In PowerShell:** Create a new asymmetric key \(with a different name from your current TDE asymmetric key\) in the Key Vault.  
  
    ```powershell  
    Add-AzureRmKeyVaultKey -VaultName 'ContosoDevKeyVault' `  
      -Name 'Key2' -Destination 'Software'  
    ```  
  
-   **Using [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] or sqlcmd.exe:** Use the following statements as shown in Step 3, section 3.  
  
     Import the new asymmetric key.  
  
    ```tsql  
    USE master  
    CREATE ASYMMETRIC KEY [MASTER_KEY2]   
    FROM PROVIDER [EKM]   
    WITH PROVIDER_KEY_NAME = 'Key2',   
    CREATION_DISPOSITION = OPEN_EXISTING   
    GO  
    ```  
  
     Create a new login to be associated with the new asymmetric key \(as shown under the TDE instructions\).  
  
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
       SECRET = 'EF5C8E094D2A4A769998D93440D8115DAADsecret123456789=’   
    FOR CRYPTOGRAPHIC PROVIDER EKM;  
  
    ALTER LOGIN TDE_Login2  
    ADD CREDENTIAL Azure_EKM_TDE_cred2;  
    GO  
    ```  
  
     Choose the database whose database encryption key you would like to re\-encrypt.  
  
    ```tsql  
    USE [database]  
    GO  
    ```  
  
     Re\-encrypt the database encryption key.  
  
    ```tsql  
    ALTER DATABASE ENCRYPTION KEY   
    ENCRYPTION BY SERVER ASYMMETRIC KEY [MASTER_KEY2];  
    GO  
    ```  
  
### Upgrade of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Connector  
  
1.  Stop the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
2.  Stop the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Connector service.  
  
3.  Uninstall the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Connector using the Windows Programs and Features feature.  
  
     \(Alternatively, you can rename the folder that the DLL file is in. The default name of the folder is  “[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] for Microsoft Azure Key Vault”.  
  
4.  Install the newest version of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Connector from the Microsoft Download Center.  
  
5.  Restart the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
6.  Run the following statement to alter the EKM Provider to start using the newest version of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Connector. Make sure that the file path is pointing to where you downloaded the newest version.  
  
    ```tsql  
    ALTER CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov   
    FROM FILE =   
    'C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault\Microsoft.AzureKeyVaultService.EKM.dll';  
    GO  
    ```  
  
7.  Check that the databases using TDE are accessible.  
  
8.  After validating that the update works, you may delete the old [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Connector folder \(if you chose to rename it instead of uninstalling in Step 3.\)  
  
### Rolling the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Service Principal  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] uses Service Principals created in Azure Active Directory as credentials to access the Key Vault.  Service Principal has a Client ID and Authentication Key.  A [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] credential is set up with the **VaultName**, **Client ID**, and **Authentication Key**.  The **Authentication Key** is valid for a certain period of time \(1 or 2 years\).   Before the time period expires a new key must be generated in Azure AD for the Service Principal.  Then the credential has to be changed in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].    [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] maintains a cache for the credential in the current session, so when a credential is changed, [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] should be restarted.  
  
### Key Backup and Recovery  
The Key vault should be regularly backed up. If an asymmetric key in the vault is lost, it can be restored from backup. The key must be restored using the same name as before, which the Restore PowerShell command will do (see below steps).  
If the vault has been lost, you will need to recreate a vault and restore the asymmetric key to the vault using the same name as before. The vault name can be different (or the same as before). You must also set the access permissions on the new vault to grant to the SQL Server service principal the access that is needed for the SQL Server encryption scenarios and then adjust the SQL Server credential so that the new vault name is reflected.  
In summary, here are the steps:  
  
* Backup the vault key (using the Backup-AzureKeyVaultKey Powershell cmdlet).  
* In the case of vault failure, create a new vault in the same geographic region*. The user creating this should be in the same default directory as the service principal setup for SQL Server.  
* Restore the key to the new vault (using the Restore-AzureKeyVaultKey Powershell cmdlet – this restores the key using the same name as before). If there is already a key with the same name, the restore will fail.  
* Grant permissions to the SQL Server service principal to use this new vault.  
* Modify the SQL Server credential used by the Database Engine to reflect the new vault name (if needed).  
  
Key backups can be restored across Azure regions, as long as they remain in the same geographic region or national cloud: USA, Canada, Japan, Australia, India, APAC, Europe Brazil, China, US Government, or Germany.  
  
  
##  <a name="AppendixB"></a> B. Frequently Asked Questions  
### On Azure Key Vault  
  
**How do key operations work with Azure Key Vault?**  
 The asymmetric key in the key vault is used to protect [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] encryption keys. Only the public portion of the asymmetric key ever leaves the vault; the private portion is never exported by the vault. All cryptographic operations using the asymmetric key are done within the Azure Key Vault service, and are protected by the service’s security.  
  
 **What is a Key URI?**  
 Every key in Azure Key Vault has a Uniform Resource Identifier \(URI\), which you can use to reference the key in your application. Use the format **https:\/\/ContosoKeyVault.vault.azure.net\/keys\/ContosoFirstKey** to get the current version, and use the format **https:\/\/ContosoKeyVault.vault.azure.net\/keys\/ContosoFirstKey\/cgacf4f763ar42ffb0a1gca546aygd87** to get a specific version.  
  
### On Configuring [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]  
  
**What are the minimum permission levels required for each configuration step in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]?**  
 Though you could perform all the configuration steps as a member of the sysadmin fixed server role, [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] encourages you to minimize the permissions you use. The following list defines the minimum permission level for each action.  
  
-   To create a cryptographic provider, requires `CONTROL SERVER` permission or membership in the **sysadmin** fixed server role.  
  
-   To change a configuration option and run the `RECONFIGURE` statement, you must be granted the `ALTER SETTINGS` server\-level permission. The `ALTER SETTINGS` permission is implicitly held by the sysadmin and **serveradmin** fixed server roles.  
  
-   To create a credential, requires `ALTER ANY CREDENTIAL` permission.  
  
-   To add a credential to a login, requires `ALTER ANY LOGIN` permission.  
  
-   To create an asymmetric key, requires `CREATE ASYMMETRIC KEY` permission.  
  
##  <a name="AppendixC"></a> C. Error Code Explanations for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Connector  
 **Provider Error Codes:**  
  
Error code  |Symbol  |Description    
---------|---------|---------  
0 | scp_err_Success | The operation has succeeded.    
1 | scp_err_Failure | The operation has failed.    
2 | scp_err_InsufficientBuffer | This error tells engine to allocate more memory for the buffer.    
3 | scp_err_NotSupported | The operation is not supported. E.g., the key type or algorithm specified is not supported by the EKM provider.    
4 | scp_err_NotFound | The specified key or algorithm could not be found by the EKM provider.    
5 | scp_err_AuthFailure | The authentication has failed with EKM provider.    
6 | scp_err_InvalidArgument | The provided argument is invalid.    
7 | scp_err_ProviderError | There is an unspecified error happened in EKM provider that is caught by SQL engine.    
2049 | scp_err_KeyNameDoesNotFitThumbprint | The key name is too long to fit into SQL engine’s thumbprint. The key name must not exceed 26 characters.    
2050 | scp_err_PasswordTooShort | The secret string which is the concatenation of AAD client id and secret is shorter than 32 characters.    
2051 | scp_err_OutOfMemory | SQL engine has run out of memory and failed to allocate memory for EKM provider.    
2052 | scp_err_ConvertKeyNameToThumbprint | Failed to convert key name to thumbprint.    
2053 | scp_err_ConvertThumbprintToKeyName|  Failed to convert thumbprint to key name.    
3000 | ErrorSuccess | The AKV operation has succeeded.    
3001 | ErrorUnknown | The AKV operation has failed with an unspecified error.    
3002 | ErrorHttpCreateHttpClientOutOfMemory  Cannot create a HttpClient for AKV operation due to out of memory.    
3003 | ErrorHttpOpenSession | Cannot open a Http session due to network error.    
3004 | ErrorHttpConnectSession | Cannot connect a Http session due to network error.    
3005 | ErrorHttpAttemptConnect | Cannot attempt a connect due to network error.    
3006 | ErrorHttpOpenRequest | Cannot open a request due to network error.    
3007 | ErrorHttpAddRequestHeader | Cannot add request header.    
3008 | ErrorHttpSendRequest | Cannot send a request due to network error.    
3009 | ErrorHttpGetResponseCode | Cannot get a response code due to network error.    
3010 | ErrorHttpResponseCodeUnauthorized | Server responded 401 for the request.    
3011 | ErrorHttpResponseCodeThrottled | Server has throttled the request.    
3012 | ErrorHttpResponseCodeClientError | Server responded a response code between 400 and 500.    
3013 | ErrorHttpResponseCodeServerError | Server responded a response code between 500 and 600.    
3014 | ErrorHttpQueryHeader | Cannot query for response header.    
3015 | ErrorHttpQueryHeaderOutOfMemoryCopyHeader | Cannot copy the response header due to out of memory.    
3016 | ErrorHttpQueryHeaderOutOfMemoryReallocBuffer | Cannot query the response header due to out of memory when reallocating a buffer.    
3017 | ErrorHttpQueryHeaderNotFound | Cannot find the query header in the response.    
3018 | ErrorHttpQueryHeaderUpdateBufferLength | Cannot update the buffer length when querying the response header.    
3019 | ErrorHttpReadData | Cannot read response data due to network error.    
  
If you don’t see your error code in this table, here are some other reasons the error may be happening:   
  
-   You may not have Internet access and cannot access your Azure Key Vault – please check your Internet connection.  
  
-   The Azure Key Vault service may be down. Please try again at another time.  
  
-   You may have dropped the asymmetric key from Azure Key Vault or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Please restore the key.  
  
-   If you’re running SQL Server 2008, 2008 R2, or 2012, and are receiving an “Cannot load library” error, make sure you have the latest version of the Visual Studio C++ redistributable installed. This can be found on the Microsoft Download Center.   
  
  
## Additional References  
 More About Extensible Key Management:  
  
-   [Extensible Key Management &#40;EKM&#41;](../Topic/Extensible%20Key%20Management%20\(EKM\).md)  
  
 SQL Encryptions supporting EKM:  
  
-   [Enable TDE on SQL Server Using EKM](../../Topics\TopicNameNotContainA/Enable-TDE-on-SQL-Server-Using-EKM.md)  
  
-   [Backup Encryption](../../Topics\TopicNameNotContainA/Backup-Encryption.md)  
  
-   [Create an Encrypted Backup](../../Topics\TopicNameNotContainA/Create-an-Encrypted-Backup.md)  
  
 Related [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] Commands:  
  
-   [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)  
  
-   [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../Topic/CREATE%20CRYPTOGRAPHIC%20PROVIDER%20\(Transact-SQL\).md)  
  
-   [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../Topic/CREATE%20CREDENTIAL%20\(Transact-SQL\).md)  
  
-   [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../Topic/CREATE%20ASYMMETRIC%20KEY%20\(Transact-SQL\).md)  
  
-   [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../Topic/CREATE%20SYMMETRIC%20KEY%20\(Transact-SQL\).md)  
  
-   [CREATE LOGIN &#40;Transact-SQL&#41;](../Topic/CREATE%20LOGIN%20\(Transact-SQL\).md)  
  
-   [ALTER LOGIN &#40;Transact-SQL&#41;](../Topic/ALTER%20LOGIN%20\(Transact-SQL\).md)  
  
 Azure Key Vault documentation:  
  
-   [What is Azure Key Vault?](https://azure.microsoft.com/documentation/articles/key-vault-whatis/)  
  
-   [Get Started with Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)  
  
-   PowerShell [Azure Key Vault Cmdlets](https://msdn.microsoft.com/library/dn868052.aspx) reference  
  
## See Also  
 [Extensible Key Management Using Azure Key Vault](Extensible%20Key%20Management%20Using%20Azure%20Key%20Vault%20\(SQL%20Server\).md)  [Use SQL Server Connector with SQL Encryption Features](../../Topics\TopicNameNotContainA/Use-SQL-Server-Connector-with-SQL-Encryption-Features.md)   
 [EKM provider enabled Server Configuration Option](../../Topics\TopicNameNotContainA/EKM-provider-enabled-Server-Configuration-Option.md)   
 [Setup Steps for Extensible Key Management Using the Azure Key Vault](../../Topics\TopicNameNotContainA/Setup-Steps-for-Extensible-Key-Management-Using-the-Azure-Key-Vault.md)  
  
  