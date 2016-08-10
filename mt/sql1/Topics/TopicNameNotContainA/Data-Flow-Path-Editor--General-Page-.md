---
title: "Data Flow Path Editor (General Page)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 72a9ff1d-3748-41d1-a9b2-63f4a77bba24
caps.latest.revision: 26
caps.handback.revision: 0
manager: jhubbard
---
# Data Flow Path Editor (General Page)
Use the **Data Flow Path Editor** dialog box to set path properties, view column metadata, and manage the data viewers attached to the path.  
  
 Use the **General** node of the **Data Flow Path Editor** dialog box to name and describe the path, and to specify the options for path annotation.  
  
## Options  
 **Name**  
 Provide a unique name for the path.  
  
 **ID**  
 The lineage identifier of the path. This property is read-only.  
  
 **IdentificationString**  
 The string that identifies the path. Automatically generated from the name entered above.  
  
 **Description**  
 Describe the path.  
  
 **PathAnnotation**  
 Specify the type of annotation to use. Choose **Never** to disable annotations, **AsNeeded** to enable annotation on demand, **SourceName** to automatically annotate using the value of the **SourceName** option, and **PathName** to automatically annotate using the value of the **Name** property.  
  
 **DestinationName**  
 Displays the input that is the end of the path.  
  
 **SourceName**  
 Displays the output that is the start of the path.  
  
## See Also  
 [Data Flow Path Editor (Metadata Page)](../../Topics/TopicNameNotContainA/Data-Flow-Path-Editor--Metadata-Page-.md)   
 [Data Flow Path Editor (Data Viewers Page)](../../Topics/TopicNameNotContainA/Data-Flow-Path-Editor--Data-Viewers-Page-.md)   
 [Data Flow](../../Topics/TopicNameNotContainA/Data-Flow.md)   
 [Use Annotations in Packages](../../Topics/TopicNameNotContainA/Use-Annotations-in-Packages.md)