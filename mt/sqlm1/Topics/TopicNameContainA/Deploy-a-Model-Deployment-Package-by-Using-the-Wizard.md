---
title: Deploy a Model Deployment Package by Using the Wizard
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4f65dc60-0ff8-46e6-9988-5bc5b9603ad0
---
# Deploy a Model Deployment Package by Using the Wizard
  Use the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] model deployment wizard to deploy packages that contain model objects only. If you need to deploy a package with data, see [Deploy a Model Deployment Package by Using MDSModelDeploy](../../Topics\TopicNameContainA/Deploy-a-Model-Deployment-Package-by-Using-MDSModelDeploy.md).  
  
> [!IMPORTANT]  
>  Packages can be deployed to the edition of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] they were created in only. This means that packages created in [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] cannot be deployed to [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)].  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** functional area in the target [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] environment.  
  
-   A model deployment package must exist. For more information, see [Create a Model Deployment Package by Using the Wizard](../../Topics\TopicNameContainA/Create-a-Model-Deployment-Package-by-Using-the-Wizard.md).  
  
-   You must be an administrator in the environment where you are deploying the model. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
### To deploy a model deployment package of model objects only  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **System Administration**.  
  
2.  On the **Model View** page, from the menu bar, point to **System** and click **Deployment**.  
  
3.  On the **Model Deployment Wizard**, click **Deploy**.  
  
4.  Click **Browse**.  
  
5.  Find your deployment package \(.pkg file\) and click **Open**.  
  
6.  Click **Next**.  
  
7.  After the package is loaded, click **Next**.  
  
8.  If the model already exists, you can update it by selecting **Update the existing model**. To create a new model, select **Create a new model** and after you click **Next** you can type a name for the new model.  
  
9. Click **Finish** to exit the wizard.  
  
 **Notes:**  
  
-   If a subscription view in the package has the same name as a subscription view in an existing model, this warning is displayed: **Deployer subscription view renamed**. In addition, the view is created as *modelname.subscriptionviewname*. If this name is already in use, the subscription view is not created.  
  
-   The deployment process has four steps:  
  
    1.  The model objects are created.  
  
    2.  Subscription views are created.  
  
    3.  Business rules are created.  
  
-   When creating a new or cloned model, if the process fails during any step, the model is deleted.  
  
     When updating a model, if the process fails during any of the first three steps, it does not proceed beyond that step; however, changes that are already made are not rolled back.  
  
## Next Steps  
 File attributes, and user and group permissions are not included in model deployment packages. After you deploy a model, you must update these manually. For more information, see:  
  
-   [Assign Model Object Permissions &#40;Master Data Services&#41;](../Topic/Assign%20Model%20Object%20Permissions%20\(Master%20Data%20Services\).md)  
  
## See Also  
 [Deploying Models &#40;Master Data Services&#41;](../Topic/Deploying%20Models%20\(Master%20Data%20Services\).md)  
  
  