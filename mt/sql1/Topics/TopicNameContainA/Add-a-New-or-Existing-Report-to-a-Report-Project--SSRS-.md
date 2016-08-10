---
title: "Add a New or Existing Report to a Report Project (SSRS)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8bc0bb53-ad8a-464d-bb6a-7fea5fa62c5c
caps.latest.revision: 19
caps.handback.revision: 0
manager: mblythe
---
# Add a New or Existing Report to a Report Project (SSRS)
In [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)], you can add a new report by using the Report Wizard or by adding a new blank report to your project. You can also add an existing report. After you add a report, you can see the report name listed under the **Reports** folder in your project.  
  
> [!NOTE]  
>  To preview a report with existing data sources, you must have permissions to the data source from your report authoring client. For more information, see [Create an Embedded or Shared Data Source (SSRS)](../../Topics/TopicNameNotContainA/Create-an-Embedded-or-Shared-Data-Source--SSRS-.md).  
  
 After you add a report, you can define data sources, datasets, and design a report layout. To get started, see [Tutorial: Creating a Basic Table Report (Reporting Services)](assetId:///3b539b4b-26f2-4c0b-b506-80f175679a46) or [Tables (Report Builder  and SSRS)](../../Topics/TopicNameNotContainA/Tables--Report-Builder--and-SSRS-.md).  
  
### To add a new report using the Report Wizard  
  
1.  In Solution Explorer, right-click the Reports folder, and then click **Add New Report**. The **Report Wizard** dialog box opens.  
  
     The wizard steps you through creating a data source, creating a dataset with a query, defining groups, specifying a layout, choosing a style that includes color and font, and creating the report. The steps include:  
  
    -   **Select a Data Source.** The first step in creating a report is to define a data source. Report Wizard provides a list of all shared data sources in the report project, in addition to an option to create a new data source.  
  
    -   **Design a Query.** The next step is to design a query. You can type the query string, build it using Query Designer, or import a query from another report. For information about Query Designers, see [Reporting Services Query Designers](../../Topics/TopicNameNotContainA/Reporting-Services-Query-Designers.md).  
  
    -   **Choose a Report Type.** The next step is to select the type of report you want. You can choose a tabular or matrix report. A tabular report has a fixed number of columns. A matrix, or crosstab, report has a variable number of columns based on the results of the query. A map report displays analytical against a geographic background.  
  
    -   **Choose a Style.** The next step is to apply a style to the report using a style template. Select a template to apply styles such as font, color, and border style to the report. Report Designer provides six style templates: Slate, Forest, Corporate, Bold, Ocean, and Generic. You can also add additional style templates.  
  
        > [!NOTE]  
        >  You can alter existing templates or add new ones by editing the StyleTemplates.xml file in the \Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\Business Intelligence Wizards\Reports\Styles\\<lang\> folder, where <lang\> is the language you are using (for example, if you are using the English language version of [!INCLUDE[vsprvs](../../Topics/TopicNameContainA/tokens/vsprvs_md.md)], the folder name is "EN"). This folder is located on the computer on which Report Designer is installed. There are two copies of the StyleTemplates.xml file. To modify the styles that are applied through the Report Wizard, edit the file that is in the folder created for the language you are using.  
  
    -   **Name the Report.**  The final step is to name the report and verify the fields that will be included in the report. When all steps are completed, Report Designer creates the report and adds it to the report server project.  
  
### To add a new blank report  
  
1.  From the **Project** menu, click **Add New Item**.  
  
2.  In **Templates**, click **Report**.  
  
3.  Click **Add**.  
  
     A new blank report is added to the project and displayed on the design surface.  
  
### To add an existing report  
  
1.  From the **Project** menu, click **Add**, and then  **Existing Item**.  
  
2.  Navigate to the location of the .rdl file, select it, and then click **Add**.  
  
     The report is added to the project under the **Reports** folder. When you close and re-open the project, reports are sorted alphabetically.  
  
## See Also  
 [Tutorials (Reporting Services)](assetId:///e90cc448-563b-4dbb-9776-defb8640ec66)