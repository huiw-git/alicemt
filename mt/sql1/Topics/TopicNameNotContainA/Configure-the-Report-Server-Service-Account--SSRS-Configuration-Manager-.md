---
title: "Configure the Report Server Service Account (SSRS Configuration Manager)"
ms.custom: na
ms.date: 2016-05-18
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f880c623-67c8-4167-b98b-ace17e800faa
caps.latest.revision: 15
caps.handback.revision: 0
manager: mblythe
---
# Configure the Report Server Service Account (SSRS Configuration Manager)
[!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] is implemented as a single service that contains a Report Server Web service, [!INCLUDE[ssRSWebPortal-Non-Markdown](../../Topics/TopicNameNotContainA/tokens/ssRSWebPortal-Non-Markdown_md.md)], and a background processing application that is used for scheduled report processing and subscription delivery. This topic explains how the service account is initially configured and how to modify the account or password using the Reporting Services Configuration tool.  
  
## Initial Configuration  
 The Report Server service account is defined during Setup. You can run the service under a domain user account, or a built-in account such as **NetworkService** account. There is no default account; whatever account you specify in the [Server Configuration - Service Accounts](../../Topics/TopicNameNotContainA/Server-Configuration---Service-Accounts.md) page of the Installation Wizard becomes the initial account of the Report Server service.  
  
> [!IMPORTANT]  
>  Although the Report Server Web service and [!INCLUDE[ssRSWebPortal-Non-Markdown](../../Topics/TopicNameNotContainA/tokens/ssRSWebPortal-Non-Markdown_md.md)] are separate [!INCLUDE[vstecasp](../../Topics/TopicNameContainA/tokens/vstecasp_md.md)] applications, they run under a single service architecture within the same Report Server process identity.  
  
> [!NOTE]  
>  Built-in Windows service accounts (Local Service or Network Service) are not supported as report server service accounts on a computer that is a domain controller.  
  
## Changing the Service Account  
 To view and reconfigure service account information, always use the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] Configuration Manager. Service identity information is stored internally in multiple locations. Using the tool ensures that all references are updated accordingly whenever you change the account or password. The [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] Configuration Manager performs the following additional steps to ensure the report server remains available:  
  
-   Automatically adds the new account to the report server group created on the local computer. This group is specified in the access control lists (ACLs) that secure [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] files.  
  
-   Automatically updates the login permissions on the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] instance used to host the report server database. The new account will be added to the **RSExecRole**.  
  
     The database login for the old account will not be removed automatically. Be sure to remove accounts that are no longer in use. For more information, see [Administer a Report Server Database (SSRS Native Mode)](../../Topics/TopicNameContainA/Administer-a-Report-Server-Database--SSRS-Native-Mode-.md) in SQL Server Books Online.  
  
     Granting database permissions to a new service account only occurs if you configured the report server database connection to use the service account in the first place. If you configured the report server database connection to use a domain user account or a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database login, the connection information is not affected by the service account update.  
  
-   Automatically updates the encryption key to include the profile information of the new account.  
  
    > [!NOTE]  
    >  If the report server is part of the scale-out deployment, only the report server that you are updating is affected. The encryption keys for other report servers in the deployment are unaffected by the service account change.  
  
#### To configure the Report Server service account  
  
1.  Start the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] Configuration manager and connect to the report server.  
  
2.  On the Service Account page, select the option that describes the type of account you want to use. For recommendations about which account type to specify, see [Configuring Service Accounts and Passwords in Reporting Services](../../Topics/TopicNameNotContainA/Configure-the-Report-Server-Service-Account--SSRS-Configuration-Manager-.md).  
  
3.  If you selected a Windows user account, specify the new account and password. The account cannot be more than 20 characters.  
  
     If the report server is deployed in a network that supports Kerberos authentication, you must register the report server Service Principal Name (SPN) with the domain user account you just specified. For more information, see [Register a Service Principal Name (SPN) for a Report Server](../../Topics/TopicNameContainA/Register-a-Service-Principal-Name--SPN--for-a-Report-Server.md).  
  
4.  Click **Apply**.  
  
5.  When prompted to back up the symmetric key, type a file name and location for the symmetric key backup, type a password to lock and unlock the file, and then click **OK**.  
  
