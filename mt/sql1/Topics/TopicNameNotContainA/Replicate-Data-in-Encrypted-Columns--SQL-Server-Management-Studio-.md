---
title: "Replicate Data in Encrypted Columns (SQL Server Management Studio)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d1f8f586-e5a3-4a71-9391-11198d42bfa3
caps.latest.revision: 9
caps.handback.revision: 0
manager: jhubbard
---
# Replicate Data in Encrypted Columns (SQL Server Management Studio)
Replication enables you to publish encrypted column data. To decrypt and use this data at the Subscriber, the key that was used to encrypt the data at the Publisher must also be present on the Subscriber. Replication does not provide a secure mechanism to transport encryption keys. You must manually re-create the encryption key at the Subscriber. This topic shows you how to encrypt a column at the Publisher and make sure that the encryption key is available at the Subscriber.  
  
 The basic steps are as follows:  
  
1.  Create the symmetric key at the Publisher.  
  
2.  Encrypt column data with the symmetric key.  
  
3.  Publish the table with the encrypted column.  
  
4.  Subscribe to the publication.  
  
5.  Initialize the subscription.  
  
6.  Recreate the symmetric key at the Subscriber using same values for ALGORITHM, KEY_SOURCE, and IDENTITY_VALUE as in step 1.  
  
7.  Access the encrypted column data.  
  
> [!NOTE]  
>  You should use a symmetric key to encrypt column data. The symmetric key itself can be secured by different means at the Publisher and Subscriber.  
  
### To create and replicate encrypted column data  
  
1.  At the Publisher, execute [CREATE SYMMETRIC KEY](assetId:///b5d23572-b79d-4cf1-9eef-d648fa3b1358).  
  
    > [!IMPORTANT]  
    >  The value of KEY_SOURCE is valuable data that can be used to re-create the symmetric key and decrypt data. KEY_SOURCE must always be stored and transported securely.  
  
2.  Execute [OPEN SYMMETRIC KEY](assetId:///ff019a7c-c373-46c7-ac43-ffb7e2ee60b3) to open the new key.  
  
3.  Use the [EncryptByKey](assetId:///0e11f8c5-f79d-46c1-ab11-b68ef05d6787) function to encrypt column data at the Publisher.  
  
4.  Execute [CLOSE SYMMETRIC KEY](assetId:///3b083cbb-3c6a-4f59-8d34-601db1efcc83) to close the key.  
  
5.  Publish the table that contains the encrypted column. For more information, see [Create a Publication](../../Topics/TopicNameContainA/Create-a-Publication.md).  
  
6.  Subscribe to the publication. For more information, see [Create a Pull Subscription](../../Topics/TopicNameContainA/Create-a-Pull-Subscription.md) or [Create a Push Subscription](../../Topics/TopicNameContainA/Create-a-Push-Subscription.md).  
  
7.  Initialize the subscription. For more information, see [Create and Apply the Initial Snapshot](../../Topics/TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md).  
  
8.  At the Subscriber, execute [CREATE SYMMETRIC KEY](assetId:///b5d23572-b79d-4cf1-9eef-d648fa3b1358) using the same values for ALGORITHM, KEY_SOURCE, and IDENTITY_VALUE as in step 1. You can specify a different value for ENCRYPTION BY.  
  
    > [!IMPORTANT]  
    >  The value of KEY_SOURCE is valuable data that can be used to re-create the symmetric key and decrypt data. KEY_SOURCE must always be stored and transported securely.  
  
9. Execute [OPEN SYMMETRIC KEY](assetId:///ff019a7c-c373-46c7-ac43-ffb7e2ee60b3) to open the new key.  
  
10. Use the [DecryptByKey](assetId:///6edf121f-ac62-4dae-90e6-6938f32603c9) function to decrypt replicated data at the Subscriber.  
  
11. Execute [CLOSE SYMMETRIC KEY](assetId:///3b083cbb-3c6a-4f59-8d34-601db1efcc83) to close the key.  
  
## Example  
 This example creates a symmetric key, a certificate that is used to help secure the symmetric key, and a master key. These keys are created in the publication database. They are then used to create an encrypted column (EncryptedCreditCardApprovalCode) in the `SalesOrderHeader` table. This column is published in the AdvWorksSalesOrdersMerge publication instead of the unencrypted CreditCardApprovalCode column. When possible, prompt users to enter security credentials at runtime. If you must store credentials in a script file, you must secure the file to prevent unauthorized access.  
  
 [!CODE [HowTo#sp_PublishEncryptedColumn](../CodeSnippet/SQL15/replication/howto#sp_publishencryptedcolumn)]  
  
 [!CODE [HowTo#sp_AddMergeArticle](../CodeSnippet/SQL15/replication/howto#sp_addmergearticle)]  
  
## Example  
 This example recreates the same symmetric key in the subscription database using the same values for ALGORITHM, KEY_SOURCE, and IDENTITY_VALUE from the first example. This example assumes that you have already initialized a subscription to the AdvWorksSalesOrdersMerge publication to replicate the encrypted column. When possible, prompt users to enter security credentials at runtime. If you must store credentials in a script file, you must secure the file during storage and transport to prevent unauthorized access.  
  
 [!CODE [HowTo#sp_SubscriberEncryptedColumn](../CodeSnippet/SQL15/replication/howto#sp_subscriberencryptedcolumn)]  
  
## See Also  
 [Security Overview (Replication)](../../Topics/TopicNameNotContainA/Security-Overview--Replication-.md)   
 [Create Identical Symmetric Keys on Two Servers](../../Topics/TopicNameNotContainA/Create-Identical-Symmetric-Keys-on-Two-Servers.md)