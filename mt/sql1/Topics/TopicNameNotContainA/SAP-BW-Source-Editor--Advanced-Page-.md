---
title: "SAP BW Source Editor (Advanced Page)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 44f3c991-9e8f-4126-a9a2-2d9da779fb11
caps.latest.revision: 11
caps.handback.revision: 0
manager: jhubbard
---
# SAP BW Source Editor (Advanced Page)
Use the **Advanced** page of the **SAP BW Source Editor** to specify the string conversion rule and the time-out period, and also to reset the status of a particular Request ID.  
  
 To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](../../Topics/TopicNameNotContainA/SAP-BW-Source.md).  
  
> [!IMPORTANT]  
>  The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment. For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.  
  
> [!IMPORTANT]  
>  Extracting data from SAP Netweaver BW requires additional SAP licensing. Check with SAP to verify these requirements.  
  
 **To open the Connection Manager page**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] package that contains the SAP BW source.  
  
2.  On the **Data Flow** tab, double-click the SAP BW source.  
  
3.  In the **SAP BW Source Editor**, click **Advanced** to open the **Advanced** page of the editor.  
  
## Options  
  
> [!NOTE]  
>  If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.  
  
 **String Conversion**  
 Specify the rule to apply for string conversion.  
  
|Option|Description|  
|------------|-----------------|  
|**Automatic string conversion**|Convert all strings to **nvarchar** when the SAP Netweaver BW system is a Unicode system. Otherwise, convert all strings to **varchar**.|  
|**Convert strings to varchar**|Convert all strings to **varchar**.|  
|**Convert strings to nvarchar**|Convert all strings to **nvarchar**.|  
  
 **Timeout (seconds)**  
 Specify the maximum number of seconds that the source should wait.  
  
> [!NOTE]  
>  This option is only valid if you have selected **W - Wait for Notify** as the value of **Execution Mode** on the **Connection Manager** page of the editor. For more information, see [SAP BW Source Editor (Connection Manager Page)](../../Topics/TopicNameNotContainA/SAP-BW-Source-Editor--Connection-Manager-Page-.md).  
  
 **Request ID**  
 Specify the Request ID whose status you want to reset to "G - Green" when you click **Reset**.  
  
 **Reset**  
 Lets you reset the status of the specified Request ID to "G - Green", after prompting you for confirmation. This can be useful when a problem has occurred, and the SAP Netweaver BW system has flagged the request with a yellow or red status.  
  
## See Also  
 [SAP BW Source Editor (Connection Manager Page)](../../Topics/TopicNameNotContainA/SAP-BW-Source-Editor--Connection-Manager-Page-.md)   
 [SAP BW Source Editor (Columns Page)](../../Topics/TopicNameNotContainA/SAP-BW-Source-Editor--Columns-Page-.md)   
 [SAP BW Source Editor (Error Output Page)](../../Topics/TopicNameNotContainA/SAP-BW-Source-Editor--Error-Output-Page-.md)   
 [Microsoft Connector for SAP BW F1 Help](../../Topics/TopicNameNotContainA/Microsoft-Connector-for-SAP-BW-F1-Help.md)