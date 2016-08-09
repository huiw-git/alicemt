---
title: "Analyze in Excel (Browser Tab, Cube Designer) (Analysis Services - Multidimensional Data)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 890ed457-137e-44ac-9b2c-83344a1b8fc9
caps.latest.revision: 24
caps.handback.revision: 0
manager: mblythe
---
# Analyze in Excel (Browser Tab, Cube Designer) (Analysis Services - Multidimensional Data)
**Analyze in Excel** provides the cube developer with a way to quickly review how a project would look to the end user. The **Analyze in Excel** feature opens Microsoft Excel, creates a data source connection to the workspace database, and automatically adds a PivotTable to the worksheet. This feature replaces the Office Web Control that provided an embedded PivotTable in the Browser tab in previous releases.  
  
 **To view cube data:**  
  
1.  In [!INCLUDE[ssBIDevStudio](../../Topics/TopicNameContainA/tokens/ssBIDevStudio_md.md)], in Solution Explorer, double-click a cube to open it in Cube Designer.  
  
2.  Click the **Browser** tab.  
  
3.  Click **Reconnect** to validate the connection.  
  
4.  Click the Excel icon in the menu bar.  
  
5.  When asked to enable data connections, click **Enable**. Excel opens using the current data connection, adding a PivotTable to the worksheet so that you can begin browsing your data.  
  
 You can now build a PivotTable interactively by dragging measures from the fact table to the Values area, and dimension attributes to the Row and Column areas. If you have hierarchies, add them to Rows or Column areas. You can roll up or drill down the hierarchy to browse fact data at different levels.  
  
 Objects and data are viewed within the context of the effective user or role and perspective. When using Excel, the credentials of the current user, not the credentials specified in the **Impersonation Information** page, are used to connect to the data source when a query is executed.  
  
> [!NOTE]  
>  To use the Analyze in Excel feature, Excel must be installed on the same computer as [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)]. If Excel is not installed on the same computer, you can use Excel on another computer and connect to the cube as a data source. You can then manually add a PivotTable to the worksheet. Model objects (tables, columns, measures, and KPIs) are included as fields in the PivotTable field list.  
  
 For more information about the **Analyze in Excel** feature, see these resources:  
  
 [Analyze in Excel (SSAS Tabular)](../../Topics/TopicNameNotContainA/Analyze-in-Excel--SSAS-Tabular-.md)  
  
 [Analyze a Tabular Model in Excel (SSAS Tabular)](../../Topics/TopicNameContainA/Analyze-a-Tabular-Model-in-Excel--SSAS-Tabular-.md)  
  
 [Browse data and metadata in Cube](../../Topics/TopicNameNotContainA/Browse-data-and-metadata-in-Cube.md)  
  
## See Also  
 [Browser (Cube Designer) (Analysis Services - Multidimensional Data)](../../Topics/TopicNameNotContainA/Browser--Cube-Designer---Analysis-Services---Multidimensional-Data-.md)   
 [Toolbar (Browser Tab, Cube Designer) (Analysis Services - Multidimensional Data)](../../Topics/TopicNameNotContainA/Toolbar--Browser-Tab--Cube-Designer---Analysis-Services---Multidimensional-Data-.md)   
 [Metadata (Browser Tab, Cube Designer) (Analysis Services - Multidimensional Data)](../../Topics/TopicNameNotContainA/Metadata--Browser-Tab--Cube-Designer---Analysis-Services---Multidimensional-Data-.md)   
 [Query and Filter (Browser Tab, Cube Designer) (Analysis Services - Multidimensional Data)](../../Topics/TopicNameNotContainA/Query-and-Filter--Browser-Tab--Cube-Designer---Analysis-Services---Multidimensional-Data-.md)