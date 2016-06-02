---
title: Partition Processing Destination Editor (Advanced Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2039ee0f-069d-479d-90b2-2a12481b1162
---
# Partition Processing Destination Editor (Advanced Page)
  Use the **Advanced** page of the **Partition Processing Destination Editor** dialog box to configure error handling.  
  
 To learn more about the Partition Processing destination, see [Partition Processing Destination](../../Topics\TopicNameNotContainA/Partition-Processing-Destination.md).  
  
> [!NOTE]  
>  Tasks described here do not apply to Analysis Services tabular models.  You cannot map input columns to partition columns for tabular models. You can instead use the Analysis Services Execute DDL task [Analysis Services Execute DDL Task](../../Topics\TopicNameNotContainA/Analysis-Services-Execute-DDL-Task.md) to process the partition.  
  
## Options  
 **Use default error configuration.**  
 Specify whether to use the default [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] error handling. By default, this value is **True**.  
  
 **Key error action**  
 Specify how to handle records that have unacceptable key values.  
  
|Value|Description|  
|-----------|-----------------|  
|**ConvertToUnknown**|Convert the unacceptable key value to the Unknown value.|  
|**DiscardRecord**|Discard the record.|  
  
 **Ignore errors**  
 Specify that errors should be ignored.  
  
 **Stop on error**  
 Specify that processing should stop when an error occurs.  
  
 **Number of errors**  
 Specify the error threshold at which processing should stop, if you have selected **Stop on error**.  
  
 **On error action**  
 Specify the action to take when the error threshold is reached, if you have selected **Stop on error**.  
  
|Value|Description|  
|-----------|-----------------|  
|**StopProcessing**|Stop processing.|  
|**StopLogging**|Stop logging errors.|  
  
 **Key not found**  
 Specify the action to take for a key not found error. By default, this value is **ReportAndContinue**.  
  
|Value|Description|  
|-----------|-----------------|  
|**IgnoreError**|Ignore the error and continue processing.|  
|**ReportAndContinue**|Report the error and continue processing.|  
|**ReportAndStop**|Report the error and stop processing.|  
  
 **Duplicate key**  
 Specify the action to take for a duplicate key error. By default, this value is **IgnoreError**.  
  
|Value|Description|  
|-----------|-----------------|  
|**IgnoreError**|Ignore the error and continue processing.|  
|**ReportAndContinue**|Report the error and continue processing.|  
|**ReportAndStop**|Report the error and stop processing.|  
  
 **Null key converted to unknown**  
 Specify the action to take when a null key has been converted to the Unknown value. By default, this value is **IgnoreError**.  
  
|Value|Description|  
|-----------|-----------------|  
|**IgnoreError**|Ignore the error and continue processing.|  
|**ReportAndContinue**|Report the error and continue processing.|  
|**ReportAndStop**|Report the error and stop processing.|  
  
 **Null key not allowed**  
 Specify the action to take when null keys are not allowed and a null key is encountered. By default, this value is **ReportAndContinue**.  
  
|Value|Description|  
|-----------|-----------------|  
|**IgnoreError**|Ignore the error and continue processing.|  
|**ReportAndContinue**|Report the error and continue processing.|  
|**ReportAndStop**|Report the error and stop processing.|  
  
 **Error log path**  
 Type the path for the error log, or select a destination by using the browse **\(...\)** button.  
  
 **Browse \(...\)**  
 Select a path for the error log.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Partition Processing Destination Editor &#40;Mappings Page&#41;](../Topic/Partition%20Processing%20Destination%20Editor%20\(Mappings%20Page\).md)  
  
  