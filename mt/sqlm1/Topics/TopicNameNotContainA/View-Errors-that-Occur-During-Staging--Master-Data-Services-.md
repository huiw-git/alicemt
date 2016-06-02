---
title: View Errors that Occur During Staging (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6d2bff84-624b-47fc-a4a5-d9ea01d13412
---
# View Errors that Occur During Staging (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], you can view errors that occur during the staging process. In the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database, there are two views that show errors:  
  
-   stg.viw\_name\_MemberErrorDetails for leaf or consolidated member updates.  
  
-   stg.viw\_name\_RelationshipErrorDetails for hierarchy relationship updates.  
  
## Prerequisites  
 To perform this procedure:  
  
-   In the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database, you must have SELECT permissions to either the stg.viw\_name\_MemberErrorDetails or stg.viw\_name\_RelationshipErrorDetails view.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
### To view staging errors  
  
1.  Open [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] and connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] instance for your [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.  
  
2.  Open a new query.  
  
3.  Type the following text, replacing name with the name of your staging table, for example, viw\_Product\_MemberErrorDetails.  
  
     `SELECT * FROM stg.viw_name_MemberErrorDetails`  
  
4.  Excecute the query. Error details are displayed in the **ErrorDescription** field.  
  
## Next Steps  
 For more details on error messages, see [Staging Process Errors &#40;Master Data Services&#41;](../Topic/Staging%20Process%20Errors%20\(Master%20Data%20Services\).md).  
  
## See Also  
 [Overview: Importing Data from Tables &#40;Master Data Services&#41;](../Topic/Overview:%20Importing%20Data%20from%20Tables%20\(Master%20Data%20Services\).md)   
 [Troubleshooting the Staging Process \(Master Data Services\)](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)  
  
  