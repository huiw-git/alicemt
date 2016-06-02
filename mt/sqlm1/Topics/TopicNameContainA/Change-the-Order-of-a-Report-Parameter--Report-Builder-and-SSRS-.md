---
title: Change the Order of a Report Parameter (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: abd61e19-dba3-423c-a26c-e8bc43197d3f
---
# Change the Order of a Report Parameter (Report Builder and SSRS)
  Change the order of report parameters when you have a dependent parameter that is listed before the parameter it is dependent on. Parameter order is important when you have cascading parameters, or when you want to show users the default value for one parameter before they choose values for other parameters. A dependent report parameter contains a reference, in either its default values query or valid values query, to a query parameter that points to a report parameter that is after it in the parameter list in the **Report Data** pane.  
  
 The order that you see parameters display on the report viewer toolbar when you run the report, is determined by the order of the parameters in the **Report Data** pane and the location of the parameters in the custom parameters pane. For more information, see [Customize the Parameters Pane in a Report &#40;Report Builder&#41;](../Topic/Customize%20the%20Parameters%20Pane%20in%20a%20Report%20\(Report%20Builder\).md)  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
## To change the order of report parameters  
  
You can change the order of report parameters by doing either of the following:  
  
-   Click a parameter in the **Report Data** pane, and use the up and down arrow buttons to move the parameter higher or lower in the list, as shown in the following image.  When you change the order of the parameter in the **Report Data** pane, the location of the parameter in the parameters pane is changed.  
  
     ![Change the order of the parameters in the Report Data pane](../../Images\Image\ImageNotContaina/ssrs_ChangeOrderofParameters_ReportData.png "ssrs_ChangeOrderofParameters_ReportData")  
  
-   In the parameters pane, drag the parameter to a new column or row in the pane. When you change the location of the parameter in the pane, the parameter order changes in the **Report Data** pane. For more information about moving parameters in the pane, see [Customize the Parameters Pane in a Report &#40;Report Builder&#41;](../Topic/Customize%20the%20Parameters%20Pane%20in%20a%20Report%20\(Report%20Builder\).md).  
  
## See Also  
 [Report Parameters &#40;Report Builder and Report Designer&#41;](../Topic/Report%20Parameters%20\(Report%20Builder%20and%20Report%20Designer\).md)   
 [Report Builder Help for Dialog Boxes, Panes, and Wizards](assetId:///2da24891-0b6d-4d3c-8b18-81b98752642f)   
 [Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](../Topic/Add%20Cascading%20Parameters%20to%20a%20Report%20\(Report%20Builder%20and%20SSRS\).md)   
 [Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../Topic/Tutorial:%20Add%20a%20Parameter%20to%20Your%20Report%20\(Report%20Builder\).md)   
 [Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](../Topic/Add%20Dataset%20Filters,%20Data%20Region%20Filters,%20and%20Group%20Filters%20\(Report%20Builder%20and%20SSRS\).md)   
 [Parameters Collection References &#40;Report Builder and SSRS&#41;](../Topic/Parameters%20Collection%20References%20\(Report%20Builder%20and%20SSRS\).md)  
  
  