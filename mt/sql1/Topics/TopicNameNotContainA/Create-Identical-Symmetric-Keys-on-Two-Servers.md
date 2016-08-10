---
title: "Create Identical Symmetric Keys on Two Servers"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a13d0b21-a43b-43c0-9c22-7ba8f3d15e80
caps.latest.revision: 24
caps.handback.revision: 0
manager: jhubbard
---
# Create Identical Symmetric Keys on Two Servers
This topic describes how to create identical symmetric keys on two different servers in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. In order to decrypt ciphertext, you need the key that was used to encrypt it. When both encryption and decryption occur in a single database, the key is stored in the database and it is available, depending on permissions, for both encryption and decryption. But when encryption and decryption occur in separate databases or on separate servers, the key stored in one database is not available for use on the second database  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   [To create identical symmetric keys on two different servers, using Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   When a symmetric key is created, the symmetric key must be encrypted by using at least one of the following: certificate, password, symmetric key, asymmetric key, or PROVIDER. The key can have more than one encryption of each type. In other words, a single symmetric key can be encrypted by using multiple certificates, passwords, symmetric keys, and asymmetric keys at the same time.  
  
-   When a symmetric key is encrypted with a password instead of the public key of the database master key, the TRIPLE DES encryption algorithm is used. Because of this, keys that are created with a strong encryption algorithm, such as AES, are themselves secured by a weaker algorithm.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER ANY SYMMETRIC KEY permission on the database. If AUTHORIZATION is specified, requires IMPERSONATE permission on the database user or ALTER permission on the application role. If encryption is by certificate or asymmetric key, requires VIEW DEFINITION permission on the certificate or asymmetric key. Only Windows logins, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] logins, and application roles can own symmetric keys. Groups and roles cannot own symmetric keys.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To create identical symmetric keys on two different servers  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Create a key by running the following CREATE MASTER KEY, CREATE CERTIFICATE, and CREATE SYMMETRIC KEY statements.  
  
    ```  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'My p@55w0Rd';  
    GO  
    CREATE CERTIFICATE [cert_keyProtection] WITH SUBJECT = 'Key Protection';  
    GO  
    CREATE SYMMETRIC KEY [key_DataShare] WITH  
        KEY_SOURCE = 'My key generation bits. This is a shared secret!',  
        ALGORITHM = AES_256,   
        IDENTITY_VALUE = 'Key Identity generation bits. Also a shared secret'  
        ENCRYPTION BY CERTIFICATE [cert_keyProtection];  
    GO  
    ```  
  
4.  Connect to a separate server instance, open a different Query Window, and run the SQL statements above to create the same key on the second server.  
  
5.  Test the keys by first running the OPEN SYMMETRIC KEY statement and the SELECT statement below on the first server.  
  
    ```  
    OPEN SYMMETRIC KEY [key_DataShare]   
        DECRYPTION BY CERTIFICATE cert_keyProtection;  
    GO  
    SELECT encryptbykey(key_guid('key_DataShare'), 'MyData' )  
    GO  
    -- For example, the output might look like this: 0x2152F8DA8A500A9EDC2FAE26D15C302DA70D25563DAE7D5D1102E3056CE9EF95CA3E7289F7F4D0523ED0376B155FE9C3  
    ```  
  
6.  On the second server, paste the result of the previous SELECT statement into the following code as the value of `@blob` and run the following code to verify that the duplicate key can decrypt the ciphertext.  
  
    ```  
    OPEN SYMMETRIC KEY [key_DataShare]   
        DECRYPTION BY CERTIFICATE cert_keyProtection;  
    GO  
    DECLARE @blob varbinary(8000);  
    SET @blob = SELECT CONVERT(varchar(8000), decryptbykey(@blob));  
    GO  
    ```  
  
7.  Close the symmetric key on both servers.  
  
    ```  
    CLOSE SYMMETRIC KEY [key_DataShare];  
    GO  
    ```  
  
 For more information, see the following:  
  
-   [CREATE MASTER KEY (Transact-SQL)](assetId:///1710a305-1a4f-48ec-836c-11ffd0356d76)  
  
-   [CREATE CERTIFICATE (Transact-SQL)](assetId:///a4274b2b-4cb0-446a-a956-1c8e6587515d)  
  
-   [CREATE SYMMETRIC KEY (Transact-SQL)](assetId:///b5d23572-b79d-4cf1-9eef-d648fa3b1358)  
  
-   [EncryptByKey (Transact-SQL)](assetId:///0e11f8c5-f79d-46c1-ab11-b68ef05d6787)  
  
-   [DecryptByKey (Transact-SQL)](assetId:///6edf121f-ac62-4dae-90e6-6938f32603c9)  
  
-   [OPEN SYMMETRIC KEY (Transact-SQL)](assetId:///ff019a7c-c373-46c7-ac43-ffb7e2ee60b3)