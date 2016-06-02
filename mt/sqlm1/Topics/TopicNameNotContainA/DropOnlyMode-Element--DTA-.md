---
title: DropOnlyMode Element (DTA)
ms.custom: na
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
  
-   [FeatureSet Element &#40;DTA&#41;](../Topic/FeatureSet%20Element%20\(DTA\).md)  
  
-   [Partitioning Element &#40;DTA&#41;](../Topic/Partitioning%20Element%20\(DTA\).md)  
  
-   [KeepExisting Element &#40;DTA&#41;](../Topic/KeepExisting%20Element%20\(DTA\).md) is set to **ALL**  
  
## Element Relationships  
 **Parent element**: [TuningOptions Element &#40;DTA&#41;](../Topic/TuningOptions%20Element%20\(DTA\).md)  
  
 **Child elements**  
  
## Example  
 The following example shows the **TuningOptions** section of a Database Engine Tuning Advisor XML input file where the **DropOnlyMode** is specified. In this example the tuning time is limited to 24 hours \(1440 minutes\) and all existing clustered and nonclustered indexes will be considered for dropping:  
  
```xml  
<TuningOptions  
  <TuningTimeInMin>1440</Name>  
  <KeepExisting>ALIGNED</KeepExisting>  
  <DropOnlyMode />  
</TuningOptions>  
```  
  
## See Also  
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../Topic/XML%20Input%20File%20Reference%20\(Database%20Engine%20Tuning%20Advisor\).md)  
  
  