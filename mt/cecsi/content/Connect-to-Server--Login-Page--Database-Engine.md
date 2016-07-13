---
title: Connect to Server (Login Page) Database Engine
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e08cfbc3-bed5-4401-a13b-1c66d902fe32
manager:jhubbard
translation.priority.mt: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Connect to Server (Login Page) Database Engine
Use this tab to view or specify options when connecting to [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssDEnoversion](../content/includes/ssDEnoversion_md.md)].  
  
> [!NOTE]  
> To connect with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] must be configured in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] and Windows Authentication mode. For more information about how to determine the authentication mode and to change the authentication mode, see [How to: Change Server Authentication Mode](assetId:///79babcf8-19fd-4495-b8eb-453dc575cac0).  
  
## Options  
**Server type**  
When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../content/includes/ssDE_md.md)], Analysis Services, Reporting Services, or Integration Services. The rest of the dialog box shows only the options that apply to the selected server type. When registering a server from Registered Servers, the **Server type** box is read\-only, and matches the type of server displayed in the Registered Servers component. To register a different type of server, select [!INCLUDE[ssDE](../content/includes/ssDE_md.md)], Analysis Services, Reporting Services, or Integration Services from the Registered Servers toolbar before starting to register a new server.  
  
When connecting to an instance of the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Database Engine through [!INCLUDE[ssSDSfull](../content/includes/ssSDSfull_md.md)], you must use [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication and specify a database in the **Connect to Server** dialog box, on the **Connection Properties** tab. Ensure that you select the **Encrypt connection** checkbox.  
  
By default, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] connects to **master**. If you specify a user database, you will only see that database and its objects in Object Explorer. If you connect to **master**, you will be able to see all databases. For more information, see the [Windows Azure SQL Database Overview](http://go.microsoft.com/fwlink/?LinkId=163948).  
  
**Server name**  
Select the server instance to connect to. The server instance last connected to is displayed by default.  
  
**Authentication**  
Two authentication modes are available when connecting to an instance of [!INCLUDE[ssDEnoversion](../content/includes/ssDEnoversion_md.md)].  
  
When connecting to an instance of the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Database Engine through [!INCLUDE[ssSDS](../content/includes/ssSDS_md.md)], you must use [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication and specify a database in the **Connect to Server** dialog box, on the **Connection Properties** tab. Ensure that you select the **Encrypt connection** checkbox.  
  
By default, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] connects to **master**. If you specify a user database, you will only see that database and its objects in Object Explorer. If you connect to **master**, you will be able to see all databases. For more information, see the [Windows Azure SQL Database Overview](http://go.microsoft.com/fwlink/?LinkId=163948).  
  
**Windows Authentication**  
[!INCLUDE[msCoName](../content/includes/msCoName_md.md)] Windows Authentication mode allows a user to connect through a Windows user account.  
  
**SQL Server Authentication**  
When a user connects with a specified login name and password from a non\-trusted connection, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] performs the authentication itself by checking to see if a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] login account has been set up and if the specified password matches the one previously recorded. If [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] does not have a login account set, authentication fails, and the user receives an error message.  
  
> [!IMPORTANT]  
> When possible, use Windows Authentication.  
  
**Active Directory Password Authentication**  
Azure Active Directory Authentication is a mechanism of connecting to [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssSDSfull](../content/includes/ssSDSfull_md.md)] by using identities in Azure Active Directory (Azure AD).  Use this method for connecting to [!INCLUDE[ssSDS](../content/includes/ssSDS_md.md)] if you are logged into Windows using credentials from a domain that is not federated with Azure, or when using Azure AD authentication using Azure AD based on the initial or the client domain. For more information, see [Connecting to SQL Database By Using Azure Active Directory Authentication](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).  
  
**Active Directory Integrated Authentication**  
Azure Active Directory Authentication is a mechanism of connecting to [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssSDSfull](../content/includes/ssSDSfull_md.md)] by using identities in Azure Active Directory (Azure AD). Use this method for connecting to [!INCLUDE[ssSDS](../content/includes/ssSDS_md.md)] if you are logged into Windows using your Azure Active Directory credentials from a federated domain. For more information, see [Connecting to SQL Database By Using Azure Active Directory Authentication](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).  
  
**User name**  
The Windows user name to connect with. This option is only available if you have selected to connect using **Active Directory Password Authentication**. It is read\-only when you selecting **Windows Authentication**.  
  
**Login**  
Enter the login to connect with. This option is only available if you have selected to connect using [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication.  
  
**Password**  
Enter the password for the login. This option is only editable if you have selected to connect using [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication.  
  
**Remember password**  
Click to have [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] store the password you have entered. This option is only displayed if you have selected to connect using [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication.  
  
**Connect**  
Click to connect to the server selected above.  
  
**Options**  
Click to change the dialog box and hide the additional server connection options, such as remembering the password.  
  
