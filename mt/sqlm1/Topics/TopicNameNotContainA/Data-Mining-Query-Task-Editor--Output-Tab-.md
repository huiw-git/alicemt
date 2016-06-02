---
title: Data Mining Query Task Editor (Output Tab)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 62f9e015-6fe0-4396-ad90-3ad51bf00025
---
# Data Mining Query Task Editor (Output Tab)
  Use the **Output** tab of the **Data Mining Query Task Editor** dialog box to specify the destination of the prediction query.  
  
 To learn about implementing data mining in packages, see [Data Mining Query Task](../../Topics\TopicNameNotContainA/Data-Mining-Query-Task.md) and [Data Mining Solutions](../../Topics\TopicNameNotContainA/Data-Mining-Solutions.md).  
  
## General Options  
 **Name**  
 Provide a unique name for the Data Mining Query task. This name is used as the label in the task icon.  
  
> [!NOTE]  
>  Task names must be unique within a package.  
  
 **Description**  
 Type a description of the Data Mining Query task.  
  
## Output Tab Options  
 **Connection**  
 Select a connection manager in the list or click **New** to create a new connection manager.  
  
 **New**  
 Create a new connection manager. Only the ADO.NET and OLE DB connection manager types can be used.  
  
 **Output table**  
 Specify the table to which the prediction query writes its results.  
  
 **Drop and re\-create the output table**  
 Indicate whether the prediction query should overwrite content in the destination table by dropping and then re\-creating the table.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Data Mining Query Task Editor &#40;Mining Model Tab&#41;](../Topic/Data%20Mining%20Query%20Task%20Editor%20\(Mining%20Model%20Tab\).md)   
 [Data Mining Query Task Editor &#40;Query Tab&#41;](../Topic/Data%20Mining%20Query%20Task%20Editor%20\(Query%20Tab\).md)   
 [Data Mining Designer](../../Topics\TopicNameNotContainA/Data-Mining-Designer.md)  
  
  