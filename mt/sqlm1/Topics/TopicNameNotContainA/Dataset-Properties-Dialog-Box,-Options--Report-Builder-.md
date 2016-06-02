---
title: Dataset Properties Dialog Box, Options (Report Builder)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 43e50133-45ef-47a2-b575-34dfcc28ec98
---
# Dataset Properties Dialog Box, Options (Report Builder)
  Select **Options** on the **DatasetProperties** dialog box to change data options, such as collation options and treating subtotals as detail data, for the query. For more information about collations, see [Collation and Unicode Support](../../Topics\TopicNameNotContainA/Collation-and-Unicode-Support.md) in [SQL Server Books Online](http://go.microsoft.com/fwlink/?linkid=98335).  
  
 Data options that are part of a shared dataset definition on the report server affect all reports that use the shared dataset. You can override options for the shared dataset after it is added to a report. These changes affect only the report in which they are defined.  
  
 Data options for an embedded dataset affect only the report in which they are defined.  
  
 For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../Topic/Report%20Embedded%20Datasets%20and%20Shared%20Datasets%20\(Report%20Builder%20and%20SSRS\).md).  
  
## Options  
 **Collation**  
 Select a locale that determines the collation sequence to be used for sorting data. **Default** indicates that the report server should attempt to derive the value from the data provider when the report runs. If the value cannot be derived, the default value is derived from the locale setting of the computer.  
  
 **Case sensitivity**  
 Select a value that determines case sensitivity. This option indicates whether the data is case\-sensitive. You can set **Case Sensitivity** to **True**, **False**, or **Auto**. The default value, **Auto**, indicates that the report server should attempt to derive the value from the data provider when the report runs. If the data provider does not support the case\-sensitivity type, the report runs as though the value were **False**. If you know the value and you know it is supported, choose **True**.  
  
 **Accent sensitivity**  
 Select a value that determines accent sensitivity. **Accent Sensitivity** indicates whether the data is accent sensitive and can be set to **True**, **False**, or **Auto**. The default value, **Auto**, indicates that the report server should attempt to derive the value from the data provider when the report is run. If the data provider does not support the accent sensitivity type, the report runs as though the value were **False**. If you know the value and you know it is supported, choose **True**.  
  
 **Kanatype sensitivity**  
 Select a value that determines kanatype sensitivity. This option indicates whether the data is kanatype sensitive; it can be set to **True**, **False**, or **Auto**. The default value, **Auto**, indicates that the report server should attempt to derive the value from the data provider when the report runs. If the data provider does not support the kanatype sensitivity type, the report runs as though the value were **False**. If you know the value and you know it is supported, choose **True**.  
  
 **Width sensitivity**  
 Select a value that determines width sensitivity. This option indicates whether the data is width\-sensitive and can be set to **True**, **False**, or **Auto**. The default value, **Auto**, indicates that the report server should attempt to derive the value from the data provider when the report runs. If the data provider does not support the width sensitivity type, the report runs as though the value were **False**. If you know the value and you know it is supported, choose **True**.  
  
 **Interpret subtotals as detail rows**  
 Select a value that indicates whether you want subtotal rows to be interpreted as detail rows instead of aggregate rows. The default value, **Auto**, indicates that the subtotal rows should be treated as detail rows if the report does not use the **Aggregate**\(\) function to access any fields in the data set. If you want subtotal rows to be interpreted as aggregate rows, choose **False**. If you want the subtotal rows to be interpreted as detail rows and you know that they do not use the **Aggregate**\(\) function, choose **True**.  
  
## See Also  
 [Report Builder Help for Dialog Boxes, Panes, and Wizards](assetId:///2da24891-0b6d-4d3c-8b18-81b98752642f)   
 [Aggregate Function &#40;Report Builder and SSRS&#41;](../Topic/Aggregate%20Function%20\(Report%20Builder%20and%20SSRS\).md)   
 [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../Topic/Filter,%20Group,%20and%20Sort%20Data%20\(Report%20Builder%20and%20SSRS\).md)   
 [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../Topic/Report%20Embedded%20Datasets%20and%20Shared%20Datasets%20\(Report%20Builder%20and%20SSRS\).md)   
 [Dataset Properties Dialog Box, Query &#40;Report Builder&#41;](../Topic/Dataset%20Properties%20Dialog%20Box,%20Query%20\(Report%20Builder\).md)  
  
  