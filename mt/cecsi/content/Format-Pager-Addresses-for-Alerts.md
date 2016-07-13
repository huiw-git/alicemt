---
title: Format Pager Addresses for Alerts
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a9797d01-1050-442c-9038-ed4bfee1e76a
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
# Format Pager Addresses for Alerts
This topic describes how to format pager addresses for [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent alerts in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../content/includes/tsql_md.md)].  
  
**In This Topic**  
  
-   **Before you begin:**  
  
    [Security](#Security)  
  
-   **To format pager addresses, using:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
By default, members of the **sysadmin** fixed server role can view information about an alert. Other users must be granted the **SQLAgentOperatorRole** fixed database role in the **msdb** database.  
  
## <a name="SSMSProcedure"></a>Using SQL Server Management Studio  
  
#### To format pager addresses  
  
1.  In **Object Explorer**, click the plus sign to expand the server that contains the alert that you want to send to a pager.  
  
2.  Right\-click **SQL Server Agent** and select **Properties**  
  
3.  Under **Select a page**, select **Alert System**.  
  
4.  In the **To line** and **CC line** boxes of the **Address formatting for pager e\-mails** field, enter the pager address prefix or suffix. The operator's actual pager address is inserted when a notification is sent.  
  
5.  In the **Subject** box, enter the subject line prefix or suffix.  
  
6.  Select the **Include body of e\-mail in notification page** check box to include the full e\-mail message with the pager message (as opposed to the subject line only).  
  
7.  When finished, click **OK**.  
  
