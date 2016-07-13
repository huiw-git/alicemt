---
title: Designate an Events Forwarding Server (SQL Server Management Studio)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 81dfcbe4-3000-4e77-99de-bf85fef63a12
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
# Designate an Events Forwarding Server (SQL Server Management Studio)
This topic describes how to designate a server to which [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] forwards events in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] . Note that event forwarding applies to events forwarded between servers, not to events forwarded between instances of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] hosted on a single computer. Also note that in order to receive forwarded events, the alerts management server must be a default instance of SQL Server.  
  
**In This Topic**  
  
-   **Before you begin:**  
  
    [Security](#Security)  
  
-   **To designate an events forwarding server, using:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
Requires membership in the **sysadmin** fixed server role.  
  
## <a name="SSMSProcedure"></a>Using SQL Server Management Studio  
  
#### To designate an events forwarding server  
  
1.  In **Object Explorer,** click the plus sign to expand the server from which you want to forward events to another server.  
  
2.  Right\-click **SQL Server Agent** and select **Properties**.  
  
3.  In the **SQL Server Agent Properties –***server\_name* dialog box, under **Select a page**, select **Advanced**.  
  
4.  Under **SQL Server event forwarding**, select the **Forward events to a different server** check box.  
  
5.  In the **Server** list, select a server, and then, under **Events**, select one of the following:  
  
    -   Select **Unhandled events** to forward only the events that have not been handled by local alerts.  
  
    -   Select **All events** to forward all events regardless of whether they have been handled by local alerts.  
  
6.  In the **If event has severity at or above** list, click the severity level at which events are forwarded to the selected server.  
  
7.  When finished, click **OK**.  
  
