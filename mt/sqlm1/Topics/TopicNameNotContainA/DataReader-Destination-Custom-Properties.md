---
title: DataReader Destination Custom Properties
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f151c3e8-3811-457d-a3d3-6158ca65a646
---
# DataReader Destination Custom Properties
  The DataReader destination has both custom properties and the properties common to all data flow components.  
  
 The following table describes the custom properties of the DataReader destination. All properties except for **DataReader** are read\/write.  
  
|Property name|Data Type|Description|  
|-------------------|---------------|-----------------|  
|DataReader|String|The class name of the DataReader destination.|  
|FailOnTimeout|Boolean|Indicates whether to fail when a **ReadTimeout** occurs. The default value of this property is **False**.|  
|ReadTimeout|Integer|The number of milliseconds before a time\-out occurs. The default value of this property is 30000 \(30 seconds\).|  
  
 The input and the input columns of the DataReader destination have no custom properties.  
  
 For more information, see [DataReader Destination](../../Topics\TopicNameNotContainA/DataReader-Destination.md).  
  
## See Also  
 [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md)  
  
  