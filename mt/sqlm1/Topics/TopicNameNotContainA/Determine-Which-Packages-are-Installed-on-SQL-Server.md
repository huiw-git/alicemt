---
title: Determine Which Packages are Installed on SQL Server
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9a7f7e43-b568-406c-9434-5a2ec64ec5f5
---
# Determine Which Packages are Installed on SQL Server
  This topic describes how you can determine which R packages are installed on the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance.  
  
By default, installation of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] creates an R package library associated with each instance. Therefore, to know which packages are installed on a computer, you must run this query on each separate instance where R Services is installed. Note that package libraries are **not** shared across instances, so it is possible for different packages to be installed on different instances.

For information about how to determine the default library location for an instance, see [Installing and Managing R Packages](../../Topics\TopicNameNotContainA/Installing-and-Managing-R-Packages.md).   
   
 
## Get a List of Installed Packages Using R  
 There are multiple ways to get a list of installed or loaded packages using R tools and R functions.  
  
-   Many R development tools provide an object browser or a list of packages that are installed or that are loaded in the current R workspace.  
  
-   You can use an R function, such as `installed.packages()`, which is included in the installed `utils` package. The function scans the DESCRIPTION files of each package that was  found in the specified library and returns a matrix of package names, library paths, and version numbers.  
  
 The following example uses the `installed.packages()` in a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] stored procedure to get a matrix of packages that have been installed in the R_SERVICES library for the current instance. To avoid parsing the fields in the DESCRIPTION file, only the name is returned.  
  
```  
EXECUTE sp_execute_external_script  
@language=N'R'  
,@script = N'str(OutputDataSet);  
packagematrix <- installed.packages();  
NameOnly <- packagematrix[,1];  
OutputDataSet <- as.data.frame(NameOnly);'  
,@input_data_1 = N'SELECT 1 as col'  
WITH RESULT SETS ((PackageName nvarchar(250) ))  
```  
  
 For more information about the default and optional fields in the R package DESCRIPTION file, see [https:\/\/cran.r\-project.org\/doc\/manuals\/R\-exts.html\#The\-DESCRIPTION\-file](https://cran.r-project.org/doc/manuals/R-exts.html).  
  
## See Also  
 [Install Additional R Packages on SQL Server](../../Topics\TopicNameNotContainA/Install-Additional-R-Packages-on-SQL-Server.md)  
  
  