---
title: "Managing Encryption Keys (Always Encrypted)"
ms.custom: na
ms.date: 06/29/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 07a305b1-4110-42f0-b7aa-28a4e32e912a
caps.latest.revision: 10
manager: jhubbard
---
# Managing Encryption Keys (Always Encrypted)

This article provides the details for managing your [Always Encrypted](https://msdn.microsoft.com/library/mt163865.aspx) keys. 

Always Encrypted uses two types of keys to protect your data - one key to encrypt your data, and another key to encrypt the key that encrypts your data. The column encryption key encrypts your data, the column master key encrypts the column encryption key.


- ***Column encryption keys*** are symmetric keys used to encrypt data stored in database columns. The column encryption keys themselves are encrypted, and stored in the database in system catalog views. You should store column encryption keys in a trusted and secure location for backup.


- ***Column master keys*** are the physical key-protecting keys used to encrypt column encryption keys. Column master keys must be stored in a trusted key store, and information about column master keys, including their location, is stored as metadata in the database (in system catalog views). It is important to note that client applications that need to access encrypted data, must have permission to access the column master key in the key store.  

The database system never has access to the plaintext values of column master keys, or column encryption keys, and does not have access to the key store. The server and database do not contain or have access to the physical keys - instead the database contains metadata about the keys and stores the metadata for Always Encrypted keys in system catalog views. For details, see [CREATE COLUMN MASTER KEY (Transact-SQL)](CREATE%20COLUMN%20MASTER%20KEY%20\(Transact-SQL\).md) and [CREATE COLUMN ENCRYPTION KEY (Transact-SQL)](CREATE%20COLUMN%20ENCRYPTION%20KEY%20\(Transact-SQL\).md).



## Always Encrypted Key Management Options

At a high level, managing your keys consists of: 

- Creating the physical keys in a trusted key store (Windows Certificate Store, Azure Key Vault, ...).
- Adding the Always Encrypted key metadata to the database (the database only contains metadata describing the physical keys - and never has access to the plaintext keys).
- Periodically rotating the keys for security.

The process of managing keys can be divided into these discreet tasks to easily separate and control who has access to the physical encryption keys in the key store, and who has access to the database. We describe this as role separation between Security Administrators and Database Administrators (DBAs). Depending on the needs of your organization you can select the key management workflow that best suits your environment:
 

## With Role Separation
The Security Administrator and DBA roles are assumed by different people. Role separation must be enforced if your goal is to ensure DBAs in your organization cannot access sensitive data.

- Use role separation to ensure cloud administrators cannot access sensitive data stored in a cloud-hosted database.  
- Use role separation to ensure DBAs in your (customer’s) organization cannot access sensitive data.  

For detailed directions on configuring Always Encrypted with Role Separation, see [Configuring Always Encrypted using PowerShell](../../Topics/TopicNameNotContainA/Configuring-Always-Encrypted-using-PowerShell.md).

## Without role separation
A single user/team assumes both Security Administrator and DBA roles. Recommended for Dev/test environments and for Production environments if restricting DBAs’ access to sensitive data is not a goal (for example, if the database is hosted in the cloud and the primary objective is to restrict cloud administrators from accessing the data).  
  
For detailed directions on configuring Always Encrypted without Role Separation, see:

- [SSMS with Azure Key Vault](https://azure.microsoft.com/documentation/articles/sql-database-always-encrypted-azure-key-vault/)
- [SSMS with Windows Certificate Store](https://azure.microsoft.com/documentation/articles/sql-database-always-encrypted/)
- [Configuring Always Encrypted using PowerShell](http://www.microsoft.com/library/mt732057.aspx).



## Key Rotation

Rotating a column master key is the process of replacing an existing column master key and column encryption key with new keys. After rotating keys you should clean up your system by removing the old encryption keys.

For detailed instructions, see [Column master Key Rotation](../../Topics/TopicNameNotContainA/Column-Master-Key-Rotation--Always-Encrypted-.md).


## Tools for Managing Always Encrypted Keys: 

[SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/mt238290.aspx)
Always Encrypted Keys can be managed using SQL Server Management Studio (SSMS) and PowerShell, although role separation is not currently supported in SSMS. 

SSMS tools (dialogs, wizards) combine tasks involving key store access and access to physical keys with tasks manipulating with key metadata. This makes configuring your keys easy to use, but without role separation only.




- PowerShell supports both (role separation/no role separation).  
- Performing key management tasks using SSMS:  
- Key Provisioning (link – we do not have a topic for it yet. It should cover New CEK, New CMK dialogs). It should also have mention the keys can be provisioned (auto-generated) using the Always Encrypted wizard (we have a topic for the wizard - link).)  

