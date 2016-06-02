---
title: Setup Steps for Extensible Key Management Using the Azure Key Vault
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c1f29c27-5168-48cb-b649-7029e4816906
---
# Setup Steps for Extensible Key Management Using the Azure Key Vault
  The following steps walkthrough the installation and configuration of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]Connector for Azure Key Vault.  
  
## Before You Start  
 To use Azure Key Vault with your SQL Server, there are a few prerequisites:  
  
-   You must have an Azure subscription  
  
-   Install the latest [Azure PowerShell](https://azure.microsoft.com/en-us/documentation/articles/powershell-install-configure/) \(1.0.1 or higher\).  
  
-   Create an Azure Active Directory  
  
-   Familiarize yourself with the principals of EKM storage using the Azure Key Vault by reviewing [Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;](../Topic/Extensible%20Key%20Management%20Using%20Azure%20Key%20Vault%20\(SQL%20Server\).md).  
  
## Part I: Set up an Azure Active Directory service principal  
 In order to grant SQL Server access permissions to your Azure Key Vault, you will need a Service Principal account in Azure Active Directory \(AAD\).  
  
1.  Go to the [Azure classic portal](https://manage.windowsazure.com), and sign in.  
  
2.  Register an application with Azure Active Directory. For detailed step\-by\-step instructions to register an application, see the **Get an identity for the application** section  of the [Azure Key Vault blog post](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/).  
  
3.  Copy the **Client ID** and **Client Secret** for a later step, where they will be used to grant [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] access to your key vault.  
  
 ![ekm-client-id](../../Images\Image\ImageNotContaina/ekm-client-id.png "ekm-client-id")  
  
 ![ekm-key-id](../../Images\Image\ImageNotContaina/ekm-key-id.png "ekm-key-id")  
  
## Part II: Create a Key Vault and Key  
 The key vault and key created here will be used by the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] for encryption key protection.  
  
> [!IMPORTANT]  
>  The subscription where the key vault is created must be in the same default Azure Active Directory where the Azure Active Directory service principal was created.  
  
1.  **Open PowerShell and Sign in**  
  
     Install and start the [latest Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/) \(1.0.1 or higher\). Sign in to your Azure account with the following command:  
  
    ```powershell  
    Login-AzureRmAccount  
    ```  
  
     The statement returns:  
  
    ```  
    Environment           : AzureCloud  
    Account               : <account_name>  
    TenantId              : <tenant_id>  
    SubscriptionId        : <subscription_id>  
    CurrentStorageAccount :  
    ```  
  
    > [!NOTE]  
    >  If you have multiple subscriptions and want to specify a specific one to use for the vault, then use `Get-AzureRmSubscription` to see the subscriptions and `Select-AzureRmSubscription` to choose the correct subscription. Otherwise, PowerShell will select one for you by default.  
  
2.  **Create a new resource group**  
  
     All Azure resources created via Azure Resource Manager must be contained in resource groups. Create a resource group to house your key vault. This example uses `ContosoDevRG`. Choose your own **unique** resource group and key vault name as all key vault names are globally unique.  
  
    ```powershell  
    New-AzureRmResourceGroup -Name ContosoDevRG -Location 'East Asia'  
    ```  
  
     The statement returns:  
  
    ```  
    ResourceGroupName: ContosoDevRB  
    Location         : eastasia  
    ProvisioningState: Succeeded  
    Tags             :   
    ResourceId       : /subscriptions/<subscription_id>/  
                        resourceGroups/ContosoDevRG  
    ```  
  
    > [!NOTE]  
    >  For the `-Location parameter`, use the command `Get-AzureLocation` to identify how to specify an alternative location to the one in this example. If you need more information, type: `Get-Help Get-AzureLocation`  
  
3.  **Create a Key Vault**  
  
     The `New-AzureRmKeyVault` cmdlet requires a resource group name, a key vault name, and a geographic location. For example, for a key vault named `ContosoDevKeyVault`, type:  
  
    ```powershell  
    New-AzureRmKeyVault -VaultName 'ContosoDevKeyVault' `  
       -ResourceGroupName 'ContosoDevRG' -Location 'East Asia'  
    ```  
  
     Record the name of your key vault.  
  
     The statement returns:  
  
    ```  
    Vault Name                       : ContosoDevKeyVault  
    Resource Group Name              : ContosoDevRG  
    Location                         : East Asia  
    ResourceId                       : /subscriptions/<subscription_id>/  
                                        resourceGroups/ContosoDevRG/providers/  
                                        Microsoft/KeyVault/vaults/ContosoDevKeyVault  
    Vault URI: https://ContosoDevKeyVault.vault.azure.net  
    Tenant ID                        : <tenant_id>  
    SKU                              : Standard  
    Enabled For Deployment?          : False  
    Enabled For Template Deployment? : False  
    Enabled For Disk Encryption?     : False  
    Access Policies                  :  
             Tenant ID              : <tenant_id>  
             Object ID              : <object_id>  
             Application ID         :   
             Display Name           : <display_name>  
             Permissions to Keys    : get, create, delete, list, update, import,   
                                      backup, restore  
             Permissions to Secrets : all  
    Tags                             :  
    ```  
  
4.  **Grant Permission for the Azure Active Directory Service Principal to Access the Key Vault**  
  
     You can authorize other users and applications to use your key vault.   
    In this case, let’s use the Azure Active Directory service principal created in Part I to authorize the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance.  
  
    > [!IMPORTANT]  
    >  The Azure Active Directory service principal must have at least the `get`, `list`, `wrapKey`, and `unwrapKey` permissions for the key vault.  
  
     As shown below, use the **Client ID** from Part I for the `ServicePrincipalName` parameter. The `Set-AzureKeyVaultAccessPolicy` runs silently with no output if it runs successfully.  
  
    ```powershell  
    Set-AzureRmKeyVaultAccessPolicy -VaultName 'ContosoDevKeyVault'`  
      -ServicePrincipalName EF5C8E09-4D2A-4A76-9998-D93440D8115D `  
      -PermissionsToKeys get, list, wrapKey, unwrapKey  
    ```  
  
     Call the `Get-AzureRmKeyVault` cmdlet to confirm the permissions. In the statement output under ‘Access Policies,’ you should see your AAD application name listed as another tenant that has access to this key vault.  
  
       
5.  **Generate an Asymmetric Key in the Key Vault**  
  
     There are two ways to generate a key in Azure Key Vault: Import an existing key or create a new key.  
  
    ###### Create a New Key  
  
    -   There are two types of keys you can generate in Azure Key Vault. Both are asymmetric 2048\-bit RSA keys.  
  
        -   **Software\-protected:** Processed in software and encrypted at rest. Operations on software\-protected keys occur on Azure Virtual Machines. Recommended for keys not used in a production deployment.  
  
        -   **HSM\-protected:** Created and protected by a hardware security module \(HSM\) for additional security. Costs  about $1 per key version.  
  
        > [!IMPORTANT]  
        >  The SQL Server Connector requires the key name to only use the characters “a\-z”, “A\-Z”, “0\-9”, and “\-“, with a 26\-character limit.   
        > Different key versions under the same key name in Azure Key Vault will not work with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Connector. To rotate an Azure Key Vault key that’s being used by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], please refer to the Key Rollover steps in the [SQL Server Connector, Appendix](../../Topics\TopicNameNotContainA/SQL-Server-Connector,-Appendix.md).  
  
         In this example, let’s create a software\-protected key using the `Add-AzureRmKeyVaultKey cmdlet`:  
  
        ```powershell  
        Add-AzureRmKeyVaultKey -VaultName 'ContosoDevKeyVault' `  
          -Name 'ContosoRSAKey0' -Destination 'Software'  
        ```  
  
         The statement returns:  
  
        ```  
        Attributes : Microsoft.Azure.Commands.KeyVault.Models.KeyAttributes  
        Key        :  {"kid":"https:contosodevKeyVault.azure.net/keys/  
                       ContosoRSAKey0/<guid>","dty":"RSA:,"key_ops": ...  
        VaultName  : contosodevkeyvault  
        Name       : contosoRSAKey0  
        Version    : <guid>  
        Id         : https://contosodevkeyvault.vault.azure.net:443/  
                     keys/ContosoRSAKey0/<guid>  
        ```  
        > [!IMPORTANT]  
        >  The key vault supports multiple versions of the same named key, but keys to be used by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Connector should not be versioned or rolled. If the administrator wants to roll the key used for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] encryption, a new key with a different name should be created in the vault and used to encrypt the DEK.  
  
    ###### Import an Existing Key File  
  
    -   Alternately, if you have an existing 2048\-bit RSA software\-protected key, you can upload the key to Azure Key Vault. For example, if you had a .PFX file saved to your **C:\\** drive in a file named **softkey.pfx** that you want to upload to Azure Key Vault, type the following to set the variable `securepfxpwd` for a password of `12987553` for the .PFX file:  
  
        ```powershell  
        $securepfxpwd = ConvertTo-SecureString –String '12987553' `  
          –AsPlainText –Force  
        ```  
  
         Then type the following to import the key from the .PFX file, which protects the key by software in the Key Vault service:  
  
        ```powershell  
        Add-AzureKeyVaultKey -VaultName 'ContosoKeyVault' `  
          -Name 'ContosoFirstKey' -KeyFilePath 'c:\softkey.pfx' `  
          -KeyFilePassword $securepfxpwd  
        ```  
  
        > [!IMPORTANT]  
        >  Importing the asymmetric key is highly recommended for production scenarios because it allows the administrator to escrow the key in a key escrow system. If the asymmetric key is created in the vault, it cannot be escrowed because the private key can never leave the vault. Keys used to protect critical data should be escrowed. The loss of an asymmetric key will result in permanently unrecoverable data.  
  
  
## Part III: Install the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Connector  
 Download the SQL Server Connector from the [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=521700). \(This should be done by the administrator of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] computer.\)  
  
 ![ekm-connector-install](../../Images\Image\ImageNotContaina/ekm-connector-install.png "ekm-connector-install")  
  
 By default, the connector installs at C:\\Program Files\\SQL Server Connector for Microsoft Azure Key Vault. This location can be changed during setup. \(If changed, adjust the scripts below.\)  
  
 There is no interface for the Connector, but if it is installed successfully, the **Microsoft.AzureKeyVaultService.EKM.dll** is installed on the machine. This is the cryptographic EKM provider DLL that needs to be registered with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] by using the `CREATE CRYPTOGRAPHIC PROVIDER` statement.  
  
 The SQL Server Connector installation also allows you to optionally download sample scripts for SQL Server encryption.  
  
 To view error code explanations, configuration settings, or maintenance tasks for SQL Server Connector, visit the appendix at the bottom of this topic:  
  
-   [A. Maintenance Instructions for SQL Server Connector](../../Topics\TopicNameNotContainA/SQL-Server-Connector,-Appendix.md)  
  
-   [C. Error Code Explanations for SQL Server Connector](../../Topics\TopicNameNotContainA/SQL-Server-Connector,-Appendix.md)  
  
  
## Part IV: Configure [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]  
 Please refer to [B. Frequently Asked Questions](../../Topics\TopicNameNotContainA/SQL-Server-Connector,-Appendix.md) to see a note about the minimum permission levels needed for each action in this section.  
  
1.  **Launch sqlcmd.exe or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Management Studio**  
  
2.  **Configure [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to use EKM**  
  
     Execute the following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] script to configure the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] to use an EKM provider.  
  
    ```tsql  
    -- Enable advanced options.  
    USE master;  
    GO  
  
    sp_configure 'show advanced options', 1;  
    GO  
    RECONFIGURE;  
    GO  
  
    -- Enable EKM provider  
    sp_configure 'EKM provider enabled', 1;  
    GO  
    RECONFIGURE;  
    ```  
  
3.  **Register \(create\) the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Connector as an EKM provider with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]**  
  
     \-\- Create a cryptographic provider, using the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Connector which is an EKM provider for the Azure Key Vault.    
    This example uses the name `AzureKeyVault_EKM_Prov`.  
  
    ```tsql  
    CREATE CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov   
    FROM FILE = 'C:\Program Files\SQL Server Connector for Microsoft   
    Azure Key Vault\Microsoft.AzureKeyVaultService.EKM.dll';  
    GO  
    ```  
  
    > [!NOTE]  
    >  The file path length can not exceed 256 charactrers.  
  
  
4.  **Setup a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] credential for a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login to use the key vault**  
  
     A credential must be added to each login that will be performing encryption using a key from the Key Vault. This might include:  
  
    -   A [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] administrator login who will use key vault in order to setup and manage [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] encryption scenarios.  
  
    -   Other [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] logins who might enable Transparent Data Encryption \(TDE\), or other [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] encryption features.  
  
     There is one\-to\-one mapping between credentials and logins. That is, each login must have a unique credential.  
  
     Modify the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] script below in the following ways:  
  
    -   Replace the `IDENTITY` argument \(`ContosoDevKeyVault`\) with the name of your Azure Key Vault from Part II.  
  
    -   Replace the first part of the `SECRET` argument with the Azure Active Directory **Client ID** from Part I. In this example, the **Client ID** is `EF5C8E094D2A4A769998D93440D8115D`.  
  
        > [!IMPORTANT]  
        >  You must remove the hyphens from the **Client ID**.  
  
    -   Complete the second part of the `SECRET` argument with **Secret** from Part I.  In this example the **Secret** from Part 1 is `AADsecret123456789=`. The final string for the `SECRET` argument will be a long sequence of letters and numbers.  
  
    ```tsql  
    USE master;  
    CREATE CREDENTIAL sysadmin_ekm_cred   
        WITH IDENTITY = 'ContosoDevKeyVault',   
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DAADsecret123456789=’   
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov;  
  
    -- Add the credential to the SQL Server administrator's domain login   
    ALTER LOGIN [<domain>\<login>]  
    ADD CREDENTIAL sysadmin_ekm_cred;  
    ```  
  
     For an example of using variables for the **CREATE CREDENTIAL** arguments and programmatically removing the hyphens from the Client ID, see [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../Topic/CREATE%20CREDENTIAL%20\(Transact-SQL\).md).  
  
5.  **Open your Azure Key Vault key in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]**  
  
     If you imported an asymmetric key as described in Part II, open the key by providing your key name in the following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] script.  
  
    -   Replace `CONTOSO_KEY` with the name you’d like the key to have in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
    -   Replace `ContosoRSAKey0` with the name of your key in Azure Key Vault.  
  
    ```tsql  
    CREATE ASYMMETRIC KEY CONTOSO_KEY   
    FROM PROVIDER [AzureKeyVault_EKM_Prov]  
    WITH PROVIDER_KEY_NAME = 'ContosoRSAKey0',  
    CREATION_DISPOSITION = OPEN_EXISTING;  
    ```  
## Next Step  
  
Now that you have completed the basic configuration, see how to [Use SQL Server Connector with SQL Encryption Features](../../Topics\TopicNameNotContainA/Use-SQL-Server-Connector-with-SQL-Encryption-Features.md)   
  
## See Also  
 [Extensible Key Management Using Azure Key Vault](Extensible%20Key%20Management%20Using%20Azure%20Key%20Vault%20\(SQL%20Server\).md)   
[SQL Server Connector, Appendix](../../Topics\TopicNameNotContainA/SQL-Server-Connector,-Appendix.md)  
  
  