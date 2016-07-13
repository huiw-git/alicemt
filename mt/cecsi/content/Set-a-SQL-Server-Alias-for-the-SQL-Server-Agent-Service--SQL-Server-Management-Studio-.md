---
title: Set a SQL Server Alias for the SQL Server Agent Service (SQL Server Management Studio)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 02d6295d-ab52-44f0-8f1b-f3910a507d8f
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
# Set a SQL Server Alias for the SQL Server Agent Service (SQL Server Management Studio)
This topic describes how to set a [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] alias for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent to use to connect to the [!INCLUDE[ssDE](../content/includes/ssDE_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)]. By default, the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service connects to an instance of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] over named pipes by using dynamic server names that require no additional client configuration. You need to configure a server connection alias only if you are not using the default network transport or if you are connecting to an instance of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] that listens on an alternate named pipe.  
  
**In This Topic**  
  
-   **Before you begin:**  
  
    [Limitations and Restrictions](#Restrictions)  
  
    [Security](#Security)  
  
-   [To set a SQL Server Alias for the SQL Server Agent Service using SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Restrictions"></a>Limitations and Restrictions  
  
-   [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent will not work correctly unless you select an alias that refers to the local instance of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].  
  
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
  
#### To set a SQL Server Alias for the SQL Server Agent Service  
  
1.  In the **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../content/includes/ssDEnoversion_md.md)] and then expand that instance.  
  
2.  Right\-click **SQL Server Agent**, and then click **Properties**.  
  
3.  In the **SQL Server Agent Properties***server\_name* dialog box, under **Select a page**, select **Connection**, and  
  
4.  In the **Alias local host server** box, type the alias of the server to which [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent should connect.  
  
5.  Click **OK**.  
  
