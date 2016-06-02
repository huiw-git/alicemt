---
title: Validation (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98eb49e7-b190-4a21-8316-08c07cde14ed
---
# Validation (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], data is validated to ensure its accuracy. Some validation occurs automatically, and other validation is based on business rules that are created by administrators.  
  
## When Data Validation Occurs  
 Validation occurs at different times, and is displayed differently in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] web application.  
  
|Validation Type|Standards Determined by|When it Occurs|Displayed in the MasterData Manager web UI as|Displayed in the Add\-in for Excel as|Is Data Saved to the MDS Repository?|  
|---------------------|-----------------------------|--------------------|---------------------------------------------------|-------------------------------------------|------------------------------------------|  
|Business rule validation|An MDS administrator|Automatically when a user adds or edits data.<br /><br /> Manually when a user applies business rules.<br /><br /> Manually when an administrator in the **Version Management** functional area of the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application validates a version against business rules.|Validation Errors|ValidationStatus|Yes|  
|Data type and content validation|An MDS administrator, when creating model objects \(for example, an attribute’s length or data type\)|Automatically when a user adds or edits data|Input Errors|InputStatus|No|  
|Data type and content validation|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)]|Automatically when a user adds or edits data|Input Errors|InputStatus|No|  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Create business rules and publish them, so that data is validated against them.|[Create and Publish a Business Rule &#40;Master Data Services&#41;](../Topic/Create%20and%20Publish%20a%20Business%20Rule%20\(Master%20Data%20Services\).md)|  
|Validate a version of data against business rules. Administrators only.|[Validate a Version against Business Rules &#40;Master Data Services&#41;](../Topic/Validate%20a%20Version%20against%20Business%20Rules%20\(Master%20Data%20Services\).md)|  
|Validate specific subsets of data against business rules. All users with permission to the **Explorer** functional area.|[Validate Specific Members against Business Rules &#40;Master Data Services&#41;](../Topic/Validate%20Specific%20Members%20against%20Business%20Rules%20\(Master%20Data%20Services\).md)|  
|Validate specific subsets of data against business rules. All users with permission to the **Explorer** functional area and using the [!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)].|[Apply Business Rules &#40;MDS Add-in for Excel&#41;](../Topic/Apply%20Business%20Rules%20\(MDS%20Add-in%20for%20Excel\).md)|  
  
## See Also  
 [Business Rules &#40;Master Data Services&#41;](../Topic/Business%20Rules%20\(Master%20Data%20Services\).md)  
  
  