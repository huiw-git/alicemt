---
title: Creating Column Master Keys (Always Encrypted)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 856e8061-c604-4ce4-b89f-a11876dd6c88
---
# Creating Column Master Keys (Always Encrypted)
[*Column master keys*](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_3) are the physical key-protecting keys used to encrypt the *column encryption keys* that protect the data in your database.  
  
Column master keys must be stored in a trusted key store, so the first step in encrypting your data with Always Encrypted is to decide where to store your encryption keys.  
  
## Select a key store to store your column master key  
    
There are several supported key stores:    
    
- Windows Certificate Store    
- Azure Key Vault   
- Hardware security module (HSM)    
- Custom implementation    
    
The physical column master key is the specific cryptographic key supported in the selected key store. In other words, if you use the Windows Certificate Store for your column master key, then your column master key is a Windows Certificate; if you use the Azure Key Vault, your column master key is an Azure Key vault key, etc...  
  
Because each column master key implementation is dependent on the selected key store, the process and tools to create each key is different.  
    
It's important to note that all client applications needing to access your database's encrypted data, must have permission to access the keys, so ensure you set the correct permissions on your key store to allow client applications to access the keys in the store.   
    
    
## Create a column master key in the Windows Certificate Store    
  
When using the Windows Certificate Store for your Always Encrypted keys your CMK will be a Windows certificate. There are several ways to create Windows Certificates but this example uses PowerShell.  
  
### Permissions   
Just need a copy of the certficate?  
??  
  
### Create the key  
The following code snippet creates a Windows Certificate:   
  
```[PowerShell]    
# Generate a certificate to be used as a column master key for Always Encrypted    
$storeLocation = "CurrentUser"    
$certPath = "Cert:\" + $storeLocation + "\My"    
$cert1 = New-SelfSignedCertificate `  
    -Subject "AlwaysEncryptedTest" `  
    -DnsName $UniqueName `  
    -CertStoreLocation $certPath `  
    -KeyExportPolicy Exportable `  
    -Type DocumentEncryptionCert `  
    -KeyUsage DataEncipherment `  
    -KeySpec KeyExchange    
```    
  
## Create a column master key in the Azure Key Vault    
    
When using Azure Key Vault for your Always Encrypted keys your CMK will be an Azure Key Vault key.  
    
  
### Permissions   
For Always Encrypted, the Azure Key Vault needs to have *create, get, wrapKey, unwrapKey, sign, and verify* permissions. Optional info - there are some tasks in SSMS that also require the *list* permission.  
  
### Create the key  
    
Replace the bracketed placeholders with your values. To get a *Client ID* follow the steps to [Register a web app (or web api) and get the client id and key](https://azure.microsoft.com/documentation/articles/sql-database-client-id-keys/#register-a-web-app-or-web-api-and-get-the-client-id-and-key).    
        
    
```[Azure-PowerShell]    
$resourceGroupName = '<your resource group name>'    
$userPrincipalName = '<your alfki@northwindtraders.com'    
$clientId = '<your Client ID>'    
$location = '<data center region>'    
$vaultName = '<Your key vault name>'    
        
# Create a new Azure resource group    
New-AzureRmResourceGroup –Name $resourceGroupName –Location $location    
    
# Create a new Azure Key Vault    
New-AzureRmKeyVault -VaultName $vaultName `  
    -ResourceGroupName $resourceGroupName `  
    -Location $location    
        
# Set the vault's access policy    
Set-AzureRmKeyVaultAccessPolicy -VaultName $vaultName `  
    -ResourceGroupName $resourceGroupName `  
    -PermissionsToKeys create,get,wrapKey,unwrapKey,sign,verify,list `  
    -UserPrincipalName $userPrincipalName    
Set-AzureRmKeyVaultAccessPolicy  -VaultName $vaultName  `  
    -ResourceGroupName $resourceGroupName `  
    -ServicePrincipalName $clientId `  
    -PermissionsToKeys get,wrapKey,unwrapKey,sign,verify,list    
    
Get-AzureRmKeyVault -VaultName $vaultName        
        
# Create our Always Encrypted column master key    
$key = Add-AzureKeyVaultKey -VaultName $vaultName -Name 'CMK1' -Destination 'Software'    
$Key.key.kid    
```    
    
## Create a column master key in a Hardware Security Module   
    
  
### Permissions   
- X  
- X   
  
### Create the key  
1. X  
2. X  
  
## Create a column master key in a custom key store   
    
  
### Permissions   
- X  
- X   
  
### Create the key  
1. X  
2. X  
  
  
## Next Steps  
  
- Configure Always Encrypted using PowerShell  
  
  
## Additional Resources  
- Always Encrypted Blog  
- Links  
  
    
