---
title: Schedule Properties (Reports Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7db728bd-4b08-43ef-a49a-e8dcdd37cf89
---
# Schedule Properties (Reports Page)
  Use this page to view a list of all reports that use this shared schedule. Schedules can be used to refresh report snapshots, generate report history, trigger a subscription, or expire a cached copy of the report. To find out how the schedule is used, view the property and subscription information of the report.  
  
 Although this page shows each report that uses the shared schedule, it does not indicate how many times the shared schedule is used within that single report. For example, suppose 20 different subscribers to the Company Sales report all use the same shared schedule to trigger subscription processing. In this case, the Company Sales report will only appear once in this list, even though the report has 20 references to the shared schedule.  
  
 To open this page, start [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], connect to a report server, open the **Shared Schedules** folder, right\-click a shared schedule, select **Properties**, and then click **Reports**.  
  
> [!NOTE]  
>  This feature is not available in every edition of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [Features Supported by the Editions of SQL Server 2012](http://go.microsoft.com/fwlink/?linkid=232473) \(http:\/\/go.microsoft.com\/fwlink\/?linkid\=232473\).  
  
## Options  
 **Folder**  
 Specifies the path of the report.  
  
 **Report**  
 Specifies the name of the report that uses the schedule.  
  
## See Also  
 [Create, Modify, and Delete Schedules](../../Topics\TopicNameNotContainA/Create,-Modify,-and-Delete-Schedules.md)   
 [Schedules](../../Topics\TopicNameNotContainA/Schedules.md)   
 [Report Server in Management Studio F1 Help](../../Topics\TopicNameNotContainA/Report-Server-in-Management-Studio-F1-Help.md)   
 [Connect to a Report Server in Management Studio](../../Topics\TopicNameContainA/Connect-to-a-Report-Server-in-Management-Studio.md)   
 [Configure General Properties for a Report \(Report Manager\)](assetId:///10b941b2-28e6-4408-9ee4-acebc63c8496)  
  
  