---
title: Database Engine Configuration - Server Configuration
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 834b26bc-49de-4033-88d5-6aa7b1609720
---
# Database Engine Configuration - Server Configuration
  Use this page to set the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] security mode, and to add Windows users or groups as administrators of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)].  
  
## Considerations for Running [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]  
 On previous versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], the **BUILTIN\\Administrators** group was provisioned as a login in the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and members of the local Administrators group could login using their Administrator credentials. Using elevated permissions is not a best practice. In [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] the **BUILTIN\\Administrators** group is not provisioned as a login. As a result, you should create a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login for each administrative user, and add that login to the sysadmin fixed server role during installation of a new instance of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. You should also do this for Windows accounts that are used to run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] agent jobs. These include replication agent jobs.  
  
## Options  
 **Security Mode** \- Select Windows Authentication or Mixed Mode Authentication for your installation.  
  
 **Windows Principal Provisioning** \- In previous versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], the Windows Builtin\\Administrator local group was placed into the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] sysadmin server role, effectively granting Windows administrators access to the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. In [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], the Builtin\\Administrator group is not provisioned in the sysadmin server role. Instead, you should explicitly provision [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] administrators for new installations during Setup.  
  
> [!IMPORTANT]  
>  You must explicitly provision [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] administrators for new installations during Setup. Setup will not allow you to continue until you complete this step.  
  
 **Specify [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Administrators** \- You must specify at least one Windows principal for the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. To add the account under which [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup is running, click the **Current User** button. To add or remove accounts from the list of system administrators, click **Add** or **Remove**, and then edit the list of users, groups, or computers that will have administrator privileges for the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
 When you are finished editing the list, click **OK**, then verify the list of administrators in the configuration dialog. When the list is complete, click **Next**.  
  
 If you select Mixed Mode Authentication, you must provide logon credentials for the builtin [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] system administrator \(SA\) account.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../Token\Other/ssNoteStrongPass_md.md)]  
  
 **Windows Authentication Mode**  
 When a user connects through a Windows user account, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] validates the account name and password using the Windows principal token in the operating system. This is the default authentication mode, and is much more secure than Mixed Mode. Windows Authentication utilizes Kerberos security protocol, provides password policy enforcement in terms of complexity validation for strong passwords, provides support for account lockout, and supports password expiration.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../Token\Other/ssNoteWinAuthentication_md.md)]  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../Token\Other/ssNoteStrongPass_md.md)] Never set a blank or weak sa password.  
  
 **Mixed Mode \(Windows Authentication or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication\)**  
 Allows users to connect by using Windows Authentication or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication. Users who connect through a Windows user account can use trusted connections that are validated by Windows.  
  
 If you must choose Mixed Mode Authentication and you have a requirement for using SQL logins to accommodate legacy applications, you must set strong passwords for all [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] accounts.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication is provided for backward compatibility only. [!INCLUDE[ssNoteWinAuthentication](../../Token\Other/ssNoteWinAuthentication_md.md)]  
  
 **Enter Password**  
 Enter and confirm the system administrator \(sa\) login. Passwords are the first line of defense against intruders, so setting strong passwords is essential to the security of your system. Never set a blank or weak sa password.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] passwords can contain from 1 to 128 characters, including any combination of letters, symbols, and numbers. If you choose Mixed Mode authentication, you must enter a strong sa password before you can continue to the next page of the Installation Wizard.  
  
 **Strong Password Guidelines**  
 Strong passwords are not readily guessed by a person, and are not easily hacked using a computer program. Strong passwords cannot use prohibited conditions or terms, including:  
  
-   A blank or NULL condition  
  
-   "Password"  
  
-   "Admin"  
  
-   "Administrator"  
  
-   "sa"  
  
-   "sysadmin"  
  
 A strong password cannot be the following terms associated with the installation computer:  
  
-   The name of the user currently logged onto the machine.  
  
-   The computer name.  
  
 A strong password must be more than 8 characters in length and satisfy at least three of the following four criteria:  
  
-   It must contain uppercase letters.  
  
-   It must contain lowercase letters.  
  
-   It must contain numbers.  
  
-   It must contain non\-alphanumeric characters; for example, \#, %, or ^.  
  
 Passwords entered on this page must meet strong password policy requirements. If you have any automation that uses [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication, ensure that the password meets strong password policy requirements.  
  
## Related Content  
 For more information about choosing Windows Authentication vs. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication, see the topic **Choose an Authentication Mode** in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online.  
  
 For more information about choosing an account to run the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], see the topic **Configure Windows Service Accounts and Permissions** in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online.  
  
## See Also  
 [Configure Windows Service Accounts and Permissions](../../Topics\TopicNameNotContainA/Configure-Windows-Service-Accounts-and-Permissions.md)  
  
  