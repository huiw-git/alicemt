---
title: "Data Mining Model Training Destination"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6bc8cbe2-46af-4f7b-93d6-86779313c9d7
caps.latest.revision: 47
caps.handback.revision: 0
manager: jhubbard
---
# Data Mining Model Training Destination
The Data Mining Model Training destination trains data mining models by passing the data that the destination receives through the data mining model algorithms. Multiple data mining models can be trained by one destination if the models are built on the same data mining structure. For more information, see [Mining Structure Columns](../../Topics/TopicNameNotContainA/Mining-Structure-Columns.md) and [Mining Model Columns](../../Topics/TopicNameNotContainA/Mining-Model-Columns.md).  
  
## Configuration of the Data Mining Model Training Destination  
 If a case level column of the target structure and the models built on the structure has the content type KEY TIME or KEY SEQUENCE, the input data must be sorted on that column. For example, models built using the Microsoft Time Series algorithm use the content type KEY TIME. If input data is not sorted, the processing of the model may fail. If the data requires sorting, you can use a Sort transformation earlier in the data flow to sort the data. This requirement does not apply to columns with the KEY content type. For more information, see [Content Types (Data Mining)](../../Topics/TopicNameNotContainA/Content-Types--Data-Mining-.md) and [Sort Transformation](../../Topics/TopicNameNotContainA/Sort-Transformation.md).  
  
> [!NOTE]  
>  The input to the Data Mining Model training destination must be sorted. To sort the data, you can include a Sort destination upstream from the Data Mining Model Training destination in the data flow. For more information, see [Sort Transformation](../../Topics/TopicNameNotContainA/Sort-Transformation.md).  
  
 This destination has one input and no output.  
  
 The Data Mining Model Training destination uses an [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] connection manager to connect to the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] project or the instance of [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] that contains the mining structure and mining models that the destination trains. For more information, see [Analysis Services Connection Manager](../../Topics/TopicNameNotContainA/Analysis-Services-Connection-Manager.md).  
  
 You can set properties through [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in the **Data Mining Model Training Editor** dialog box, click one of the following topics:  
  
-   [Data Mining Model Training Editor (Connection Tab)](../../Topics/TopicNameNotContainA/Data-Mining-Model-Training-Editor--Connection-Tab-.md)  
  
-   [Data Mining Model Training Editor (Columns Tab)](../../Topics/TopicNameNotContainA/Data-Mining-Model-Training-Editor--Columns-Tab-.md)  
  
 The **Advanced Editor** dialog box reflects the properties that can be set programmatically. For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:  
  
-   [Common Properties](../../Topics/TopicNameNotContainA/Common-Properties.md)  
  
-   [Data Mining Model Training Destination Custom Properties](../../Topics/TopicNameNotContainA/Data-Mining-Model-Training-Destination-Custom-Properties.md)  
  
 For more information about how to set properties, see [Set the Properties of a Data Flow Component](../../Topics/TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md).