---
title: Run a Package in SQL Server Data Tools
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 318e6beb-5540-4101-82a5-18c9d47f0570
---
# Run a Package in SQL Server Data Tools
  You typically run packages in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] during the development, debugging, and testing of packages. When you run a package from [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, the package always runs immediately.  
  
 While a package is running, [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer displays the progress of package execution on the **Progress** tab. You can view the start and finish time of the package and its tasks and containers, in addition to information about any tasks or containers in the package that failed. After the package finishes running, the run\-time information remains available on the **Execution Results** tab. For more information, see the section, "Progress Reporting," in the topic, [Debugging Control Flow](../../Topics\TopicNameNotContainA/Debugging-Control-Flow.md).  
  
 **Design\-time deployment**. When you run a package in [!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)], the package is built and then deployed to a folder. Before you run the package, you can specify the folder to which the package is deployed. If you do not specify a folder, the **bin** folder is used by default. This type of deployment is called design\-time deployment.  
  
### To run a package in SQL Server Data Tools  
  
1.  In Solution Explorer, if your solution contains multiple projects, right\-click the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project that contains the package, and then click **Set as StartUp Object** to set the startup project.  
  
2.  In Solution Explorer, if your project contains multiple packages, right\-click a package, and then click **Set as StartUp Object** to set the startup package.  
  
3.  To run a package, use one of the following procedures:  
  
    -   Open the package that you want to run and then click **Start Debugging** on the menu bar, or press F5. After the package finishes running, press Shift\+F5 to return to design mode.  
  
    -   In Solution Explorer, right\-click the package, and then click **Execute Package**.  
  
### To specify a different folder for design\-time deployment  
  
1.  In Solution Explorer, right\-click the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project folder that contains the package you want to run, and then click **Properties**.  
  
2.  In the **\<project name\> Property Pages** dialog box, click **Build**.  
  
3.  Update the value in the OutputPath property to specify the folder you want to use for design\-time deployment, and click **OK**.  
  
## See Also  
 [Execution of Projects and Packages](../../Topics\TopicNameNotContainA/Execution-of-Projects-and-Packages.md)   
 [Integration Services &#40;SSIS&#41; Packages](../Topic/Integration%20Services%20\(SSIS\)%20Packages.md)  
  
  