6.  If the report server uses the service account to connect to the report server database, the connection information will be updated to use the new account or password. Updating the connection information requires that you connect to the database. If the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] **Database Connection** dialog box appears, enter credentials that have permission to connect to the database, and then click **OK**.  
  
7.  When prompted to restore the symmetric key, type the password you specified in step 5, and then click **OK**.  
  
8.  Review the status messages in the Results pane to verify all tasks completed successfully.  
  
## Choosing an Account  
 You can configure the Report Server service to run under any of these account types:  
  
-   Least-privileged Windows user account  
  
-   NetworkService  
  
-   LocalSystem  
  
-   LocalService  
  
 There is no single best approach for choosing an account type. Each account has advantages and disadvantages that you must consider. If you are deploying [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] on a production server, best practices suggest that you configure the service to run under a domain user account so that you can avoid widespread damage if a shared account is compromised by a malicious user. It also makes it easier to audit the logon activity for this account. A trade-off to using a Windows user account is that if you are deploying [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] in a network that uses Kerberos authentication, you must register the service with the user account. For more information, see [Register a Service Principal Name (SPN) for a Report Server](../../Topics/TopicNameContainA/Register-a-Service-Principal-Name--SPN--for-a-Report-Server.md).  
  
 The following guidelines and links in this section can help you decide on an approach that is best for your deployment.  
  
-   [Service Account  - Reporting Services Native mode (Configuration Manager)](../../Topics/TopicNameNotContainA/Service-Account----Reporting-Services-Native-mode--Configuration-Manager-.md).  
  
-   [Configure Windows Service Accounts and Permissions](../../Topics/TopicNameNotContainA/Configure-Windows-Service-Accounts-and-Permissions.md) in SQL Server Books Online.  
  
-   [The Services and Service Accounts Security Planning Guide](http://go.microsoft.com/fwlink/?LinkId=69155) on MSDN.  
  
## Updating an Expired Password  
 If the Report Server service runs under a domain account and the password expires before you can update it in the Reporting Services Configuration Manager, the service will not start until you specify a new password.  
  
 If the service account password for the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] expires, the **rsReportServerDatabaseUnavailable** error occurs when you try to connect to the report server. Resetting the password resolves this error.  
  
## Troubleshooting Service Identity Update Errors  
 Changing the service identity initiates a series of events that include restarting the service, updating the password-protected encryption key, updating URL reservations, and updating the report server database connection information if you are using the service account to connect to the report server database. You can monitor the status of these events by viewing the notifications in the Results panel at the bottom of the page. If errors occur during this process, you can try to resolve them using the following techniques:  
  
-   If the symmetric key cannot be restored, you can try to restore it manually by using **Restore** in the Encryption Keys page. If that does not work, consider deleting the encrypted content. You will have to re-create data source connection information and subscriptions, but the rest of your content will still be available. For more information, see [Back Up and Restore Reporting Services Encryption Keys](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-Reporting-Services-Encryption-Keys.md).  
  
-   If the service will not start, restart it manually by using the Services console application in Administrator Tools.  
  
-   URL reservation errors can occur when you update the service account. Each URL reservation includes a security descriptor that includes a Discretionary Access Control List (DACL) that grants permission to the service account to accept requests on the URL. When you update the account, the URL must be recreated to update the DACL with the new account information. If the URL reservation cannot be recreated, and you know the account to be valid, try to restart the computer. If the error persists, try to use a different account.  
  
## See Also  
 [Configure a Service Account (SSRS Configuration Manager)](../../Topics/TopicNameContainA/Configure-a-Service-Account--SSRS-Configuration-Manager-.md)   
 [Service Account  - Reporting Services Native mode (Configuration Manager)](../../Topics/TopicNameNotContainA/Service-Account----Reporting-Services-Native-mode--Configuration-Manager-.md)   
 [Configure Report Server URLs  (SSRS Configuration Manager)](../../Topics/TopicNameNotContainA/Configure-Report-Server-URLs---SSRS-Configuration-Manager-.md)   
 [Reporting Services Configuration Manager (Native Mode)](../../Topics/TopicNameNotContainA/Reporting-Services-Configuration-Manager--Native-Mode-.md)