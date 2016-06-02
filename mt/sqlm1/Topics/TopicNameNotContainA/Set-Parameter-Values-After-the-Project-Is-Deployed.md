---
title: Set Parameter Values After the Project Is Deployed
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c9dcca4d-f1a0-45ec-b078-f4d372589baf
---
# Set Parameter Values After the Project Is Deployed
  The Deployment Wizard allows you to set server default parameter values when you deploy your project to the catalog. After your project is in the catalog, you can use SQL Server Management Studio \(SSMS\) Object Explorer or Transact\-SQL to set server default values.  
  
### To set server defaults with SSMS Object Explorer:  
  
1.  Select and right\-click the project under the **Integration Services** node.  
  
2.  Click **Properties** to open the **Project Properties** dialog window.  
  
3.  Open the parameters page by clicking **Parameters** under **Select a page**.  
  
4.  Select the desired parameter in the **Parameters** list. Note: The **Container** column helps distinguish project parameters from package parameters.  
  
5.  In the **Value** column, specify the desired server default parameter value.  
  
 To set server defaults with Transact\-SQL, use the [catalog.set_object_parameter_value &#40;SSISDB Database&#41;](../Topic/catalog.set_object_parameter_value%20\(SSISDB%20Database\).md) stored procedure. To view current server defaults, query the [catalog.object_parameters &#40;SSISDB Database&#41;](../Topic/catalog.object_parameters%20\(SSISDB%20Database\).md) view. To clear a server default value, use the [catalog.clear_object_parameter_value &#40;SSISDB Database&#41;](../Topic/catalog.clear_object_parameter_value%20\(SSISDB%20Database\).md) stored procedure.  
  
## See Also  
 [Integration Services &#40;SSIS&#41; Parameters](../Topic/Integration%20Services%20\(SSIS\)%20Parameters.md)  
  
  