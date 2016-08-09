---
title: "ADO NET Source Editor (Error Output Page)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4dd9d129-a95c-4d3a-bbbf-e84a39089950
caps.latest.revision: 15
caps.handback.revision: 0
manager: jhubbard
---
# ADO NET Source Editor (Error Output Page)
Use the **Error Output** page of the **ADO NET Source Editor** dialog box to select error handling options and to set properties on error output columns.  
  
 To learn more about the ADO NET source, see [ADO NET Source](../../Topics/TopicNameNotContainA/ADO-NET-Source.md).  
  
 **To open the Error Output page**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] package that has the ADO NET source.  
  
2.  On the **Data Flow** tab, double-click the ADO NET source.  
  
3.  In the **ADO NET Source Editor**, click **Error Output**.  
  
## Options  
 **Input/Output**  
 View the name of the data source.  
  
 **Column**  
 View the external (source) columns that you selected on the **Connection Manager** page of the **ADO NET Source Editor** dialog box.  
  
 **Error**  
 Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.  
  
 **Related Topics:** [Error Handling in Data](../../Topics/TopicNameNotContainA/Error-Handling-in-Data.md)  
  
 **Truncation**  
 Specify what should happen when a truncation occurs: ignore the failure, redirect the row, or fail the component.  
  
 **Description**  
 View the description of the error.  
  
 **Set this value to selected cells**  
 Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.  
  
 **Apply**  
 Apply the error handling option to the selected cells.  
  
## See Also  
 [ADO NET Source Editor (Connection Manager Page)](../../Topics/TopicNameNotContainA/ADO-NET-Source-Editor--Connection-Manager-Page-.md)   
 [ADO NET Source Editor (Columns Page)](../../Topics/TopicNameNotContainA/ADO-NET-Source-Editor--Columns-Page-.md)   
 [ADO.NET Connection Manager](../../Topics/TopicNameNotContainA/ADO.NET-Connection-Manager.md)