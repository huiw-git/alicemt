---
title: Import Data from Excel to Master Data Services (MDS Add-in for Excel)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 89fce454-a816-4b33-a26a-d1b9741d269b
---
# Import Data from Excel to Master Data Services (MDS Add-in for Excel)
  In the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)], publish data to the MDS repository when you are finished working in Excel and want to save your changes so other users have access to them.  
  
> [!NOTE]  
>  -   When you publish changes, comments on MDS\-managed cells are deleted.  
> -   A formula is not supported in an MDS\-managed cell. A formula in an MDS\-managed cell is handled as a text value.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **Explorer** functional area.  
  
-   The active worksheet must contain MDS\-managed data and you must have made changes or additions to the MDS\-managed data.  
  
-   If you are adding members, you do not have to specify a **Code** value if codes for the entity are being automatically generated. For more information, see [Automatic Code Creation &#40;Master Data Services&#41;](../Topic/Automatic%20Code%20Creation%20\(Master%20Data%20Services\).md).  
  
### To publish data to the MDS repository  
  
1.  In the **Publish and Validate** group, click **Publish**.  
  
2.  Optional. If the **Publish and Annotate** dialog box is displayed, choose to share the same annotation \(comment\) for all updates, or to annotate each change individually.  
  
3.  Optional. Select the **Do not show this dialog box again** check box. You can always show the dialog box in the future by choosing **Settings** and selecting the **Show Publish and Annotate dialog box when publishing** check box.  
  
4.  Click **Publish**.  
  
> [!NOTE]  
>  If you are adding new members \(rows\) to your worksheet and you cannot successfully publish them to the MDS repository, you may not have **Update** permission to all of the attributes in the worksheet. On the **Review** tab, in the **Changes** group, click **Unprotect Sheet** and try to publish again.  
  
## Next Steps  
 [Apply Business Rules &#40;MDS Add-in for Excel&#41;](../Topic/Apply%20Business%20Rules%20\(MDS%20Add-in%20for%20Excel\).md)  
  
## See Also  
 [Overview: Importing Data from Excel &#40;MDS Add-in for Excel&#41;](../Topic/Overview:%20Importing%20Data%20from%20Excel%20\(MDS%20Add-in%20for%20Excel\).md)   
 [Validating Data &#40;MDS Add-in for Excel&#41;](../Topic/Validating%20Data%20\(MDS%20Add-in%20for%20Excel\).md)  
  
  