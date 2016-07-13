---
title: Write Execution Trace Messages to the SQL Server Agent Error Log (SQL Server Management Studio)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 90e3731e-6fae-43db-833e-9accecdd1c03
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
# Write Execution Trace Messages to the SQL Server Agent Error Log (SQL Server Management Studio)
This topic describes how to configure [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent to include execution trace messages in its error log in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)].  
  
**In This Topic**  
  
-   **Before you begin:**  
  
    [Limitations and Restrictions](#Restrictions)  
  
    [Security](#Security)  
  
-   To write execution trace messages to the SQL Server Agent Error Log using SQL Server Management Studio  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Restrictions"></a>Limitations and Restrictions  
  
-   Object Explorer only displays the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent node if you have permission to use it.  
  
-   Because this option can cause the error log to become large, only include execution trace messages in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent error logs when investigating a specific [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent problem.  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
To perform its functions, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]. The account must have the following Windows permissions:  
  
-   Log on as a service (SeServiceLogonRight)  
  
-   Replace a process\-level token (SeAssignPrimaryTokenPrivilege)  
  
-   Bypass traverse checking (SeChangeNotifyPrivilege)  
  
-   Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)  
  
For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](../content/Select-an-Account-for-the-SQL-Server-Agent-Service.md) and [Setting Up Windows Service Accounts](assetId:///309b9dac-0b3a-4617-85ef-c4519ce9d014).  
  
## <a name="SSMSProcedure"></a>  
#### To write execution trace messages to the SQL Server Agent error log  
  
1.  In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent error log to which you want to write execution trace messages.  
  
2.  Right\-click **SQL Server Agent** and select **Properties**.  
  
3.  In the **SQL Server Agent Properties –***server\_name* dialog box, under **Error log** on the **General** page, select the **Include execution trace messages** check box.  
  
4.  Click **OK**.  
  
