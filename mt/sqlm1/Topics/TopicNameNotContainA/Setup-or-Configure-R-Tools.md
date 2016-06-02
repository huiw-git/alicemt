---
title: Setup or Configure R Tools
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c04ae30-d391-4369-9742-d2b275e14c0d
---
# Setup or Configure R Tools
  Microsoft R Server provides all the base R libraries, the Scale R packages, and standard R tools that you need to develop and test R code. However, if you want to use a dedicated R development environment, there are several available, including many free tools.  
  
## Basic R Tools  
 Additional tools aren't required in an installation of Microsoft R Server, as all the standard base R tools are included in `C:\Program Files\Microsoft SQL Server\130\R_SERVER\bin`:  
  
-   **RTerm**: A command\-line tool for running R scripts. Rterm.exe can allocate more memory when running in 64\-bit Windows  
  
-   **RGui.exe**:  A simple interactive editor for R. The command\-line arguments are  
    the same for RGui.exe and RTerm  
  
-   **RScript**: A command\-line tool for running R scripts in batch mode.  
  
> [!TIP]  
>  Need more help?  
>   
>  Documentation for these tools can be found in the setup folder: `C:\Program Files\Microsoft SQL Server\R_SERVER\doc` and in `C:\Program Files\Microsoft SQL Server\R_SERVER\doc\manual`.  
>   
>  One easy way to open these files is to open **RGui**, click **Help**, and select one of the options.  
  
##  <a name="bkmk_RTools"></a> R Tools for Visual Studio  
 For convenience in working with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] databases, consider using [!INCLUDE[rsql_rtvs](../../Token\Other/rsql_rtvs_md.md)] as your development environment. [!INCLUDE[rsql_rtvs](../../Token\Other/rsql_rtvs_md.md)] is a free add\-in for Visual Studio that works in all editions of Visual Studio. Visual Studio also provides support for Python and F\# integration.  
  
 This section describes how to install [!INCLUDE[rsql_rtvs](../../Token\Other/rsql_rtvs_md.md)] using the free Community Edition of Visual Studio.  
  
#### Install Visual Studio  
  
1.  The free Community edition of Visual Studio is available for download from this page: [Visual Studio Community](http://visualstudio.com/products/visual-studio-community-vs.aspx)  
  
2.  When the download completes, click **Run** and select the components to install.  
  
     If you do a custom setup, note that the Microsoft Web Developer components are required.  
  
3.  Choose the **General** setting for now. [!INCLUDE[rsql_rtvs](../../Token\Other/rsql_rtvs_md.md)] includes a template that you can use to customizing shortcuts for R development.  
  
#### Register R  
  
1.  Open a Windows command prompt as administrator.  
  
2.  Navigate to the folder that contains RSetReg.exe, typically `C:\Program Files\Microsoft SQL Server\R_SERVER\bin\x64`.  
  
3.  Run RSetReg. This creates several registry entries that specify the default location of the R executables.  
  
#### Install and use [!INCLUDE[rsql_rtvs](../../Token\Other/rsql_rtvs_md.md)]  
  
1.  The tools and download instructions are available from this page: [Welcome to R Tools for Visual Studio Preview\!](https://microsoft.github.io/RTVS-docs/)  
  
2.  After the download is complete, click **Run** to begin installation and follow the prompts.  
  
3.  If you see a warning that  setup could not locate the R engine, click **No**. It is a known issue that the pre\-release version of [!INCLUDE[rsql_rtvs](../../Token\Other/rsql_rtvs_md.md)] sometimes does not detect Microsoft R Open.  
  
     You should **not** install a different version of Microsoft R Open, because all required packages are already installed. Instead, you can either:  
  
    -   Cancel setup, register the default R libraries using RSetReg as described above, and then rerun setup.  
  
    -   Ignore the prompt to get new R libraries, and then specify the R libraries in the R\_SERVER folder after installation is complete.  
  
4.  Restart Visual Studio, and click **New Project**.  
  
5.  In the list of project templates, select **R**, and then click **R Project**.  
  
     For more information about how to develop and debug R code using [!INCLUDE[rsql_rtvs](../../Token\Other/rsql_rtvs_md.md)], see these topics:  
  
    -   [Editor](http://microsoft.github.io/RTVS-docs/editing.html)  
  
    -   [Debugging](https://microsoft.github.io/RTVS-docs/debugging.html)  
  
    -   [Variable Explorer](http://microsoft.github.io/RTVS-docs/variable-explorer.html)  
  
## See Also  
 [Create a Standalone R Server](../../Topics\TopicNameContainA/Create-a-Standalone-R-Server.md)   
 [Getting Started with Microsoft R Server &#40;Standalone&#41;](../Topic/Getting%20Started%20with%20Microsoft%20R%20Server%20\(Standalone\).md)  
  
  