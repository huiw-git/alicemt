---
title: Server Properties (Execution Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 53b77db1-b013-4dac-82dd-30c0de276639
---
# Server Properties (Execution Page)
  Use this page to set a timeout value for report execution. This value applies to all reports that are processed by the current report server instance. You can override this value for individual reports. The value you specify must accommodate all report processing that occurs on the report server, plus query processing performed on the database server when the report server retrieves data that is used in the report.  
  
 To open this page, start [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], connect to a report server instance, right\-click the report server name, and select **Properties**. Click **Execution** to open this page.  
  
## Options  
 **Do not timeout report execution**  
 Allow a report server unlimited time to complete report processing.  
  
 **Limit report execution to the following number of seconds**  
 Set a time constraint on report execution. The time period starts when the report is requested. If the time period ends before the report is fully processed, the report server cancels the process and any in\-process queries to external data sources.  
  
## See Also  
 [Set Report Server Properties &#40;Management Studio&#41;](../Topic/Set%20Report%20Server%20Properties%20\(Management%20Studio\).md)   
 [Connect to a Report Server in Management Studio](../../Topics\TopicNameContainA/Connect-to-a-Report-Server-in-Management-Studio.md)   
 [Set Report Processing Properties](../../Topics\TopicNameNotContainA/Set-Report-Processing-Properties.md)   
 [Setting Time-out Values for Report and Shared Dataset Processing &#40;SSRS&#41;](../Topic/Setting%20Time-out%20Values%20for%20Report%20and%20Shared%20Dataset%20Processing%20\(SSRS\).md)   
 [Report Server in Management Studio F1 Help](../../Topics\TopicNameNotContainA/Report-Server-in-Management-Studio-F1-Help.md)  
  
  