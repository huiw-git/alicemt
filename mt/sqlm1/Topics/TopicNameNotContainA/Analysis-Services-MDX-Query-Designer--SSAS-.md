---
title: Analysis Services MDX Query Designer (SSAS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a2fb0b79-802a-4dac-bd9a-32dfe2e8c4d4
---
# Analysis Services MDX Query Designer (SSAS)
  The Analysis Services Multidimensional Expression \(MDX\) query designer provides a graphical user interfaces to help you create MDX queries for a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] data source. The MDX graphical query designer has two modes: design mode and query mode. Each mode provides a metadata pane from which you can drag members from the selected cubes to build an MDX query that retrieves the data you want to use.  
  
> [!IMPORTANT]  
>  Users access data sources when they create and run queries. You should grant minimal permissions on the data sources, such as read\-only permissions.  
>   
>  The credentials of the current user, not the credentials specified in the Impersonation Information page, are used to connect to the data source when a query is executed.  
  
 The following sections describe the toolbar buttons and query designer panes for each mode of the graphical query designer.  
  
## Graphical MDX Query Designer in Design Mode  
 When you edit an MDX query, the graphical MDX query designer opens in Design mode.  
  
 The following figure labels the panes for Design mode.  
  
 ![Analysis Services MDX query designer, design view](../../Images\Image\ImageNotContaina/rsQD_DSAWAS_MDX_DesignMode.gif "rsQD_DSAWAS_MDX_DesignMode")  
  
 The following table lists the panes in this mode:  
  
|Pane|Function|  
|----------|--------------|  
|Select Cube button \(**...**\)|Displays the currently selected cube.|  
|Metadata pane|Displays a hierarchical list of measures, Key Performance Indicators \(KPIs\), and dimensions defined on the selected cube.|  
|Calculated Members pane|Displays the currently defined calculated members available for use in the query.|  
|Filter pane|Use to choose dimensions and related hierarchies to filter data at the source and limit data returned.|  
|Data pane|Displays the column headings for the result set as you drag items from the Metadata pane and the Calculated Members pane. Automatically updates the result set if the **AutoExecute** button is selected.|  
  
 You can drag dimensions, measures, and KPIs from the Metadata pane, and calculated members from the Calculated Member pane, onto the Data pane. In the Filter pane, you can select dimensions and related hierarchies, and set filter expressions to limit the data available to query. If the **AutoExecute** \(![AutoExecute the query](../../Images\Image\ImageNotContaina/rsQDIcon_AutoExecute.gif "rsQDIcon_AutoExecute")\) toggle button on the toolbar is selected, the query designer runs the query every time that you drop a metadata object onto the Data pane. You can manually run the query using the **Run** \(![Run the query](../../Images\Image\ImageNotContaina/rsQDIcon_Run.gif "rsQDIcon_Run")\) button on the toolbar.  
  
 When you create an MDX query in this mode, the following additional properties are automatically included in the query:  
  
 **Member Properties** MEMBER\_CAPTION, MEMBER\_UNIQUE\_NAME  
  
 **Cell Properties** VALUE, BACK\_COLOR, FORE\_COLOR, FORMATTED\_VALUE, FORMAT\_STRING, FONT\_NAME, FONT\_SIZE, FONT\_FLAGS  
  
 To specify your own additional properties, you must manually edit the MDX query in Query mode.  
  
 Importing an .mdx query from a file is not supported.  
  
