---
title: Connect to Server (Database Engine)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ee9017b4-8a19-4360-9003-9e6484082d41
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
# Connect to Server (Database Engine)
Use this dialog to view or specify options when connecting to [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssDEnoversion](../content/includes/ssDEnoversion_md.md)]. In most cases, you can connect by entering the computer name of the database server in the **Server name** box and then clicking **Connect**. If you are connecting to [!INCLUDE[ssExpress](../content/includes/ssExpress_md.md)], use the computer name followed by **\\sqlexpress**.  
  
Many factors can affect your ability to connect to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].  
  
## Options  
**Server type**  
When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../content/includes/ssDE_md.md)], [!INCLUDE[ssASnoversion](../content/includes/ssASnoversion_md.md)], [!INCLUDE[ssRSnoversion](../content/includes/ssRSnoversion_md.md)], or [!INCLUDE[ssISnoversion](../content/includes/ssISnoversion_md.md)]. The rest of the dialog shows only the options that apply to the selected server type. When registering a server from Registered Servers, the **Server type** box is read\-only, and matches the type of server displayed in the Registered Servers component. To register a different type of server, select [!INCLUDE[ssDE](../content/includes/ssDE_md.md)], [!INCLUDE[ssASnoversion](../content/includes/ssASnoversion_md.md)], [!INCLUDE[ssRSnoversion](../content/includes/ssRSnoversion_md.md)], [!INCLUDE[ssEW](../content/includes/ssEW_md.md)], or [!INCLUDE[ssISnoversion](../content/includes/ssISnoversion_md.md)] from the Registered Servers toolbar before starting to register a new server.  
  
**Server name**  
Select the server instance to connect to. The server instance last connected to is displayed by default.  
  
> [!NOTE]  
> To connect to an active user instance of [!INCLUDE[ssExpress](../content/includes/ssExpress_md.md)] connect using named pipes protocol specifying the pipe name, such as np:\\\\.\\pipe\\3C3DF6B1\-2262\-47\\tsql\\query For more information, see the [!INCLUDE[ssExpress](../content/includes/ssExpress_md.md)] documentation.  
  
**Authentication**  
Three authentication modes are available when connecting to an instance of the [!INCLUDE[ssDE](../content/includes/ssDE_md.md)].  
  
**Windows Authentication**  
[!INCLUDE[msCoName](../content/includes/msCoName_md.md)] Windows Authentication mode allows a user to connect through a Windows user account.  
  
**SQL Server Authentication**  
When a user connects with a specified login name and password from a non\-trusted connection, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] performs the authentication itself by checking to see if a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] login account has been set up and if the specified password matches the one previously recorded. If [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] does not have a login account set, authentication fails, and the user receives an error message.  
  
> [!IMPORTANT]  
> When possible, use Windows Authentication or Active Directory Password Authentication.  
  
**Active Directory Password Authentication**  
Azure Active Directory Authentication is a mechanism of connecting to [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssSDSfull](../content/includes/ssSDSfull_md.md)] by using identities in Azure Active Directory (Azure AD).  Use this method for connecting to [!INCLUDE[ssSDS](../content/includes/ssSDS_md.md)] if you are logged into Windows using credentials from a domain that is not federated with Azure, or when using Azure AD authentication using Azure AD based on the initial or the client domain. For more information, see [Connecting to SQL Database By Using Azure Active Directory Authentication](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).  
  
**Active Directory Integrated Authentication**  
Azure Active Directory Authentication is a mechanism of connecting to [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssSDSfull](../content/includes/ssSDSfull_md.md)] by using identities in Azure Active Directory (Azure AD). Use this method for connecting to [!INCLUDE[ssSDS](../content/includes/ssSDS_md.md)] if you are logged into Windows using your Azure Active Directory credentials from a federated domain. For more information, see [Connecting to SQL Database By Using Azure Active Directory Authentication](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).  
  
**User name**  
The Windows user name to connect with. This option is only available if you have selected to connect using **Active Directory Password Authentication**. It is read\-only when you selecting **Windows Authentication**.  
  
**Login**  
Enter the login to connect with. This option is only available if you have selected to connect using [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication or or Active Directory Password Authentication.  
  
**Password**  
Enter the password for the login. This option is only editable if you have selected to connect using [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication or or Active Directory Password Authentication.  
  
**Connect**  
Click to connect to the server selected above.  
  
**Options**  
Click to display additional server connection options, such as registering a server and remembering the password.  
  
