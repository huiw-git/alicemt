---
title: "Delete a Version (Master Data Services)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a4eeffe-8379-4744-ad44-c27d8c8ac9a8
caps.latest.revision: 7
caps.handback.revision: 0
manager: jhubbard
---
# Delete a Version (Master Data Services)
In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], delete a version when you are sure you no longer need the master data associated with the version. After you delete a version, you cannot retrieve the associated master data.  
  
> [!WARNING]  
>  If a model has only one version and you delete it, the model becomes unusable.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to view the mdm.viw_SYSTEM_SCHEMA_VERSION view and to execute the mds.udpVersionDelete stored procedure in the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database. For more information, see [Database Object Security (Master Data Services)](../../Topics/TopicNameNotContainA/Database-Object-Security--Master-Data-Services-.md).  
  
### To delete a version  
  
1.  Open [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] and connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] instance for your [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database.  
  
2.  Open the mdm.viw_SYSTEM_SCHEMA_VERSION view.  
  
3.  Find the version of the model you want to delete and copy the value in the **ID** field.  
  
4.  Create a new query.  
  
5.  Type the following text, replacing *version_ID* with the value you copied in step 2.  
  
    ```  
    EXEC [mdm].[udpVersionDelete] @Version_ID='version_ID'  
    ```  
  
6.  Run the query.  
  
    > [!NOTE]  
    >  You may have to wait a few minutes before the Web application reflects the change.  
  
## See Also  
 [Versions (Master Data Services)](../../Topics/TopicNameNotContainA/Versions--Master-Data-Services-.md)   
 [Copy a Version (Master Data Services)](../../Topics/TopicNameContainA/Copy-a-Version--Master-Data-Services-.md)