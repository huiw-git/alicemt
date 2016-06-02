---
title: Install Additional R Packages on SQL Server
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
---
# Install Additional R Packages on SQL Server
This topic describes how to install new R packages to an instance of [!INCLUDE[rsql_productname_md](../../Token\Other/rsql_productname_md.md)] on a computer that has access to the Internet.

## 1. Locate the Windows binaries in ZIP file format

R packages are supported on many platforms. You must ensure that the package you  want to install has a binary format for the Windows platform. Otherwise the downloaded package will not work.

For example, to obtain the [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) package from Bioconductor:  
  
1.  In the **Package Archives** list, find the **Windows binary** version.  
  
2.  Right\-click the link to the .ZIP file, and select  **Save target as**.  
  
3.  Navigate to  the local folder where zipped packages are stored, and click **Save**.  
  
 This process creates a local copy of the package. You can then install the package, or copy the zipped package to a server that does not have Internet access.  
  
  
## 2. Open the default R package library for SQL Server R Services 

1.  Navigate to the folder on the server where the R packages associated with [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] have been installed.  
  
It is important that you install packages to the default library that is associated with the current instance. For instructions on how to locate this library, see [Installing and Managing R Packages](Installing and).

Also, for each instance where you will run a package, you must install a separate copy of the packages. Currently packages cannot be shared across instances.
  
> [!IMPORTANT]  
>  If you installed new packages in a pre-release version of [!INCLUDE[rsql_productname_md](../../Token\Other/rsql_productname_md.md)], be aware that the default package library changed location after RC3. Therefore, you might need to reinstall packages to the correct location. 
>  

 
  
## 3. Install the package 

2.  Open R as an administrator:  
  
    -   **Using the Windows command prompt**  
  
         Open a Windows command prompt as administrator, and navigate to the directory where the RTerm.Exe or RGui.exe files are located.  
  
         In a default install, this is the R **\\bin** directory. For example, in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], the R tools are located here:  `C:\Program files\MSSQL13.MSSQLSERVER\R_SERVICES\bin` or  `C:\Program files\MSSQL13.<instanceName>\R_SERVICES\bin\x64`  
  
         Run **R.Exe**.  
  
    -   **Using the R command\-line utilities**  
  
         Use Windows Explorer to navigate to the directory containing the R tools.  
  
         Right\-click **RGui.exe** or **RTerm.exe**, and select **Run as administrator**.  
  
3.  At the R command prompt, type one of the following commands to install the package, depending on whether you are getting the package from the Internet or from a local zipped file.  
  
    -   **On a computer with Internet access**  
  
        1.  In general, you use the following command to install a new package.  
  
            ```  
            install.packages("<target_package_name>")  
            ```  
  
             Note that double quotation marks are always required for the package name.  
  
        2.  To specify the library where the package should be installed, use a command like this one to set the library location:  
  
            ```  
            lib.SQL <- "C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library"  
  
            ```  
  
             Note that for [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)], currently only one package library is allowed. Do not install packages to a user library, or you will not be able to run the package from [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)].   
     
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
  
    -   **Manual installation method on computer with no Internet access**  
  
        1.  At the R command prompt, type the following command to specify the path and name of the package to install:  
  
            ```  
            install.packages(“C:\\Temp\\mynewpackage.zip”, repos=NULL)  
            ```  
  
        2.  This command extracts the R package from its local zipped file, assuming you saved the copy in the directory `c:\Temp`, and installs the package \(with its dependencies\) into the R library on the local computer.  
  
4.  If you have previously modified the R environment on the computer, you should ensure that the R environment variable `.libPath` uses just one path, which points to the R\_SERVICES folder for the instance.  
  
> [!NOTE]
> If you have installed Microsoft R Server \(Standalone\) in addition to [!INCLUDE[rsql_productname_md](../../Token\Other/rsql_productname_md.md)], your computer will have a separate installation of R with all the R tools and libraries. Packages that are installed to this library are used only by Microsoft R Server and cannot be accessed by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
>  

  
## See Also  
 [Set up SQL Server R Services &#40;In-Database&#41;](../Topic/Set%20up%20SQL%20Server%20R%20Services%20\(In-Database\).md)  
  
  