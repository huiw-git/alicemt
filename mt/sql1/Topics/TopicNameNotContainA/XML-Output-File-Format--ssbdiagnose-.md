---
title: "XML Output File Format (ssbdiagnose)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
caps.latest.revision: 14
caps.handback.revision: 0
manager: jhubbard
---
# XML Output File Format (ssbdiagnose)
The **ssbdiagnose** utility delivers its output as an XML file when you run it with the **-XML** switch. The XML output file lists header information and the errors that it found in the [!INCLUDE[ssSB](../../Topics/TopicNameContainA/tokens/ssSB_md.md)] configuration or conversation that was analyzed. You can write an application to analyze or report on the errors listed in the file. Or, you can view the XML file in a general XML editor, such as XML Notepad.  
  
 An **ssbdiangose** output file contains a DiagnosticInformation root element with two child types:  
  
-   A Banner element with header information.  
  
-   An Issue element for each issue that is reported by **ssbdiagnose**.  
  
## DiagnosticInformation Root Element  
  
-   [DiagnosticInformation Element (ssbdiagnose)](../../Topics/TopicNameNotContainA/DiagnosticInformation-Element--ssbdiagnose-.md)  
  
## Banner Element  
  
-   [Banner Element (ssbdiagnose)](../../Topics/TopicNameNotContainA/Banner-Element--ssbdiagnose-.md)  
  
## Issue Element  
  
-   [Issue Element (ssbdiagnose)](../../Topics/TopicNameNotContainA/Issue-Element--ssbdiagnose-.md)  
  
## See Also  
 [ssbdiagnose Utility (Service Broker)](../../Topics/TopicNameNotContainA/ssbdiagnose-Utility--Service-Broker-.md)