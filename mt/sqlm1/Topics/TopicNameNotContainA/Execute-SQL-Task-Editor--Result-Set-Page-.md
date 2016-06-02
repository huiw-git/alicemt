---
title: Execute SQL Task Editor (Result Set Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d27000c8-8d91-4e1c-b45e-bca9a3c12f6d
---
# Execute SQL Task Editor (Result Set Page)
  Use the **Result Set** page of the **Execute SQL Task Editor** dialog to map the result of the SQL statement to new or existing variables. The options in this dialog box are disabled if **ResultSet** on the General page is set to **None**.  
  
 For more information about this task, see [Execute SQL Task](../../Topics\TopicNameNotContainA/Execute-SQL-Task.md) and [Result Sets in the Execute SQL Task](../../Topics\TopicNameNotContainA/Result-Sets-in-the-Execute-SQL-Task.md).  
  
## Options  
 **Result Name**  
 After you have added a result set mapping set by clicking **Add**, provide a name for the result. Depending on the result set type, you must use specific result names.  
  
 If the result set type is **Single row**, you can use either the name of a column returned by the query or the number that represents the position of a column in the column list of a column returned by the query.  
  
 If the result set type is **Full result set** or **XML**, you must use 0 as the result set name.  
  
 **Related Topics**: [Result Sets in the Execute SQL Task](../../Topics\TopicNameNotContainA/Result-Sets-in-the-Execute-SQL-Task.md)  
  
 **Variable Name**  
 Map the result set to a variable by selecting a variable or click \<**New variable...**\> to add a new variable by using the **Add Variable** dialog box.  
  
 **Add**  
 Click to add a result set mapping.  
  
 **Remove**  
 Select a result set mapping in the list and then click **Remove**.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Execute SQL Task Editor &#40;General Page&#41;](../Topic/Execute%20SQL%20Task%20Editor%20\(General%20Page\).md)   
 [Execute SQL Task Editor &#40;Parameter Mapping Page&#41;](../Topic/Execute%20SQL%20Task%20Editor%20\(Parameter%20Mapping%20Page\).md)   
 [Transact-SQL Reference &#40;Database Engine&#41;](../Topic/Transact-SQL%20Reference%20\(Database%20Engine\).md)  
  
  