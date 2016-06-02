---
title: Add HTML into a Report (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 30bd631a-f774-48e7-a13a-b6c2eb54d9bb
---
# Add HTML into a Report (Report Builder and SSRS)
  Using a placeholder, you can import HTML from a field in your dataset for use in the report. By default, a placeholder represents plain text, so you will need to change the placeholder mark\-up type to HTML. For more information, see [Importing HTML into a Report &#40;Report Builder and SSRS&#41;](../Topic/Importing%20HTML%20into%20a%20Report%20\(Report%20Builder%20and%20SSRS\).md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
### To add HTML from a field in your dataset into a text box  
  
1.  On the **Insert** tab, click **List**. Click the design surface, and then drag to create a box that is the size you want.  
  
     The **Dataset Properties** dialog box opens. You can use a shared dataset or a dataset embedded in your report. For more information, click [Dataset Properties Dialog Box, Query &#40;Report Builder&#41;](../Topic/Dataset%20Properties%20Dialog%20Box,%20Query%20\(Report%20Builder\).md) or [Dataset Properties Dialog Box, Query](../../Topics\TopicNameNotContainA/Dataset-Properties-Dialog-Box,-Query.md).  
  
2.  On the **Insert** tab, click **Text Box**. Click in the list, and then drag to create a box that is the size you want.  
  
3.  Drag an HTML field from your dataset into the text box. A placeholder is created for your field.  
  
4.  Right\-click the placeholder, and then click **Placeholder Properties**.  
  
5.  On the **General** tab, verify that the **Value** box contains an expression that evaluates to the field you dropped in step 3.  
  
6.  Click **HTML \- Interpret HTML tags as styles**. This causes the field to be evaluated as HTML.  
  
7.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
## See Also  
 [Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20Numbers%20and%20Dates%20\(Report%20Builder%20and%20SSRS\).md)   
 [Formatting Lines, Colors, and Images &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20Lines,%20Colors,%20and%20Images%20\(Report%20Builder%20and%20SSRS\).md)   
 [Placeholder Properties Dialog Box, General &#40;Report Builder and SSRS&#41;](../Topic/Placeholder%20Properties%20Dialog%20Box,%20General%20\(Report%20Builder%20and%20SSRS\).md)  
  
  