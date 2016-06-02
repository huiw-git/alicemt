---
title: Execute SQL Task Editor (Parameter Mapping Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8ebe020a-7921-46b2-8823-398748f379b2
---
# Execute SQL Task Editor (Parameter Mapping Page)
  Use the **Parameter Mapping** page of the **Execute SQL Task Editor** dialog box to map variables to parameters in the SQL statement.  
  
 To learn about this task, see [Execute SQL Task](../../Topics\TopicNameNotContainA/Execute-SQL-Task.md) and [Parameters and Return Codes in the Execute SQL Task](../../Topics\TopicNameNotContainA/Parameters-and-Return-Codes-in-the-Execute-SQL-Task.md).  
  
## Options  
 **Variable Name**  
 After you have added a parameter mapping by clicking **Add**, select a system or user\-defined variable from the list or click \<**New variable...**\> to add a new variable by using the **Add Variable** dialog box.  
  
 **Related Topics:** [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md)  
  
 **Direction**  
 Select the direction of the parameter. Map each variable to an input parameter, output parameter, or a return code.  
  
 **Data Type**  
 Select the data type of the parameter. The list of available data types is specific to the provider selected in the connection manager used by the task.  
  
 **Parameter Name**  
 Provide a parameter name.  
  
 Depending on the connection manager type that the task uses, you must use numbers or parameter names. Some connection manager types require that the first character of the parameter name is the @ sign , specific names like @Param1, or column names as parameter names.  
  
 **Related Topics:** [Parameters and Return Codes in the Execute SQL Task](../../Topics\TopicNameNotContainA/Parameters-and-Return-Codes-in-the-Execute-SQL-Task.md)  
  
 **Parameter Size**  
 Provide the size of parameters that have variable length, such as strings and binary fields.  
  
 This setting ensures that the provider allocates sufficient space for variable\-length parameter values.  
  
 **Add**  
 Click to add a parameter mapping.  
  
 **Remove**  
 Select a parameter mapping in the list and then click **Remove**.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Execute SQL Task Editor &#40;General Page&#41;](../Topic/Execute%20SQL%20Task%20Editor%20\(General%20Page\).md)   
 [Execute SQL Task Editor &#40;Result Set Page&#41;](../Topic/Execute%20SQL%20Task%20Editor%20\(Result%20Set%20Page\).md)   
 [Transact-SQL Reference &#40;Database Engine&#41;](../Topic/Transact-SQL%20Reference%20\(Database%20Engine\).md)  
  
  