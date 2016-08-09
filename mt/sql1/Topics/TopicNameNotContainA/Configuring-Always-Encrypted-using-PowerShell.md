---
title: "Configuring Always Encrypted using PowerShell"
ms.custom: na
ms.date: 06/29/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3bdf8629-738c-489f-959b-2f5afdaf7d61
caps.latest.revision: 12
manager: jhubbard
---
# Configuring Always Encrypted using PowerShell
    
PowerShell cmdlets for configuring Always Encrypted are now available and located in the [SQL Server PowerShell (SQLPS) module](https://msdn.microsoft.com/library/hh245198.aspx).    
    
This article provides the steps to configure encryption in organizations where the security administrator and database administrator (DBA) are different people.   
  
When security and database administration roles are separated, it is important to understand the responsibilities of each role in relation to configuring encryption for Always Encrypted.    
    
- ***Security Administrator*** - The role of the security administrator is to provision and manage the physical cryptographic keys (CMK and CEK). The security administrator has no access to the database.    
- ***Database administrator (DBA)*** - The role of the DBA is to add and manage the encryption metadata in the database. The DBA has no access to the key store or keys in the store (the DBA cannot see plaintext keys).    
    
    
## Part 1: Security Administrator - Provision keys for the DBA  
    
The security administrator provisions and manages the physical cryptographic keys (CMK and CEK) in the key store. The security administrator has no access to the database.    
    
## Create a Column Master Key (CMK)    
  
A column master key is a key-protecting key used to encrypt the column encryption key.    
  
Because each column master key implementation is dependent on the selected key store, the process and tools to create each key is different. Follow the steps to create a cmk in [Creating Column Master Keys](../../Topics/TopicNameNotContainA/Creating-Column-Master-Keys--Always-Encrypted-.md), and then return to this article and follow the steps below for your specific type of key store.  
    
    
## Provision Keys in the Azure Key Vault    
    
  
  
    
### Create the column encryption key and encrypt it with the CMK    
    
Now that we have our key in the Azure Key Vault lets create our column encryption key (CEK) and encrypt it with the key in the vault.     
    
For CMKs stored in Azure Key Vault we must login to Azure to access the vault and create the encrypted CEK, but we need to use the SQL Server PowerShell module (not Azure PowerShell) so first we need to import the module and then call the **Add-SqlAzureAuthenticationContext** cmdlet to login.     
    
    
```[SQL-PowerShell]    
# import the SQL PowerShell module    
Import-Module -Name 'SQLPS'    
    
# Sign in to Azure    
Add-SqlAzureAuthenticationContext -Interactive    
    
# Create a variable to hold a pointer to our key vault    
$keyVaultKeyUrl = 'https://aekeyvault051510.vault.azure.net/keys/CMK1/4226f00a0c4643728e473a9f3147ee5e'    
       
# Create the CMK settings object that encapsulates the type of key store provider (Azure Key Vault) and URL to the key in the key store    
$cmkSettings = New-SqlAzureKeyVaultColumnMasterKeySettings -KeyUrl $keyVaultUrl    
        
# Create a new CEK and encrypt it with our CMK    
$encryptedCEK = New-SqlColumnEncryptionKeyEncryptedValue $cmkSettings    
```    
    
    
Provide the location of the CMK, and the encrypted CEK to your DBA (the **$keyVaultKeyUrl** and **$cmkSettings** values from the previous step).     
    
  
## Provision Keys in the Windows Certificate Store  
  
  
  
```[PowerShell]    
# Generate and encrypt a column encryption key value    
Import-Module “sqlps” -DisableNameChecking     
$cmkSettings = New-SqlCertificateStoreColumnMasterKeySettings -CertificateStoreLocation "CurrentUser" -Thumbprint $cert1.Thumbprint    
$encryptedValue = New-SqlColumnEncryptionKeyEncryptedValue -TargetColumnMasterKeySettings $cmkSettings    
$encryptedValue    
    
# Output the information for a DBA    
$storeLocation > $home\storeLocation.txt    
$cert1.Thumbprint > $home\thumbprint.txt    
$encryptedValue > $home\encryptedValue.txt  
```    
  
   
## Provision Keys in a Hardware Security Module (HSM)  
  
```[PowerShell]    
# Generate and encrypt a column encryption key value    
Import-Module “sqlps” -DisableNameChecking     
$cmkSettings = New-SqlXXXColumnMasterKeySettings   
    
# Output the information for a DBA    
$storeLocation   
```    
  
  
  
## Provision Keys in a Custom Implemented Key Store  
  
```[PowerShell]    
# Generate and encrypt a column encryption key value    
Import-Module “sqlps” -DisableNameChecking     
$cmkSettings = New-SqlXXXColumnMasterKeySettings   
    
# Output the information for a DBA    
$storeLocation   
```    
    
  
-------------------------------    
    
## Part 2: DBA - Create the metadata entries in the database that represent the keys    
    
The DBA creates and manages the key metadata in the database that describe the Always Encrypted keys. The DBA creates and manages key metadata only, the DBA does not have access to the keys or key store (no access to the plaintext keys).    
    
    
Using the location of the CMK, and the encrypted CEK (the information provided by the Security Administrator), the DBA creates metadata objects in the database that describe the keys:    
    
- CMK metadata - the location and name of the cmk.    
- CEK metadata - the encrypted CEK.    
  
  
### Connecting to a SQL Server or Azure SQL Database  
  
  
```[PowerShell]    
# import the SQL PowerShell module    
Import-Module -Name 'SQLPS'    
    
#Connect to the database     
$serverName = '<server name>.database.windows.net'    
$databaseName = '<your db name>'    
$connection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection     
        
$connection.ConnectionString = 'Data Source=' + $serverName + 'srv;Initial Catalog=Clinic; Integrated Security=True'     
$connection.Connect()     
$server = New-Object Microsoft.SqlServer.Management.Smo.Server($connection)     
$database = $server.Databases[$databaseName]     
```  
  
  
  
### Creating the meta data objects in the database:    
    
    
```[PowerShell]    
# import the SQL PowerShell module    
Import-Module -Name 'SQLPS'    
    
#Connect to the database     
$serverName = '<server name>.database.windows.net'    
$databaseName = '<your db name>'    
$connection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection     
        
$connection.ConnectionString = 'Data Source=' + $serverName + 'srv;Initial Catalog=Clinic; Integrated Security=True'     
$connection.Connect()     
$server = New-Object Microsoft.SqlServer.Management.Smo.Server($connection)     
$database = $server.Databases[$databaseName]     
        
# Create the CMK (metadata) in the database  (AZURE KEY VAULT)  
    $cmkSettings = New-SqlAzureKeyVaultColumnMasterKeySettings `  
    -KeyUrl 'https://aekeyvault1234.vault.azure.net/keys/CMK1/4232f00a0c4643738e473a9f3147ae3e'  
  
**# Create the CMK (metadata) in the database  (WINDOWS CERTIFICATE STORE)**  
   $cmkSettings = New-SqlCertificateStoreColumnMasterKeySettings `  
      -CertificateStoreLocation $storeLocation `  
      -Thumbprint $thumbprint  
   New-SqlColumnMasterKey -Name "CMK1" `  
      -InputObject $database `  
      -ColumnMasterKeySettings $cmksettings  
  
   # Define a CEK object  
   New-SqlColumnEncryptionKey -Name "CEK1" `  
      -InputObject $database `  
      -ColumnMasterKey "CMK1" `  
      -EncryptedValue $encryptedValue  
  
  
  
  
# Create the CMK (metadata) in the database  (HARDWARE SECURITY MODULE)  
  
# Create the CMK (metadata) in the database  (CUSTOM IMPLEMENTED KEY STORE)  
  
# Create the CMK metadata object        
New-SqlColumnMasterKey -Name 'CMK1' -InputObject $database -ColumnMasterKeySettings $CMKSettings     
    
# Copy the CEK cipherText that you obtained from the security admin into a variable    
$encryptedCEK =      '0x016E000001630075007200720065006E00740075007300650072002F006D0079002F0064006500650063006200660034006100340031003000380034006200350033003200360066003200630062006200350030003600380065003900620061003000320030003600610037003800310066001DDA6134C3B73A90D349C8905782DD819B428162CF5B051639BA46EC69A7C8C8F81591A92C395711493B25DCBCCC57836E5B9F17A0713E840721D098F3F8E023ABCDFE2F6D8CC4339FC8F88630ED9EBADA5CA8EEAFA84164C1095B12AE161EABC1DF778C07F07D413AF1ED900F578FC00894BEE705EAC60F4A5090BBE09885D2EFE1C915F7B4C581D9CE3FDAB78ACF4829F85752E9FC985DEB8773889EE4A1945BD554724803A6F5DC0A2CD5EFE001ABED8D61E8449E4FAA9E4DD392DA8D292ECC6EB149E843E395CDE0F98D04940A28C4B05F747149B34A0BAEC04FFF3E304C84AF1FF81225E615B5F94E334378A0A888EF88F4E79F66CB377E3C21964AACB5049C08435FE84EEEF39D20A665C17E04898914A85B3DE23D56575EBC682D154F4F15C37723E04974DB370180A9A579BC84F6BC9B5E7C223E5CBEE721E57EE07EFDCC0A3257BBEBF9ADFFB00DBF7EF682EC1C4C47451438F90B4CF8DA709940F72CFDC91C6EB4E37B4ED7E2385B1FF71B28A1D2669FBEB18EA89F9D391D2FDDEA0ED362E6A591AC64EF4AE31CA8766C259ECB77D01A7F5C36B8418F91C1BEADDD4491C80F0016B66421B4B788C55127135DA2FA625FB7FD195FB40D90A6C67328602ECAF3EC4F5894BFD84A99EB4753BE0D22E0D4DE6A0ADFEDC80EB1B556749B4A8AD00E73B329C95827AB91C0256347E85E3C5FD6726D0E1FE82C925D3DF4A9'    
    
# Create the CEK metadata in the database using the received CEK ciphertext     
New-SqlColumnEncryptionKey -Name “CEK1" -InputObject $database -ColumnMasterKeyName 'CMK1' -ColumnEncryptionKeyCiphertext $encryptedCEK     
```    
    
    
## Encrypt data in your database    
    
Always Encrypted is configured (the key metadata is in the database) so the next step is to encrypt some data. To encrypt a specific column in a table, associate a column encryption key (CEK) with the column that you want to encrypt    
    
Use the **New-SqlColumnEncryptionSettings** cmdlet to associate a column encryption key (CEK) with the column in your table that you want to encrypt, then run the **Set-SqlColumnEncryption** cmdlet to encrypt the data.      
    
To encrypt data in a column set the [encryption type](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_2) to **Deterministic** or **Randomized**. To decrypt a column set it's **EncryptionType** to **Plaintext**.    
    
    
Set the desired target encryption settings for selected columns:     
    
    
```[PowerShell]    
$ces = New-Object SqlColumnEncryptionSettings[2]     
$ces = @()     
$ces += New-SqlColumnEncryptionSettings -ColumnName dbo.Patients.SSN -EncryptionType Deterministic -EncryptionKey 'CEK1'     
$ces += New-SqlColumnEncryptionSettings -ColumnName dbo.Patients.BirthDate -EncryptionType Randomized -EncryptionKey 'CEK1'    
Set-SqlColumnEncryption -ColumnEncryptionSettings $ces -InputObject $database     
```    
    
## Next Steps    
    
[Rotate your keys](https://msdn.microsoft.com/library/mt607048.aspx)    
    
## See Also    
    
[Always Encrypted](https://msdn.microsoft.com/library/mt163865.aspx)    
    
