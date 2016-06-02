---
title: Analyze in Excel (Browser Tab, Cube Designer) (Analysis Services - Multidimensional Data)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 890ed457-137e-44ac-9b2c-83344a1b8fc9
---
# Analyze in Excel (Browser Tab, Cube Designer) (Analysis Services - Multidimensional Data)
  **Analyze in Excel** provides the cube developer with a way to quickly review how a project would look to the end user. The **Analyze in Excel** feature opens Microsoft Excel, creates a data source connection to the workspace database, and automatically adds a PivotTable to the worksheet. This feature replaces the Office Web Control that provided an embedded PivotTable in the Browser tab in previous releases.  
  
 **To view cube data:**  
  
1.  In [!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)], in Solution Explorer, double\-click a cube to open it in Cube Designer.  
  
2.  Click the **Browser** tab.  
  
3.  Click **Reconnect** to validate the connection.  
  
4.  Click the Excel icon in the menu bar.  
  
5.  When asked to enable data connections, click **Enable**. Excel opens using the current data connection, adding a PivotTable to the worksheet so that you can begin browsing your data.  
  
 You can now build a PivotTable interactively by dragging measures from the fact table to the Values area, and dimension attributes to the Row and Column areas. If you have hierarchies, add them to Rows or Column areas. You can roll up or drill down the hierarchy to browse fact data at different levels.  
  
 Objects and data are viewed within the context of the effective user or role and perspective. When using Excel, the credentials of the current user, not the credentials specified in the **Impersonation Information** page, are used to connect to the data source when a query is executed.  
  
> [!NOTE]  
>  To use the Analyze in Excel feature, Excel must be installed on the same computer as [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)]. If Excel is not installed on the same computer, you can use Excel on another computer and connect to the cube as a data source. You can then manually add a PivotTable to the worksheet. Model objects \(tables, columns, measures, and KPIs\) are included as fields in the PivotTable field list.  
  
 For more information about the **Analyze in Excel** feature, see these resources:  
  
 [Analyze in Excel &#40;SSAS Tabular&#41;](../Topic/Analyze%20in%20Excel%20\(SSAS%20Tabular\).md)  
  
 [Analyze a Tabular Model in Excel &#40;SSAS Tabular&#41;](../Topic/Analyze%20a%20Tabular%20Model%20in%20Excel%20\(SSAS%20Tabular\).md)  
  
 [Browse data and metadata in Cube](../../Topics\TopicNameNotContainA/Browse-data-and-metadata-in-Cube.md)  
  
## See Also  
 [Browser &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Browser%20\(Cube%20Designer\)%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Toolbar &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Toolbar%20\(Browser%20Tab,%20Cube%20Designer\)%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Metadata &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Metadata%20\(Browser%20Tab,%20Cube%20Designer\)%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Query and Filter &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Query%20and%20Filter%20\(Browser%20Tab,%20Cube%20Designer\)%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
  