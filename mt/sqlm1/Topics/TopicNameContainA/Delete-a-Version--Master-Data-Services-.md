---
title: Delete a Version (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a4eeffe-8379-4744-ad44-c27d8c8ac9a8
---
# Delete a Version (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], delete a version when you are sure you no longer need the master data associated with the version. After you delete a version, you cannot retrieve the associated master data.  
  
> [!WARNING]  
>  If a model has only one version and you delete it, the model becomes unusable.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to view the mdm.viw\_SYSTEM\_SCHEMA\_VERSION view and to execute the mds.udpVersionDelete stored procedure in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database. For more information, see [Database Object Security &#40;Master Data Services&#41;](../Topic/Database%20Object%20Security%20\(Master%20Data%20Services\).md).  
  
### To delete a version  
  
1.  Open [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] and connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] instance for your [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.  
  
2.  Open the mdm.viw\_SYSTEM\_SCHEMA\_VERSION view.  
  
3.  Find the version of the model you want to delete and copy the value in the **ID** field.  
  
4.  Create a new query.  
  
5.  Type the following text, replacing *version\_ID* with the value you copied in step 2.  
  
    ```  
    EXEC [mdm].[udpVersionDelete] @Version_ID='version_ID'  
    ```  
  
6.  Run the query.  
  
    > [!NOTE]  
    >  You may have to wait a few minutes before the Web application reflects the change.  
  
## See Also  
 [Versions &#40;Master Data Services&#41;](../Topic/Versions%20\(Master%20Data%20Services\).md)   
 [Copy a Version &#40;Master Data Services&#41;](../Topic/Copy%20a%20Version%20\(Master%20Data%20Services\).md)  
  
  