> [!NOTE]  
>  For more information about MDX and general information about the MDX query designer, see "MDX Query Editor \(Analysis Services \- Multidimensional Data\)" in [SQL Server Books Online](http://go.microsoft.com/fwlink/?linkid=98335).  
  
### Graphical MDX Query Designer Toolbar in Design Mode  
 The query designer toolbar provides buttons to help you design MDX queries using the graphical interface. The following table lists the buttons and their functions.  
  
|Button|Description|  
|------------|-----------------|  
|**Edit As Text**|Not enabled for this data source type.|  
|**Import**|Import an existing query from a report definition \(.rdl\) file on the file system.|  
|![Change to MDX query view](../../Images\Image\ImageNotContaina/rsQDIcon_CommandTypeMDX.gif "rsQDIcon_CommandTypeMDX")|Switch to Command Type MDX.|  
|![Refresh result data](../../Images\Image\ImageNotContaina/rsQDIcon_Refresh.gif "rsQDIcon_Refresh")|Refresh metadata from the data source.|  
|![Add calculated member](../../Images\Image\ImageNotContaina/rsQDIcon_AddCalculatedMember.gif "rsQDIcon_AddCalculatedMember")|Display the **Calculated Member Builder** dialog box.|  
|![Toggle for show empty cells](../../Images\Image\ImageNotContaina/rsQDIcon_ShowEmptyCells.gif "rsQDIcon_ShowEmptyCells")|Toggle between showing and not showing empty cells in the Data pane. \(This is the equivalent to using the NON EMPTY clause in MDX\).|  
|![AutoExecute the query](../../Images\Image\ImageNotContaina/rsQDIcon_AutoExecute.gif "rsQDIcon_AutoExecute")|Automatically run the query and show the result every time a change is made. Results are shown in the Data pane.|  
|![Show Aggregations button](../../Images\Image\ImageNotContaina/rsQDIcon_ShowAggregations.gif "rsQDIcon_ShowAggregations")|Show aggregations in the Data pane.|  
|![Delete](../../Images\Image\ImageNotContaina/rsQDIcon_Delete.gif "rsQDIcon_Delete")|Delete the selected column in the Data pane from the query.|  
|![Icon for the Query Parameters dialog box](../../Images\Image\ImageNotContaina/IconQueryParameter.gif "IconQueryParameter")|Display the **Query Parameters** dialog box. When you specify values for a query parameter, a parameter with the same name is automatically created.|  
|![Prepare Query button](../../Images\Image\ImageNotContaina/rsQDIcon_PrepareQuery.gif "rsQDIcon_PrepareQuery")|Prepare the query.|  
|![Run the query](../../Images\Image\ImageNotContaina/rsQDIcon_Run.gif "rsQDIcon_Run")|Run the query and display the results in the Data pane.|  
|![Cancel the query](../../Images\Image\ImageNotContaina/rsQDIcon_Cancel.gif "rsQDIcon_Cancel")|Cancel the query.|  
|![Switch to Design mode](../../Images\Image\ImageNotContaina/rsQDIcon_DesignMode.gif "rsQDIcon_DesignMode")|Toggle between Design mode and Query mode.|  
  
## Graphical MDX Query Designer in Query Mode  
 To change the graphical query designer to **Query** mode, click the **Design Mode** button on the toolbar.  
  
 The following figure labels the panes for Query mode.  
  
 ![Analysis Services MDX query designer, query view](../../Images\Image\ImageNotContaina/rsQD_DSAWAS_MDX_QueryMode.gif "rsQD_DSAWAS_MDX_QueryMode")  
  
 The following table lists the panes in this mode:  
  
|Pane|Function|  
|----------|--------------|  
|Select Cube button \(**...**\)|Displays the currently selected cube.|  
|Metadata\/Functions\/Templates pane|Displays a hierarchical list of measures, KPIs, and dimensions defined on the selected cube.|  
|Query pane|Displays the query text.|  
|Result pane|Displays the results of running the query.|  
  
 The Metadata pane displays tabs for **Metadata**, **Functions**, and **Templates**. From the **Metadata** tab, you can drag dimensions, hierarchies, KPIs, and measures onto the MDX Query pane. From the **Functions** tab, you can drag functions onto the MDX Query pane. From the **Templates** tab, you can add MDX templates to the MDX Query pane. When you execute the query, the Result pane displays the results for the MDX query.  
  
 You can extend the default MDX query generated in Design mode to include additional member properties and cell properties. When you run the query, these values do not appear in the result set. However, they are passed back with the dataset field collection and you can use these values.  
  
### Graphical Query Designer Toolbar in Query Mode  
 The query designer toolbar provides buttons to help you design MDX queries using the graphical interface.  
  
 The toolbar buttons are identical between Design mode and Query mode, but the following buttons are not enabled for Query mode:  
  
-   **Edit As Text**  
  
-   **Add Calculated Member** \(![Add calculated member](../../Images\Image\ImageNotContaina/rsQDIcon_AddCalculatedMember.gif "rsQDIcon_AddCalculatedMember")\)  
  
-   **Show Empty Cells** \(![Toggle for show empty cells](../../Images\Image\ImageNotContaina/rsQDIcon_ShowEmptyCells.gif "rsQDIcon_ShowEmptyCells")\)  
  
-   **AutoExecute** \(![AutoExecute the query](../../Images\Image\ImageNotContaina/rsQDIcon_AutoExecute.gif "rsQDIcon_AutoExecute")\)  
  
-   **Show Aggregations** \(![Show Aggregations button](../../Images\Image\ImageNotContaina/rsQDIcon_ShowAggregations.gif "rsQDIcon_ShowAggregations")\)  
  
  