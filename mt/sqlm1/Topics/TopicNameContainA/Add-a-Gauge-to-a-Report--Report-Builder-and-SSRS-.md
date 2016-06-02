---
title: Add a Gauge to a Report (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45da4fef-2b02-40e1-977c-f8f80d87155e
---
# Add a Gauge to a Report (Report Builder and SSRS)
  In a [!INCLUDE[ssRSnoversion_md](../../Token\Other/ssRSnoversion_md.md)] paginated report, when you want to summarize data in a visual format, you can use a gauge data region. After you add a gauge data region to the design surface, you can drag report dataset fields to a data pane on the gauge.  
  
## To add a gauge to your report  
  
1.  Create a report or open an existing report.  
  
2.  On the Insert tab, double\-click Gauge. The **Select Gauge Type** dialog box opens.  
  
3.  Select the type of gauge you want to add. [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
    > [!NOTE]  
    >  Unlike charts, gauges have only two types: linear and radial. The available gauges in the **Select a Gauge Type** dialog box are templates for these two types of gauges. For this reason, you cannot change the gauge type after you add the gauge to your report. You must delete and re\-add a gauge to change its type.  
  
     If the report has no data source and dataset the **Data Source Properties** dialog box opens and takes you through the steps to create both. For more information see, [Add and Verify a Data Connection &#40;Report Builder and SSRS&#41;](../Topic/Add%20and%20Verify%20a%20Data%20Connection%20\(Report%20Builder%20and%20SSRS\).md).  
  
     If the report has a data source, but no dataset the **Dataset Properties** dialog box opens and takes you through the steps to create one. For more information, see [Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](../Topic/Create%20a%20Shared%20Dataset%20or%20Embedded%20Dataset%20\(Report%20Builder%20and%20SSRS\).md).  
  
4.  Click the gauge to display the data pane. By default, a gauge has one pointer corresponding to one value. You can add additional pointers.  
  
5.  Add one field from the dataset to the data field drop\-zone. You can add only one field. If you want to display multiple fields, you must add additional pointers, one for each field.  
  
     Right\-click the gauge scale, and select **Scale Properties**. Type a value for the **Minimum** and **Maximum** of the scale. For more information, see [Set a Minimum or Maximum on a Gauge &#40;Report Builder and SSRS&#41;](../Topic/Set%20a%20Minimum%20or%20Maximum%20on%20a%20Gauge%20\(Report%20Builder%20and%20SSRS\).md).  
  
## See Also  
 [Nested Data Regions &#40;Report Builder and SSRS&#41;](../Topic/Nested%20Data%20Regions%20\(Report%20Builder%20and%20SSRS\).md)   
 [Gauges &#40;Report Builder and SSRS&#41;](../Topic/Gauges%20\(Report%20Builder%20and%20SSRS\).md)  
  
  