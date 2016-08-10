---
title: "Create a Credential"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c1e77e91-2a69-40d9-b8b3-97cffc710586
caps.latest.revision: 18
caps.handback.revision: 0
manager: jhubbard
---
# Create a Credential
This topic describes how to create a credential in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 Credentials provide a way to allow [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Authentication users to have an identity outside of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. This is primarily used to execute code in Assemblies with EXTERNAL_ACCESS permission set. Credentials can also be used when a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Authentication user needs access to a domain resource, such as a file location to store a backup.  
  
 A credential can be mapped to several [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] logins at the same time. A [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login can only be mapped to one credential at a time. After a credential is created, use the **Login Properties (General Page)** to map a login to a credential.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To create a credential, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   If there is no login mapped credential for the provider, the credential mapped to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] service account is used.  
  
-   A login can have multiple credentials mapped to it as long as they are used with distinctive providers. There must be only one mapped credential per provider per login. The same credential can be mapped to other logins.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER ANY CREDENTIAL permission to create or modify a credential and ALTER ANY LOGIN permission to map a login to a credential.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To create a credential  
  
1.  In Object Explorer, expand  the **Security** folder.  
  
2.  Right-click the **Credentials** folder and select **New Credential…**.  
  
3.  In the **New Credential** dialog box, in the **Credential Name** box, type a name for the credential.  
  
4.  In the **Identity** box, type the name of the account used for outgoing connections (when leaving the context of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]). Typically, this will be a Windows user account, but the identity can be an account of another type.  
  
     Alternately, click the ellipsis **(…)** to open the **Select User or Group** dialog box.  
  
5.  In the **Password** and **Confirm password** boxes, type the password of the account specified in the **Identity** box. If **Identity** is a Windows user account, this is the Windows password. The **Password** can be blank, if no password is required.  
  
6.  Select **Use Encryption Provider** to set the credential to be verified by an Extensible Key Management (EKM) Provider. For more information, see [Extensible Key Management (EKM)](../../Topics/TopicNameNotContainA/Extensible-Key-Management--EKM-.md)  
  
7.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To create a credential  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    -- Creates the credential called "AlterEgo.".   
    -- The credential contains the Windows user "Mary5" and a password.  
    CREATE CREDENTIAL AlterEgo WITH IDENTITY = 'Mary5',   
        SECRET = '<EnterStrongPasswordHere>';  
    GO  
    ```  
  
 For more information, see [CREATE CREDENTIAL (Transact-SQL)](assetId:///d5e9ae69-41d9-4e46-b13d-404b88a32d9d).