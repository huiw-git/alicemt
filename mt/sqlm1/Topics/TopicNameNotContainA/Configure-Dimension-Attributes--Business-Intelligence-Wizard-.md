---
title: Configure Dimension Attributes (Business Intelligence Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3d046e63-bcb1-4ab1-9c37-652463fa68c3
---
# Configure Dimension Attributes (Business Intelligence Wizard)
  Use the **Configure Dimension Attributes** page to map the dimension attributes to the attribute types that [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] uses to identify attributes for account dimensions.  
  
## Options  
 **Dimension type**  
 Displays the selected dimension type.  
  
> [!NOTE]  
>  This option is not available because the **Type** property of the dimension cannot be changed to a value other than *Account* for account dimensions.  
  
 **Dimension attributes**  
 Displays the valid attribute types that can be mapped to existing dimension attributes in the dimension.  
  
 **Include**  
 Select a check box to include the corresponding attribute type in the dimension.  
  
 **Attribute Type**  
 Lists the attribute types that can be mapped to existing dimension attributes in the dimension.  
  
 **Dimension Attribute**  
 Select the dimension attribute that should be mapped to the corresponding attribute type.  
  
 **Set measures to be semiadditive based on account type**  
 Select to change every measure associated with this dimension to be aggregated by account type.  
  
> [!NOTE]  
>  This option does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right\-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)].  
  
## See Also  
 [Business Intelligence Wizard F1 Help](../../Topics\TopicNameNotContainA/Business-Intelligence-Wizard-F1-Help.md)   
 [Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Cube%20Designer%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Dimension%20Designer%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
  