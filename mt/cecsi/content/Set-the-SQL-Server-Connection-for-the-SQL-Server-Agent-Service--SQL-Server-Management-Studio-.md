---
title: "Set the SQL Server Connection for the SQL Server Agent Service (SQL Server Management Studio)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 28b6178b-0a9e-4f2c-8562-7a62d2d2a285
caps.latest.revision: 5
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
# Set the SQL Server Connection for the SQL Server Agent Service (SQL Server Management Studio)
This topic describes how to set the connection between [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent and the [!INCLUDE[ssDE](../content/includes/ssDE_md.md)] in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)]. The [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service can connect to a local instance of SQL Server by using Windows Authentication.  
  
**In This Topic**  
  
-   **Before you begin:**  
  
    [Limitations and Restrictions](#Restrictions)  
  
    [Security](#Security)  
  
-   **To set the SQL Server Connection for the SQL Server Agent, using:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Restrictions"></a>Limitations and Restrictions  
  
-   Object Explorer only displays the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent node if you have permission to use it.  
  
-   Beginning with [!INCLUDE[ssVersion2005](../content/includes/ssVersion2005_md.md)], [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent does not support [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication. This option is available only when you administer an earlier version of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
To perform its functions, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]. The account must have the following Windows permissions:  
  
-   Log on as a service (SeServiceLogonRight)  
  
-   Replace a process-level token (SeAssignPrimaryTokenPrivilege)  
  
-   Bypass traverse checking (SeChangeNotifyPrivilege)  
  
-   Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)  
  
For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](../content/Select-an-Account-for-the-SQL-Server-Agent-Service.md) and [Setting Up Windows Service Accounts](assetId:///309b9dac-0b3a-4617-85ef-c4519ce9d014).  
  
## <a name="SSMSProcedure"></a>Using SQL Server Management Studio  
  
#### To set the SQL Server connection  
  
1.  In **Object Explorer**, click the plus sign to expand the server that you want to set up with a connection to its SQL Server Agent Service.  
  
2.  Right-click **SQL Server Agent** and select **Properties**.  
  
3.  In the **SQL Server Agent Properties***sever_name* dialog box, under **Select a page**, click **Connection**.  
  
4.  Under **SQL Server connection**, select **Use Windows Authentication** to enable [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent to connect to an instance of the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] [!INCLUDE[ssDE](../content/includes/ssDE_md.md)] with [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] Windows Authentication. Connections to [!INCLUDE[ssVersion2005](../content/includes/ssVersion2005_md.md)] and later databases require Windows Authentication.  
  
