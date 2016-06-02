---
title: Create Database Mail Profile and Account Dialog Box (Master Data Services Configuration Manager)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b93ea3d4-9f22-490e-8e26-d766b454aed6
---
# Create Database Mail Profile and Account Dialog Box (Master Data Services Configuration Manager)
  Use the **Create Database Mail Profile and Account** dialog box to create a Database Mail profile and a Database Mail account for the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database. This profile will be used to notify users and groups by email when business rule validation fails.  
  
## Database Mail Profile and Account  
 A *Database Mail profile* is a collection of Database Mail accounts. A *Database Mail account* contains the information that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] uses to send email messages to an SMTP server. When you create the profile and account in [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)], the account is automatically added to the profile and that account information is used to send emails.  
  
> [!NOTE]  
>  You cannot use [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)] to update existing Database Mail profiles or accounts, nor can you configure more than one account for a profile. To perform more advanced tasks with Database Mail, you can use [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or Transact\-SQL scripts. For more information, see the [Database Mail Configuration Objects](../../Topics\TopicNameNotContainA/Database-Mail-Configuration-Objects.md) section in SQL Server Books Online.  
  
|Control Name|Description|  
|------------------|-----------------|  
|**Profile name**|Type a name for the new Database Mail profile. This name must be unique among the Database Mail profiles configured for the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.<br /><br /> After you create this profile, it is available and selected on the **Database** page in [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)].|  
|**Account name**|Type a name for the new Database Mail account to associate with this profile. This name must be unique among the Database Mail accounts configured for the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database. This account does not correspond to a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] account nor to a Windows user account.|  
  
## Outgoing \(SMTP\) Mail Server  
  
|Control Name|Description|  
|------------------|-----------------|  
|**Email address**|Type the name of the email address for the account. This is the email address that email is sent from, and it must be in the format *email\_name*@*domain\_name*. An example email address is sales@contoso.com.|  
|**Display name**|Optional setting. Type the name to display on email messages sent from this account. An example display name is Contoso Sales Group.|  
|**Reply email address**|Optional setting. Type the email address to use for replies to email messages sent from this account. An example reply email address is admin@contoso.com.|  
|**SMTP server**|Type the name or IP address of the SMTP server the account uses to send email. An example SMTP server format is **smtp.***\<company\_name\>***.com**. For help with this, consult your mail administrator.|  
|**Port number**|Type the port number of the SMTP server for this account. The default SMTP port is 25.|  
|**This server requires a secure connection \(SSL\)**|Encrypts communication using Secure Sockets Layer \(SSL\).|  
  
## SMTP Authentication  
 Database Mail can be sent by using the credentials of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], by using other credentials that you supply, or anonymously. As a best practice, if your email server requires authentication, create a specific user account to use for Database Mail. This user account should have minimal permissions, and should not be used for any other purpose.  
  
|Control Name|Description|  
|------------------|-----------------|  
|**Windows Authentication using Database Engine service credentials**|Specify that Database Mail should use the credentials of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] Windows service account for authentication on the SMTP server.|  
|**Basic authentication**|Specify that Database Mail should use a specific user name and password to authenticate on the SMTP server. This information is used only for authentication with the email server, and the account need not correspond to a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] user or user on the computer running [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|  
|**User name**|Type the name of the user account that Database Mail uses to log on to the SMTP server. A user name is required if the SMTP server requires basic authentication.|  
|**Password**|Type the password that Database Mail uses to log on to the SMTP server. A password is required if the SMTP server requires basic authentication.|  
|**Confirm password**|Type the password again to confirm the password.|  
|**Anonymous authentication**|Specify that the SMTP server does not require authentication. Database Mail will not use any credentials to authenticate on the SMTP server.|  
  
## See Also  
 [Database Configuration Page &#40;Master Data Services Configuration Manager&#41;](../Topic/Database%20Configuration%20Page%20\(Master%20Data%20Services%20Configuration%20Manager\).md)   
 [Get Started with Master Data Services &#40;SQL Server 2016&#41;](../Topic/Get%20Started%20with%20Master%20Data%20Services%20\(SQL%20Server%202016\).md)  
  
  