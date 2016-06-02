---
title: View Spatial Data in Object Explorer
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 59cca562-e3f5-4257-b868-adcbcc0142cc
---
# View Spatial Data in Object Explorer
  The **Spatial results** window in Query Editor provides visual mapping tools for viewing spatial data results in addition to the data displayed in grid format in the **Results** window. To display spatial data in the **Spatial Results** window, your query results must contain at least one spatial data column with either geometry or geography data.  
  
### To view spatial data in the Spatial results window  
  
1.  In Query Editor, click the **Spatial results** tab.  
  
    > [!NOTE]  
    >  This window is not available if your query results do not contain spatial data or if you specify that your results are returned as text.  
  
2.  Select the column you want to view from the **Select spatial column** list. If there is only one spatial column in your table, this column is the default option in the list.  
  
3.  Select the non\-spatial column you want to use as data labels from the **Select label columns** list.  
  
4.  Select the projection you want for geography data from the **Select projection** list. The default projection is Equirectangular; other projections available are Mercator, Robinson, or Bonne.  
  
    > [!NOTE]  
    >  **Select projection** is not available if your spatial column contains geometry data.  
  
5.  Adjust the **Zoom** slider to increase the visual size of mapped elements. For polygon shapes, the label is visible only when the shape is large enough to hold the label text.  
  
## See Also  
 [Spatial Results Window](../../Topics\TopicNameNotContainA/Spatial-Results-Window.md)   
 [Database Engine Query Editor &#40;SQL Server Management Studio&#41;](../Topic/Database%20Engine%20Query%20Editor%20\(SQL%20Server%20Management%20Studio\).md)   
 [Query and Text Editors &#40;SQL Server Management Studio&#41;](../Topic/Query%20and%20Text%20Editors%20\(SQL%20Server%20Management%20Studio\).md)  
  
  