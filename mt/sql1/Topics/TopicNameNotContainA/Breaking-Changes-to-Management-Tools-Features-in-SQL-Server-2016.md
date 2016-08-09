---
title: "Breaking Changes to Management Tools Features in SQL Server 2016"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3ff3fad8-b569-4516-bd58-5a3efeb537e2
caps.latest.revision: 19
caps.handback.revision: 0
manager: jhubbard
---
# Breaking Changes to Management Tools Features in SQL Server 2016
This topic describes breaking changes to management tools features. These changes might break applications, scripts, or functionalities that are based on earlier versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. You might encounter these issues when you upgrade.  
  
## Breaking Changes in [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)]  
 Information to come later.  
  
## Breaking Changes in [!INCLUDE[ssSQL14](../../Topics/TopicNameContainA/tokens/ssSQL14_md.md)]  
 None.  
  
## Breaking Changes in [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)]  
  
### You cannot use [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)] Management Tools to create a utility control point on a [!INCLUDE[ssKilimanjaro](../../Topics/TopicNameContainA/tokens/ssKilimanjaro_md.md)] instance of SQL Server  
 To create a utility control point on an instance of [!INCLUDE[ssKilimanjaro](../../Topics/TopicNameContainA/tokens/ssKilimanjaro_md.md)], use [!INCLUDE[ssKilimanjaro](../../Topics/TopicNameContainA/tokens/ssKilimanjaro_md.md)] Management Tools.  
  
### SMO has been reversioned in [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)]  
 Code developed with SMO from [!INCLUDE[ssKilimanjaro](../../Topics/TopicNameContainA/tokens/ssKilimanjaro_md.md)] or earlier versions might not build against [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)] without minor modifications. For more information, see [Backward Compatibility in SMO](assetId:///2f986436-aaf2-4eaf-9809-df849d97d4fb).  
  
## See Also  
 [Backward Compatibility](assetId:///15d9117e-e2fa-4985-99ea-66a117c1e9fd)