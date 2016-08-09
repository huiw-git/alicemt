---
title: "Create a Currency type Dimension"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b1f037d1-ce47-4e47-a1c2-5ec9e781cff6
caps.latest.revision: 17
caps.handback.revision: 0
manager: mblythe
---
# Create a Currency type Dimension
In [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)], a currency type dimension is a dimension whose attributes represent a list of currencies for financial reporting purposes.  
  
 A currency dimension lets you add currency conversion capabilities to a cube in [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)]. To add currency conversion to a cube, you use the Business Intelligence Wizard define a Multidimensional Expressions (MDX) script command that converts currency measures to values that are appropriate for the locale of the client application. To create this MDX script, the Business Intelligence Wizard needs the following information:  
  
-   A currency dimension that represents source currencies. (This dimension is the source currency dimension.)  
  
-   A measure group that represents the exchange rates that will be used.  
  
 From this information, the Business Intelligence Wizard will design a currency conversion process that identifies the appropriate destination currency dimension (the currency dimension that represents destination currencies). Depending on the number of currency conversions that your business intelligence solution requires, the Business Intelligence Wizard can define multiple destination currency dimensions. For more information about defining currency conversions, see [Currency Conversions (Analysis Services)](../../Topics/TopicNameNotContainA/Currency-Conversions--Analysis-Services-.md).  
  
 To identify a dimension as a currency dimension, set the **Type** property of the dimension to **Currency**.  
  
## Dimension Structure  
 A currency dimension contains, at least, a key attribute identifying individual currencies in the dimension table for the currency dimension. The value of the key attribute is different in both source and destination currency dimensions:  
  
-   To identify an attribute as the key attribute of a source currency dimension, set the **Type** property of the attribute to **CurrencySource**.  
  
-   To identify an attribute as the destination currency dimension, set the **Type** property of the attribute to **CurrencyDestination**.  
  
 For reporting purposes, both source and destination currency dimensions can optionally contain the following attributes:  
  
-   A currency name attribute.  
  
     To identify an attribute as a currency name attribute, set the **Type** property of the attribute to **CurrencyName**.  
  
-   A currency source attribute.  
  
     To identify an attribute as a currency source attribute, set the **Type** property of the attribute to **CurrencySource**.  
  
-   A currency International Standards Organization (ISO) code.  
  
     To identify an attribute as a currency ISO code attribute, set the **Type** property of the attribute to **CurrencyIsoCode**.  
  
 For more information about attribute types, see [Configure Attribute Types](../../Topics/TopicNameNotContainA/Configure-Attribute-Types.md).  
  
## Defining Account Intelligence with the Business Intelligence Wizard  
 After you have defined an account dimension and added that dimension to a cube, you can use the Business Intelligence Wizard to add account intelligence functionality, such as identifying and mapping account types, to the dimension. For more information, see [Add Account Intelligence to a Dimension](../../Topics/TopicNameContainA/Add-Account-Intelligence-to-a-Dimension.md).  
  
## See Also  
 [Attributes (SSAS)](assetId:///59de1ea2-e7a9-4a53-9ee0-14be52e95643)   
 [Business Intelligence Wizard F1 Help](../../Topics/TopicNameNotContainA/Business-Intelligence-Wizard-F1-Help.md)   
 [Dimension Types (SSAS)](assetId:///bd3195da-e762-4c98-b643-34c76e842343)