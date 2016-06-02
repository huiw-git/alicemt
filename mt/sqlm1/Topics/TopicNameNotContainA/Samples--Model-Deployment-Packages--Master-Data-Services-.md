---
title: Samples: Model Deployment Packages (Master Data Services)
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
  Sample model packages with data are included when you install [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)]. The default location for these package files is \<drive\>\\Program Files\\Microsoft SQL Server\\130\\Master Data Services\\Samples\\Packages.  
  
 For instructions on how to deploy the sample model packages, see [Deploying Sample Models and Data](Master%20Data%20Services.md\#deploySample). You deploy the sample model packages by using the [MDSModelDeploy tool](../../Topics\TopicNameContainA/Deploy-a-Model-Deployment-Package-by-Using-MDSModelDeploy.md).  
  
> [!IMPORTANT]  
>  **Sample Updates in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]**  
>   
>  The sample packages were updated to support the following new capabilities.  
>   
>  -   Show Many\-to\-Many Relationships.  
>   
>      For more information, see [M2M Relationship in Sample Model](../Topic/Show%20Many-to-Many%20Relationships%20in%20Derived%20Hierarchies%20\(Master%20Data%20Services\).md\#M2MSample).  
> -   Constrain Allowed Values for Domain\-based Attributes.  
>   
>      For more information, see [Create a Domain-Based Attribute &#40;Master Data Services&#41;](../Topic/Create%20a%20Domain-Based%20Attribute%20\(Master%20Data%20Services\).md).  
> -   Require Approval for Entity Changes.  
>   
>      For more information, see [Approval Required &#40;Master Data Services&#41;](../Topic/Approval%20Required%20\(Master%20Data%20Services\).md).  
> -   Use Not and Else Operators in Business Rules  
>   
>      For more information, see [Business Rule Examples](Business%20Rule%20Examples%20\(Master%20Data%20Services\).md).  
> -   Implement Custom Index  
>   
>      For more information, see [Custom Index &#40;Master Data Services&#41;](../Topic/Custom%20Index%20\(Master%20Data%20Services\).md).  
  
 In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], a package is an XML file that contains a deployable model structure, and optionally, data from the model. Use model packages to move copies of models from one MDS environment to another, or to create new models in your existing [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] environment.  
  
## See Also  
 [Deploy a Model Deployment Package by Using MDSModelDeploy](../../Topics\TopicNameContainA/Deploy-a-Model-Deployment-Package-by-Using-MDSModelDeploy.md)  
  
  