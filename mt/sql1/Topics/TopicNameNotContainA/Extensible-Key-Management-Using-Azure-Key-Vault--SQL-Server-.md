---
title: "Extensible Key Management Using Azure Key Vault (SQL Server)"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-05-18
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3efdc48a-8064-4ea6-a828-3fbf758ef97c
caps.latest.revision: 66
manager: jhubbard
---
# Extensible Key Management Using Azure Key Vault (SQL Server)
The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector for [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Azure Key Vault enables [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] encryption to leverage the Azure Key Vault service as an [Extensible Key Management (EKM)](../../Topics/TopicNameNotContainA/Extensible-Key-Management--EKM-.md) provider to protect its encryption keys.  
  
 Included in this topic:  
  
-   [Uses of EKM](#Uses)  
  
-   [Setup steps](#SetupSteps)  
  
    -   [Step 1: Setting up the Key Vault for use by SQL Server](#Step1)  
  
    -   [Step 2: Installing the SQL Server Connector](#Step2)  
  
    -   [Step 3: Configure SQL Server to use an EKM provider for the Key Vault](#Step3)  
  
-   [Using EKM with SQL Server Encryption Features](#UsesOfEKM)  
  
    -   [Transparent Data Encryption by Using an Asymmetric Key from the Key Vault](#ExampleA)  
  
    -   [Encrypting Backups by Using an Asymmetric Key from the Key Vault](#ExampleB)  
  
    -   [Column Level Encryption by Using an Asymmetric Key from the Key Vault](#ExampleC)  
  
-   [Appendix](#Appendix)  
  
##  <a name="Uses"></a> Uses of EKM  
 An organization can use [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] encryption to protect sensitive data. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] encryption includes [Transparent Data Encryption (TDE)](../../Topics/TopicNameNotContainA/Transparent-Data-Encryption--TDE-.md), [Column Level Encryption](assetId:///0be5626b-5a25-4d8c-9f44-7abbfccf816c) (CLE), and [Backup Encryption](../../Topics/TopicNameNotContainA/Backup-Encryption.md). In all of these cases the data is encrypted using a symmetric data encryption key. The symmetric data encryption key is further protected by encrypting it with a hierarchy of keys stored in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. Alternatively, the EKM provider architecture enables [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to protect the data encryption keys by using an asymmetric key stored outside of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] in an external cryptographic provider. Using the EKM provider architecture adds an additional layer of security and allows organizations to separate the management of keys and data.  
  
 The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector for Azure Key Vault lets [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] leverage the scalable, high performance, and highly available key vault service as an EKM provider for encryption key protection. The key vault service can be used with [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] installations on [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Azure Virtual Machines and for on-premises servers. The key vault service also provides the option to use tightly controlled and monitored Hardware Security Modules (HSMs) for a higher level of protection for asymmetric encryption keys. For more information about the key vault, see [Azure Key Vault](http://go.microsoft.com/fwlink/?LinkId=521401).  
  
 The following image summarizes the process flow of EKM using the key vault. The process step numbers in the image are not meant to match the setup step numbers that follow the image.  
  
 ![SQL Server EKM using the Azure Key Vault](../../Topics/TopicNameNotContainA/images/EKM_using_Azure_Key_Vault.png "EKM_using_Azure_Key_Vault")  
  
##  <a name="SetupSteps"></a> Setup steps  
  
###  <a name="Step1"></a> Step 1: Set up the Key Vault for use by SQL Server  
 Use the following steps to set up a key vault for use with the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] for encryption key protection. A vault may already be in use for the organization. When a vault does not exist, the Azure Administrator in your organization that is designated to manage encryption keys can create a vault, generate an asymmetric key in the vault, and then authorize [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to use the key. To familiarize yourself with the key vault service review [Get Started with Azure Key Vault](http://go.microsoft.com/fwlink/?LinkId=521402), and the PowerShell [Azure Key Vault Cmdlets](http://go.microsoft.com/fwlink/?LinkId=521403) reference.  
  
> [!IMPORTANT]  
>  The default Azure Active Directory for the subscription in which the key vault is created must be the same as the default Azure Active Directory used for registering [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
 Below is a basic overview of the steps to set up Azure Key Vault by using PowerShell. For more detailed instructions, see the instructions in the **Create a key vault** section of [Get Started with Azure Key Vault](http://go.microsoft.com/fwlink/?LinkId=521402).  
  
1.  **Get an Azure Active Directory Service Principal to use for SQL Server:** When the organization signs up for a Microsoft cloud service, it gets an Azure Active Directory. Create **Service Principals** in the Azure Active Directory for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to use (to authenticate itself to Azure Active Directory) while accessing the key vault.  
  
     For more information about how to register an application and generate a service principal, see the **Register an Application with Azure Active Directory** section in [Get Started with Azure Key Vault](http://go.microsoft.com/fwlink/?LinkId=521402).  
  
     Record the **Application ID** (also known as a **CLIENT ID**) and the **Authentication Key** (also known as a **Secret**) for use later in Step 3. In this document we use the Client ID `EF5C8E09-4D2A-4A76-9998-D93440D8115D`.  
  
2.  **Sign in:** Start an Azure PowerShell session and sign in to your Azure account with the following command:  
  
    ```  
    Add-AzureAccount  
    ```  
  
     In the pop-up browser window, enter your Azure account user name and password. Windows PowerShell will get all the subscriptions that are associated with this account and by default, uses the first one.  
    If you have multiple subscriptions and want to specify a specific one to use for the vault, then use `Get-AzureSubscription` to see the subscriptions and `Select-AzureSubscription` to choose the correct subscription.  
  
3.  **Switch to using Azure Resource Manager mode:** The Key Vault cmdlets require Azure Resource Manager, so type the following to switch to Azure Resource Manager mode:  
  
    ```  
    Switch-AzureMode AzureResourceManager  
    ```  
  
4.  **Create a new resource group:** When you use Azure Resource Manager, all related resources are created inside a resource group. We will create a new resource group named `ContosoResourceGroup` for this tutorial. Choose your own unique resource group and key vault name as all key vault names are globally unique.  
  
    ```  
    New-AzureResourceGroup –Name 'ContosoResourceGroup' –Location 'East US'  
    ```  
  
     For the `-Location` parameter, use the command `Get-AzureLocation` to identify how to specify an alternative location to the one in this example. If you need more information, type: `Get-Help Get-AzureLocation`  
  
     When successful, you will see a list of resource group attributes, including the provisioning state and permissions.  
  
5.  **Create a key vault:** Use the `New-AzureKeyVault` cmdlet to create a key vault. This cmdlet has three mandatory parameters: a resource group name, a key vault name, and the geographic location.  
    For example, if you use the vault name of `ContosoKeyVault`, the resource group name of `ContosoResourceGroup`, and the location of East US, type:  
  
    ```  
    New-AzureKeyVault -VaultName 'ContosoKeyVault' -ResourceGroupName 'ContosoResourceGroup' -Location 'East US'  
    ```  
  
     Record the name of the vault. (This topic uses `ContosoKeyVault` as the key vault name.)  
  
     When successful, you will see a list of key vault attributes, including the resource ID and vault URI.  
  
6.  **Generate an asymmetric key:** Generate an asymmetric key in the vault.  
    If you want Azure Key Vault to create a software-protected key for you, use the [Add-AzureKeyVaultKey](https://msdn.microsoft.com/library/azure/dn868048.aspx) cmdlet, and type the following:  
  
    ```  
    $key = Add-AzureKeyVaultKey -VaultName 'ContosoKeyVault' -Name 'ContosoFirstKey' -Destination 'Software'  
    ```  
  
     When successful, no text will be returned after the command.  
  
     Alternately, if you have an existing software-protected key in a .PFX file saved to your C:\ drive in a file named `softkey.pfx` that you want to upload to Azure Key Vault, type the following to set the variable `securepfxpwd` for a password of `123` for the .PFX file:  
  
    ```  
    $securepfxpwd = ConvertTo-SecureString –String '123' –AsPlainText –Force  
    ```  
  
     Then type the following to import the key from the .PFX file, which protects the key by software in the Key Vault service:  
  
    ```  
    $key = Add-AzureKeyVaultKey -VaultName 'ContosoKeyVault' -Name 'ContosoFirstKey' -KeyFilePath 'c:\softkey.pfx' -KeyFilePassword $securepfxpwd  
    ```  
  
     You can now reference this key that you created or uploaded to Azure Key Vault, by using its Uniform Resource Identifier (URI). Use the format **https://ContosoKeyVault.vault.azure.net/keys/ContosoFirstKey** to get the current version, and use the format **https://ContosoKeyVault.vault.azure.net/keys/ContosoFirstKey/cgacf4f763ar42ffb0a1gca546aygd87** to get a specific version.  
  
     The asymmetric key in the key vault is used to protect [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] encryption keys. Only the public portion of the asymmetric key ever leaves the vault, the private portion is never exported by the vault. All cryptographic operations using the asymmetric key are delegated to the Azure Key Vault, and are protected by the key vault security.  
  
     There are several ways that you can generate an asymmetric key and store it in the vault. You can externally generate a key, and import the key into the vault as a .pfx file. Or create the key directly in the vault by using the key vault APIs.  
  
     The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector requires the asymmetric keys to be 2048-bit RSA, and the key name can only use the characters "a-z", "A-Z", "0-9", and "-". In this document the name of the asymmetric key is referred to as **ContosoMasterKey**. Replace this with the unique name you use for the key.  
  
    > [!IMPORTANT]  
    >  Importing the asymmetric key is highly recommended for production scenarios because it allows the administrator to escrow the key in a key escrow system. If the asymmetric key is created in the vault, it cannot be escrowed because the private key can never leave the vault. Keys used to protect critical data should be escrowed. The loss of an asymmetric key will result in permanently unrecoverable data.  
  
    > [!IMPORTANT]  
    >  The key vault supports multiple versions of the same named key. Keys to be used by [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector should not be versioned or rolled. If the administrator wants to roll the key used for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] encryption, a new key with a different name should be created in the vault and used to encrypt the DEK.  
  
     For more information on how to import a key into the key vault or to create a key in the key vault (not recommended for a production environment), see the **Add a key or secret to the key vault** section in [Get Started with Azure Key Vault](http://go.microsoft.com/fwlink/?LinkId=521402).  
  
7.  **Grant Permission for the Service Principal to access the Key Vault:** The **Service Principal** requires the **get**, **list**, **wrapKey**, and **unwrapKey** permissions in the key vault. If you intend to create keys through [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] you also need to grant the **create** permission in key vault.  
  
     To authorize the application to access the key or secret in the vault, use the `Set-AzureKeyVaultAccessPolicy` cmdlet.  
  
     For example, if your vault name is `ContosoKeyVault` and the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Application Service Principal you want to authorize has a Client ID of `EF5C8E09-4D2A-4A76-9998-D93440D8115D`, and you want to authorize the application to protect the SQL Server data encryption keys with the master keys in your vault, run the following:  
  
    ```  
    Set-AzureKeyVaultAccessPolicy -VaultName 'ContosoKeyVault' -ServicePrincipalName EF5C8E09-4D2A-4A76-9998-D93440D8115D -PermissionsToKeys get, list, wrapKey, unwrapKey  
    ```  
  
    > [!IMPORTANT]  
    >  The user must have at least the **get**, **list**, **wrapKey** and **unwrapKey** operations for the key vault, and may need the **create** permission.  
  
     For more information about granting permissions to the vault, see the **Authorize the application to use the key or secret** section in [Get Started with Azure Key Vault](http://go.microsoft.com/fwlink/?LinkId=521402).  
  
     Links to Azure Key Vault documentation  
  
    -   [What is Azure Key Vault?](http://go.microsoft.com/fwlink/?LinkId=521401)  
  
    -   [Get Started with Azure Key Vault](http://go.microsoft.com/fwlink/?LinkId=521402)  
  
    -   PowerShell [Azure Key Vault Cmdlets](http://go.microsoft.com/fwlink/?LinkId=521403) reference  
  
###  <a name="Step2"></a> Step 2: Install the SQL Server Connector  
 The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector is downloaded and installed by the administrator of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] computer. The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector is available as a download from the [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=521700).  Search for **SQL Server Connector for Microsoft Azure Key Vault**, review the details, system requirements and install instructions and choose to download the connector and start the installation using **Run**. Review the license and accept the license and continue.  
  
 By default, the connector installs at **C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault**. This location can be changed during setup. (If changed, adjust the scripts below.)  
  
 There is no interface for the Connector, but if it is installed successfully, the following are installed on the machine:  
  
-   **Microsoft.AzureKeyVaultService.EKM.dll**: This is the cryptographic EKM provider DLL that needs to be registered with [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] by using the CREATE CRYPTOGRAPHIC PROVIDER statement.  
  
-   **Azure Key Vault SQL Server Connector**: This is a Windows service that enables the cryptographic EKM provider to communicate with the key vault.  
  
 The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector installation also allows you to optionally download sample scripts for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] encryption.  
  
 To view error code explanations, configuration settings, or maintenance tasks for SQL Server Connector, visit the appendix at the bottom of this topic:  
  
-   [Appendix A: Error Code Explanations for SQL Server Connector](#AppendixA)  
  
-   [Appendix B: Configuration Settings for SQL Server Connector](#AppendixB)  
  
-   [Appendix C: Maintenance Instructions for SQL Server Connector](#AppendixC)  
  
###  <a name="Step3"></a> Step 3: Configure SQL Server to use an EKM provider for the Key Vault  
  
####  <a name="Permissions"></a> Permissions  
 Though you could perform all the configuration steps as a member of the **sysadmin** fixed server role, [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] encourages you to minimize the permissions you use.  The following list defines the minimum permission level for each action.  
  
-   To create a cryptographic provider, requires CONTROL SERVER permission or membership in the **sysadmin** fixed server role.  
  
-   To change a configuration option and run the RECONFIGURE statement, you must be granted the ALTER SETTINGS server-level permission. The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.  
  
-   To create a credential, requires ALTER ANY CREDENTIAL permission.  
  
-   To add a credential to a login, requires ALTER ANY LOGIN permission.  
  
-   To create an asymmetric key, requires CREATE ASYMMETRIC KEY permission.  
  
####  <a name="TsqlProcedure"></a> To configure SQL Server to use a cryptographic provider  
  
1.  Using [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)], configure the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] to use EKM, and register (create) the cryptographic provider with [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
    ```  
    -- Enable advanced options.  
    USE master;  
    GO  
  
    sp_configure 'show advanced options', 1 ;  
    GO  
    RECONFIGURE ;  
    GO  
    -- Enable EKM provider  
    sp_configure 'EKM provider enabled', 1 ;  
    GO  
    RECONFIGURE ;  
    GO  
  
    -- Create a cryptographic provider, using the SQL Server Connector  
    -- which is an EKM provider for the Azure Key Vault. This example uses   
    -- the name AzureKeyVault_EKM_Prov.  
  
    CREATE CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov   
    FROM FILE = 'C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault\Microsoft.AzureKeyVaultService.EKM.dll';  
    GO   
    ```  
  
2.  Setup a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] credential for a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] administrator login to use the key vault in order to setup and manage [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] encryption scenarios. A credential must be created and added to any login that will be performing  encryption using a key from the Key Vault.  
  
    > [!IMPORTANT]  
    >  The **IDENTITY** argument of **CREATE CREDENTIAL** requires the key vault name. The **SECRET** argument of **CREATE CREDENTIAL** requires the *<Client ID\>* (without hyphens) and *<Secret\>* to be passed together without a space between them.  
  
     In the following example, the **Client ID** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) is stripped of the hyphens and entered as the string `EF5C8E094D2A4A769998D93440D8115D` and the corresponding **Secret/Authentication Key** is represented by the string *PUT_SECRET_HERE*. The final string will be a long sequence of letters and numbers.  
  
    ```  
    USE master;  
    CREATE CREDENTIAL sysadmin_ekm_cred   
        WITH IDENTITY = 'ContosoKeyVault',   
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DPUT_SECRET_HERE'   
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;  
  
    -- Add the credential to the SQL Server administrator's domain login   
    ALTER LOGIN [<domain>\<login>]  
    ADD CREDENTIAL sysadmin_ekm_cred;  
    ```  
  
     For an example of using variables for the **CREATE CREDENTIAL** arguments and programmatically removing the hyphens from the Client ID, see [CREATE CREDENTIAL (Transact-SQL)](assetId:///d5e9ae69-41d9-4e46-b13d-404b88a32d9d).  
  
3.  If you imported an asymmetric key as described earlier in Step 1, section 5, open the key by providing your key name in the following example.  
  
    ```  
    CREATE ASYMMETRIC KEY CONTOSO_KEY   
    FROM PROVIDER [AzureKeyVault_EKM_Prov]  
    WITH PROVIDER_KEY_NAME = 'ContosoMasterKey',  
    CREATION_DISPOSITION = OPEN_EXISTING;  
    ```  
  
    > [!TIP]  
    >  Users receiving the error **Cannot export public key from the provider. Provider error code: 2053.** should check their **get**, **list**, **wrapKey**, and **unwrapKey** permissions in the key vault.  
  
     Though not recommended for production (because the key cannot be exported), it is possible to create an asymmetric key directly in the vault from [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. If you did not import a key earlier, then create an asymmetric key in the key vault for testing by using the following script. Execute the script, using a login provisioned with the **sysadmin_ekm_cred** credential.  
  
    ```  
    CREATE ASYMMETRIC KEY CONTOSO_KEY   
    FROM PROVIDER [AzureKeyVault_EKM_Prov]  
    WITH ALGORITHM = RSA_2048,  
    PROVIDER_KEY_NAME = 'ContosoMasterKey';  
    ```  
  
    > [!TIP]  
    >  Creating a key in the Key Vault requires **create** permissions in the key vault.  
  
 For more information, see the following:  
  
-   [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)  
  
-   [CREATE CRYPTOGRAPHIC PROVIDER (Transact-SQL)](assetId:///059a39a6-9d32-4d3f-965b-0a1ce75229c7)  
  
-   [CREATE CREDENTIAL (Transact-SQL)](assetId:///d5e9ae69-41d9-4e46-b13d-404b88a32d9d)  
  
-   [CREATE ASYMMETRIC KEY (Transact-SQL)](assetId:///141bc976-7631-49f6-82bd-a235028645b1)  
  
-   [CREATE LOGIN (Transact-SQL)](assetId:///eb737149-7c92-4552-946b-91085d8b1b01)  
  
-   [ALTER LOGIN (Transact-SQL)](assetId:///e247b84e-c99e-4af8-8b50-57586e1cb1c5)  
  
##  <a name="UsesOfEKM"></a> Using EKM with SQL Server Encryption Features  
  
###  <a name="ExampleA"></a> Transparent Data Encryption by Using an Asymmetric Key from the Key Vault  
 After completing the steps above, create a credential and a login, create a database encryption key protected by the asymmetric key in the key vault. Use the database encryption key to encrypt a database with TDE.  
  
 To encrypt a database requires CONTROL permission on the database.  
  
1.  Create a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] credential for the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] to use when accessing the key vault EKM during database load.  
  
    > [!IMPORTANT]  
    >  The **IDENTITY** argument of **CREATE CREDENTIAL** requires the key vault name. The **SECRET** argument of **CREATE CREDENTIAL** requires the *<Client ID\>* (without hyphens) and *<Secret\>* to be passed together without a space between them.  
  
     In the following example, the **Client ID** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) is stripped of the hyphens and entered as the string `EF5C8E094D2A4A769998D93440D8115D` and the **Secret** is represented by the string *SECRET_DBEngine*. The same Azure Active Directory Client ID and Secret from the main section may be used here, but a new Credential (shown as "Azure_EKM_TDE_cred" below) must be created.  
  
    ```  
    USE master;  
    CREATE CREDENTIAL Azure_EKM_TDE_cred   
        WITH IDENTITY = 'ContosoKeyVault',   
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_DBEngine'   
        FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;  
    ```  
  
2.  Create a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login to be used by the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] for TDE, and add the credential to it. This example uses the CONTOSO_KEY asymmetric key stored in the key vault, which was imported or created earlier for the master database, as described in [Step 3, section 3](#Step3) above.  
  
    ```  
    USE master;  
    -- Create a SQL Server login associated with the asymmetric key   
    -- for the Database engine to use when it loads a database   
    -- encrypted by TDE.  
    CREATE LOGIN TDE_Login   
    FROM ASYMMETRIC KEY CONTOSO_KEY;  
    GO   
  
    -- Alter the TDE Login to add the credential for use by the   
    -- Database Engine to access the key vault  
    ALTER LOGIN TDE_Login   
    ADD CREDENTIAL Azure_EKM_TDE_cred ;  
    GO  
    ```  
  
3.  Create the database encryption key (DEK) that will be used for TDE. The DEK can be created using any SQL Server supported algorithm or key length. The DEK will be protected by the asymmetric key in the key vault.  
  
     This example uses the CONTOSO_KEY asymmetric key stored in the key vault, which was imported or created earlier, as described in [Step 3, section 3](#Step3) above.  
  
    ```  
    USE ContosoDatabase;  
    GO  
  
    CREATE DATABASE ENCRYPTION KEY   
    WITH ALGORITHM = AES_128   
    ENCRYPTION BY SERVER ASYMMETRIC KEY CONTOSO_KEY;  
    GO  
  
    -- Alter the database to enable transparent data encryption.  
    ALTER DATABASE ContosoDatabase   
    SET ENCRYPTION ON ;  
    GO  
    ```  
  
     For more information, see the following:  
  
    -   [CREATE DATABASE ENCRYPTION KEY (Transact-SQL)](assetId:///2ee95a32-5140-41bd-9ab3-a947b9990688)  
  
    -   [ALTER DATABASE (Transact-SQL)](assetId:///15f8affd-8f39-4021-b092-0379fc6983da)  
  
###  <a name="ExampleB"></a> Encrypting Backups by Using an Asymmetric Key from the Key Vault  
 Encrypted backups are supported starting with [!INCLUDE[ssSQL14](../../Topics/TopicNameContainA/tokens/ssSQL14_md.md)]. The following example creates and restores a backup encrypted a data encryption key protected by the asymmetric key in the key vault.  
  
1.  Create a SQL Server credential for the Database Engine to use when accessing the key vault EKM during database load.  
  
    > [!IMPORTANT]  
    >  The **IDENTITY** argument of **CREATE CREDENTIAL** requires the key vault name. The **SECRET** argument of **CREATE CREDENTIAL** requires the `<Client ID>` (without hyphens) and `<Secret>` to be passed together without a space between them.  
  
2.  In the following example, the Client ID (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) is stripped of the hyphens and entered as the string `EF5C8E094D2A4A769998D93440D8115D` and the Secret is represented by the string `SECRET_DBEngine`. The same Azure Active Directory Client ID and Secret from the main section may be used here, but a new Credential (shown as "`Azure_EKM_Backup_cred`" below) must be created.  
  
    ```  
    USE master;  
    CREATE CREDENTIAL Azure_EKM_Backup_cred   
        WITH IDENTITY = 'ContosoKeyVault',   
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_DBEngine'   
        FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;  
    ```  
  
3.  Create a SQL Server login to be used by the Database Engine for encrypting backups, and add the credential to it. You cannot use an asymmetric key for backup encryption if you’ve already used that key for TDE (above example) or column level Encryption (below example). This example uses the `CONTOSO_KEY_BACKUP` asymmetric key stored in the key vault, which can be imported or created earlier for the master database, as described in Step 3, section 3 above.  
  
    ```  
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
  
4.  Now backup the database specifying encryption with the symmetric key stored in the key vault.  
  
    ```  
    USE master;  
    BACKUP DATABASE [DATABASE_TO_BACKUP]  
    TO DISK = N'[PATH TO BACKUP FILE]'   
    WITH FORMAT, INIT, SKIP, NOREWIND, NOUNLOAD,   
    ENCRYPTION(ALGORITHM = AES_256, SERVER ASYMMETRIC KEY = [CONTOSO_KEY]);  
    GO  
    ```  
  
     Sample restore code.  
  
    ```  
    RESTORE DATABASE [DATABASE_TO_BACKUP]  
    FROM DISK = N'[PATH TO BACKUP FILE]' WITH FILE = 1, NOUNLOAD, REPLACE;  
    GO  
    ```  
  
     For more information about backup options, see [BACKUP (Transact-SQL)](assetId:///89a4658a-62f1-4289-8982-f072229720a1).  
  
###  <a name="ExampleC"></a> Column Level Encryption by Using an Asymmetric Key from the Key Vault  
 The following example creates a symmetric key protected by the asymmetric key in the key vault. Then the symmetric key is used to encrypt data in the database.  
  
 This example uses the `CONTOSO_KEY_COLUMNS` asymmetric key stored in the key vault, which can be imported or created earlier, as described in [Step 3, section 3](#Step3) above. To use this asymmetric key in the `ContosoDatabase` database, you must execute the CREATE ASYMMETRIC KEY statement again, to provide the `ContosoDatabase` database with a reference to the key.  
  
```  
USE [ContosoDatabase];  
GO  
  
-- Create a reference to the key in the key vault  
CREATE ASYMMETRIC KEY CONTOSO_KEY_COLUMNS   
FROM PROVIDER [AzureKeyVault_EKM_Prov]  
WITH PROVIDER_KEY_NAME = 'ContosoMasterKey',  
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
SELECT @DATA = ENCRYPTBYKEY(KEY_GUID('DATA_ENCRYPTION_KEY'), CONVERT(VARBINARY,'Plain text data to encrypt'));  
  
-- Decrypt syntax  
SELECT CONVERT(VARCHAR, DECRYPTBYKEY(@DATA));  
  
--Close the symmetric key  
CLOSE SYMMETRIC KEY DATA_ENCRYPTION_KEY;  
```  
  
##  <a name="Appendix"></a> Appendix  
  
###  <a name="AppendixA"></a> A. Error Code Explanations for SQL Server Connector  
 **Provider Error Codes:**  
  
|Provider Error Code|Explanation|  
|-------------------------|-----------------|  
|2050|Run time failure due to unhandled exception.|  
|2053|Web request failed. A generic vault error to represent unexpected failures.|  
|2055|Error creating key in the vault because it already exists.|  
  
###  <a name="AppendixB"></a> B. Configuration Settings for SQL Server Connector  
 **Configuration AppConfig Settings:**  
  
 The **appSettings** are in the **Microsoft.ManagedEKM.Service.exe** configuration file in the directory where the SQL Server Connector for Microsoft Azure Key Vault program files are installed on your computer.  
  
|Setting|Details|Values|  
|-------------|-------------|------------|  
|LogLevel|The Azure Key Vault SQL Connector windows service writes to the Application event log.  The service can be configured to write events at the various levels which controls the type of events logged and in term determines the verbosity of logging.|Verbose, Trace, Error, Critical<br /><br /> Default is Error|  
|Use SoftKeys|Controls whether the SQL Server Connector creates a software controlled key or a HSM controlled key when a new asymmetric key is created in the Key Vault EKM using  `CREATE ASYMMETRIC KEY`.|true, false<br /><br /> Default is true|  
|Disable Cache|The SQL Server Connector caches decrypted Data Encryption Keys it gets back from the Key vault.  This helps minimize latencies in fetching a key for the column level encryption scenario.   The Disable Cache setting lets you disable any caching of results.|true, false<br /><br /> Default is false<br /><br /> If the value is set to true, the Cache Duration setting has no effect.|  
|Cache Duration|The duration for which the SQL Server Connector caches the decrypted data encryption keys from the vault.|.NET timespan:<br /><br /> 1:00:00 represents a one hour expiration<br /><br /> 30:00 represents 30 minutes<br /><br /> Default is 30 minutes|  
  
###  <a name="AppendixC"></a> C. Maintenance Instructions for SQL Server Connector  
 **Key Rollover:**  
  
 Typically  server asymmetric keys for SQL Server Encryption  need to be versioned every 1-2 years. It's important to note that although the Key Vault allows keys to be versioned, customers should not use that feature to implement versioning. The SQL Server Connector cannot deal with changes in Key Vault key version. To implement key versioning, the customer need to create a new key in the Key Vault and then re-encrypt the data encryption key in [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)].  
  
 For TDE, this is how this would be achieved:  
  
-   Create a new asymmetric key in the Key Vault using PowerShell.  
  
-   Import the new asymmetric key into [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)] (as shown in Step 3, section 3).  
  
-   Create a new login to be associated with the new asymmetric key (as shown under the TDE instructions).  
  
-   Create a new credential to be mapped to the login (as shown under the TDE instructions).  
  
-   Choose the database whose database encryption key you would like to re-encrypt.  
  
-   Re-encrypt the database encryption key using the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] command below:  
  
    ```  
    ALTER DATABASE ENCRYPTION KEY   
    ENCRYPTION BY SERVER ASYMMETRIC KEY NewKeyName  
    GO  
    ```  
  
 **Upgrade of SQL Server Connector:**  
  
 The following steps upgrade the SQL Server Connector that is installed on [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]:  
  
-   Re-encrypt the data encryption keys (DEKs) used with a local encryption key.  
  
-   Drop the SQL Server Connector provider.  
  
-   Uninstall the SQL Server Connector using the Windows **Programs and Features** feature.  
  
-   Download and install the latest version of the SQL Server Connector from the Microsoft Download Center.  
  
-   Re-register the SQL Server Connector provider with your [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
-   Re-encrypt the DEK with the asymmetric key in the Key Vault.  
  
 **Rolling the SQL Server Service Principal:**  
  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] uses Service Principals created in Azure AD as credentials to access the Key Vault.  Service Principal has a Client ID and Authentication Key.  A [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] credential is set up with the VaultName, Client ID and Authentication Key.  The Authentication Key is valid for a certain period of time (1 or 2 years).   Before the time period expires a new key must be generated in Azure AD for the Service Principal.  Then the credential has to be changed in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].    [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)] maintains a cache for the credential in the current session, so when a credential is changed, [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)] should be closed and  restarted.  
  
 **Key Backup and Recovery;**  
  
 The Key vault should be regularly backed up. If an asymmetric key in the vault is lost, it can be restored from backup.  The key must be restored using the same name as before.  
  
 If the vault has been lost, you will need to recreate a vault and restore the asymmetric key to the vault using the same name as before.  The vault name can be different (or the same as before).   You must also set the access permissions on the new vault to grant to the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] service principal the access that is needed for the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] encryption scenarios and then adjust the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] credential so that the new vault name is reflected.  
  
 In summary, here are the steps:  
  
-   Backup the vault key (using the `Backup-AzureKeyVaultKey Powershell` cmdlet).  
  
-   In the case of vault failure, create a new vault in the same region.  The user creating this should be in the same default directory as the service principal setup for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
-   Restore the key to the new vault (using the `Restore-AzureKeyVaultKey` Powershell cmdlet – this restores the key using the same name as before).  
  
-   Grant permissions to the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] service principal to use this new vault.  
  
-   Modify the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] credential used by the Database Engine to reflect the new vault name (if needed).  
  
## See Also  
 [CREATE CRYPTOGRAPHIC PROVIDER (Transact-SQL)](assetId:///059a39a6-9d32-4d3f-965b-0a1ce75229c7)   
 [CREATE CREDENTIAL (Transact-SQL)](assetId:///d5e9ae69-41d9-4e46-b13d-404b88a32d9d)   
 [CREATE ASYMMETRIC KEY (Transact-SQL)](assetId:///141bc976-7631-49f6-82bd-a235028645b1)   
 [CREATE SYMMETRIC KEY (Transact-SQL)](assetId:///b5d23572-b79d-4cf1-9eef-d648fa3b1358)   
 [Extensible Key Management (EKM)](../../Topics/TopicNameNotContainA/Extensible-Key-Management--EKM-.md)   
 [Enable TDE on SQL Server Using EKM](../../Topics/TopicNameNotContainA/Enable-TDE-on-SQL-Server-Using-EKM.md)   
 [Backup Encryption](../../Topics/TopicNameNotContainA/Backup-Encryption.md)   
 [Create an Encrypted Backup](../../Topics/TopicNameNotContainA/Create-an-Encrypted-Backup.md)