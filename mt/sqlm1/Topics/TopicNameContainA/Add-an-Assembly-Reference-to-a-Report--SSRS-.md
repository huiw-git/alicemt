---
title: Add an Assembly Reference to a Report (SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0a03939e-48ce-4c30-b227-98533f2e0ccb
---
# Add an Assembly Reference to a Report (SSRS)
  When you embed custom code that contains references to [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)] classes that are not in [System.Math](assetId:///T:System.Math) or [System.Convert](assetId:///T:System.Convert), you must provide an assembly reference to the report so that the report processor can resolve the names. For more information, see [Add Code to a Report &#40;SSRS&#41;](../Topic/Add%20Code%20to%20a%20Report%20\(SSRS\).md).  
  
### To add an assembly reference to a report  
  
1.  In **Design** view, right\-click the design surface outside the border of the report and click **Report Properties**.  
  
2.  Click **References**.  
  
3.  In **Add or remove assemblies**, click **Add** and then click the ellipsis button to browse to the assembly.  
  
4.  In **Add or remove classes**, click **Add** and then type name of the class and provide an instance name to use within the report.  
  
    > [!NOTE]  
    >  Specify a class and instance name only for instance\-based members. Do not specify static members in the **Classes** list. For more information, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](../Topic/Custom%20Code%20and%20Assembly%20References%20in%20Expressions%20in%20Report%20Designer%20\(SSRS\).md).  
  
5.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
## See Also  
 [Using Custom Assemblies with Reports](../Topic/Using%20Custom%20Assemblies%20with%20Reports.md)   
 [Report Properties Dialog Box, References](../../Topics\TopicNameNotContainA/Report-Properties-Dialog-Box,-References.md)  
  
  