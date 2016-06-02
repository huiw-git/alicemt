---
title: Business Rules (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a9f9e41a-2461-4845-b947-58b3a205543f
---
# Business Rules (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], a business rule is a rule that you use to ensure the quality and accuracy of your master data. You can use a business rule to automatically update data, to send email, or to start a business process or workflow.  
  
 To view examples of business rules, see [Business Rule Examples &#40;Master Data Services&#41;](../Topic/Business%20Rule%20Examples%20\(Master%20Data%20Services\).md).  
  
## Create and Publish Business Rules  
 Business rules are **If\/Then\/Else** statements that you create in [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)]. If an attribute value meets a specified condition, then an action is taken, otherwise a Else action is taken. Possible actions include setting a default value or changing a value. These actions can be combined with sending an email notification.  
  
 Business rules can be based on specific attribute values \(for example, take action if Color\=Blue\), or when attribute values change \(for example, take action if the value of the Color attribute changes\). For more information about tracking non\-specific changes, see [Change Tracking &#40;Master Data Services&#41;](../Topic/Change%20Tracking%20\(Master%20Data%20Services\).md).  
  
 To use business rules you must first create and publish your rules, then apply the published rules to data. You can apply rules to subsets of data or to all data for a version by validating the version. A version cannot be committed until all attributes pass business rule validation.  
  
 If a user attempts to add an attribute value that doesn’t pass business rule validation, the value can still be saved. You can review and correct validation issues, which are displayed in [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)].  
  
 When you create a model deployment package, if you want to include business rules you must include data from the version in the package.  
  
 If you create a business rule that uses the **OR** operator, you should create a separate rule for each conditional statement that can be evaluated independently. You can then exclude rules as needed, providing more flexibility and easier troubleshooting.  
  
## How Business Rules Are Applied  
 You can set priority order for rules to run in by moving business rules up and down. However, before priority is taken into account, business rules are applied based on the type of action the rule takes. The order is as follows:  
  
1.  **Default Value**  
  
2.  **Change Value**  
  
3.  **Validation**  
  
4.  **External Action**  
  
5.  **User Defined Action Script**  
  
 Within these groups, actions are applied in priority order, from lowest to highest. So for example, four separate rules might have **Default Value** actions. The **Default Value** action that occurs first depends on the priority order specified in the web UI.  
  
 Other important notes about applying rules:  
  
-   If a business rule is excluded or is not published with a status of **Active**, the rule is still available but is not included when business rules are applied.  
  
-   Business rules apply to the attribute values for all leaf or all consolidated members, not both.  
  
-   Business rules can be applied to any version of a model that is **Open** or **Locked**.  
  
-   Changes made to data when business rules are applied are not logged as transactions.  
  
-   A business rule cannot contain more than one **start workflow** action.  
  
## System Settings  
 There are two settings in [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)] that affect business rules. You can adjust these settings in [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)] or directly in the System Settings table. For more information, see [System Settings &#40;Master Data Services&#41;](../Topic/System%20Settings%20\(Master%20Data%20Services\).md).  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Create and publish a new business rule.|[Create and Publish a Business Rule &#40;Master Data Services&#41;](../Topic/Create%20and%20Publish%20a%20Business%20Rule%20\(Master%20Data%20Services\).md)|  
|Add multiple conditions to a business rule.|[Add Multiple Conditions to a Business Rule &#40;Master Data Services&#41;](../Topic/Add%20Multiple%20Conditions%20to%20a%20Business%20Rule%20\(Master%20Data%20Services\).md)|  
|Create a business rule to require that attributes have values.|[Require Attribute Values &#40;Master Data Services&#41;](../Topic/Require%20Attribute%20Values%20\(Master%20Data%20Services\).md)|  
|Create a business rule to take an action based on changes to attribute values.|[Initiate Actions Based on Attribute Value Changes &#40;Master Data Services&#41;](../Topic/Initiate%20Actions%20Based%20on%20Attribute%20Value%20Changes%20\(Master%20Data%20Services\).md)|  
|Create a business rule to take user\-defined script as a condition|[Business Rules Extension &#40;Master Data Services&#41;](../Topic/Business%20Rules%20Extension%20\(Master%20Data%20Services\).md)|  
|Create a business rule to take a user\-defined script as an action|[Business Rules Extension &#40;Master Data Services&#41;](../Topic/Business%20Rules%20Extension%20\(Master%20Data%20Services\).md)|  
|Change the name of an existing business rule.|[Change a Business Rule Name &#40;Master Data Services&#41;](../Topic/Change%20a%20Business%20Rule%20Name%20\(Master%20Data%20Services\).md)|  
|Configure [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] to send notifications when business rules are applied.|[Configure Business Rules to Send Notifications &#40;Master Data Services&#41;](../Topic/Configure%20Business%20Rules%20to%20Send%20Notifications%20\(Master%20Data%20Services\).md)|  
|Apply business rules to specific members.|[Validate Specific Members against Business Rules &#40;Master Data Services&#41;](../Topic/Validate%20Specific%20Members%20against%20Business%20Rules%20\(Master%20Data%20Services\).md)|  
|Exclude a business rule so it is not used.|[Exclude a Business Rule &#40;Master Data Services&#41;](../Topic/Exclude%20a%20Business%20Rule%20\(Master%20Data%20Services\).md)|  
|Delete an existing business rule.|[Delete a Business Rule &#40;Master Data Services&#41;](../Topic/Delete%20a%20Business%20Rule%20\(Master%20Data%20Services\).md)|  
  
## Related Content  
  
-   [Master Data Services Overview &#40;MDS&#41;](../Topic/Master%20Data%20Services%20Overview%20\(MDS\).md)  
  
-   [Versions &#40;Master Data Services&#41;](../Topic/Versions%20\(Master%20Data%20Services\).md)  
  
-   [Validation &#40;Master Data Services&#41;](../Topic/Validation%20\(Master%20Data%20Services\).md)  
  
-   [Change Tracking &#40;Master Data Services&#41;](../Topic/Change%20Tracking%20\(Master%20Data%20Services\).md)  
  
  