---
title: Hyperion Essbase Query Designer User Interface
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bc91b422-c6ab-4062-a300-8290fae6191b
---
# Hyperion Essbase Query Designer User Interface
  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] provides a graphical query designer for building Multidimensional Expression \(MDX\) queries for a [!INCLUDE[extEssbase](../../Token\Other/extEssbase_md.md)] data source. The MDX graphical query designer has two modes: Design mode and Query mode. Each mode provides a Metadata pane from which you can drag members from a cube defined on the data source to build an MDX query that retrieves data when the report is processed.  
  
> [!IMPORTANT]  
>  Users access data sources when they create and run queries. You should grant minimal permissions on the data sources, such as read\-only permissions.  
  
 For more information about working with a [!INCLUDE[extEssbase](../../Token\Other/extEssbase_md.md)] multidimensional data source, see [Hyperion Essbase Connection Type &#40;SSRS&#41;](../Topic/Hyperion%20Essbase%20Connection%20Type%20\(SSRS\).md).  
  
 This section describes the toolbar buttons and query designer panes for each mode of the graphical query designer.  
  
## Graphical Query Designer in Design Mode  
 When you edit an MDX query for a dataset that uses a [!INCLUDE[extEssbase](../../Token\Other/extEssbase_md.md)] data source, the graphical query designer opens in Design mode.  
  
 The following figure labels the panes for Design mode.  
  
 ![Query Designer for Hyperion Essbase data source](../../Images\Image\ImageNotContaina/rsQD_DSHyperionEssbase_MDX_DesignMode.gif "rsQD_DSHyperionEssbase_MDX_DesignMode")  
  
 The following table lists the panes in this mode.  
  
|Pane|Function|  
|----------|--------------|  
|Select Cube button|Displays the currently selected cube.|  
|Metadata pane|Displays a hierarchical list of cubes.|  
|Calculated Members pane|Displays the currently defined calculated members available for use in the query.|  
|Filter pane|Displays the filters to apply in the query.|  
|Data pane|Displays the results of running the query.|  
  
 You can drag dimensions and measures from the Metadata pane, and calculated members from the Calculated Member pane onto the Data pane. If the **AutoExecute** toggle button on the toolbar is on, the query designer runs the query every time you drop an object onto the Data pane. If **AutoExecute** is off, the query designer does not run the query as you make changes to the Data pane. You can manually run the query using the **Run** button on the toolbar.  
  
 In the Filter pane, you can select dimension values to limit the data retrieved from the data source. Values you define in the filter in Design mode appear in the MDX Where clause in Query mode.  
  
### Toolbar for the Graphical Query Designer in Design Mode Toolbar  
 The query designer toolbar provides buttons to help you design MDX queries using the graphical interface. The following table shows the buttons and describes their functions.  
  
|Button|Description|  
|------------|-----------------|  
|**Edit As Text**|Toggle between the text\-based query designer and the graphical query designer. Not available for this data source type.|  
|**Import**|Import an existing query from a report definition \(.rdl\) file on the file system. For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../Topic/Report%20Embedded%20Datasets%20and%20Shared%20Datasets%20\(Report%20Builder%20and%20SSRS\).md).|  
|![Refresh dataset fields](../../Images\Image\ImageNotContaina/rsQDIcon_RefreshFields.gif "rsQDIcon_RefreshFields")|Refresh metadata from the data source.|  
|![Add calculated member](../../Images\Image\ImageNotContaina/rsQDIcon_AddCalculatedMember.gif "rsQDIcon_AddCalculatedMember")|Display the **Calculated Member Builder** dialog box. Use this to create or edit expressions for a calculated member, including setting the **Solve Order** property.|  
|![Toggle for show empty cells](../../Images\Image\ImageNotContaina/rsQDIcon_ShowEmptyCells.gif "rsQDIcon_ShowEmptyCells")|Switch between showing and not showing empty cells in the Data pane. \(This is the equivalent to using the NON EMPTY clause in MDX\).|  
|![AutoExecute the query](../../Images\Image\ImageNotContaina/rsQDIcon_AutoExecute.gif "rsQDIcon_AutoExecute")|Automatically run the query and show the result every time a change is made, for example, deleting a column in the Data pane. Results are shown in the Data pane.|  
|![Delete](../../Images\Image\ImageNotContaina/rsQDIcon_Delete.gif "rsQDIcon_Delete")|Delete the selected item from the query. Use this button to delete selected rows in the Filter pane.|  
|![Run the query](../../Images\Image\ImageNotContaina/rsQDIcon_Run.gif "rsQDIcon_Run")|Run the query and display the results in the Data pane.|  
|![Cancel the query](../../Images\Image\ImageNotContaina/rsQDIcon_Cancel.gif "rsQDIcon_Cancel")|Cancel the query.|  
|![Switch to Design mode](../../Images\Image\ImageNotContaina/rsQDIcon_DesignMode.gif "rsQDIcon_DesignMode")|Switch between Design mode and Query mode.|  
  
## Graphical Query Designer in Query Mode  
 To change the graphical query designer to Query mode, click the **Design Mode** toggle button on the toolbar. The following figure indicates the parts of the query designer in Query mode.  
  
 ![Query Designer in Query Mode for Hyperion](../../Images\Image\ImageNotContaina/rsQD_HyperionEssbase_MDX_QueryMode.gif "rsQD_HyperionEssbase_MDX_QueryMode")  
  
 The following table describes the function of each pane.  
  
|Pane|Function|  
|----------|--------------|  
|Select Cube button|Displays the currently selected cube.|  
|Metadata\/Functions pane|Displays a tabbed window that shows a list of available metadata or functions that can be used to build the query text.|  
|Query pane|Displays the current query text.|  
|Result pane|Displays the results of the query.|  
  
 From the Metadata pane, you can drag measures and dimensions from the **Metadata** tab onto the MDX Query pane. You can drag functions from the **Functions** tab onto the MDX Query pane. When you execute the query, the Result pane displays the results for the current MDX query.  
  
### Toolbar for the Graphical Query Designer in Query Mode  
 The query designer toolbar provides buttons to help you design MDX queries using the graphical interface. The toolbar buttons are identical between Design mode and Query mode, but the following buttons are not enabled for Query mode:  
  
-   **Edit As Text**  
  
-   **Add Calculated Member** \(![Add calculated member](../../Images\Image\ImageNotContaina/rsQDIcon_AddCalculatedMember.gif "rsQDIcon_AddCalculatedMember")\)  
  
-   **Show Empty Cells** \(![Toggle for show empty cells](../../Images\Image\ImageNotContaina/rsQDIcon_ShowEmptyCells.gif "rsQDIcon_ShowEmptyCells")\)  
  
-   **AutoExecute** \(![AutoExecute the query](../../Images\Image\ImageNotContaina/rsQDIcon_AutoExecute.gif "rsQDIcon_AutoExecute")\)  
  
## See Also  
 [Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](../Topic/Create%20a%20Shared%20Dataset%20or%20Embedded%20Dataset%20\(Report%20Builder%20and%20SSRS\).md)   
 [RSReportDesigner Configuration File](../../Topics\TopicNameNotContainA/RSReportDesigner-Configuration-File.md)  
  
  