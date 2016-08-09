---
title: "Define Account Intelligence (Dimension Wizard)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cbcff072-3a7e-4e98-858f-1b4265461561
caps.latest.revision: 28
caps.handback.revision: 0
manager: mblythe
---
# Define Account Intelligence (Dimension Wizard)
Use the **Define Account Intelligence** page to map account types defined on the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] instance to account types defined in the dimension attribute associated with the **Account Type** attribute type in the dimension.  
  
> [!NOTE]  
>  This page is displayed only if you selected **Standard dimension** on the **Select the Dimension Type** page and if you mapped a dimension attribute to the **Account Type** attribute type on the **Specify Dimension Type** page.  
  
## Options  
 **Source Table Account Types**  
 Displays the values contained in the dimension attribute assigned to the **Account Type** attribute type in the **Specify Dimension Key and Type** page.  
  
 **Built-In Account Types**  
 Select the account type defined on the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] instance that maps to the account types in the source table.  
  
 The following table lists the account types that are defined on an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] instance.  
  
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
 [Dimension Wizard F1 Help](../../Topics/TopicNameNotContainA/Dimension-Wizard-F1-Help.md)   
 [Dimensions (SSAS)](assetId:///2b114135-2572-4479-8c81-3ccf0cfeb9f7)   
 [Dimensions in Multidimensional Models](../../Topics/TopicNameNotContainA/Dimensions-in-Multidimensional-Models.md)