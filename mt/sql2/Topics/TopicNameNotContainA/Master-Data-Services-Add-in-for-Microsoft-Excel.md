---
title: Master Data Services Add-in for Microsoft Excel
H1: na
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 33d9c8fc-9602-494d-b9ab-8f0f42785974
---
# Master Data Services Add-in for Microsoft Excel
  With the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)][!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/includes/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Topics/TopicNameContainA/includes/ssMDSXLS_md.md)], you can load filtered lists of data from MDS into Excel, where you can work with it just as you would any other data. When you are done, you can publish the data back to MDS, where it is centrally stored. Security determines which data you can view and update.  
  
 If you are an administrator, use the [!INCLUDE[ssMDSXLS](../../Topics/TopicNameContainA/includes/ssMDSXLS_md.md)] to create entities and attributes and to load them with data. This eliminates the need to use any other tools to load data into your models.  
  
 In the [!INCLUDE[ssMDSXLS](../../Topics/TopicNameContainA/includes/ssMDSXLS_md.md)], you can use Data Quality Services (DQS) to match data before loading it into MDS. This helps to prevent duplicate data in MDS.  
  
> [!NOTE]  
>  You can download the latest [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/includes/ssCurrent_md.md)] [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/includes/ssMDSshort_md.md)] [!INCLUDE[ssMDSXLS](../../Topics/TopicNameContainA/includes/ssMDSXLS_md.md)] from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=398159).  
  
## Terms  
 When working with the Add-in, you may encounter the following terms. For more information about these concepts, see [Master Data Services Overview &#40;MDS&#41;](../../Topics/TopicNameNotContainA/Master-Data-Services-Overview--MDS-.md).  
  
-   The *MDS repository* is where all master data is stored. It is a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] database that is configured to store MDS data. To work with data from the repository, you load data it into Excel; when you’re done working with it, you publish changes back to the repository. Administrators can add new entities and attributes to the repository.  
  
-   *MDS-managed data* is data that is stored in the MDS repository and that you load into Excel, where the data is displayed as highlighted rows. You can add data that is not MDS-managed to your worksheet, and it is not affected when you refresh the MDS-managed data.  
  
-   A *model* is a container of data. Versions of these containers can be created, and usually the latest version is the most recent. For more information, see [Models &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Models--Master-Data-Services-.md).  
  
-   An *entity* is a list of data. You might think of an entity as a table in a database. For example, the **Color** entity might contain a list of colors. For more information, see [Entities &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Entities--Master-Data-Services-.md).  
  
-   A *member* is a row of data (a record). Each entity contains members. An example of a member is **Blue**. For more information, see [Members &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Members--Master-Data-Services-.md).  
  
-   An *attribute* is a column of data. Each member has attributes. For example, the **Code** attribute for the **Blue** member is **B**. For more information about attributes, see [Attributes &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Attributes--Master-Data-Services-.md).  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Create a connection to a [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/includes/ssMDSshort_md.md)] repository.|[Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;](../../Topics/TopicNameNotContainA/Connect-to-an-MDS-Repository--MDS-Add-in-for-Excel-.md)|  
|Load MDS-managed data into Excel.|[Export Data to Excel from Master Data Services](../../Topics/TopicNameNotContainA/Export-Data-to-Excel-from-Master-Data-Services.md)|  
|Save a shortcut query that you can use open the currently displayed MDS-managed data in the future.|[Save a Shortcut Query File &#40;MDS Add-in for Excel&#41;](../../Topics/TopicNameContainA/Save-a-Shortcut-Query-File--MDS-Add-in-for-Excel-.md)|  
|Share shortcuts with others.|[Email a Shortcut Query File &#40;MDS Add-in for Excel&#41;](../../Topics/TopicNameContainA/Email-a-Shortcut-Query-File--MDS-Add-in-for-Excel-.md)|  
|View all changes that have been made to a member.|[View All Annotations or Transactions for a Member &#40;MDS Add-in for Excel&#41;](../../Topics/TopicNameContainA/View-All-Annotations-or-Transactions-for-a-Member--MDS-Add-in-for-Excel-.md)|  
|Before publishing new data, find out whether duplication exists.|[Match Similar Data &#40;MDS Add-in for Excel&#41;](../../Topics/TopicNameNotContainA/Match-Similar-Data--MDS-Add-in-for-Excel-.md)|  
|Publish data from a worksheet into the MDS repository.|[Import Data from Excel to Master Data Services &#40;MDS Add-in for Excel&#41;](../../Topics/TopicNameNotContainA/Import-Data-from-Excel-to-Master-Data-Services--MDS-Add-in-for-Excel-.md)|  
|Create a new entity with data in the worksheet. (Administrators only)|[Create an Entity &#40;MDS Add-in for Excel&#41;](../../Topics/TopicNameNotContainA/Create-an-Entity--MDS-Add-in-for-Excel-.md)|  
|Create a domain-based attribute, also known as a constrained list. (Administrators only)|[Create a Domain-based Attribute &#40;MDS Add-in for Excel&#41;](../../Topics/TopicNameContainA/Create-a-Domain-based-Attribute--MDS-Add-in-for-Excel-.md)|  
|Set properties for loading and publishing data in the Master Data Services Add-in for Excel. (Administrators only)|[Setting Properties for Master Data Services Add-in for Excel](../../Topics/TopicNameNotContainA/Setting-Properties-for-Master-Data-Services-Add-in-for-Excel.md)|  
  
## Related Content  
  
-   [Connections &#40;MDS Add-in for Excel&#41;](../../Topics/TopicNameNotContainA/Connections--MDS-Add-in-for-Excel-.md)  
  
-   [Overview: Exporting Data to Excel &#40;MDS Add-in for Excel&#41;](../Topic/Overview:%20Exporting%20Data%20to%20Excel%20\(MDS%20Add-in%20for%20Excel\).md)  
  
-   [Shortcut Query Files &#40;MDS Add-in for Excel&#41;](../../Topics/TopicNameNotContainA/Shortcut-Query-Files--MDS-Add-in-for-Excel-.md)  
  
-   [Refreshing Data &#40;MDS Add-in for Excel&#41;](../../Topics/TopicNameNotContainA/Refreshing-Data--MDS-Add-in-for-Excel-.md)  
  
-   [Overview: Importing Data from Excel &#40;MDS Add-in for Excel&#41;](../Topic/Overview:%20Importing%20Data%20from%20Excel%20\(MDS%20Add-in%20for%20Excel\).md)  
  
-   [Validating Data &#40;MDS Add-in for Excel&#41;](../../Topics/TopicNameNotContainA/Validating-Data--MDS-Add-in-for-Excel-.md)  
  
-   [Data Quality Matching in the MDS Add-in for Excel](../../Topics/TopicNameNotContainA/Data-Quality-Matching-in-the-MDS-Add-in-for-Excel.md)  
  
-   [Building a Model &#40;MDS Add-in for Excel&#41;](../../Topics/TopicNameContainA/Building-a-Model--MDS-Add-in-for-Excel-.md)  
  
-   [Setting Properties for Master Data Services Add-in for Excel](../../Topics/TopicNameNotContainA/Setting-Properties-for-Master-Data-Services-Add-in-for-Excel.md)  
  
-   [Security &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Security--Master-Data-Services-.md)  
  
  