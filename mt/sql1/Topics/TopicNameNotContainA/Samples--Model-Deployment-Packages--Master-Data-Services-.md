---
title: Samples: Model Deployment Packages (Master Data Services)
H1: na
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b31b7b6-319b-4840-b67d-eb383e7762b1
---
# Samples: Model Deployment Packages (Master Data Services)
  Sample model packages with data are included when you install [!INCLUDE[ssMDSshort](../../Token/Other/ssMDSshort_md.md)]. The default location for these package files is \<drive\>\\Program Files\\Microsoft SQL Server\\130\\Master Data Services\\Samples\\Packages.  
  
 For instructions on how to deploy the sample model packages, see [Deploying Sample Models and Data](Master%20Data%20Services.md\#deploySample). You deploy the sample model packages by using the [MDSModelDeploy tool](../../Topics/TopicNameContainA/Deploy-a-Model-Deployment-Package-by-Using-MDSModelDeploy.md).  
  
> [!IMPORTANT]  
>  **Sample Updates in [!INCLUDE[ssCurrent](../../Token/Other/ssCurrent_md.md)]**  
>   
>  The sample packages were updated to support the following new capabilities.  
>   
>  -   Show Many\-to\-Many Relationships.  
>   
>      For more information, see [M2M Relationship in Sample Model](../Topic/Show%20Many-to-Many%20Relationships%20in%20Derived%20Hierarchies%20\(Master%20Data%20Services\).md\#M2MSample).  
> -   Constrain Allowed Values for Domain\-based Attributes.  
>   
>      For more information, see [Create a Domain-Based Attribute &#40;Master Data Services&#41;](../../Topics/TopicNameContainA/Create-a-Domain-Based-Attribute--Master-Data-Services-.md).  
> -   Require Approval for Entity Changes.  
>   
>      For more information, see [Approval Required &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Approval-Required--Master-Data-Services-.md).  
> -   Use Not and Else Operators in Business Rules  
>   
>      For more information, see [Business Rule Examples](../../Topics/TopicNameNotContainA/Business-Rule-Examples--Master-Data-Services-.md).  
> -   Implement Custom Index  
>   
>      For more information, see [Custom Index &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Custom-Index--Master-Data-Services-.md).  
  
 In [!INCLUDE[ssMDSshort](../../Token/Other/ssMDSshort_md.md)], a package is an XML file that contains a deployable model structure, and optionally, data from the model. Use model packages to move copies of models from one MDS environment to another, or to create new models in your existing [!INCLUDE[ssMDSshort](../../Token/Other/ssMDSshort_md.md)] environment.  
  
## See Also  
 [Deploy a Model Deployment Package by Using MDSModelDeploy](../../Topics/TopicNameContainA/Deploy-a-Model-Deployment-Package-by-Using-MDSModelDeploy.md)  
  
  