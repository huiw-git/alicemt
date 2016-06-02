---
title: XML Input File Sample with Inline Workload (DTA)
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
ms.assetid: 7c04fe1d-6669-44a1-8b73-36d469e9b002
---
# XML Input File Sample with Inline Workload (DTA)
  Copy and paste this sample of an XML input file that specifies a workload with the **EventString** element into your favorite XML editor or text editor. You can use the **EventString** element to specify a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] script workload in the XML input file instead of using a separate workload file. After copying this sample into your editing tool, replace the values specified for the **Server**, **Database**, **Schema**, **Table**, **Workload**, **EventString**, and **TuningOptions** elements with those for your specific tuning session. For more information about all of the attributes and child elements that you can use with these elements, see the [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../Topic/XML%20Input%20File%20Reference%20\(Database%20Engine%20Tuning%20Advisor\).md). The following sample uses only a subset of available attribute and child element options.  
  
## Code  
 [!CODE [InputFileSamples#InlineWorkloadInputFile](../CodeSnippet/SQL15/dta_xml/inputfilesamples#inlineworkloadinputfile)]  
  
## Comments  
 `USE database_name` statements can be specified in the inline workload that is contained in the **EventString** element.  
  
## See Also  
 [Start and Use the Database Engine Tuning Advisor](../../Topics\TopicNameNotContainA/Start-and-Use-the-Database-Engine-Tuning-Advisor.md)   
 [View and Work with the Output from the Database Engine Tuning Advisor](../../Topics\TopicNameNotContainA/View-and-Work-with-the-Output-from-the-Database-Engine-Tuning-Advisor.md)   
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../Topic/XML%20Input%20File%20Reference%20\(Database%20Engine%20Tuning%20Advisor\).md)  
  
  