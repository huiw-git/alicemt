---
title: SAP BW Destination Editor (Error Output Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a543d811-0bd2-4890-a0d3-f5fdcd4524b8
---
# SAP BW Destination Editor (Error Output Page)
  Use the **Error Output** page of the **SAP BW Destination Editor** to specify error handling options.  
  
 To learn more about the SAP BW destination of the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Connector 1.1 for SAP BW, see [SAP BW Destination](../../Topics\TopicNameNotContainA/SAP-BW-Destination.md).  
  
> [!IMPORTANT]  
>  The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment. For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.  
  
 **To open the Error Output page**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package that contains the SAP BW destination.  
  
2.  On the **Data Flow** tab, double\-click the SAP BW destination.  
  
3.  In the **SAP BW Destination Editor**, click **Error Output** to open the **Error Output** page of the editor.  
  
## Options  
  
> [!NOTE]  
>  If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.  
  
 **Input or Output**  
 View the name of the input.  
  
 **Column**  
 This option is not used.  
  
 **Error**  
 Specify what the destination should do when an error occurs: ignore the failure, redirect the row, or fail the component.  
  
 **Truncation**  
 This option is not used.  
  
 **Description**  
 View the description of the operation.  
  
 **Set this value to selected cells**  
 Specify what the destination should do to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.  
  
 **Apply**  
 Apply the error handling option to the selected cells.  
  
## See Also  
 [SAP BW Destination Editor &#40;Connection Manager Page&#41;](../Topic/SAP%20BW%20Destination%20Editor%20\(Connection%20Manager%20Page\).md)   
 [SAP BW Destination Editor &#40;Mappings Page&#41;](../Topic/SAP%20BW%20Destination%20Editor%20\(Mappings%20Page\).md)   
 [SAP BW Destination Editor &#40;Advanced Page&#41;](../Topic/SAP%20BW%20Destination%20Editor%20\(Advanced%20Page\).md)   
 [Microsoft Connector for SAP BW F1 Help](../../Topics\TopicNameNotContainA/Microsoft-Connector-for-SAP-BW-F1-Help.md)  
  
  