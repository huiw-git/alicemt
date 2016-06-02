---
title: SAP BW Source Editor (Connection Manager Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a6dc531-85ca-43c5-a65f-3ad3f7d537c4
---
# SAP BW Source Editor (Connection Manager Page)
  Use the **Connection Manager** page of the **SAP BW Source Editor** to select the SAP BW connection manager for the SAP BW source. On this page, you also select the execution mode and the parameters for extracting the data from the SAP Netweaver BW system.  
  
 To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](../../Topics\TopicNameNotContainA/SAP-BW-Source.md).  
  
> [!IMPORTANT]  
>  The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment. For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.  
  
> [!IMPORTANT]  
>  Extracting data from SAP Netweaver BW requires additional SAP licensing. Check with SAP to verify these requirements.  
  
 **To open the Connection Manager page**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package that contains the SAP BW source.  
  
2.  On the **Data Flow** tab, double\-click the SAP BW source.  
  
3.  In the **SAP BW Source Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.  
  
## Static Options  
  
> [!NOTE]  
>  If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.  
  
 **SAP BW connection manager**  
 Select an existing connection manager from the list, or create a new connection by clicking **New**.  
  
 **New**  
 Create a new connection manager by using the **SAP BW Connection Manager** dialog box.  
  
 For more information about this dialog box, see [SAP BW Connection Manager Editor](../../Topics\TopicNameNotContainA/SAP-BW-Connection-Manager-Editor.md).  
  
 **OHS destination**  
 Select the Open Hub Service \(OHS\) destination to use to extract data from the source.  
  
 **Execution mode**  
 Specify the method for extracting data from the source.  
  
|Option|Description|  
|------------|-----------------|  
|**P \- Trigger Process Chain**|Trigger a process chain. In this case, the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package starts the extraction process.|  
|**W \- Wait for Notify**|Wait for notification from the SAP Netweaver BW system to begin extracting the data. In this case, the SAP Netweaver BW system starts the extraction process.|  
|**E \- Extract Only**|Retrieve the data that is associated with a particular Request ID. In this case, the SAP Netweaver BW system has already extracted the data into an internal table, and the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package just reads the data.|  
  
 **Preview**  
 Open the **Preview** dialog box in which you can preview results. For more information, see [Preview](../../Topics\TopicNameNotContainA/Preview.md).  
  
> [!IMPORTANT]  
>  The **Preview** option, that is available on the **Connection Manager** page of the SAP BW Source Editor, actually extracts data. If you have configured SAP Netweaver BW to extract only data that has changed since the previous extraction, selecting **Preview** will exclude the previewed data from the next extraction.  
  
 When you click **Preview**, you also open the **Request Log** dialog box. You can use this dialog box to view the events that are logged during the request that is made to the SAP Netweaver BW system for sample data. For more information, see [Request Log](../../Topics\TopicNameNotContainA/Request-Log.md).  
  
## Execution Mode Dynamic Options  
  
> [!NOTE]  
>  If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.  
  
### Execution Mode \= P \- Trigger Process Chain  
  
#### RFC Destination Options  
 You do not have to know and enter these values in advance. Use the **Look up** button to find and select the appropriate RFC destination. After you select an RFC destination, the component enters the appropriate values for these options.  
  
 **Gateway host**  
 Enter the server name or IP address of the gateway host. Usually, the name or IP address is the same as the SAP application server.  
  
 **Gateway service**  
 Enter the name of the gateway service, in the format **sapgwNN**, where **NN** is the system number.  
  
 **Program ID**  
 Enter the Program ID that is associated with the RFC destination.  
  
 **Look up**  
 Look up the RFC destination by using the **Look Up RFC Destination** dialog box. For more information about this dialog box, see [Look Up RFC Destination](../../Topics\TopicNameNotContainA/Look-Up-RFC-Destination.md).  
  
#### Process Chain Options  
 You do not have to know and enter these values in advance. Use the **Look up** button to find and select the appropriate process chain. After you select a process chain, the component enters the appropriate value for the option.  
  
 **Process chain**  
 Enter the name of the process chain to be triggered by the source.  
  
 **Look up**  
 Look up the process chain by using the **Look Up Process Chain** dialog box. For more information about this dialog box, see [Look Up Process Chain](../../Topics\TopicNameNotContainA/Look-Up-Process-Chain.md).  
  
### Execution Mode \= W \- Wait for Notify  
  
#### RFC Destination Options  
 You do not have to know and enter these values in advance. Use the **Look up** button to find and select the appropriate RFC destination. After you select an RFC destination, the component enters the appropriate values for the options.  
  
 **Gateway host**  
 Enter the server name or IP address of the gateway host. Usually, the name or IP address is the same as the SAP application server.  
  
 **Gateway service**  
 Enter the name of the gateway service, in the format **sapgwNN**, where **NN** is the system number.  
  
 **Program ID**  
 Enter the Program ID that is associated with the RFC destination.  
  
 **Look up**  
 Look up the RFC destination by using the **Look Up RFC Destination** dialog box. For more information about this dialog box, see [Look Up RFC Destination](../../Topics\TopicNameNotContainA/Look-Up-RFC-Destination.md).  
  
### Execution Mode \= E \- Extract Only  
 **Request ID**  
 Enter the Request ID that is associated with the extraction.  
  
## See Also  
 [SAP BW Source Editor &#40;Columns Page&#41;](../Topic/SAP%20BW%20Source%20Editor%20\(Columns%20Page\).md)   
 [SAP BW Source Editor &#40;Error Output Page&#41;](../Topic/SAP%20BW%20Source%20Editor%20\(Error%20Output%20Page\).md)   
 [SAP BW Source Editor &#40;Advanced Page&#41;](../Topic/SAP%20BW%20Source%20Editor%20\(Advanced%20Page\).md)   
 [Microsoft Connector for SAP BW F1 Help](../../Topics\TopicNameNotContainA/Microsoft-Connector-for-SAP-BW-F1-Help.md)  
  
  