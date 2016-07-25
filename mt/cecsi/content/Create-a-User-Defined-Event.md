---
title: "Create a User-Defined Event"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 03d71a35-97fa-4bba-aa9a-23ac9c9cf879
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
# Create a User-Defined Event
You can create user-defined events if you want to monitor events other than events that are predefined by [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]. You can also assign a severity level to each user-defined event.  
  
> [!NOTE]  
> When using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)], select the **Write to Windows application event log** option for each user-defined event message, to ensure that the messages are logged. By default, user-defined messages of severity lower than 19 are not sent to the [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] Windows application log when they occur. User-defined messages of severity lower than 19 therefore do not trigger SQL Server Agent alerts.  
  
User-defined events must have a unique message number. Message numbers for a user-defined event must be greater than 50,000. You can define messages for the event in multiple languages. However, an **En-US** error message must exist before messages in other languages can be added.  
  
If you administer a multiple-language [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] environment, create user-defined messages in each of the languages that are supported. For example, if you are creating a new event message to be used on both an English and a German server, use the same message number and severity for both, but assign a different language to each.  
  
The following tasks provide information about how to create user-defined events and alerts that respond to them:  
  
**To create an alert based on a message number**  
  
-   [SQL Server Management Studio](../content/Create-an-Alert-Using-an-Error-Number.md)  
  
-   [Transact-SQL](assetId:///d9b41853-e22d-4813-a79f-57efb4511f09)  
  
**To create an alert based on severity levels**  
  
-   [SQL Server Management Studio](../content/Create-an-Alert-Using-Severity-Level.md)  
  
-   [Transact-SQL](assetId:///d9b41853-e22d-4813-a79f-57efb4511f09)  
  
**To define the response to an alert**  
  
-   [SQL Server Management Studio](../content/Define-the-Response-to-an-Alert--SQL-Server-Management-Studio-.md)  
  
-   [Transact-SQL](assetId:///0525e0a2-ed0b-4e69-8a4c-a9e3e3622fbd)  
  
**To create a user-defined event error message**  
  
-   [Transact-SQL](assetId:///54746d30-f944-40e5-a707-f2d9be0fb9eb)  
  
**To modify a user-defined event error message**  
  
-   [Transact-SQL](assetId:///1b28f280-8ef9-48e9-bd99-ec14d79abaca)  
  
**To delete a user-defined event error message**  
  
-   [Transact-SQL](assetId:///17287a15-cdde-43d1-bb18-9f920bc15db8)  
  
**To disable or reactivate an alert**  
  
-   [SQL Server Management Studio](../content/Disable-or-Reactivate-an-Alert.md)  
  
-   [Transact-SQL](assetId:///4bbaeaab-8aca-4c9e-abc1-82ce73090bd3)  
  
## See Also  
[sp_update_alert (Transact-SQL)](assetId:///4bbaeaab-8aca-4c9e-abc1-82ce73090bd3)  
  
