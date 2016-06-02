---
title: Add a BI Semantic Model Connection Content Type to a Library (Power Pivot for SharePoint)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 145505ed-50bc-4528-912b-2a5cd2566011
---
# Add a BI Semantic Model Connection Content Type to a Library (Power Pivot for SharePoint)
  A BI semantic model connection is created in SharePoint and provides redirection to business intelligence semantic model data in a [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] workbook or Analysis Services tabular model database on a network server. Before you can create a BI semantic model connection in SharePoint, you must extend a document library to allow the creation of a .bism file. This step only needs to be performed once for each library, but you will need to repeat it for any library from which you want to create .bism files. Best practices recommend that you create a centralized library for storing .bism files so that you can manage permissions in one place.  
  
> [!NOTE]  
>  If you already use SharePoint Data Connection Libraries, the BI Semantic Model Connection content type is automatically added to that library template. You can skip the steps in this section if you use a data connection library that already lets you create new BI semantic model connection documents.  
  
##  <a name="bkmk_addtype"></a> Add the content type to a document library  
 You must have at least the Manage Lists permission to add and configure a content type. This permission is built into the Design permission level and above.  
  
 The site that contains the document library must have feature activation for [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] for SharePoint. For more information, see [Activate Power Pivot Feature Integration for Site Collections in Central Administration](../../Topics\TopicNameNotContainA/Activate-Power-Pivot-Feature-Integration-for-Site-Collections-in-Central-Administration.md).  
  
1.  Open the document library for which you want to enable the BI Semantic Model Connection content type.  
  
2.  On the SharePoint ribbon, in Library Tools, click **Library**.  
  
3.  Click **Library Settings**.  
  
4.  In General Settings, click **Advanced settings**.  
  
5.  In Content Types, in the "Allow management of content types?" section, click **Yes**.  
  
6.  Click **OK**.  
  
7.  In the Content Types section, click **Add from existing site content types**. If you do not see this page, go back to the site, click **Library** in Library Tools, and then click **Library Settings**.  
  
8.  In Content Types, click **Add from existing site content types**.  
  
9. In Select site content types from:, select **Business Intelligence**.  
  
10. In Available Site Content Types, click **BI Semantic Model Connection File**, and then click **Add** to move the selected content type to the Content types to add list.  
  
11. Click **OK**.  
  
12. To verify you added the content type, go back to the library and click **New Document** on the Documents area of the library ribbon. You should see **BI Semantic Model Connection File** in the New Documents list.  
  
     ![New Document submenu in a SharePoint library](../../Images\Image\ImageContaina/SSAS_BISMConnection_New.gif "SSAS_BISMConnection_New")  
  
 After you enable the BI semantic model connection content type for a library, you can create a connection that provides redirection to business semantic model data that can be used by Excel or [!INCLUDE[ssCrescent](../../Token\Other/ssCrescent_md.md)] reports. Choose from the following links to learn more about this next step:  
  
 [Create a BI Semantic Model Connection to a Power Pivot Workbook](../../Topics\TopicNameContainA/Create-a-BI-Semantic-Model-Connection-to-a-Power-Pivot-Workbook.md)  
  
 [Create a BI Semantic Model Connection to a Tabular Model Database](../../Topics\TopicNameContainA/Create-a-BI-Semantic-Model-Connection-to-a-Tabular-Model-Database.md)  
  
## See Also  
 [Power Pivot BI Semantic Model Connection &#40;.bism&#41;](../Topic/Power%20Pivot%20BI%20Semantic%20Model%20Connection%20\(.bism\).md)   
 [Use a BI Semantic Model Connection in Excel or Reporting Services](../../Topics\TopicNameContainA/Use-a-BI-Semantic-Model-Connection-in-Excel-or-Reporting-Services.md)  
  
  