---
title: Upgrade Lookup Transformations
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9b2c281-91ee-4e20-bdf0-0cd77d4a4241
robots: noindex,nofollow
---
# Upgrade Lookup Transformations
  When you upgrade from [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] consider modifying packages to take advantage of the new features in the Lookup Transformation. The transformation supports the caching types and data output options available in [!INCLUDE[ssISversion2005](../../Token\Other/ssISversion2005_md.md)]. For more information about additional the caching and data outputs, see [Lookup Transformation](../../Topics\TopicNameNotContainA/Lookup-Transformation.md).  
  
 In [!INCLUDE[ssISversion2005](../../Token\Other/ssISversion2005_md.md)], the available caching types are full caching, partial caching, and no caching. In [!INCLUDE[ssISCurrent](../../Token\Other/ssISCurrent_md.md)], you can configure a Lookup transformation to use one of these caching types. For more information about how to implement partial caching or no caching, see [Implement a Lookup in No Cache or Partial Cache Mode](../../Topics\TopicNameContainA/Implement-a-Lookup-in-No-Cache-or-Partial-Cache-Mode.md). For information about how to implement full caching, see [Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager](../../Topics\TopicNameContainA/Implement-a-Lookup-Transformation-in-Full-Cache-Mode-Using-the-Cache-Connection-Manager.md) and [Implement a Lookup Transformation in Full Cache Mode Using the OLE DB Connection Manager](../../Topics\TopicNameContainA/Implement-a-Lookup-Transformation-in-Full-Cache-Mode-Using-the-OLE-DB-Connection-Manager.md).  
  
 In [!INCLUDE[ssISversion2005](../../Token\Other/ssISversion2005_md.md)], the Lookup transformation had an input, an output, and an error output. Rows in the input that had matching entries in the reference dataset were handled by the output. Rows in the input that did not have matching entries were treated as errors and could be redirected to the error output. In [!INCLUDE[ssISCurrent](../../Token\Other/ssISCurrent_md.md)], the Lookup transformation has two outputs: a match output and a no match output.  
  
 By default, when you run a Lookup transformation that was created in [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)], [!INCLUDE[ssISCurrent](../../Token\Other/ssISCurrent_md.md)] treats the rows without matching entries as errors and enables you to redirect the rows to an error output. You have the option of configuring the Lookup transformation to treat the rows as non\-errors and redirect the rows to the no match output.  
  
 For more information, see [Lookup Transformation Editor &#40;General Page&#41;](../Topic/Lookup%20Transformation%20Editor%20\(General%20Page\).md).  
  
## See Also  
 [Lookup Transformation](../../Topics\TopicNameNotContainA/Lookup-Transformation.md)  
  
  