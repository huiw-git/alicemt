---
title: Remote Blob Store (RBS) (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-blob
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 31c947cf-53e9-4ff4-939b-4c1d034ea5b1
---
# Remote Blob Store (RBS) (SQL Server)
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Remote BLOB Store \(RBS\) is an optional add\-on component that lets database administrators store binary large objects in commodity storage solutions instead of directly on the main database server.  
  
 RBS is included on the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] installation media, but is not installed by the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup program.  
  
 For more information about RBS, see [RBS Resources](#rbsresources) in this topic.  
  
## Benefits of RBS  
 RBS provides the following benefits:  
  
### Optimized database storage and performance  
 Storing BLOBs in the database can consume large amounts of file space and expensive server resources. RBS efficiently transfers the BLOBs to a dedicated storage solution of your choosing, and stores references to them in the database. This frees server storage for structured data, and frees server resources for database operations.  
  
### Efficient management of BLOBs  
 Several RBS features support the convenient management of stored BLOBs:  
  
-   BLOBS are managed with ACID \(atomic consistency isolation durable\) transactions.  
  
-   BLOBs are organized into collections.  
  
-   Garbage collection, consistency checking, and other maintenance functions are included.  
  
### Standardized API  
 RBS defines a set of APIs that provide a standardized programming model for applications to access and modify any BLOB store. Each BLOB store can specify its own provider library, which plugs into the RBS client library and specifies how BLOBs are stored and accessed.  
  
 A number of third\-party storage solution vendors have developed RBS providers that conform to these standard APIs and support BLOB storage on various storage platforms.  
  
## RBS Requirements  
 RBS requires [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Enterprise for the main database server in which the BLOB metadata is stored. However, if you use the supplied FILESTREAM provider, you can store the BLOBs themselves on [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Standard.  
  
 RBS includes a FILESTREAM provider that lets you use RBS to store BLOBs on an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. If you want use RBS to store BLOBs in a different storage solution, you have to use a third party RBS provider developed for that storage solution, or develop a custom RBS provider using the RBS API. A sample provider that stores BLOBs in the NTFS file system is available as a learning resource on [Codeplex](http://go.microsoft.com/fwlink/?LinkId=210190).  
  
## RBS Security  
 The SQL Remote Blob Storage Team Blog is a good source of information about this feature. The RBS security model is described in the post at [RBS Security Model](http://blogs.msdn.com/b/sqlrbs/archive/2010/08/05/rbs-security-model.aspx).  
  
### Custom providers  
 When you use a custom provider to store BLOBs outside of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], make sure that you protect the stored BLOBs with permissions and encryption options that are appropriate to the storage medium used by the custom provider.  
  
### Credential store symmetric key  
 If a provider requires the setup and use of a secret stored within the credential store, RBS uses a symmetric key to encrypt the  provider secrets which a client may use to gain authorization to the provider’s blob store.  
  
-   RBS 2016 uses an **AES\_128** symmetric key. [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] does not allow the creation of new **TRIPLE\_DES** keys except for backwards compatibility reasons. For more information, see [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../Topic/CREATE%20SYMMETRIC%20KEY%20\(Transact-SQL\).md).  
  
-   RBS 2014 and prior versions use a credential store which holds secrets encrypted using the **TRIPLE\_DES** symmetric key algorithm which is outdated. If you are currently using **TRIPLE\_DES**[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] recommends that you enhance your security by following the steps in this topic to rotate your key to a stronger encryption method.  
  
 You can determine the RBS credential store symmetric key properties by executing the following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement in the RBS database:   
`SELECT * FROM sys.symmetric_keys WHERE name = 'mssqlrbs_encryption_skey';` If the output from that statement shows that **TRIPLE\_DES** is still used, then you should rotate this key.  
  
### Rotating the symmetric key  
 When using RBS, you should periodically rotate the credential store symmetric key. This is a common security best practice to meet organizational security policies.  One way to rotate the RBS credential store symmetric key, is to use the [script below](#Key_rotation) in the RBS database.  You can also use this script to migrate to stronger encryption strength properties, such as algorithm or key length. Backup your database prior to key rotation.  At the script’s conclusion, it has some verification steps.  
If your security policies require different key properties \(e.g., algorithm or key length\) from the ones provided, then the script may be used as a template. Modify the key properties in two places: 1\) the creation of the temporary key 2\) the creation of the permanent key.  
  
##  <a name="rbsresources"></a> RBS Resources  
 **RBS documentation**  
 The RBS documentation is included in the Windows installer package. If you want to review the RBS documentation without installing RBS, you can view the [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] version of the documentation [online in the MSDN Library](http://go.microsoft.com/fwlink/?LinkId=210192).  
  
 **RBS white paper**  
 The white paper "[Remote BLOB Storage](http://go.microsoft.com/fwlink/?LinkId=210422)", which is available for download as a Microsoft Word document, provides detailed information about installing and configuring RBS.  
  
 **RBS samples**  
 The RBS samples available on [Codeplex](http://go.microsoft.com/fwlink/?LinkId=210190) demonstrate how to develop an RBS application, and how to develop and install a custom RBS provider.  
  
 **RBS blog**  
 The [RBS blog](http://go.microsoft.com/fwlink/?LinkId=210315) provides additional information to help you understand, deploy, and maintain RBS.  
  
##  <a name="Key_rotation"></a> Key rotation script  
 This example creates a stored procedure named `sp_rotate_rbs_symmetric_credential_key` to replace the currently used RBS credential store symmetric key  
with one of your choosing.  You may want to do this if there is a security policy requiring   
periodic key rotation or if there are specific algorithm requirements.  
 In this stored procedure, a symmetric key using **AES\_256** will replace the current one.  As a result of  
the symmetric key replacement, secrets need to be re\-encrypted with the new key.  This stored   
procedure will also re\-encrypt the secrets.  The database should be backed up prior to key rotation.  
  
```  
CREATE PROC sp_rotate_rbs_symmetric_credential_key  
AS  
BEGIN  
BEGIN TRANSACTION;  
BEGIN TRY  
CLOSE ALL SYMMETRIC KEYS;  
  
/* Prove that all secrets can be re-encrypted, by creating a   
temporary key (#mssqlrbs_encryption_skey) and create a   
temp table (#myTable) to hold the re-encrypted secrets.    
Check to see if all re-encryption worked before moving on.*/  
  
CREATE TABLE #myTable(sql_user_sid VARBINARY(85) NOT NULL,  
    blob_store_id SMALLINT NOT NULL,  
    credential_name NVARCHAR(256) COLLATE Latin1_General_BIN2 NOT NULL,  
    old_secret VARBINARY(MAX), -- holds secrets while existing symmetric key is deleted  
    credential_secret VARBINARY(MAX)); -- holds secrets with the new permanent symmetric key  
  
/* Create a new temporary symmetric key with which the credential store secrets   
can be re-encrypted. These will be used once the existing symmetric key is deleted.*/  
CREATE SYMMETRIC KEY #mssqlrbs_encryption_skey    
    WITH ALGORITHM = AES_256 ENCRYPTION BY   
    CERTIFICATE [cert_mssqlrbs_encryption];  
  
OPEN SYMMETRIC KEY #mssqlrbs_encryption_skey    
    DECRYPTION BY CERTIFICATE [cert_mssqlrbs_encryption];  
  
INSERT INTO #myTable   
    SELECT cred_store.sql_user_sid, cred_store.blob_store_id, cred_store.credential_name,   
    encryptbykey(  
        key_guid('#mssqlrbs_encryption_skey'),   
        decryptbykeyautocert(cert_id('cert_mssqlrbs_encryption'),   
            NULL, cred_store.credential_secret)  
        ),   
    NULL  
    FROM [mssqlrbs_resources].[rbs_internal_blob_store_credentials] AS cred_store;  
  
IF( EXISTS(SELECT * FROM #myTable WHERE old_secret IS NULL))  
BEGIN  
    PRINT 'Abort. Failed to read some values';  
    SELECT * FROM #myTable;  
    ROLLBACK;  
END;  
ELSE  
BEGIN  
/* Re-encryption worked, so go ahead and drop the existing RBS credential store   
 symmetric key and replace it with a new symmetric key.*/  
DROP SYMMETRIC KEY [mssqlrbs_encryption_skey];  
  
CREATE SYMMETRIC KEY [mssqlrbs_encryption_skey]   
WITH ALGORITHM = AES_256   
ENCRYPTION BY CERTIFICATE [cert_mssqlrbs_encryption];  
  
OPEN SYMMETRIC KEY [mssqlrbs_encryption_skey]   
DECRYPTION BY CERTIFICATE [cert_mssqlrbs_encryption];  
  
/*Re-encrypt using the new permanent symmetric key.    
Verify if encryption provided a result*/  
UPDATE #myTable   
SET [credential_secret] =   
    encryptbykey(key_guid('mssqlrbs_encryption_skey'), decryptbykey(old_secret))  
  
IF( EXISTS(SELECT * FROM #myTable WHERE credential_secret IS NULL))  
BEGIN  
    PRINT 'Aborted. Failed to re-encrypt some values'  
    SELECT * FROM #myTable  
    ROLLBACK  
END  
ELSE  
BEGIN  
  
/* Replace the actual RBS credential store secrets with the newly   
encrypted secrets stored in the temp table #myTable.*/                
SET NOCOUNT ON;  
DECLARE @sql_user_sid varbinary(85);  
DECLARE @blob_store_id smallint;  
DECLARE @credential_name varchar(256);  
DECLARE @credential_secret varbinary(256);  
DECLARE curSecretValue CURSOR   
    FOR SELECT sql_user_sid, blob_store_id, credential_name, credential_secret   
FROM #myTable ORDER BY sql_user_sid, blob_store_id, credential_name;  
  
OPEN curSecretValue;  
FETCH NEXT FROM curSecretValue   
    INTO @sql_user_sid, @blob_store_id, @credential_name, @credential_secret  
WHILE @@FETCH_STATUS = 0  
BEGIN  
    UPDATE [mssqlrbs_resources].[rbs_internal_blob_store_credentials]   
        SET [credential_secret] = @credential_secret   
        FROM [mssqlrbs_resources].[rbs_internal_blob_store_credentials]   
        WHERE sql_user_sid = @sql_user_sid AND blob_store_id = @blob_store_id AND   
            credential_name = @credential_name  
FETCH NEXT FROM curSecretValue   
    INTO @sql_user_sid, @blob_store_id, @credential_name, @credential_secret  
END  
CLOSE curSecretValue  
DEALLOCATE curSecretValue  
  
DROP TABLE #myTable;  
CLOSE ALL SYMMETRIC KEYS;  
DROP SYMMETRIC KEY #mssqlrbs_encryption_skey;  
  
/* Verify that you can decrypt all encrypted credential store entries using the certificate.*/  
IF( EXISTS(SELECT * FROM [mssqlrbs_resources].[rbs_internal_blob_store_credentials]   
WHERE decryptbykeyautocert(cert_id('cert_mssqlrbs_encryption'),   
    NULL, credential_secret) IS NULL))  
BEGIN  
    print 'Aborted. Failed to verify key rotation'  
    ROLLBACK;  
END;  
ELSE  
    COMMIT;  
END;  
END;  
END TRY  
BEGIN CATCH  
     PRINT 'Exception caught: ' + cast(ERROR_NUMBER() as nvarchar) + ' ' + ERROR_MESSAGE();  
     ROLLBACK  
END CATCH  
END;  
GO  
```  
  
 Now you can use the `sp_rotate_rbs_symmetric_credential_key` stored procedure to rotate the RBS credential store symmetric key, and the secrets remain the same before and after the key rotation.  
  
```  
SELECT *, decryptbykeyautocert(cert_id('cert_mssqlrbs_encryption'), NULL, credential_secret)   
FROM [mssqlrbs_resources].[rbs_internal_blob_store_credentials];  
  
EXEC sp_rotate_rbs_symmetric_credential_key;  
  
SELECT *, decryptbykeyautocert(cert_id('cert_mssqlrbs_encryption'), NULL, credential_secret)   
FROM [mssqlrbs_resources].[rbs_internal_blob_store_credentials];  
  
/* See that the RBS credential store symmetric key properties reflect the new changes*/  
SELECT * FROM sys.symmetric_keys WHERE name = 'mssqlrbs_encryption_skey';  
```  
  
## See Also  
 [Remote Blob Store &#40;RBS&#41; and AlwaysOn Availability Groups &#40;SQL Server&#41;](../Topic/Remote%20Blob%20Store%20\(RBS\)%20and%20AlwaysOn%20Availability%20Groups%20\(SQL%20Server\).md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../Topic/CREATE%20SYMMETRIC%20KEY%20\(Transact-SQL\).md)  
  
  