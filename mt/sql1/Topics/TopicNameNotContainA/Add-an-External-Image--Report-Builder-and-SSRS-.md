---
title: "Add an External Image (Report Builder and SSRS)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 81fd4a1f-79a9-4967-86d6-6229413c0995
caps.latest.revision: 9
caps.handback.revision: 0
manager: mblythe
---
# Add an External Image (Report Builder and SSRS)
External images can be on a report server in native mode or SharePoint integrated mode, or on any other Web site. When you include external images in your report, you must verify that the image exists and that the report reader has permissions to access the image. For more information, see [Images (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Images--Report-Builder-and-SSRS-.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Topics/TopicNameContainA/tokens/ssRBRDDup_md.md)]  
  
### To add an external image  
  
1.  In report design view, on the **Insert** tab, click **Image**.  
  
2.  On the design surface, click and then drag a box to the desired size of the image.  
  
3.  On the **General** tab of the **Image Properties** dialog box, type a name in the **Name** text box or accept the default.  
  
4.  (Optional) In the **Tooltip** text box, type text to display when the user hovers over the image in a report rendered for HTML.  
  
5.  In **Select the image source**, select **External**.  
  
     For an image on a report server in native mode, type a relative path to the image in the **Use this image** box—for example, ../images/image1.jpg.  
  
     For an image on a report server in SharePoint integrated mode, or any other Web site, type a full URL to the image in the **Use this image** box—for example, http://<SharePointservername\>/<site\>/Documents/images/image1.jpg.  
  
     For more information, see [Specifying Paths to External Items (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Specifying-Paths-to-External-Items--Report-Builder-and-SSRS-.md).  
  
6.  (Optional) Click **Size**, **Visibility**, **Action**, or **Border** to set additional properties for the image report item.  
  
7.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
## See Also  
 [Embed an Image in a Report (Report Builder and SSRS)](../../Topics/TopicNameContainA/Embed-an-Image-in-a-Report--Report-Builder-and-SSRS-.md)   
 [Add a Background Image (Report Builder and SSRS)](../../Topics/TopicNameContainA/Add-a-Background-Image--Report-Builder-and-SSRS-.md)   
 [Image Properties Dialog Box, General (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Image-Properties-Dialog-Box--General--Report-Builder-and-SSRS-.md)