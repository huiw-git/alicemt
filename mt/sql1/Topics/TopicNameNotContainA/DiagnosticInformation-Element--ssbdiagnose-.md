---
title: "DiagnosticInformation Element (ssbdiagnose)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0cfda544-542c-4cf4-86d2-8031c91b10f6
caps.latest.revision: 15
manager: jhubbard
---
# DiagnosticInformation Element (ssbdiagnose)
The **DiagnosticInformation** element contains all elements that report the diagnostic information found by the utility. **DiagnosticInformation** is the root element of a **ssbdiagnostic** XML output file.  
  
## Syntax  
  
```  
  
<DiagnosticInformation>   
    ...   
</DiagnosticInformation>  
```  
  
## Element Attributes  
  
|Attribute|Description|  
|---------------|-----------------|  
|**None**|N/A|  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|None.|  
|**Default value**|None.|  
|**Occurrence**|Once per **ssbdiagnose** XML output file.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|None.|  
|**Child elements**|[Banner Element (ssbdiagnose)](../../Topics/TopicNameNotContainA/Banner-Element--ssbdiagnose-.md)<br /><br /> [Issue Element (ssbdiagnose)](../../Topics/TopicNameNotContainA/Issue-Element--ssbdiagnose-.md)|  
  
## Remarks  
 For more information about XML namespaces, see [Namespaces in an XML Document](http://go.microsoft.com/fwlink/?LinkId=7341) in the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] MSDN Library.  
  
## See Also  
 [ssbdiagnose Utility (Service Broker)](../../Topics/TopicNameNotContainA/ssbdiagnose-Utility--Service-Broker-.md)