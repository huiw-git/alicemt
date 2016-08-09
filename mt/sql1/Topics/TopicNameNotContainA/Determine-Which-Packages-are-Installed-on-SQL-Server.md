---
title: "Determine Which Packages are Installed on SQL Server"
ms.custom: na
ms.date: 2016-05-27
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9a7f7e43-b568-406c-9434-5a2ec64ec5f5
caps.latest.revision: 10
caps.handback.revision: 0
manager: paulettm
---
# Determine Which Packages are Installed on SQL Server
This topic describes how you can determine which R packages are installed on the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance.  
  
 By default, installation of [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] creates a package library located in this folder: C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library  
  
 However, users might also install packages used by their solutions, into user libraries.  The database administrator can get a list of all local packages by running an R script from [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
> [!NOTE]  
>  This topic is intended to provide a temporary solution, until a more complete package management solution using [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)] or Distributed Management Views (DMVs) is available.  
  
## Find Installed Packages Using R  
 There are multiple ways to get a list of installed or loaded packages using R tools and R functions.  
  
-   Many R development tools provide an object browser or a list of packages that are installed or that are loaded in the current R workspace.  
  
-   You can use an R function, such as `installed.packages()`, which is included in the installed `utils` package. The function scans the DESCRIPTION files of each package that was  found in the specified library and returns a matrix of package names, library paths and version numbers.  
  
### Example  
 This example uses the `installed.packages()` in a [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] stored procedure to get a matrix of packages that have been installed in the R working directory on the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] computer. To avoid parsing the fields in the DESCRIPTION file, only the name is returned.  
  
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
  
 For more information about the default and optional fields in the R package DESCRIPTION file, see [https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file](https://cran.r-project.org/doc/manuals/R-exts.html).  
  
## See Also  
 [Install Additional R Packages on SQL Server](../../Topics/TopicNameNotContainA/Install-Additional-R-Packages-on-SQL-Server.md)