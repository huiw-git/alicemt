---
title: Dataset Properties Dialog Box, Parameters (Report Builder)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3a0672ad-c969-455b-b952-585164ce1dda
robots: noindex,nofollow
---
# Dataset Properties Dialog Box, Parameters (Report Builder)
  Select **Parameters** on the **Dataset Properties** dialog box to add, change, and delete query parameters.  
  
 For an embedded dataset, options apply to the dataset in the report definition.  
  
 For a shared dataset, options apply to the shared dataset definition on the report server.  
  
 For more information, see [Embedded and Shared Datasets &#40;Report Builder and SSRS&#41;](../Topic/Embedded%20and%20Shared%20Datasets%20\(Report%20Builder%20and%20SSRS\).md).  
  
## Options  
 **Add**  
 Add a new parameter to the list.  
  
 **Delete**  
 Remove the selected parameter from the list.  
  
 **Up arrow**  
 Move the selected parameter up in the list.  
  
 **Down arrow**  
 Move the selected parameter down in the list.  
  
 **Parameter name**  
 Type the name of a query parameter that you added to the dataset on the **Query** tab of the **Dataset Properties** dialog box.  
  
 **Parameter value**  
 For embedded datasets only.  
  
 Enter a value for the query parameter. This can be a static value or an expression that refers to an object within the report, but it cannot refer to any report items or fields. By default, **Value** contains an expression that points to a report parameter.  
  
 **Default value**  
 For shared datasets only.  
  
 Select the check box to specify a default value.  
  
 Enter a default value. This can be a static value or an expression that refers to an object within the report. The expression cannot refer to report items, report parameters, or fields.  
  
 To specify a blank, leave the text box empty.  
  
 To specify a null, select the Nullable option.  
  
 **Read Only**  
 For shared datasets only.  
  
 Select this option to mark this parameter read only in the shared dataset definition. When the shared dataset is added to a report, the parameter does not appear in the properties. When the shared dataset is cached on the report server, the value cannot be changed.  
  
 **Nullable**  
 For shared datasets only.  
  
 Select this option to allow a null value.  
  
 **Omit From Query**  
 For shared datasets only.  
  
 Select this option when a reference to a report parameter is in an expression in the shared dataset filter and not in the query. When you select this option, you do not need to specify a default value for this parameter when the query runs.  
  
## See Also  
 [Report Builder Help for Dialog Boxes, Panes, and Wizards](assetId:///2da24891-0b6d-4d3c-8b18-81b98752642f)   
 [Dataset Properties Dialog Box, Query &#40;Report Builder&#41;](../Topic/Dataset%20Properties%20Dialog%20Box,%20Query%20\(Report%20Builder\).md)   
 [Expressions &#40;Report Builder and SSRS&#41;](../Topic/Expressions%20\(Report%20Builder%20and%20SSRS\).md)   
 [Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../Topic/Tutorial:%20Add%20a%20Parameter%20to%20Your%20Report%20\(Report%20Builder\).md)   
 [Report Parameters &#40;Report Builder and Report Designer&#41;](../Topic/Report%20Parameters%20\(Report%20Builder%20and%20Report%20Designer\).md)   
 [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../Topic/Report%20Embedded%20Datasets%20and%20Shared%20Datasets%20\(Report%20Builder%20and%20SSRS\).md)   
 [Query Designers &#40;Report Builder&#41;](../Topic/Query%20Designers%20\(Report%20Builder\).md)   
 [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../Topic/Report%20Embedded%20Datasets%20and%20Shared%20Datasets%20\(Report%20Builder%20and%20SSRS\).md)   
 [Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](../Topic/Create%20a%20Shared%20Dataset%20or%20Embedded%20Dataset%20\(Report%20Builder%20and%20SSRS\).md)  
  
  