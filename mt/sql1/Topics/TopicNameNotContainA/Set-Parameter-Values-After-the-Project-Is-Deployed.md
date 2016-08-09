---
title: "Set Parameter Values After the Project Is Deployed"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c9dcca4d-f1a0-45ec-b078-f4d372589baf
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Set Parameter Values After the Project Is Deployed
The Deployment Wizard allows you to set server default parameter values when you deploy your project to the catalog. After your project is in the catalog, you can use SQL Server Management Studio (SSMS) Object Explorer or Transact-SQL to set server default values.  
  
### To set server defaults with SSMS Object Explorer:  
  
1.  Select and right-click the project under the **Integration Services** node.  
  
2.  Click **Properties** to open the **Project Properties** dialog window.  
  
3.  Open the parameters page by clicking **Parameters** under **Select a page**.  
  
4.  Select the desired parameter in the **Parameters** list. Note: The **Container** column helps distinguish project parameters from package parameters.  
  
5.  In the **Value** column, specify the desired server default parameter value.  
  
 To set server defaults with Transact-SQL, use the [catalog.set_object_parameter_value (SSISDB Database)](assetId:///fb887543-f92f-404d-9495-a1dd23a6716e) stored procedure. To view current server defaults, query the [catalog.object_parameters (SSISDB Database)](assetId:///d7b04903-2d61-4159-9456-475942d1f732) view. To clear a server default value, use the [catalog.clear_object_parameter_value (SSISDB Database)](assetId:///dcbbb714-a051-4805-9e2b-2c2fb647c890) stored procedure.  
  
## See Also  
 [Integration Services (SSIS) Parameters](../../Topics/TopicNameNotContainA/Integration-Services--SSIS--Parameters.md)