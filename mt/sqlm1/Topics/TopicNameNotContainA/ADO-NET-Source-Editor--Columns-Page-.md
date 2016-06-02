---
title: ADO NET Source Editor (Columns Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fbc205b9-2001-4737-a76b-1ba777344bd9
---
# ADO NET Source Editor (Columns Page)
  Use the **Columns** page of the **ADO NET Source Editor** dialog box to map an output column to each external \(source\) column.  
  
 To learn more about the ADO NET source, see [ADO NET Source](../../Topics\TopicNameNotContainA/ADO-NET-Source.md).  
  
 **To open the Columns page**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package that has the ADO NET source.  
  
2.  On the **Data Flow** tab, double\-click the ADO NET source.  
  
3.  In the **ADO NET Source Editor**, click **Columns**.  
  
## Options  
 **Available External Columns**  
 View the list of available external columns in the data source. You cannot use this table to add or delete columns.  
  
 **External Column**  
 View external \(source\) columns in the order in which you will see them when configuring components that consume data from this source.  
  
 **Output Column**  
 Provide a unique name for each output column. The default is the name of the selected external \(source\) column; however, you can choose any unique, descriptive name. The name provided will be displayed within the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer.  
  
## See Also  
 [ADO NET Source Editor &#40;Connection Manager Page&#41;](../Topic/ADO%20NET%20Source%20Editor%20\(Connection%20Manager%20Page\).md)   
 [ADO NET Source Editor &#40;Error Output Page&#41;](../Topic/ADO%20NET%20Source%20Editor%20\(Error%20Output%20Page\).md)   
 [ADO.NET Connection Manager](../../Topics\TopicNameNotContainA/ADO.NET-Connection-Manager.md)  
  
  