---
title: "Back Up a Database Master Key"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7ad9a0a0-6e4f-4f7b-8801-8c1b9d49c4d8
caps.latest.revision: 20
caps.handback.revision: 0
manager: jhubbard
---
# Back Up a Database Master Key
This topic describes how to back up a database master key in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. The database master key is used to encrypt other keys and certificates inside a database. If it is deleted or corrupted, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] may be unable to decrypt those keys, and the data encrypted using them will be effectively lost. For this reason, you should back up the database master key and store the backup in a secure off-site location.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   [To back up a database master key using Transact-SQL](#Procedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   The master key must be open and, therefore, decrypted before it is backed up. If it is encrypted with the service master key, the master key does not have to be explicitly opened. But if the master key is encrypted only with a password, it must be explicitly opened.  
  
-   We recommend that you back up the master key as soon as it is created, and store the backup in a secure, off-site location.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires CONTROL permission on the database.  
  
##  <a name="Procedure"></a> Using SQL Server Management Studio with Transact-SQL  
  
#### To back-up the database master key  
  
1.  In [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], connect to the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance containing the database master key you wish to back up.  
  
2.  Choose a password that will be used to encrypt the database master key on the backup medium. This password is subject to complexity checks.  
  
3.  Obtain a removable backup medium for storing a copy of the backed-up key.  
  
4.  Identify an NTFS directory in which to create the backup of the key. This is where you will create the file specified in the next step. The directory should be protected with highly restrictive access control lists (ACLs).  
  
5.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
6.  On the Standard bar, click **New Query**.  
  
7.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    -- Creates a backup of the "AdventureWorks2012" master key. Because this master key is not encrypted by the service master key, a password must be specified when it is opened.  
    USE AdventureWorks2012;   
    GO  
    OPEN MASTER KEY DECRYPTION BY PASSWORD = 'sfj5300osdVdgwdfkli7';   
  
    BACKUP MASTER KEY TO FILE = 'c:\temp\exportedmasterkey'   
        ENCRYPTION BY PASSWORD = 'sd092735kjn$&adsg';   
    GO  
    ```  
  
    > [!NOTE]  
    >  The file path to the key and the key's password (if it exists) will be different than what is indicated above. Please make sure that both are specific to your server and key set-up.  
  
8.  Copy the file to the backup medium and verify the copy.  
  
9. Store the backup in a secure, off-site location.  
  
 For more information, see [OPEN MASTER KEY (Transact-SQL)](assetId:///1674753e-ca1e-4913-9ba4-b442e7106121) and [BACKUP MASTER KEY (Transact-SQL)](assetId:///0e25fe22-2536-4d7e-ba4a-1921e880f367).