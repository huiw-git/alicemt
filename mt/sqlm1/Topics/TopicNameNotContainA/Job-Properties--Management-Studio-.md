---
title: Job Properties (Management Studio)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 807ffd0e-9363-4f8f-9c36-c5d746ad19fd
---
# Job Properties (Management Studio)
  Use the **Job Properties** page to view information about an in\-progress report or subscription before you cancel it.  
  
 To open this page, start [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], connect to a report server, and open the **Jobs** folder. Right\-click a job that is running, and then click **Properties**.  
  
> [!NOTE]  
>  This feature is not supported in [!INCLUDE[ssExpress](../../Token\Other/ssExpress_md.md)] with Advanced Services. The page does not appear when you are running [!INCLUDE[ssExpress](../../Token\Other/ssExpress_md.md)].  
  
## Tasks  
 Before you can view information about a job, refresh the page to retrieve information about jobs that are currently running on the report server:  
  
1.  Open the report server folder.  
  
2.  Right\-click **Jobs**, and then click **Refresh**.  
  
3.  If a job is listed, right\-click the job, and then click **Properties**.  
  
## Options  
 **Job ID**  
 A GUID that is assigned to a job while it is processing. The value is randomly generated each time a report or subscription runs.  
  
 **Job Status**  
 Valid values are **New** and **Running**. Status is always **New** when the job begins. After 60 seconds, status changes to **Running**. You must refresh the page to pick up the change.  
  
 **Job Type**  
 Valid values are **User** and **System**. A user job is any job that is initiated by an individual user. This includes running a report on\-demand, manually generating a report history snapshot, or manually creating a report execution snapshot. An in\-progress standard subscription is also a user job. A system job is one that is initiated by the report server. System jobs include report processing that is triggered by a schedule.  
  
 **Job Action**  
 For reports, this column shows which report execution processes are underway. This value is always **Render**.  
  
 **Job Description**  
 [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] does not provide job descriptions by default.  
  
 **Server Name**  
 Shows the name of the report server that is processing the job. If you configured a scale\-out deployment, this value will show which server is processing the job.  
  
 **Report Name**  
 Shows the name of the report. Subscriptions are identified by their descriptions.  
  
 **Report Path**  
 Shows the path of the report in the report server folder hierarchy.  
  
 **Start Time**  
 Shows when the process started.  
  
 **User Name**  
 For processes initiated by a user, this column shows the name of the user. For system jobs, this is the name of the report server.  
  
## See Also  
 [Report Server in Management Studio F1 Help](../../Topics\TopicNameNotContainA/Report-Server-in-Management-Studio-F1-Help.md)   
 [Connect to a Report Server in Management Studio](../../Topics\TopicNameContainA/Connect-to-a-Report-Server-in-Management-Studio.md)   
 [Manage a Running Process](../../Topics\TopicNameContainA/Manage-a-Running-Process.md)  
  
  