---
title: Define Account Intelligence (Business Intelligence Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fe4c204b-1031-4ac4-9916-8052ce2301cc
---
# Define Account Intelligence (Business Intelligence Wizard)
  Use the **Define Account Intelligence** page to map account types defined on the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance to account types defined by a source table in the data source that supplies the data for the account dimension.  
  
> [!NOTE]  
>  This page will appear if a dimension attribute was mapped to the **Account Type** attribute type on the **Configure Dimension Attributes** page.  
  
## Options  
 **Source Table Account Types**  
 Displays the values that are contained in the dimension attribute assigned to the **Account Type** attribute type on the **Configure Dimension Attributes** page.  
  
 **Built\-In Account Types**  
 Select the account type defined on the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance that maps to the account types in the source table.  
  
 The following table lists the account types that are defined on an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance.  
  
|Value|Description|  
|-----------|-----------------|  
|**Asset**|Value of things owned at a specific time.|  
|**Balance**|Count of something at a specific time.|  
|**Expense**|Value of things spent.|  
|**Flow**|Incremental count of things.|  
|**Income**|Value of things received.|  
|**Liability**|Value of things owed at a specific time.|  
|**Statistical**|Calculated ratio of something, or count of something that does not aggregate.|  
  
## See Also  
 [Business Intelligence Wizard F1 Help](../../Topics\TopicNameNotContainA/Business-Intelligence-Wizard-F1-Help.md)   
 [Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Cube%20Designer%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Dimension%20Designer%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
  