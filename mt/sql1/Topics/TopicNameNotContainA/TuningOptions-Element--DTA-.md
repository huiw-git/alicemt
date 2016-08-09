---
title: "TuningOptions Element (DTA)"
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
ms.assetid: 58a22ba1-8e03-411f-bd46-85e4540f217a
caps.latest.revision: 13
caps.handback.revision: 0
manager: jhubbard
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
|**Parent element**|[DTAInput Element (DTA)](../../Topics/TopicNameNotContainA/DTAInput-Element--DTA-.md)|  
|**Child elements**|**ReportSet** element. For more information, see the [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> **TuningLogTable** element. For more information, see the [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> **NumberOfEvents** element. For more information, see the [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> [TuningTimeInMin Element (DTA)](../../Topics/TopicNameNotContainA/TuningTimeInMin-Element--DTA-.md)<br /><br /> [StorageBoundInMB Element (DTA)](../../Topics/TopicNameNotContainA/StorageBoundInMB-Element--DTA-.md)<br /><br /> **MaxKeyColumnsInIndex** element. For more information, see the [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> **MaxColumnsInIndex** element. For more information, see the [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> **MinPercentageImprovement** element. For more information, see the [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100)<br /><br /> [TestServer Element (DTA)](../../Topics/TopicNameNotContainA/TestServer-Element--DTA-.md)<br /><br /> [FeatureSet Element (DTA)](../../Topics/TopicNameNotContainA/FeatureSet-Element--DTA-.md)<br /><br /> [Partitioning Element (DTA)](../../Topics/TopicNameNotContainA/Partitioning-Element--DTA-.md)<br /><br /> [DropOnlyMode Element (DTA)](../../Topics/TopicNameNotContainA/DropOnlyMode-Element--DTA-.md)<br /><br /> [KeepExisting Element (DTA)](../../Topics/TopicNameNotContainA/KeepExisting-Element--DTA-.md)<br /><br /> [OnlineIndexOperation Element (DTA)](../../Topics/TopicNameNotContainA/OnlineIndexOperation-Element--DTA-.md)<br /><br /> [DatabaseToConnect Element (DTA)](../../Topics/TopicNameNotContainA/DatabaseToConnect-Element--DTA-.md)<br /><br /> **IgnoreConstantsInWorkload** element. For more information, see the [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> **RetainShellDB** element. For more information, see the [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).|  
  
## Example  
 For examples of the **TuningOptions** element, see the [XML Input File Samples (DTA)](../../Topics/TopicNameNotContainA/XML-Input-File-Samples--DTA-.md).  
  
## See Also  
 [XML Input File Reference (Database Engine Tuning Advisor)](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)