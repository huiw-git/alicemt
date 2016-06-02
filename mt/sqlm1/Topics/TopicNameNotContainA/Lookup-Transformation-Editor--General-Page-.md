---
title: Lookup Transformation Editor (General Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4bd15e48-0feb-4f95-be91-5df58105dbfb
---
# Lookup Transformation Editor (General Page)
  Use the **General** page of the Lookup Transformation Editor dialog box to select the cache mode, select the connection type, and specify how to handle rows with no matching entries.  
  
 To learn more about the Lookup transformation, see [Lookup Transformation](../../Topics\TopicNameNotContainA/Lookup-Transformation.md).  
  
## Options  
 **Full cache**  
 Generate and load the reference dataset into cache before the Lookup transformation is executed.  
  
 **Partial cache**  
 Generate the reference dataset during the execution of the Lookup transformation. Load the rows with matching entries in the reference dataset and the rows with no matching entries in the dataset into cache.  
  
 **No cache**  
 Generate the reference dataset during the execution of the Lookup transformation. No data is loaded into cache.  
  
 **Cache connection manager**  
 Configure the Lookup transformation to use a Cache connection manager. This option is available only if the Full cache option is selected.  
  
 **OLE DB connection manager**  
 Configure the Lookup transformation to use an OLE DB connection manager.  
  
 **Specify how to handle rows with no matching entries**  
 Select an option for handling rows that do not match at least one entry in the reference dataset.  
  
 When you select **Redirect rows to no match output**, the rows are redirected to a no match output and are not handled as errors. The **Error** option on the **Error Output** page of the **Lookup Transformation Editor** dialog box is not available.  
  
 When you select any other option in the **Specify how to handle rows with no matching entries** list box, the rows are handled as errors. The **Error** option on the **Error Output** page is available.  
  
## External Resources  
 Blog entry, [Lookup cache modes](http://go.microsoft.com/fwlink/?LinkId=219518) on blogs.msdn.com  
  
## See Also  
 [Cache Connection Manager](../../Topics\TopicNameNotContainA/Cache-Connection-Manager.md)   
 [Lookup Transformation Editor &#40;Connection Page&#41;](../Topic/Lookup%20Transformation%20Editor%20\(Connection%20Page\).md)   
 [Lookup Transformation Editor &#40;Columns Page&#41;](../Topic/Lookup%20Transformation%20Editor%20\(Columns%20Page\).md)   
 [Lookup Transformation Editor &#40;Advanced Page&#41;](../Topic/Lookup%20Transformation%20Editor%20\(Advanced%20Page\).md)   
 [Lookup Transformation Editor &#40;Error Output Page&#41;](../Topic/Lookup%20Transformation%20Editor%20\(Error%20Output%20Page\).md)  
  
  