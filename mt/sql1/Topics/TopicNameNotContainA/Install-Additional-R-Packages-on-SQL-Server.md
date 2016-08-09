---
title: "Install Additional R Packages on SQL Server"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-05-27
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: 13
manager: paulettm
---
# Install Additional R Packages on SQL Server
When you install  [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)], by default the R **base** packages are installed, such as `stats` and `utils`, together with the **RevoScaleR** package that supports connections to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
 If you need an additional package from CRAN or another repository, you must download the package and install it on your workstation.  
  
 If you need to run the new package in the context of the server, you will need to ask the database administrator to install it on the server.  
  
> [!NOTE]  
>  For a list of all packages installed by Microsoft R Open, see [https://mran.revolutionanalytics.com/rro/installed/](https://mran.revolutionanalytics.com/rro/installed/).  
  
## Where and How to Get New Packages  
 There are multiple sources for R packages, the best known among them being CRAN and Bioconductor. The official site for the R language ([https://www.r-project.org/](https://www.r-project.org/)) lists many of these resources. Many packages are also published to GitHub, where you can obtain the source code. However, you may also have been given R packages that were developed by someone in your company.  
  
 Regardless of the source, packages must be provided in the format of a zipped file to be installed. For more information about the contents of the zip file format, and how to create an R package, see one of the tutorials on the R project site.  
  
 In general, R packages can be installed easily from the command line without downloading them in advance,  if the computer you are installing the package to has Internet access.  
  
 If the computer where you are installing the R package does **not** have Internet access, you must download the package in a zipped format ahead of time and then copy the zipped files to a folder that is accessible by the computer.  
  
 For example, to obtain the [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) package from Bioconductor:  
  
1.  In the **Package Archives** list, find the **Windows binary** version.  
  
2.  Right-click the link to the .ZIP file, and select  **Save target as**.  
  
3.  Navigate to  the local folder where zipped packages are stored, and click **Save**.  
  
 This process creates a local copy of the package. You can then install the package, copy the zipped package to a server that does not have Internet access, or upload the zipped package to your workspace in Azure Machine Learning Studio.  
  
> [!NOTE]  
>  Using the R package **miniCran** can make package installation much easier.  
  
## Installing Packages  
 In Microsoft Windows, folders that are located under Program Files are, by default, not writable. This is to protect files used by installed applications, and is similar to the default behavior of CRAN_R. However, as a consequence, to install new packages in this folder requires some additional steps to install the packages as administrator  
  
 There are two ways to do this:  
  
-   Open a Windows command prompt as administrator, navigate to the folder containing the R runtime, and install the packages.  
  
-   Locate the R command-line utilities, run RTerm.exe or Rgui. exe as administrator, and install the packages.  
  
#### To install a new R package to the default library for R Services (in-databaae)  
  
1.  Take a minute to verify the location on the local computer where the R packages associated with [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] have been installed.  
  
    -   If you installed [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] RC2, locate the **R_SERVICES** folder for the instance where you want to use the packages.  
  
         For example, if you installed the default instance using setup default folders, the path would be: `C:\Program files\MSSQL13.MSSQLSERVER\R_SERVICES`.  
  
        > [!NOTE]  
        >  The package library has changed since CTP3. If you installed packages earlier, you might need to reinstall them.  
  
2.  Open R as an administrator. There are two ways to do this:  
  
    -   **Using the Windows command prompt**  
  
         Open a Windows command prompt as administrator, and navigate to the directory where the RTerm.Exe or RGui.exe files are located.  
  
         In a default install, this is the R **\bin** directory. For example, in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] RC3, the R tools are located here:  `C:\Program files\MSSQL13.MSSQLSERVER\R_SERVICES\bin` or  `C:\Program files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`  
  
         Run **R.Exe**.  
  
    -   **Using the R command-line utilities**  
  
         Use Windows Explorer to navigate to the directory containing the R tools.  
  
         Right-click **RGui.exe** or **RTerm.exe**, and select **Run as administrator**.  
  
3.  At the R command prompt, type one of the following commands to install the package, depending on whether you are getting the package from the Internet or from a local zipped file.  
  
    -   **On a computer with Internet access**  
  
        1.  In general, you use the following command to install a new package.  
  
            ```  
            install.packages(“<target package name>”)  
            ```  
  
             Note that double quotation marks are always required for the package name.  
  
        2.  To specify the library where the package should be installed, use a command like this one to set the library location:  
  
            ```  
            lib.SQL <- "C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library"  
  
            ```  
  
             Note that for [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)], currently only one package library is allowed.  
  
             If you are installing the packages for your personal use, you would use a different folder:  
  
            ```  
            lib.usr <- "C:\Users\<<user>>\Documents\R\win-library\3.2"  
            ```  
  
             The general rule is to always install new packages into your user library, because this is the location where you have write permissions.  
  
            > [!NOTE]  
            >  We recommend that you never install new packages into the folder Program Files\Microsoft SQL Server\130\R_SERVER\library), but reserve that library for base R packages and packages installed by default.  
  
        3.  Having defined the library location, the following statement installs the popular e1070 package into the package library used by SQL Server R Services.  
  
            ```  
            install.packages("e1070", lib = lib.SQL)  
            ```  
  
        4.  You will be asked for a mirror site from which to obtain the package. Select any mirror site that is convenient for your location.  
  
             For a list of current CRAN mirrors, see [this site](https://cran.r-project.org/mirrors.html).  
  
            > [!TIP]  
            >  To avoid having to select a mirror site each time you add a new package, you can configure your R development environment to always use the same repository.  
            >   
            >  To do this, edit the global R settings file, .Rprofile, and add the following line:  
            >   
            >  `options(repos=structure(c(CRAN="<mirror site URL>")))`  
            >   
            >  For detailed information about preferences and other files loaded when the R runtime starts, run this command from an R console:  
            >   
            >  `?Startup`  
  
        5.  If the target package depends on additional packages, the R installer will automatically download the dependencies and install them for you.  
  
    -   **On  a computer with no Internet access**  
  
        1.  At the R command prompt, type the following command to specify the path and name of the package to install:  
  
            ```  
            install.packages(“C:\\Temp\\mynewpackage.zip”, repos=NULL)  
            ```  
  
        2.  This command extracts the R package from its local zipped file, assuming you saved the copy in the directory **c:\Temp**, and installs the package (with its dependencies) into the R library on the local computer.  
  
4.  To ensure that the packages are accessible by R Services (In-Database), review your R configuration and check that .libPath uses just one path, the R_SERVICES path for the instance.  
  
 If you have installed the Shared Components using the option, R Server (Standalone), your computer will have a separate installation of R for the client tools. Do not install packages to this path if you need to use the packages in the content of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
## User Libraries  
 Typically, on a server, only administrators have access to the folder used by [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] and therefore you might not be able to install packages to the required folder. In this case, you can also create a second folder and install packages in a *user library*. If there are multiple users of R, multiple user libraries might be needed.  
  
 Typically this is not a problem. However, if you need to run packages that are called from stored procedures in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], referring to packages that might be stored in various user libraries could cause errors.  
  
 One option is to manually specify the source of the package, assuming the package was installed in a local user library. The following script prints as a message the library for the current user and then references a library using a specific path.  
  
```  
exec sp_external_script  
  @language = N'R'  
 ,@script = N'  
   #print(libPaths())   
   library("e1071", lib.loc="C:/<path>/win-library/3/2");  
'  
  
```  
  
 Another option is to create a dynamic call to the R function **.libpaths** from the stored procedure, and get the location of the package based on the user identity. For example, you could add the following code to your script to get the list of paths for the current library, and append the user library for the current user.  
  
```  
.lib.Paths( c(.libPaths, "~/userLibrary") )  
```  
  
## Permissions Required for Installing R Packages  
  
-   To install a new R package on a computer that is running [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)], you must have administrative rights to the computer. You must also have administrative rights to the server if you want to enable the package to run in the context of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
     If you do not have these rights, contact your administrator and provide the information about the package to install.  
  
-   If you are installing a new R package on a computer that is being used as an R workstation and the computer does **not** have an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] installed, you still need administrative rights to the computer to install the package. After you have installed the package, you can run it locally.  
  
     If you intend to run the package in the context of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], you must contact your database administrator and ask him or her to enable the package on the server as well.  
  
## See Also  
 [Set up SQL Server R Services (In-Database)](../../Topics/TopicNameNotContainA/Set-up-SQL-Server-R-Services--In-Database-.md)