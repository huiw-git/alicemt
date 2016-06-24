---
title: TuningOptions Element (DTA)
H1: na
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
ms.assetid: 58a22ba1-8e03-411f-bd46-85e4540f217a
---
# TuningOptions Element (DTA)
  Contains the tuning options for a specific tuning session.  
  
## Syntax  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|None.|  
|**Default value**|None.|  
|**Occurrence**|Optional. If used, can only be used once for each **DTAInput** element.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[DTAInput Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/DTAInput-Element--DTA-.md)|  
|**Child elements**|**ReportSet** element. For more information, see the [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> **TuningLogTable** element. For more information, see the [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> **NumberOfEvents** element. For more information, see the [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> [TuningTimeInMin Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/TuningTimeInMin-Element--DTA-.md)<br /><br /> [StorageBoundInMB Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/StorageBoundInMB-Element--DTA-.md)<br /><br /> **MaxKeyColumnsInIndex** element. For more information, see the [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> **MaxColumnsInIndex** element. For more information, see the [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> **MinPercentageImprovement** element. For more information, see the [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100)<br /><br /> [TestServer Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/TestServer-Element--DTA-.md)<br /><br /> [FeatureSet Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/FeatureSet-Element--DTA-.md)<br /><br /> [Partitioning Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Partitioning-Element--DTA-.md)<br /><br /> [DropOnlyMode Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/DropOnlyMode-Element--DTA-.md)<br /><br /> [KeepExisting Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/KeepExisting-Element--DTA-.md)<br /><br /> [OnlineIndexOperation Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/OnlineIndexOperation-Element--DTA-.md)<br /><br /> [DatabaseToConnect Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/DatabaseToConnect-Element--DTA-.md)<br /><br /> **IgnoreConstantsInWorkload** element. For more information, see the [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> **RetainShellDB** element. For more information, see the [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).|  
  
## Example  
 For examples of the **TuningOptions** element, see the [XML Input File Samples &#40;DTA&#41;](../../Topics/TopicNameNotContainA/XML-Input-File-Samples--DTA-.md).  
  
## See Also  
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)  
  
  