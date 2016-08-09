---
title: "DropOnlyMode Element (DTA)"
ms.custom: na
ms.date: 06/29/2016
ms.devlang: 
  - XML
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 80960676-7581-4074-889b-80ee665963dd
caps.latest.revision: 15
caps.handback.revision: 0
manager: jhubbard
---
# DropOnlyMode Element (DTA)
Specifies that Database Engine Tuning Advisor should only consider dropping existing indexes, indexed views, or partitions during the tuning session. No new physical design structures are considered when this tuning option is specified.  
  
## Syntax  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <DropOnlyMode>...</DropOnlyMode>  
```  
  
## Element Characteristics  
 **Data type and length**  
  
 **Default value**  
  
 **Occurrence**: Optional. Can be used only once for each **TuningOptions** element. Cannot be used if the following elements are specified in the **TuningOptions** element:  
  
-   [FeatureSet Element (DTA)](../../Topics/TopicNameNotContainA/FeatureSet-Element--DTA-.md)  
  
-   [Partitioning Element (DTA)](../../Topics/TopicNameNotContainA/Partitioning-Element--DTA-.md)  
  
-   [KeepExisting Element (DTA)](../../Topics/TopicNameNotContainA/KeepExisting-Element--DTA-.md) is set to **ALL**  
  
## Element Relationships  
 **Parent element**: [TuningOptions Element (DTA)](../../Topics/TopicNameNotContainA/TuningOptions-Element--DTA-.md)  
  
 **Child elements**  
  
## Example  
 The following example shows the **TuningOptions** section of a Database Engine Tuning Advisor XML input file where the **DropOnlyMode** is specified. In this example the tuning time is limited to 24 hours (1440 minutes) and all existing clustered and nonclustered indexes will be considered for dropping:  
  
```xml  
<TuningOptions  
  <TuningTimeInMin>1440</Name>  
  <KeepExisting>ALIGNED</KeepExisting>  
  <DropOnlyMode />  
</TuningOptions>  
```  
  
## See Also  
 [XML Input File Reference (Database Engine Tuning Advisor)](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)