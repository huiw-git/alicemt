---
title: "Could not load file or assembly &#39;Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089&#39; or one of its dependencies. The system cannot find the file specified."
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 81ed0f44-8782-462d-af8f-0ba5b975df27
caps.latest.revision: 8
caps.handback.revision: 0
manager: mblythe
---
# Could not load file or assembly &#39;Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089&#39; or one of its dependencies. The system cannot find the file specified.
In SharePoint 2010 environments that have [!INCLUDE[ssGemini](../../Topics/TopicNameContainA/tokens/ssGemini_md.md)] for SharePoint, this error will occur if you attempt a data feed export and the system is missing the required version of Microsoft ADO.NET Data Services.  
  
## Details  
  
|||  
|-|-|  
|Applies to|[!INCLUDE[ssGemini](../../Topics/TopicNameContainA/tokens/ssGemini_md.md)] for SharePoint|  
|Product Version|[!INCLUDE[ssKilimanjaro](../../Topics/TopicNameContainA/tokens/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)], [!INCLUDE[ssSQL14](../../Topics/TopicNameContainA/tokens/ssSQL14_md.md)]|  
|Cause|ADO.NET Data Services 3.5 SP1 was not found.|  
|Message Text|Could not load file or assembly 'Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The system cannot find the file specified|  
  
## Explanation  
 SharePoint 2010 includes an Export as Data Feed button that you can use to export a SharePoint list as an XML data feed. In addition, both Reporting Services in SharePoint mode and [!INCLUDE[ssGemini](../../Topics/TopicNameContainA/tokens/ssGemini_md.md)] for SharePoint support data feed features that require ADO.NET Data Services.  
  
 If ADO.NET Data Services is not installed, this error will occur when you request a data feed.  
  
## User Action  
  
1.  Go to the hardware and software requirements documentation for SharePoint 2010, [Determine Hardware and Software Requirements (SharePoint 2010)](http://go.microsoft.com/fwlink/?LinkId=169734) (http://go.microsoft.com/fwlink/?LinkId=169734).  
  
2.  In **Installing software prerequisites**, find the link for ADO.NET Data Services 3.5 that corresponds to the operating system you are using.  
  
3.  Click the link and run the setup program that installs the service.  
  
## See Also  
 [Deploy Power Pivot Solutions to SharePoint](../../Topics/TopicNameNotContainA/Deploy-Power-Pivot-Solutions-to-SharePoint.md)