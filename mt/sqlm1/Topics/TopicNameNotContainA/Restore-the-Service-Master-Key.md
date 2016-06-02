---
title: Restore the Service Master Key
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 14bdbbbe-d384-4692-b670-4243d2466fe1
---
# Restore the Service Master Key
  This topic describes how to restore the service master key in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
> [!WARNING]  
>  It is unlikely that you will ever need to restore the service master key. If you do, you should proceed with extreme caution. For more information, see [Back Up the Service Master Key](../../Topics\TopicNameNotContainA/Back-Up-the-Service-Master-Key.md).  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   [To restore the service master key using Transact\-SQL](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   When the service master key is restored, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] decrypts all the keys and secrets that have been encrypted with the current service master key, and then encrypts them with the service master key loaded from the backup file.  
  
-   If any one of the decryptions fails, the restore will fail. You can use the FORCE option to ignore errors, but this option will cause the loss of any data that cannot be decrypted.  
  
-   Regenerating the encryption hierarchy is a resource\-intensive operation. You should schedule this during a period of low demand.  
  
> [!CAUTION]  
>  The service master key is the root of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] encryption hierarchy. The service master key directly or indirectly secures all other keys in the tree. If a dependent key cannot be decrypted during a forced restore, data that is secured by that key will be lost.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires CONTROL SERVER permission on the server.  
  
##  <a name="SSMSProcedure"></a> Using Transact\-SQL  
  
#### To restore the service master key  
  
1.  Retrieve a copy of the backed\-up service master key, either from a physical backup medium or a directory on the local file system.  
  
2.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
3.  On the Standard bar, click **New Query**.  
  
4.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    -- Restores the service master key from a backup file.  
    RESTORE SERVICE MASTER KEY   
        FROM FILE = 'c:\temp_backups\keys\service_master_key'   
        DECRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
    GO  
    ```  
  
    > [!NOTE]  
    >  The file path to the key and the key's password \(if it exists\) will be different than what is indicated above. Please make sure that both are specific to your server and key set\-up.  
  
  