---
title: "Specify Dimension Type (Dimension Wizard)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3215282a-532d-4ff2-b721-286f088967fc
caps.latest.revision: 25
caps.handback.revision: 0
manager: mblythe
---
# Specify Dimension Type (Dimension Wizard)
Use the **Specify Dimension Type** page to define the dimension type and add special attribute types associated with the selected dimension type to the dimension.  
  
> [!NOTE]  
>  This page is displayed only if you selected **Standard dimension** on the **Select the Dimension Type** page.  
  
## Options  
 **Dimension type**  
 Select the dimension type for the dimension. The following table lists the dimension types that are available.  
  
|Value|Description|  
|-----------|-----------------|  
|**Accounts**|Account dimensions contain data and metadata that represents a list of accounts.<br /><br /> For more information about account dimensions, see [Create a Finance Account of parent-child type Dimension](../../Topics/TopicNameContainA/Create-a-Finance-Account-of-parent-child-type-Dimension.md).|  
|**BillOfMaterials**|Bill-of-material (or BOM) dimensions are regular dimensions in which the data and metadata represent inventory or manufacturing information, such as part lists for products.<br /><br /> For more information about regular dimensions, see [Dimension Types (SSAS)](assetId:///bd3195da-e762-4c98-b643-34c76e842343).|  
|**Channel**|Channel dimensions are regular dimensions in which the data and metadata represent channel information.<br /><br /> For more information about regular dimensions, see [Dimension Types (SSAS)](assetId:///bd3195da-e762-4c98-b643-34c76e842343).|  
|**Currency**|Currency dimensions contain data and metadata that represent currency information.<br /><br /> For more information about currency dimensions, see [Create a Currency type Dimension](../../Topics/TopicNameContainA/Create-a-Currency-type-Dimension.md).|  
|**Customers**|Customer dimensions are regular dimensions in which the data and metadata represent customer or contact information.<br /><br /> For more information about regular dimensions, see [Dimension Types (SSAS)](assetId:///bd3195da-e762-4c98-b643-34c76e842343).|  
|**Geography**|Geography dimensions are regular dimensions in which the data and metadata represent geographic information, such as cities or postal codes.<br /><br /> For more information about regular dimensions, see [Dimension Types (SSAS)](assetId:///bd3195da-e762-4c98-b643-34c76e842343).|  
|**Organization**|Organization dimensions are regular dimensions in which the data and metadata represent organizational information, such as employees or subsidiaries.<br /><br /> For more information about regular dimensions, see [Dimension Types (SSAS)](assetId:///bd3195da-e762-4c98-b643-34c76e842343).|  
|**Products**|Product dimensions are regular dimensions in which the data and metadata represent product information.<br /><br /> For more information about regular dimensions, see [Dimension Types (SSAS)](assetId:///bd3195da-e762-4c98-b643-34c76e842343).|  
|**Promotion**|Promotion dimensions are regular dimensions in which the data and metadata represent marketing promotion information.<br /><br /> For more information about regular dimensions, see [Dimension Types (SSAS)](assetId:///bd3195da-e762-4c98-b643-34c76e842343).|  
|**Quantitative**|Quantitative dimensions are regular dimensions in which the data and metadata represent quantitative information.<br /><br /> For more information about regular dimensions, see [Dimension Types (SSAS)](assetId:///bd3195da-e762-4c98-b643-34c76e842343).|  
|**Rates**|Rate dimensions contain data and metadata that represent exchange rate and currency conversion information.|  
|**Regular**|Regular dimensions are the most common dimension type used in [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)].<br /><br /> For more information about regular dimensions, see [Dimension Types (SSAS)](assetId:///bd3195da-e762-4c98-b643-34c76e842343).|  
|**Scenario**|Scenario dimensions are regular dimensions in which the data and metadata represent planning or strategic analysis information.<br /><br /> For more information about regular dimensions, see [Dimension Types (SSAS)](assetId:///bd3195da-e762-4c98-b643-34c76e842343).|  
|**Time**|Time dimensions contain time-oriented data and metadata.<br /><br /> For more information about time dimensions, see [Create a Date type Dimension](../../Topics/TopicNameContainA/Create-a-Date-type-Dimension.md).|  
|**Utility**|Utility dimensions are regular dimensions in which the data and metadata represents information that does not readily match another dimension type.<br /><br /> For more information about regular dimensions, see [Dimension Types (SSAS)](assetId:///bd3195da-e762-4c98-b643-34c76e842343).|  
  
## Dimension attributes Options  
  
> [!NOTE]  
>  The options in this section become available only if the selected **Dimension type** has special attribute types associated with it. Not all dimension types have special attribute types associated with them.  
  
 **Include**  
 Select to include the attribute type in the dimension.  
  
 **Attribute Type**  
 Displays the attribute type associated with the dimension type selected in **Dimension type**. For more information about attribute types, see [Type Element (Dimension Attribute)](assetId:///64fce1f5-39b7-4d0a-ae60-21203a03bd0d).  
  
 **Dimension Attribute**  
 Select the dimension attribute to which the Dimension Wizard will assign the special attribute type displayed in **Attribute Type**.  
  
## See Also  
 [Dimension Wizard F1 Help](../../Topics/TopicNameNotContainA/Dimension-Wizard-F1-Help.md)   
 [Dimensions (SSAS)](assetId:///2b114135-2572-4479-8c81-3ccf0cfeb9f7)   
 [Dimensions in Multidimensional Models](../../Topics/TopicNameNotContainA/Dimensions-in-Multidimensional-Models.md)