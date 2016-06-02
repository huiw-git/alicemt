---
title: XML Output File Format (ssbdiagnose)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
---
# XML Output File Format (ssbdiagnose)
  The **ssbdiagnose** utility delivers its output as an XML file when you run it with the **\-XML** switch. The XML output file lists header information and the errors that it found in the [!INCLUDE[ssSB](../../Token\Other/ssSB_md.md)] configuration or conversation that was analyzed. You can write an application to analyze or report on the errors listed in the file. Or, you can view the XML file in a general XML editor, such as XML Notepad.  
  
 An **ssbdiangose** output file contains a DiagnosticInformation root element with two child types:  
  
-   A Banner element with header information.  
  
-   An Issue element for each issue that is reported by **ssbdiagnose**.  
  
## DiagnosticInformation Root Element  
  
-   [DiagnosticInformation Element &#40;ssbdiagnose&#41;](../Topic/DiagnosticInformation%20Element%20\(ssbdiagnose\).md)  
  
## Banner Element  
  
-   [Banner Element &#40;ssbdiagnose&#41;](../Topic/Banner%20Element%20\(ssbdiagnose\).md)  
  
## Issue Element  
  
-   [Issue Element &#40;ssbdiagnose&#41;](../Topic/Issue%20Element%20\(ssbdiagnose\).md)  
  
## See Also  
 [ssbdiagnose Utility &#40;Service Broker&#41;](../Topic/ssbdiagnose%20Utility%20\(Service%20Broker\).md)  
  
  