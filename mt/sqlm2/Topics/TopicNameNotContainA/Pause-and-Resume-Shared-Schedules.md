---
title: Pause and Resume Shared Schedules
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e416be75-5234-4aa6-a3de-77f60f25169a
---
# Pause and Resume Shared Schedules
  You can pause and resume a shared schedule that is in use. Pausing a shared schedule provides a way to temporarily freeze a schedule that is used to trigger report processing and subscriptions. Only shared schedules can be paused and resumed. You cannot pause report\-specific schedules.  
  
 You cannot pause and resume report processing that is in progress. You can only pause and resume schedules that are in the scheduling queue of SQL Server Agent service. A job that is in progress is outside the scope of the scheduling engine. For more information, see [Manage a Running Process](../../Topics\TopicNameContainA/Manage-a-Running-Process.md)  
  
 While a shared schedule is paused, any operations that would have occurred are allowed to lapse. After you resume a shared schedule, report and subscription processing occurs at the next scheduled time, using the local time of the server. The native mode report server or SharePoint service applications, do not make up scheduled operations that would have occurred had the schedule not been paused.  
  
 In this Topic:  
  
-   [Pause and Resume Shared Schedules (Native Mode)](#bkmk_native)  
  
-   [Pause and Resume Shared Schedules (SharePoint mode)](#bkmk_sharepoint)  
  
##  <a name="bkmk_native"></a> Pause and Resume Shared Schedules \(Native Mode\)  
 To pause and resume a shared schedule, use the Schedules page in Report Manager. You cannot use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)]; it does not provide options for pausing and resuming schedules. For more information, see [Create, Modify, and Delete Schedules](../../Topics\TopicNameNotContainA/Create,-Modify,-and-Delete-Schedules.md).  
  
#### To pause or resume a shared schedule  
  
1.  From Report Manager Click, **Site Settings**.  
  
2.  Click **Schedules**.  
  
3.  Select the schedule, and click **Pause** or **Resume** in the ribbon. If a Schedule is currently paused, the **Status** column will contain **Paused**.  
  
##  <a name="bkmk_sharepoint"></a> Pause and Resume Shared Schedules \(SharePoint mode\)  
 To pause and resume a shared schedule, use the Site Settings page or PowerShell. Schedules are managed per SharePoint site.  
  
#### To pause or resume a shared schedule  
  
1.  Click **Site Actions**.  
  
2.  Click **Site Settings**.  
  
3.  In the Reporting Services section, click **Manage Shared Schedules**.  
  
4.  Select the schedule, and click **Pause Selected Schedules** or **Run Selected Schedules**. If a Schedule is currently paused, the **Status** column will contain **Paused**.  
  
## See Also  
 [Schedules](../../Topics\TopicNameNotContainA/Schedules.md)   
 [Create, Modify, and Delete Schedules](../../Topics\TopicNameNotContainA/Create,-Modify,-and-Delete-Schedules.md)   
 [Change Time Zones and Clock Settings on a Report Server](../../Topics\TopicNameContainA/Change-Time-Zones-and-Clock-Settings-on-a-Report-Server.md)   
 [Manage a Running Process](../../Topics\TopicNameContainA/Manage-a-Running-Process.md)  
  
  