---
title: Installing and Managing R Packages
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d426cf6-a658-4d9d-bfca-4cdfc8f1567f
---
# Installing and Managing R Packages
 Any R solution that runs in [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] must use packages that are installed in the default R library. More typically, R solutions will reference user libraries by specifying a file path in the R code, but this is not recommended for production.

Therefore, it is the task of the database administrator or other administrator on the server to ensure that all required packages are installed on the [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)] instance. If you do not have administrative privileges on the computer that hosts the [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)]  instance, you can provide to the administrator information about how to install R packages, and provide access to a secure package repository where packages requested by users can be obtained. This section provides that information. 

## Installed Packages
When you install  [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)],  by default the R **base** packages are installed, such as `stats` and `utils`, together with the **RevoScaleR** package that supports connections to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
 
> [!NOTE]  
>  For a list of packages installed by default, see [Packages Installed with Microsoft R Open](https://mran.microsoft.com/rro/installed/).  

 If you need an additional package from CRAN or another repository, you must download the package and install it on your workstation.  
  
 If you need to run the new package in the context of the server, an administrator must install it on the server as well.   
   
## Where and How to Get New Packages  
 There are multiple sources for R packages, the best known among them being CRAN and Bioconductor. The official site for the R language \([https:\/\/www.r\-project.org\/](https://www.r-project.org/)\) lists many of these resources. Many packages are also published to GitHub, where you can obtain the source code. However, you may also have been given R packages that were developed by someone in your company.  
  
 Regardless of the source, packages must be provided in the format of a zipped file to be installed. Moreover, to use the package with [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)], be sure to get the zipped file in the  Windows binary format. \(Some packages might not support this format.\) For more information about the contents of the zip file format, and how to create an R package, we recommend this tutorial, which you can download in PDF format from the R project site: [Freidrich Leisch: Creating R Packages](http://cran.r-project.org/doc/contrib/Leisch-CreatingPackages.pdf). 
  
 In general, R packages can be installed easily from the command line without downloading them in advance,  if the computer has Internet access.  Generally this is not the case with servers running [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)] .  Therefore, to install an  R package to a computer that does **not** have Internet access, you must download the package in the correct zipped format ahead of time and then copy the zipped files to a folder that is accessible by the computer. 
 
 The following topics describe two methods for installing packages off-line: 

+ [Create an Offline Package Repository using miniCRAN](../../Topics\TopicNameContainA/Create-a-Local-Package-Repository-Using-miniCRAN.md)

  Describes how to use the R package **miniCRAN** to create an off-line repository. This is probably the most efficient method if you need to install packages to multiple servers and manage the repository from a single location. 
+ [Install New R Packages from the Internet](../../Topics\TopicNameNotContainA/Install-Additional-R-Packages-on-SQL-Server.md)

  Includes instructions for installing packages off-line by manually copying zipped files.   

## Permissions Required for Installing R Packages  
  
To install a new R package on a computer that is running [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], you must have administrative rights to the computer.   

If you do not have these rights, contact your administrator and provide the information about the package to install.  
  

If you are installing a new R package on a computer that is being used as an R workstation and the computer does **not** have an instance of [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)] installed, you still need administrative rights to the computer to install the package. After you have installed the package, you can run it locally.  
 

## Managing Installed Packages

To determine which packages are installed on the [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)] computer, use one of these options:

+ View the default library, if you have permissions to the folder.
+ Run an R command to list the available packages

### Location of default R library location for R Services

If you installed  [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] using the default instance, the R package library used by the instance is located under the [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)] instance folder. For example: 

+ Default instance _MSSQLSERVER_
  `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`
+ Named instance _MyNamedInstance_
  `C:\Program Files\Microsoft SQL Server\MSSQL13.MyNamedInstance\R_SERVICES\library` 


You can run the following statement to verify the default library for the current instance of R. 
~~~~
EXECUTE sp_execute_external_script
       @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS ((
       [DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
~~~~

For more information, see [Determine Which Packages are Installed on SQL Server](../../Topics\TopicNameNotContainA/Determine-Which-Packages-are-Installed-on-SQL-Server.md).

### Packages installed in user libraries
If a user needs a new R package and is not an administrator, the packages cannot be installed to the default location and are by default installed into a private, user library. 

Thereafter, to reference the package in code, the user would have to add the location to the R environment variable `libPath`, or reference the full package path, like this:  
  
~~~~
library("c:/Users/<username>/R/win-library/packagename")  
~~~~


In [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)], this workaround is **not** supported; packages must be installed to the default library. 

Therefore, when you migrate R solutions to run in [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)], it is important that you do the following:
+ Check the code to make sure that there are no calls to uninstalled packages.
+ Modify any code that would try to install packages dynamically.
+ Edit code to ensure that packages are loaded from the default library,  not from user libraries.

If a package is installed in the default library, the R runtime will load the package from the default library, even if a different library is specified in the R code.



 ## See Also  
 [Managing and Monitoring R Solutions](../../Topics\TopicNameNotContainA/Managing-and-Monitoring-R-Solutions.md)  