---
title: Send SQL Server Agent Error Messages
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2597d0d7-951a-48cf-989f-abb67b9fdb36
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
# Send SQL Server Agent Error Messages
This topic describes how to how to configure [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent to send its error messages by way of net send in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)].  
  
**In This Topic**  
  
-   **Before you begin:**  
  
    [Limitations and Restrictions](#Restrictions)  
  
    [Security](#Security)  
  
-   [To send SQL Server Agent error messages using SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Restrictions"></a>Limitations and Restrictions  
  
-   Object Explorer only displays the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent node if you have permission to use it.  
  
-   The [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] Windows Messenger service must be running to receive net send events.  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
To perform its functions, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]. The account must have the following Windows permissions:  
  
-   Log on as a service (SeServiceLogonRight)  
  
-   Replace a process\-level token (SeAssignPrimaryTokenPrivilege)  
  
-   Bypass traverse checking (SeChangeNotifyPrivilege)  
  
-   Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)  
  
For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](../content/Select-an-Account-for-the-SQL-Server-Agent-Service.md) and [Setting Up Windows Service Accounts](assetId:///309b9dac-0b3a-4617-85ef-c4519ce9d014).  
  
## <a name="SSMSProcedure"></a>Using SQL Server Management Studio  
  
#### To send SQL Server Agent error messages  
  
1.  In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent error log from which you want to send error messages via net send.  
  
2.  Right\-click **SQL Server Agent** and select **Properties**.  
  
3.  In the **SQL Server Agent Properties –***server\_name* dialog box, under **Error log** on the **General** page, , type the user name or computer name to which you want to send error messages in the **Net send recipient** box.  
  
4.  Click **OK**.  
  
