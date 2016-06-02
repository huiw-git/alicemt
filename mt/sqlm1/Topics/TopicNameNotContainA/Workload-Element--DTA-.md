---
title: Workload Element (DTA)
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
ms.assetid: 68ffd473-6546-4015-98d0-3763165de65c
---
# Workload Element (DTA)
  Specifies the workload to be used for a tuning session.  
  
## Syntax  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|None.|  
|**Default value**|None.|  
|**Occurrence**|Required once for each **DTAInput** element.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[Start and Use the Database Engine Tuning Advisor](../../Topics\TopicNameNotContainA/Start-and-Use-the-Database-Engine-Tuning-Advisor.md)|  
|**Child elements**|[File Element &#40;DTA&#41;](../Topic/File%20Element%20\(DTA\).md)<br /><br /> [Database Element for Workload &#40;DTA&#41;](../Topic/Database%20Element%20for%20Workload%20\(DTA\).md)<br /><br /> [EventString Element &#40;DTA&#41;](../Topic/EventString%20Element%20\(DTA\).md)|  
  
## Remarks  
 A workload is a set of [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements that execute against a database or databases that you want to tune. The Database Engine Tuning Advisor can use [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] scripts, trace files, and trace tables as workloads.  
  
 If you specify a workload in an XML input file and a workload on the command line with the **dta** tool, the workload specified on the command line will be used for tuning. All tuning options specified on the command line override those that are specified in an XML input file. The only exception is if a user\-specified configuration is entered in the evaluate mode in the XML input file. For example, if a configuration is entered in the **Configuration** element of the XML input file and the **EvaluateConfiguration** element is also specified as one of the tuning options, the tuning options specified in the XML input file will override any tuning options entered at the command line.  
  
 One workload must be specified for each tuning session.  
  
## Example  
 The following code example specifies the **MyDatabase.MyDBOwner.TuningTable001** trace table for the **Workload** element. The **TuningTable001** was created by using the Tuning template with SQL Server Profiler and saving the trace output as a table.  
  
```  
<DTAXML ...>  
  <DTAInput>  
    <Server>  
...code removed here...  
    </Server>  
    <Workload>  
      <Database>  
        <Name>MyDatabase</Name>  
        <Schema>  
          <Name>MyDBOwner</Name>  
            <Table>  
              <Name>TuningTable001</Name>  
            </Table>  
        </Schema>  
      </Database>  
    </Workload>  
...code removed here...  
  </DTAInput>  
</DTAXML>  
```  
  
## See Also  
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../Topic/XML%20Input%20File%20Reference%20\(Database%20Engine%20Tuning%20Advisor\).md)  
  
  