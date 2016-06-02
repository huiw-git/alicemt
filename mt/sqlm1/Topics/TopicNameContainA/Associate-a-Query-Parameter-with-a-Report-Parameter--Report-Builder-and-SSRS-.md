---
title: Associate a Query Parameter with a Report Parameter (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6d297e1a-ff71-472a-addc-349e863092b5
---
# Associate a Query Parameter with a Report Parameter (Report Builder and SSRS)
  When you define a dataset query that contains a query variable, the query command is parsed. For each query variable, a corresponding dataset parameter and report parameter are created. The dataset parameter points to the report parameter. This enables a user to enter a value that passes directly to the query. Each time you edit the query command, the same process takes place.  
  
 If you rename a report parameter that is bound to a query parameter, you need to manually link the query parameters to the renamed report parameter by using the procedure in this topic.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
### To associate a query parameter with a report parameter  
  
1.  In the Report Data pane, right\-click the dataset, click **Dataset Properties**, and then click **Parameters**.  
  
    > [!NOTE]  
    >  If the Report Data pane is not visible, click **Report Data** on the **View** menu.  
  
2.  In the column **Parameter Name**, find the name of the query parameter. Parameter names are automatically populated based on the query. Every time you change the query, the query is checked for new query parameters. Query parameters that you create manually are not changed when the query changes.  
  
    -   In **Parameter Name**, find the query parameter name as it exists in the query. You can also manually add a new query parameter and enter a name.  
  
    -   In **Parameter Value**, type or select an expression that evaluates to the value to pass to the query parameter. This is typically the name of the report parameter.  
  
        > [!NOTE]  
        >  You are not limited to report parameters as values for a query parameter. You can use any expression that evaluates to a value for the parameter value.  
  
3.  Repeat step 2 for additional query parameters.  
  
## See Also  
 [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../Topic/Report%20Embedded%20Datasets%20and%20Shared%20Datasets%20\(Report%20Builder%20and%20SSRS\).md)   
 [Report Parameters Concept &#40;Report Builder and SSRS&#41;](../Topic/Report%20Parameters%20Concept%20\(Report%20Builder%20and%20SSRS\).md)  
  
  