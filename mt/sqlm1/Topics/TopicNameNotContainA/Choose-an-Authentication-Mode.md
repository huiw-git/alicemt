---
title: Choose an Authentication Mode
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ff7a6a48-3d38-4209-aa0f-7d6c0a8c64ef
---
# Choose an Authentication Mode
  During setup, you must select an authentication mode for the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]. There are two possible modes: Windows Authentication mode and mixed mode. Windows Authentication mode enables Windows Authentication and disables [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication. Mixed mode enables both Windows Authentication and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication. Windows Authentication is always available and cannot be disabled.  
  
## Configuring the Authentication Mode  
 If you select Mixed Mode Authentication during setup, you must provide and then confirm a strong password for the built\-in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] system administrator account named sa. The sa account connects by using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication.  
  
 If you select Windows Authentication during setup, Setup creates the sa account for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication but it is disabled. If you later change to Mixed Mode Authentication and you want to use the sa account, you must enable the account. Any Windows or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] account can be configured as a system administrator. Because the sa account is well known and often targeted by malicious users, do not enable the sa account unless your application requires it. Never set a blank or weak password for the sa account. To change from Windows Authentication mode to Mixed Mode Authentication and use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication, see [Change Server Authentication Mode](../../Topics\TopicNameNotContainA/Change-Server-Authentication-Mode.md).  
  
## Connecting Through Windows Authentication  
 When a user connects through a Windows user account, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] validates the account name and password using the Windows principal token in the operating system. This means that the user identity is confirmed by Windows. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] does not ask for the password, and does not perform the identity validation. Windows Authentication is the default authentication mode, and is much more secure than [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication. Windows Authentication uses Kerberos security protocol, provides password policy enforcement with regard to complexity validation for strong passwords, provides support for account lockout, and supports password expiration. A connection made using Windows Authentication is sometimes called a trusted connection, because [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] trusts the credentials provided by Windows.  
  
 By using Windows Authentication, Windows groups can be created at the domain level, and a login can be created on [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] for the entire group. Managing access from at the domain level can simplify account administration.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../Token\Other/ssNoteWinAuthentication_md.md)]  
  
## Connecting Through SQL Server Authentication  
 When using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication, logins are created in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that are not based on Windows user accounts. Both the user name and the password are created by using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and stored in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Users connecting using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication must provide their credentials \(login and password\) every time that they connect. When using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication, you must set strong passwords for all [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] accounts. For strong password guidelines, see [Strong Passwords](../../Topics\TopicNameNotContainA/Strong-Passwords.md).  
  
 Three optional password policies are available for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] logins.  
  
-   User must change password at next login  
  
     Requires the user to change the password the next time that the user connects. The ability to change the password is provided by [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. Third\-party software developers should provide this feature if this option is used.  
  
-   Enforce password expiration  
  
     The maximum password age policy of the computer is enforced for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] logins.  
  
-   Enforce password policy  
  
     The Windows password policies of the computer are enforced for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] logins. This includes password length and complexity. This functionality depends on the `NetValidatePasswordPolicy` API, which is only available in [!INCLUDE[winxpsvr](../../Token\Other/winxpsvr_md.md)] and later versions.  
  
#### To determine the password policies of the local computer  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **secpol.msc**, and then click **OK**.  
  
3.  In the **Local Security Settings** application, expand **Security Settings**, expand **Account Policies**, and then click **Password Policy**.  
  
     The password policies are described in the results pane.  
  
### Disadvantages of SQL Server Authentication  
  
-   If a user is a Windows domain user who has a login and password for Windows, he must still provide another \([!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\) login and password to connect. Keeping track of multiple names and passwords is difficult for many users. Having to provide [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] credentials every time that one connects to the database can be annoying.  
  
-   [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication cannot use Kerberos security protocol.  
  
-   Windows offers additional password policies that are not available for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] logins.  
  
-   The encrypted [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication login password, must be passed over the network at the time of the connection. Some applications that connect automatically will store the password at the client. These are additional attack points.  
  
### Advantages of SQL Server Authentication  
  
-   Allows [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to support older applications and applications provided by third parties that require [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication.  
  
-   Allows [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to support environments with mixed operating systems, where all users are not authenticated by a Windows domain.  
  
-   Allows users to connect from unknown or untrusted domains. For instance, an application where established customers connect with assigned [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] logins to receive the status of their orders.  
  
-   Allows [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to support Web\-based applications where users create their own identities.  
  
-   Allows software developers to distribute their applications by using a complex permission hierarchy based on known, preset [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] logins.  
  
    > [!NOTE]  
    >  Using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication does not limit the permissions of local administrators on the computer where [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is installed.  
  
## See Also  
 [Security Considerations for a SQL Server Installation](../../Topics\TopicNameContainA/Security-Considerations-for-a-SQL-Server-Installation.md)  
  
  