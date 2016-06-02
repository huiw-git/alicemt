---
title: Create a Credential
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c1e77e91-2a69-40d9-b8b3-97cffc710586
---
# Create a Credential
  This topic describes how to create a credential in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 Credentials provide a way to allow [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication users to have an identity outside of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. This is primarily used to execute code in Assemblies with EXTERNAL\_ACCESS permission set. Credentials can also be used when a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication user needs access to a domain resource, such as a file location to store a backup.  
  
 A credential can be mapped to several [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] logins at the same time. A [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login can only be mapped to one credential at a time. After a credential is created, use the **Login Properties \(General Page\)** to map a login to a credential.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To create a credential, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   If there is no login mapped credential for the provider, the credential mapped to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service account is used.  
  
-   A login can have multiple credentials mapped to it as long as they are used with distinctive providers. There must be only one mapped credential per provider per login. The same credential can be mapped to other logins.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER ANY CREDENTIAL permission to create or modify a credential and ALTER ANY LOGIN permission to map a login to a credential.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To create a credential  
  
1.  In Object Explorer, expand  the **Security** folder.  
  
2.  Right\-click the **Credentials** folder and select **New Credential…**.  
  
3.  In the **New Credential** dialog box, in the **Credential Name** box, type a name for the credential.  
  
4.  In the **Identity** box, type the name of the account used for outgoing connections \(when leaving the context of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\). Typically, this will be a Windows user account, but the identity can be an account of another type.  
  
     Alternately, click the ellipsis **\(…\)** to open the **Select User or Group** dialog box.  
  
5.  In the **Password** and **Confirm password** boxes, type the password of the account specified in the **Identity** box. If **Identity** is a Windows user account, this is the Windows password. The **Password** can be blank, if no password is required.  
  
6.  Select **Use Encryption Provider** to set the credential to be verified by an Extensible Key Management \(EKM\) Provider. For more information, see [Extensible Key Management &#40;EKM&#41;](../Topic/Extensible%20Key%20Management%20\(EKM\).md)  
  
7.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To create a credential  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    -- Creates the credential called "AlterEgo.".   
    -- The credential contains the Windows user "Mary5" and a password.  
    CREATE CREDENTIAL AlterEgo WITH IDENTITY = 'Mary5',   
        SECRET = '<EnterStrongPasswordHere>';  
    GO  
    ```  
  
 For more information, see [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../Topic/CREATE%20CREDENTIAL%20\(Transact-SQL\).md).  
  
  