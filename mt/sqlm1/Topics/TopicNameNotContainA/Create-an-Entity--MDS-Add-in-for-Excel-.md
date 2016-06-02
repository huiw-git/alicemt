---
title: Create an Entity (MDS Add-in for Excel)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d354abb3-88fe-4b40-a374-f6256b84ffae
---
# Create an Entity (MDS Add-in for Excel)
  In the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)], administrators can create new entities to store data. When you create an entity you should load at least a sampling of the data you want to store.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** and **Explorer** functional areas.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
-   You must have an existing model to create the entity in. For more information, see [Create a Model &#40;Master Data Services&#41;](../Topic/Create%20a%20Model%20\(Master%20Data%20Services\).md).  
  
-   Ensure that your data meets the following requirements:  
  
    -   The data should have a header row.  
  
    -   It is helpful to have **Name** and **Code** columns. **Code** is a unique identifier for each row.  
  
    -   You should have at least one row of data other than the header. All columns do not need values, but the data should be representative of the data that will be in the entity.  
  
    -   If you have a column that contains a unique identifier \(known in MDS as **Code**\), ensure that the values are unique. If no column contains identifiers, you can have them generated automatically when you create the entity.  
  
    -   Ensure that no cells contain formulas.  
  
    -   Ensure that no cells contain time values. Date values can be saved in MDS but time values cannot.  
  
### To create an entity and load data  
  
1.  Open or create an Excel worksheet that contains data you want to load.  
  
2.  Select the cells you want to load into the new entity.  
  
3.  On the **Master Data** tab, in the **Build Model** group, click **Create Entity**.  
  
4.  If you are prompted to connect to an MDS repository, connect.  
  
5.  In the **Create Entity** dialog box, leave the default range or change it to apply to the data you want to load.  
  
6.  Do not clear the **My data has headers** check box.  
  
7.  From the **Model** list, select a model.  
  
8.  From the **Version** list, select a version.  
  
9. In the **New entity name** box, type a name for the entity.  
  
10. From the **Code** list, select the column that contains unique identifiers or have codes generated automatically.  
  
11. Optional. From the **Name** list, select a column that contains names for each member.  
  
12. Click **OK**. When the entity has been created successfully, a new header row is displayed, the cells are highlighted, and the sheet name is updated to match the entity name.  
  
## Next Steps  
  
-   To view errors that occurred, in the **Publish and Validate** group, click **Show Status**. ValidationStatus and InputStatus columns are displayed. For more information, see [Validating Data &#40;MDS Add-in for Excel&#41;](../Topic/Validating%20Data%20\(MDS%20Add-in%20for%20Excel\).md).  
  
-   Confirm that the attributes were created as the data type you expected.  
  
## See Also  
 [Create a Domain-based Attribute &#40;MDS Add-in for Excel&#41;](../Topic/Create%20a%20Domain-based%20Attribute%20\(MDS%20Add-in%20for%20Excel\).md)  
  
  