---
title: Change the Attribute Type (MDS Add-in for Excel)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9d3001d9-8d0f-4e4a-8e04-4f666bf0df69
---
# Change the Attribute Type (MDS Add-in for Excel)
  In the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)], administrators can change the attribute type when the data type or number of allowed characters is incorrect.  
  
 If you want to change the attribute type to create a constrained list \(domain\-based attribute\), see [Create a Domain-based Attribute &#40;MDS Add-in for Excel&#41;](../Topic/Create%20a%20Domain-based%20Attribute%20\(MDS%20Add-in%20for%20Excel\).md).  
  
> [!NOTE]  
>  You cannot update the type or length of the **Name** or **Code** columns.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** and **Explorer** functional areas.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
-   There must be an existing model, entity, and attribute.  
  
### To change the attribute type  
  
1.  In Excel, load the entity that contains the column \(attribute\) you want to change. For more information, see [Export Data to Excel from Master Data Services](../../Topics\TopicNameNotContainA/Export-Data-to-Excel-from-Master-Data-Services.md).  
  
2.  Click any cell in the column you want to change.  
  
3.  In the **Build Model** group, click **Attribute Properties**.  
  
4.  In the **Attribute Properties** dialog box, update settings as needed.  
  
5.  Click **OK**.  
  
## What happens when you change the attribute type?  
 If there is any dependency on the attribute, such as the attribute is referenced by any MDS business rule or derived hierarchy, you cannot change the data type of the attribute. You get an error stating that the attribute type cannot be modified because it is referenced by an object.  
  
 If there is any error during data type conversion for the attribute values, MDS does the following.  
  
-   Changes the data type of the attribute.  
  
-   Generates a copy of the attribute with the suffix “\_old” that contains the previous values. This is called a deprecated attribute.  
  
## See Also  
 [Attributes &#40;Master Data Services&#41;](../Topic/Attributes%20\(Master%20Data%20Services\).md)   
 [Building a Model &#40;MDS Add-in for Excel&#41;](../Topic/Building%20a%20Model%20\(MDS%20Add-in%20for%20Excel\).md)  
  
  