---
title: Models (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9f862a3d-25ab-41e9-b833-1db99959e825
---
# Models (Master Data Services)
  Models are the highest level of data organization in [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)]. A model defines the structure of data in your master data management solution. A model contains the following objects:  
  
-   Entities  
  
-   Attributes and attribute groups  
  
-   Explicit and derived hierarchies  
  
-   Collections  
  
 Models organize the structure of your master data. Your [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] implementation can have one or many models that each group similar kinds of data. In general, master data can be categorized in one of four ways: people, places, things, or concepts. For example, you can create a Product model to contain product\-related data or a Customer model to contain customer\-related data.  
  
 You can assign users and groups permission to view and update objects within the model. If you do not give permission to the model, it is not displayed.  
  
 At any given time, you can create copies of the master data within a model. These copies are called versions.  
  
 When you have defined a model in a test environment, you can deploy it, with or without the corresponding data, from the test environment to a production environment. This eliminates the need to recreate your models in your production environment.  
  
## How Models Relate to Other Objects  
 A model contains entities. Entities contain attributes, explicit hierarchies, and collections. Attributes can be contained in attribute groups. Domain\-based attributes exist when an entity is used as an attribute for another entity.  
  
 This image shows the relationships among the objects in a model.  
  
 ![Objects in a Master Data Services Model](../../Images\Image\ImageContaina/mds_conc_model_circles.gif "mds_conc_model_circles")  
  
> [!NOTE]  
>  Derived hierarchies are also model objects, but they are not shown in the image. Derived hierarchies are derived from the domain\-based attribute relationships that exist between entities. See [Derived Hierarchies &#40;Master Data Services&#41;](../Topic/Derived%20Hierarchies%20\(Master%20Data%20Services\).md) for more information.  
  
 Master data is the data that is contained in the model objects. In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], master data is stored as members in an entity.  
  
 Model objects are maintained in the **System Administration** functional area of the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] user interface.  
  
## Model Example  
 In the following example, the objects in the Product model logically group product\-related data.  
  
 ![Product Model Master Data Example](../../Images\Image\ImageNotContaina/mds_conc_model.gif "mds_conc_model")  
  
 Other common models are:  
  
-   Accounts, which could include entities such as balance sheet accounts, income statement accounts, statistics, and account type.  
  
-   Customer, which could include entities such as gender, education, occupation, and marital status.  
  
-   Geography, which could include entities such as postal codes, cities, counties, states, provinces, regions, territories, countries, and continents.  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Create a model to organize your master data.|[Create a Model &#40;Master Data Services&#41;](../Topic/Create%20a%20Model%20\(Master%20Data%20Services\).md)|  
|Change the name of an existing model.|[Edit Model &#40;Master Data Services&#41;](../Topic/Edit%20Model%20\(Master%20Data%20Services\).md)|  
|Delete an existing model.|[Delete a Model &#40;Master Data Services&#41;](../Topic/Delete%20a%20Model%20\(Master%20Data%20Services\).md)|  
  
## Related Content  
  
-   [Master Data Services Overview &#40;MDS&#41;](../Topic/Master%20Data%20Services%20Overview%20\(MDS\).md)  
  
-   [Entities &#40;Master Data Services&#41;](../Topic/Entities%20\(Master%20Data%20Services\).md)  
  
-   [Attributes &#40;Master Data Services&#41;](../Topic/Attributes%20\(Master%20Data%20Services\).md)  
  
-   [Deploying Models &#40;Master Data Services&#41;](../Topic/Deploying%20Models%20\(Master%20Data%20Services\).md)  
  
-   [Model Object Permissions &#40;Master Data Services&#41;](../Topic/Model%20Object%20Permissions%20\(Master%20Data%20Services\).md)  
  
  