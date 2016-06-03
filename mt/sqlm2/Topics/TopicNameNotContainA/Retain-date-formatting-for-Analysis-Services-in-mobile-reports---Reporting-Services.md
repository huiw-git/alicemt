---
title: Retain date formatting for Analysis Services in mobile reports | Reporting Services
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e9a9a199-40e3-4381-b250-1b99fb83aa62
---
# Retain date formatting for Analysis Services in mobile reports | Reporting Services
Add a measure to a shared dataset in Report Builder so dates in [!INCLUDE[ssASnoversion_md](../../Token\Other/ssASnoversion_md.md)] data sources retain their data type in [!INCLUDE[SS_MobileReptPub_Long](../../Token\Other/SS_MobileReptPub_Short.md)].

The default return type for [!INCLUDE[ssASnoversion_md](../../Token\Other/ssASnoversion_md.md)] queries is a string.  When you build a dataset in [!INCLUDE[ssRSnoversion_md](../../Token\Other/ssRSnoversion_md.md)] Report Builder, the string type is respected and gets saved to the server. 

However, when the JSON table renderer processes the dataset, it reads the value of the column as a string and renders strings.  Then when [!INCLUDE[SS_MobileReptPub_Long](../../Token\Other/SS_MobileReptPub_Long.md)] fetches the table, it also only sees strings.

The workaround for this is to add a calculated member when you're creating a shared dataset in Report Builder. It works for both [!INCLUDE[ssASnoversion_md](../../Token\Other/ssASnoversion_md.md)] multidimensional and tabular models.

## Create a measure to retain a date field data type

1. Create a measure to hold the value of the date field in question, and in the expression field, choose the hierarchy/level of the date and append **.CurrentMember.MemberValue**. For example:
 
   [Internet Sales].[Ship Date].CurrentMember.MemberValue
   
   ![ssas-calculated-member-report-builder](../../Images\Image\ImageNotContaina/ssas-calculated-member-report-builder.png)
   
2. Now you can append this calculated member to the set of columns by dragging it from the Calculated Members list in the bottom left and dropping it in the column grid on the right.  

   ![ssas-query-designer-calculated-member-report-builder](../../Images\Image\ImageNotContaina/ssas-query-designer-calculated-member-report-builder.png) 
   
### See also

-  [Data for Reporting Services mobile reports](../../Topics\TopicNameNotContainA/Data-for-Reporting-Services-mobile-reports.md)
-  [Prepare data for Reporting Services mobile reports](../../Topics\TopicNameNotContainA/Prepare-data-for-Reporting-Services-mobile-reports.md)