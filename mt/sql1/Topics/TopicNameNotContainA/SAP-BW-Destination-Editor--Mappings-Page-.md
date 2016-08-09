---
title: "SAP BW Destination Editor (Mappings Page)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dfa1f1d6-6b64-4331-bdc5-eaa8b7aa41a1
caps.latest.revision: 11
caps.handback.revision: 0
manager: jhubbard
---
# SAP BW Destination Editor (Mappings Page)
Use the **Mappings** page of the **SAP BW Destination Editor** to map input columns to destination columns.  
  
 To learn more about the SAP BW destination of the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Connector 1.1 for SAP BW, see [SAP BW Destination](../../Topics/TopicNameNotContainA/SAP-BW-Destination.md).  
  
> [!IMPORTANT]  
>  The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment. For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.  
  
 **To open the Mappings page**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] package that contains the SAP BW destination.  
  
2.  On the **Data Flow** tab, double-click the SAP BW destination.  
  
3.  In the **SAP BW Destination Editor**, click **Mappings** to open the **Mappings** page of the editor.  
  
## Options  
  
> [!NOTE]  
>  If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.  
  
 The **Mappings** page of the **SAP BW Destination Editor consists** of two sections:  
  
-   The upper section shows the available input and destination columns and lets you create mappings between these two types of columns.  
  
-   The lower section is a table that lists which input columns have been mapped to which output columns.  
  
### Upper Section Options  
 The upper section has the following options:  
  
 **Available Input Columns**  
 View the list of available input columns.  
  
 To map an input column to a destination column, drag a column from the **Available Input Columns** list and drop that column onto a column in the **Available Destination Columns** list.  
  
 **Available Destination Columns**  
 View the list of available destination columns.  
  
 To map an input column to destination column, drag a column from the **Available Input Columns** list and drop that column onto a column in the **Available Destination Columns** list.  
  
 The upper section also has a context menu that you can open by right-clicking on the background. This context menu contains the following options:  
  
-   **Select All Mappings**  
  
-   **Delete Selected Mappings**  
  
-   **Map Items by Matching Names**  
  
### Lower Section Columns  
 The lower section is a table of the mappings, and has the following columns:  
  
 **Input Column**  
 View the input columns that you have selected.  
  
 To map a different input column to the same destination column, select a different input column in the list. To remove a mapping, select **<ignore\>** to exclude the input column from the output.  
  
 **Destination Column**  
 View each available destination column, regardless of whether that column is mapped or not.  
  
## See Also  
 [SAP BW Destination Editor (Connection Manager Page)](../../Topics/TopicNameNotContainA/SAP-BW-Destination-Editor--Connection-Manager-Page-.md)   
 [SAP BW Destination Editor (Error Output Page)](../../Topics/TopicNameNotContainA/SAP-BW-Destination-Editor--Error-Output-Page-.md)   
 [SAP BW Destination Editor (Advanced Page)](../../Topics/TopicNameNotContainA/SAP-BW-Destination-Editor--Advanced-Page-.md)   
 [Microsoft Connector for SAP BW F1 Help](../../Topics/TopicNameNotContainA/Microsoft-Connector-for-SAP-BW-F1-Help.md)