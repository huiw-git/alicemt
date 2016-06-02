---
title: Report Parameters Concepts (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b0aa2159-4e49-4713-8824-5ef9a9edbc62
---
# Report Parameters Concepts (Report Builder and SSRS)
  You can add parameters to a report to link related reports, to control the report appearance, to filter report data, or to narrow the scope of a report to specific users or locations.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
 Report parameters are created in the following ways:  
  
-   Automatically, when you define dataset query that contains query variables. For each query variable, a corresponding dataset query parameter and report parameter with the same names are created. A query parameter can be a reference to a query variable or to an input parameter for a stored procedure.  
  
-   Automatically, when you add a reference to a shared dataset that contains query parameters.  
  
-   Manually, when you create report parameters in the Report Data pane. Parameters are one of the built\-in collections that you can include in an expression in a report. Because expressions are used to define values throughout a report definition, you can use parameters to control report appearance or to pass values to related subreports or reports that also use parameters.  
  
 For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../Topic/Report%20Parameters%20\(Report%20Builder%20and%20Report%20Designer\).md).  
  
 Parameters are frequently used to filter report data both before and after the data is returned to the report. For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../Topic/Filter,%20Group,%20and%20Sort%20Data%20\(Report%20Builder%20and%20SSRS\).md).  
  
 When you design a report, report parameters are saved in the report definition. When you publish a report, report parameters are saved and managed separately from the report definition. After you save the report to the report server, you can do the following:  
  
-   Change report parameter values directly on the report server independently from the report definition.  
  
-   Create multiple linked reports in which each linked report is a link to the report definition with a separate set of parameter values that can be managed independently on the report server.  
  
 If you plan to create report snapshots, histories, or subscriptions to a published report, you must understand how report parameters affect the design requirements for the report.  
  
## See Also  
 [Report Authoring Concepts &#40;Report Builder and SSRS&#41;](../Topic/Report%20Authoring%20Concepts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../Topic/Report%20Embedded%20Datasets%20and%20Shared%20Datasets%20\(Report%20Builder%20and%20SSRS\).md)   
 [Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../Topic/Tutorial:%20Add%20a%20Parameter%20to%20Your%20Report%20\(Report%20Builder\).md)  
  
  