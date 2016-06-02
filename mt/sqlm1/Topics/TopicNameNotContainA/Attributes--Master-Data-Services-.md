---
title: Attributes (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 95ecb75f-c559-41c3-933c-40ae60a4c2fd
robots: noindex,nofollow
---
# Attributes (Master Data Services)
  Attributes are objects that are contained in [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] entities. Attribute values describe the members of the entity. An attribute can be used to describe a leaf member, a consolidated member, or a collection.  
  
## How Attributes Relate to Other Model Objects  
 You can think of an attribute as a column in an entity table. An attribute value is the value used to describe a specific member.  
  
 ![Master Data Services Entity Represented as Table](../../Images\Image\ImageNotContaina/mds_conc_entity_table.gif "mds_conc_entity_table")  
  
 When you create an entity that contains many attributes, you can organize the attributes into attribute groups. For more information, see [Attribute Groups &#40;Master Data Services&#41;](../Topic/Attribute%20Groups%20\(Master%20Data%20Services\).md).  
  
## Required Attributes  
 When you create an entity, the Name and Code attributes are automatically created. Code requires a value and must be unique within the entity. You cannot remove the Name and Code attributes.  
  
## Attribute Types  
 There are three types of attributes:  
  
-   Free\-form attributes, which allow free\-form input for text, numbers, dates, or links.  
  
-   Domain\-based attributes, which are populated by entities. For more information, see [Domain-Based Attributes &#40;Master Data Services&#41;](../Topic/Domain-Based%20Attributes%20\(Master%20Data%20Services\).md).  
  
-   File attributes, which are used to store files, documents, or images. File attributes are intended to help with the consistency of your data by requiring files to have a specific extension. File attributes cannot be guaranteed to prevent a malicious user from uploading a file of a different type.  
  
### Numeric Free\-Form Attributes  
 Numeric free\-form attributes require special handling, because numeric free\-form attribute values are limited to the **SqlDouble** value type.  
  
 By default, a **SqlDouble** value contains 15 decimal digits of precision, although a maximum of 17 digits is maintained internally. The precision of a floating\-point number has several consequences:  
  
-   Two floating\-point numbers that appear equal for a particular precision might not compare equal because their least significant digits are different.  
  
-   A mathematical or comparison operation that uses a floating\-point number might not yield the same result if a decimal number is used because the floating\-point number might not exactly approximate the decimal number.  
  
-   A value might not *roundtrip* if a floating\-point number is involved. A value is said to roundtrip if an operation converts an original floating\-point number to another form, an inverse operation transforms the converted form back to a floating\-point number, and the final floating\-point number is equal to the original floating\-point number. The roundtrip might fail because one or more least significant digits are lost or changed in a conversion.  
  
## Attribute Examples  
 In the following example, the entity has the attributes: Name, Code, Subcategory, StandardCost, ListPrice, and FilePhoto. These attributes describe the members. Each member is represented by a single row of attribute values.  
  
 ![Bike Product Entity Table](../../Images\Image\ImageNotContaina/mds_conc_entity_table_w_data.gif "mds_conc_entity_table_w_data")  
  
 In the following example, the Product entity contains:  
  
-   The free\-form attributes of Name, Code, StandardCost and ListPrice.  
  
-   The domain\-based attribute of Subcategory.  
  
-   The file attribute of FilePhoto.  
  
 Subcategory is an entity that is used as a domain\-based attribute of Product. Category is an entity that is used as a domain\-based attribute of Subcategory. Like the Product entity, the Category and Subcategory entities each contain the default Name and Code attributes.  
  
 ![Product Entity Tree Structure](../../Images\Image\ImageNotContaina/mds_conc_entity_UI.gif "mds_conc_entity_UI")  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Create a new free\-form text attribute.|[Create a Text Attribute &#40;Master Data Services&#41;](../Topic/Create%20a%20Text%20Attribute%20\(Master%20Data%20Services\).md)|  
|Create a new free\-form numeric attribute.|[Create a Numeric Attribute &#40;Master Data Services&#41;](../Topic/Create%20a%20Numeric%20Attribute%20\(Master%20Data%20Services\).md)|  
|Create a new free\-form link attribute.|[Create a Link Attribute &#40;Master Data Services&#41;](../Topic/Create%20a%20Link%20Attribute%20\(Master%20Data%20Services\).md)|  
|Create a new file attribute.|[Create a File Attribute &#40;Master Data Services&#41;](../Topic/Create%20a%20File%20Attribute%20\(Master%20Data%20Services\).md)|  
|Create a new domain\-based attribute.|[Create a Domain-Based Attribute &#40;Master Data Services&#41;](../Topic/Create%20a%20Domain-Based%20Attribute%20\(Master%20Data%20Services\).md)|  
|Change the name of an existing attribute.|[Change an Attribute Name and Data Type &#40;Master Data Services&#41;](../Topic/Change%20an%20Attribute%20Name%20and%20Data%20Type%20\(Master%20Data%20Services\).md)|  
|Add existing attributes to a change tracking group.|[Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../Topic/Add%20Attributes%20to%20a%20Change%20Tracking%20Group%20\(Master%20Data%20Services\).md)|  
|Delete an existing attribute.|[Delete an Attribute &#40;Master Data Services&#41;](../Topic/Delete%20an%20Attribute%20\(Master%20Data%20Services\).md)|  
|Change the order of attributes.|[Change the Order of Attributes](../../Topics\TopicNameNotContainA/Change-the-Order-of-Attributes.md)|  
|Create a date attribute|[Create a Date Attribute &#40;Master Data Services&#41;](../Topic/Create%20a%20Date%20Attribute%20\(Master%20Data%20Services\).md)|  
  
## Related Content  
  
-   [Domain-Based Attributes &#40;Master Data Services&#41;](../Topic/Domain-Based%20Attributes%20\(Master%20Data%20Services\).md)  
  
-   [Attribute Groups &#40;Master Data Services&#41;](../Topic/Attribute%20Groups%20\(Master%20Data%20Services\).md)  
  
-   [Members &#40;Master Data Services&#41;](../Topic/Members%20\(Master%20Data%20Services\).md)  
  
-   [Leaf Permissions &#40;Master Data Services&#41;](../Topic/Leaf%20Permissions%20\(Master%20Data%20Services\).md)  
  
-   [Consolidated Permissions &#40;Master Data Services&#41;](../Topic/Consolidated%20Permissions%20\(Master%20Data%20Services\).md)  
  
  