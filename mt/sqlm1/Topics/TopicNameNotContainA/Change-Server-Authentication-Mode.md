---
title: Change Server Authentication Mode
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 79babcf8-19fd-4495-b8eb-453dc575cac0
---
# Change Server Authentication Mode
  This topic describes how to change the server authentication mode in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. During installation, [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] is set to either **Windows Authentication mode** or **SQL Server and Windows Authentication mode**. After installation, you can change the authentication mode at any time.  
  
 If **Windows Authentication mode** is selected during installation, the sa login is disabled and a password is assigned by setup. If you later change authentication mode to **SQL Server and Windows Authentication mode**, the sa login remains disabled. To use the sa login, use the ALTER LOGIN statement to enable the sa login and assign a new password. The sa login can only connect to the server by using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To change server authentication mode, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
 The sa account is a well\-known [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] account and it is often targeted by malicious users. Do not enable the sa account unless your application requires it. It is very important that you use a strong password for the sa login.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To change security authentication mode  
  
1.  In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] Object Explorer, right\-click the server, and then click **Properties**.  
  
2.  On the **Security** page, under **Server authentication**, select the new server authentication mode, and then click **OK**.  
  
3.  In the [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] dialog box, click **OK** to acknowledge the requirement to restart [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
4.  In Object Explorer, right\-click your server, and then click **Restart**. If [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent is running, it must also be restarted.  
  
#### To enable the sa login  
  
1.  In Object Explorer, expand **Security**, expand Logins, right\-click **sa**, and then click **Properties**.  
  
2.  On the **General** page, you might have to create and confirm a password for the  login.  
  
3.  On the **Status** page, in the **Login** section, click **Enabled**, and then click **OK**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To enable the sa login**  
  
1.  In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. The following example enables the sa login and sets a new password.  
  
    ```  
    ALTER LOGIN sa ENABLE ;  
    GO  
    ALTER LOGIN sa WITH PASSWORD = '<enterStrongPasswordHere>' ;  
    GO  
  
    ```  
  
## See Also  
 [Strong Passwords](../../Topics\TopicNameNotContainA/Strong-Passwords.md)   
 [Security Considerations for a SQL Server Installation](../../Topics\TopicNameContainA/Security-Considerations-for-a-SQL-Server-Installation.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../Topic/ALTER%20LOGIN%20\(Transact-SQL\).md)   
 [Connect to SQL Server When System Administrators Are Locked Out](../../Topics\TopicNameNotContainA/Connect-to-SQL-Server-When-System-Administrators-Are-Locked-Out.md)  
  
  