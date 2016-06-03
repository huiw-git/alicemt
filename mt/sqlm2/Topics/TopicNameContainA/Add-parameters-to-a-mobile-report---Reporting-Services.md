---
title: Add parameters to a mobile report | Reporting Services
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 113cb057-deec-40eb-abc8-f35d3900eaa6
---
# Add parameters to a mobile report | Reporting Services
You can create [!INCLUDE[ssRSnoversion_md](../../Token\Other/ssRSnoversion_md.md)] mobile report with parameters, so you and your report readers can filter your reports. A reports with parameters can also be the target of a [drillthrough from a source report](../../Topics\TopicNameContainA/Add-drillthrough-from-a-mobile-report-to-other-mobile-reports-or-URLs.md). 

To create a mobile report with parameters, you start with a shared dataset with at least one parameter. Read about [creating parameters in a shared dataset](../../Topics\TopicNameContainA/Create-a-Shared-Dataset-or-Embedded-Dataset--Report-Builder-and-SSRS-.md).  
1. In the top bar of the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion.md)] web portal, select **New** > **Mobile Report**.  
  
   ![PBI_SSMRP_NewMenu](../../Images\Image\ImageNotContaina/PBI_SSMRP_NewMenu.png)  
     
2. Select the **Data** tab in the upper-left corner of [!INCLUDE[SS_MobileReptPub_Long](../../Token\Other/SS_MobileReptPub_Long.md)].   
  
3. In the upper-right corner, select **Add Data**.  
  
4. Select **Report Server**, then select a server.  
  
5. Navigate to the shared datasets on the server and select one that has parameters.  
  
   In the grid, you see the data in the dataset. The green **P** marks a dataset with a parameter.  
     
   ![SSMRP_PforParam](../../Images\Image\ImageNotContaina/SSMRP_PforParam.png)  
  
6. Select the cog on the tab, then select **Param {}**.  
  
   ![SSMRP_ParamWheel](../../Images\Image\ImageNotContaina/SSMRP_ParamWheel.png)  
  
7. Select the report element that will pass values to the parameter.  
  
   ![SSMRP_SetParam](../../Images\Image\ImageNotContaina/SSMRP_SetParam.png)  
     
Now when someone selects a value in your report, the dataset is queried again with the parameter value to return the appropriate result set.     
  
### See also  
-  [Add drillthrough from a mobile report to other mobile reports or URLs](../../Topics\TopicNameContainA/Add-drillthrough-from-a-mobile-report-to-other-mobile-reports-or-URLs.md)
-  [Create a shared or embedded dataset](../../Topics\TopicNameContainA/Create-a-Shared-Dataset-or-Embedded-Dataset--Report-Builder-and-SSRS-.md)
- [Create and publish mobile reports with SQL Server Mobile Report Publisher](../../Topics\TopicNameNotContainA/Create-mobile-reports-with-SQL-Server-Mobile-Report-Publisher.md)  
  
  
