---
title: Validating Data (MDS Add-in for Excel)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 71eda98f-01a4-4fff-8246-be3133782523
---
# Validating Data (MDS Add-in for Excel)
  In the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)], when you publish data, two types of validation take place:  
  
-   Any defined business rules are applied to the data.  
  
-   Data is checked against allowed attribute values \(for example, number of characters or type of data\).  
  
 In each case, valid data is published to the MDS repository. Data that is not valid is highlighted, and details of the error can be shown in status columns.  
  
## When Validation Occurs  
 In the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] [!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)], validation occurs when you publish new or changed data, or when you manually apply business rules.  
  
 When business rules fail, the data is still published to the MDS repository. When input validation fails, the data is not published to the repository.  
  
## Validation Statuses  
 In the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)], the following validation statuses are possible.  
  
 For information about additional statuses, see [Validation Statuses &#40;Master Data Services&#41;](../Topic/Validation%20Statuses%20\(Master%20Data%20Services\).md)  
  
|Status|Description|  
|------------|-----------------|  
|Validation Failed|One or more values in the row failed validation against business rules defined by an MDS administrator.|  
|Validation Succeeded|All values in the row have passed validation against business rules.|  
  
## Input Statuses  
 In the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)], the following input statuses are possible  
  
|Status|Description|  
|------------|-----------------|  
|Error|One or more values in the row don’t meet system requirements like length or data type. The value is not updated in the MDS repository.|  
|New Row|The values in the row have not yet been published to the MDS repository.|  
|Read Only|The logged in user has Read\-only permissions to one or more values in the row and the value\(s\) cannot be updated.|  
|Unchanged|No values in the row have been changed in the worksheet. This does not mean the values in the repository have not changed; to get the latest data in the sheet, in the **Connect and Load** group, click **Load or Refresh**.<br /><br /> This is the default setting for each row.|  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Determine which values do not pass the defined business rules.|[Apply Business Rules &#40;MDS Add-in for Excel&#41;](../Topic/Apply%20Business%20Rules%20\(MDS%20Add-in%20for%20Excel\).md)|  
|To help correct validation errors, view all transactions that have taken place for a member.|[View All Annotations or Transactions for a Member &#40;MDS Add-in for Excel&#41;](../Topic/View%20All%20Annotations%20or%20Transactions%20for%20a%20Member%20\(MDS%20Add-in%20for%20Excel\).md)|  
  
## Related Content  
  
-   [Overview: Importing Data from Excel &#40;MDS Add-in for Excel&#41;](../Topic/Overview:%20Importing%20Data%20from%20Excel%20\(MDS%20Add-in%20for%20Excel\).md)  
  
  