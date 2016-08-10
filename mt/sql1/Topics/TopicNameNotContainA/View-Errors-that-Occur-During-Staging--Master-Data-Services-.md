---
title: "View Errors that Occur During Staging (Master Data Services)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6d2bff84-624b-47fc-a4a5-d9ea01d13412
caps.latest.revision: 9
caps.handback.revision: 0
manager: jhubbard
---
# View Errors that Occur During Staging (Master Data Services)
In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], you can view errors that occur during the staging process. In the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database, there are two views that show errors:  
  
-   stg.viw_name_MemberErrorDetails for leaf or consolidated member updates.  
  
-   stg.viw_name_RelationshipErrorDetails for hierarchy relationship updates.  
  
## Prerequisites  
 To perform this procedure:  
  
-   In the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database, you must have SELECT permissions to either the stg.viw_name_MemberErrorDetails or stg.viw_name_RelationshipErrorDetails view.  
  
-   You must be a model administrator. For more information, see [Administrators (Master Data Services)](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md).  
  
### To view staging errors  
  
1.  Open [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] and connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] instance for your [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database.  
  
2.  Open a new query.  
  
3.  Type the following text, replacing name with the name of your staging table, for example, viw_Product_MemberErrorDetails.  
  
     `SELECT * FROM stg.viw_name_MemberErrorDetails`  
  
4.  Excecute the query. Error details are displayed in the **ErrorDescription** field.  
  
## Next Steps  
 For more details on error messages, see [Staging Process Errors (Master Data Services)](../../Topics/TopicNameNotContainA/Staging-Process-Errors--Master-Data-Services-.md).  
  
## See Also  
 [Overview: Importing Data from Tables (Master Data Services)](../Topic/Overview:%20Importing%20Data%20from%20Tables%20\(Master%20Data%20Services\).md)   
 [Troubleshooting the Staging Process (Master Data Services)](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)