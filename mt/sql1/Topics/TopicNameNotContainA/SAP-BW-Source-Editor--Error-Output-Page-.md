---
title: "SAP BW Source Editor (Error Output Page)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b6e23b0c-949a-46d1-8424-4dc3d9035e79
caps.latest.revision: 11
caps.handback.revision: 0
manager: jhubbard
---
# SAP BW Source Editor (Error Output Page)
Use the **Error Output** page of the **SAP BW Source Editor** to select error handling options and to set properties on error output columns.  
  
 To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](../../Topics/TopicNameNotContainA/SAP-BW-Source.md).  
  
> [!IMPORTANT]  
>  The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment. For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.  
  
> [!IMPORTANT]  
>  Extracting data from SAP Netweaver BW requires additional SAP licensing. Check with SAP to verify these requirements.  
  
 **To open the Error Output page**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] package that contains the SAP BW source.  
  
2.  On the **Data Flow** tab, double-click the SAP BW source.  
  
3.  In the **SAP BW Source Editor**, click **Error Output** to open the **Error Output** page of the editor.  
  
## Options  
  
> [!NOTE]  
>  If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.  
  
 **Input or Output**  
 View the name of the data source.  
  
 **Column**  
 View the external (source) columns that you selected on the **Columns** page of the **SAP BW Source Editor** dialog box. For more information about this dialog box, see [SAP BW Source Editor (Columns Page)](../../Topics/TopicNameNotContainA/SAP-BW-Source-Editor--Columns-Page-.md).  
  
 **Error**  
 Specify what the SAP BW source component should do when there is an error: ignore the failure, redirect the row, or fail the component.  
  
 **Truncation**  
 Specify what the SAP BW source component should do when a truncation occurs: ignore the failure, redirect the row, or fail the component.  
  
 **Description**  
 View the description of the error.  
  
 **Set this value to selected cells**  
 Specify what the SAP BW source component should do to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.  
  
 **Apply**  
 Apply the error handling option to the selected cells.  
  
## See Also  
 [SAP BW Source Editor (Connection Manager Page)](../../Topics/TopicNameNotContainA/SAP-BW-Source-Editor--Connection-Manager-Page-.md)   
 [SAP BW Source Editor (Columns Page)](../../Topics/TopicNameNotContainA/SAP-BW-Source-Editor--Columns-Page-.md)   
 [SAP BW Source Editor (Advanced Page)](../../Topics/TopicNameNotContainA/SAP-BW-Source-Editor--Advanced-Page-.md)   
 [Microsoft Connector for SAP BW F1 Help](../../Topics/TopicNameNotContainA/Microsoft-Connector-for-SAP-BW-F1-Help.md)