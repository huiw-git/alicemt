---
title: General (Database Designer) (Analysis Services - Multidimensional Data)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 00c9c42b-db2b-4620-8fb6-1e165ff0cbdd
---
# General (Database Designer) (Analysis Services - Multidimensional Data)
  Use the **General** tab to change the properties of an [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database.  
  
 **To display the General tab**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project.  
  
2.  In **Solution Explorer**, right\-click the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project, click **Edit Database**, and then click the **General** tab.  
  
## Basic Options  
 Expand the **Basic** section to modify basic information about the database. This section contains the following options:  
  
 **Database name**  
 Displays the name of the database.  
  
> [!NOTE]  
>  To rename the database, in **Solution Explorer**, right\-click the project, and then click **Properties**. In the database's **Property Pages** dialog box, on the **Deployment** page, change the value of the **Database** property to the new database name.  
  
 **Description**  
 Type the description of the database.  
  
## Translations Options  
 Expand the **Translations** section to create and modify translations for the caption and description of the database. This section contains a grid with the following columns:  
  
 **Language**  
 Select the language for the specified transaction.  
  
 To add a new translation to the grid, click **\<Add new translation\>**.  
  
 **Translated Caption**  
 Type the caption of the database in the appropriate language for the translation. If blank, the default caption for the database is used.  
  
 **Translated Description**  
 Type the description of the database in the appropriate language for the translation. If blank, the default description for the database is used.  
  
## Account Type Mapping Options  
 Expand the **Account Type Mapping** section to modify the default aggregation function associated with each account **type** the selected database.  
  
> [!NOTE]  
>  This option is applicable only to cubes in which one or more measures use the *ByAccount* aggregation function.  
  
 This section contains a grid with the following columns:  
  
 **Name**  
 Type the name of the account type.  
  
 To add a new account type, click **\<Add new account type\>**.  
  
 **Alias**  
 Sets the default name of the account type, for use by the Business Intelligence Wizard. If this column is left empty, the default in the **Name** column will be used.  
  
 **Aggregation Function**  
 Select the aggregation function that will be used for the selected account type.  
  
## See Also  
 [Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](../Topic/Analysis%20Services%20Designers%20and%20Dialog%20Boxes%20\(Multidimensional%20Data\).md)   
 [Multidimensional Model Databases &#40;SSAS&#41;](../Topic/Multidimensional%20Model%20Databases%20\(SSAS\).md)   
 [Warnings &#40;Database Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Warnings%20\(Database%20Designer\)%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
  