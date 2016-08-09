---
title: "Preview"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 551494c4-9e27-4592-9200-c6bf19e80c9a
caps.latest.revision: 11
caps.handback.revision: 0
manager: jhubbard
---
# Preview
Use the **Preview** dialog box to preview the data that the SAP BW source will extract.  
  
> [!IMPORTANT]  
>  The **Preview** option, that is available on the **Connection Manager** page of the **SAP BW Source Editor**, actually extracts data. If you have configured SAP Netweaver BW to extract only data that has changed since the previous extraction, selecting **Preview** will exclude the previewed data from the next extraction.  
  
 To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](../../Topics/TopicNameNotContainA/SAP-BW-Source.md).  
  
> [!IMPORTANT]  
>  The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment. For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.  
  
> [!IMPORTANT]  
>  Extracting data from SAP Netweaver BW requires additional SAP licensing. Check with SAP to verify these requirements.  
  
 **To open the Preview dialog box**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] package that contains the SAP BW source.  
  
2.  On the **Data Flow** tab, double-click the SAP BW source.  
  
3.  In the **SAP BW Source Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.  
  
4.  Configure the SAP BW source.  
  
5.  After you configure the SAP BW source, on the **Connection Manager** page, click **Preview** to preview the data in the **Preview** dialog box.  
  
    > [!NOTE]  
    >  Clicking **Preview** also opens the **Request Log** dialog box. For more information about this dialog box, see [Request Log](../../Topics/TopicNameNotContainA/Request-Log.md).  
  
## Options  
 The **Preview** dialog box displays the rows that are requested from the SAP Netweaver BW system. The columns that are displayed are the columns that are defined in the source data.  
  
 There are no other options in this dialog box.  
  
## See Also  
 [SAP BW Source Editor (Connection Manager Page)](../../Topics/TopicNameNotContainA/SAP-BW-Source-Editor--Connection-Manager-Page-.md)   
 [Microsoft Connector for SAP BW F1 Help](../../Topics/TopicNameNotContainA/Microsoft-Connector-for-SAP-BW-F1-Help.md)