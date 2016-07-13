---
title: Start, Stop, or Pause the SQL Server Agent Service
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c95a9759-dd30-4ab6-9ab0-087bb3bfb97c
manager: jhubbard
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
# Start, Stop, or Pause the SQL Server Agent Service
This topic describes how to start, stop, or restart the SQL Server Agent Service in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)].  
  
You can configure the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service to start automatically when the operating system starts, or you can start it manually when you need to complete jobs. You can stop or pause the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service to suspend jobs, operator notifications, and alerts.  
  
**In This Topic**  
  
-   **Before you begin:**  
  
    [Limitations and Restrictions](#Restrictions)  
  
    [Security](#Security)  
  
-   [To start, stop, or restart the SQL Server Agent Service using SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Restrictions"></a>Limitations and Restrictions  
  
-   [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent must be running as a service in order to automate administrative tasks. For more information, see [Configure SQL Server Agent](../content/Configure-SQL-Server-Agent.md).  
  
-   Object Explorer only displays the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent node if you have permission to use it.  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
To perform its functions, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]. The account must have the following Windows permissions:  
  
-   Log on as a service (SeServiceLogonRight)  
  
-   Replace a process\-level token (SeAssignPrimaryTokenPrivilege)  
  
-   Bypass traverse checking (SeChangeNotifyPrivilege)  
  
-   Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)  
  
For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](../content/Select-an-Account-for-the-SQL-Server-Agent-Service.md) and [Setting Up Windows Service Accounts](assetId:///309b9dac-0b3a-4617-85ef-c4519ce9d014).  
  
## <a name="SSMSProcedure"></a>Using SQL Server Management Studio  
  
#### To start, stop, or restart the SQL Server Agent Service  
  
1.  In **Object Explorer**, click the plus sign to expand the server where you want to manage SQL Server Agent Service.  
  
2.  Right\-click **SQL Server Agent**, and then select either **Start**, **Stop**, or **Restart**.  
  
3.  In the **User Account Control** dialog box, click **Yes**.  
  
4.  When prompted if you want to perform the action, click **Yes**.  
  
For more information, see:  
  
-   [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](assetId:///32660a02-e5a1-411a-9e57-7066ca459df6)  
  
-   [Autostart SQL Server Agent &#40;SQL Server Management Studio&#41;](../content/Autostart-SQL-Server-Agent--SQL-Server-Management-Studio-.md)  
  
