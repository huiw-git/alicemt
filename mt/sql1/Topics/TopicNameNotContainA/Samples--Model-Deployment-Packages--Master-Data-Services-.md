---
title: "Samples: Model Deployment Packages (Master Data Services)"
ms.custom: na
ms.date: 2016-04-08
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b31b7b6-319b-4840-b67d-eb383e7762b1
caps.latest.revision: 20
caps.handback.revision: 0
manager: jhubbard
---
# Samples: Model Deployment Packages (Master Data Services)
Sample model packages with data are included when you install [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)]. The default location for these package files is <drive\>\Program Files\Microsoft SQL Server\130\Master Data Services\Samples\Packages.  
  
 For instructions on how to deploy the sample model packages, see [Deploying Sample Models and Data](../../Topics/TopicNameNotContainA/Get-Started-with-Master-Data-Services--SQL-Server-2016-.md#deploySample). You deploy the sample model packages by using the [MDSModelDeploy tool](../../Topics/TopicNameContainA/Deploy-a-Model-Deployment-Package-by-Using-MDSModelDeploy.md).  
  
> [!IMPORTANT]  
>  **Sample Updates in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)]**  
>   
>  The sample packages were updated to support the following new capabilities.  
>   
>  -   Show Many-to-Many Relationships.  
>   
>      For more information, see [Show Many-to-Many Relationships in Derived Hierarchies (Master Data Services)](../../Topics/TopicNameNotContainA/Show-Many-to-Many-Relationships-in-Derived-Hierarchies--Master-Data-Services-.md).  
> -   Constrain Allowed Values for Domain-based Attributes.  
>   
>      For more information, see [Create a Domain-Based Attribute (Master Data Services)](../../Topics/TopicNameContainA/Create-a-Domain-Based-Attribute--Master-Data-Services-.md).  
> -   Require Approval for Entity Changes.  
>   
>      For more information, see [Approval Required (Master Data Services)](../../Topics/TopicNameNotContainA/Approval-Required--Master-Data-Services-.md).  
> -   Use Not and Else Operators in Business Rules  
>   
>      For more information, see [Business Rules (Master Data Services)](../../Topics/TopicNameNotContainA/Business-Rules--Master-Data-Services-.md).  
> -   Implement Custom Index  
>   
>      For more information, see [Custom Index (Master Data Services)](../../Topics/TopicNameNotContainA/Custom-Index--Master-Data-Services-.md).  
  
 In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], a package is an XML file that contains a deployable model structure, and optionally, data from the model. Use model packages to move copies of models from one MDS environment to another, or to create new models in your existing [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] environment.  
  
## See Also  
 [Deploy a Model Deployment Package by Using MDSModelDeploy](../../Topics/TopicNameContainA/Deploy-a-Model-Deployment-Package-by-Using-MDSModelDeploy.md)