---
title: Search a Report Using URL Access
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6f3410c4-7944-448f-bae8-bab3e8152d46
---
# Search a Report Using URL Access
  You can search a report for a specific set of text using URL access. To search a report, set the value of the *rc:FindString* parameter on the URL equal to the text for which you want to search. Additionally, use the *rc:StartFind* and *rc:EndFind* parameters to narrow your search to specific pages within the report.  
  
## Example  
 The following URL access example searches for the first occurrence of the text "Mountain\-400" in the Product Catalog sample report starting with page one and ending with page five:  
  
```  
http://server/Reportserver?/SampleReports/Product Catalog&rs:Command=Render&rc:StartFind=1&rc:EndFind=5&rc:FindString=Mountain-400  
```  
  
## See Also  
 [URL Access &#40;SSRS&#41;](../Topic/URL%20Access%20\(SSRS\).md)   
 [URL Access Parameter Reference](../../Topics\TopicNameNotContainA/URL-Access-Parameter-Reference.md)  
  
  