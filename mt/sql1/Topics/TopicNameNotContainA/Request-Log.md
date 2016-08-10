---
title: "Request Log"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 165d3833-0493-490c-9f63-8a134a7fafb8
caps.latest.revision: 11
manager: jhubbard
---
# Request Log
Use the **Request Log** dialog box to view the events that are logged during the request that is made to the SAP Netweaver BW system for sample data. This information can be useful if you have to troubleshoot your configuration of the SAP BW source.  
  
 To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](../../Topics/TopicNameNotContainA/SAP-BW-Source.md).  
  
> [!IMPORTANT]  
>  The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment. For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.  
  
> [!IMPORTANT]  
>  Extracting data from SAP Netweaver BW requires additional SAP licensing. Check with SAP to verify these requirements.  
  
 **To open the Request Log dialog box**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] package that contains the SAP BW source.  
  
2.  On the **Data Flow** tab, double-click the SAP BW source.  
  
3.  In the **SAP BW Source Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.  
  
4.  After you configure the SAP BW source, click **Preview** to preview the events in the **Request Log** dialog box.  
  
    > [!NOTE]  
    >  Clicking **Preview** also opens the **Preview** dialog box. For more information about this dialog box, see [Preview](../../Topics/TopicNameNotContainA/Preview.md).  
  
## Options  
 **Time**  
 Displays the time that the event that was logged.  
  
 **Type**  
 Displays the type of the event that was logged. The following table lists the possible event types.  
  
|Value|Description|  
|-----------|-----------------|  
|S|Success message.|  
|E|Error message|  
|W|Warning message.|  
|I|Informational message.|  
|A|The operation was aborted.|  
  
 **Message**  
 Displays the message text that is associated with the logged event.  
  
## See Also  
 [SAP BW Source Editor (Connection Manager Page)](../../Topics/TopicNameNotContainA/SAP-BW-Source-Editor--Connection-Manager-Page-.md)   
 [Microsoft Connector for SAP BW F1 Help](../../Topics/TopicNameNotContainA/Microsoft-Connector-for-SAP-BW-F1-Help.md)