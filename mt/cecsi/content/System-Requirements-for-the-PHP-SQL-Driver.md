---
title: System Requirements for the PHP SQL Driver
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5db4b75f-c605-4785-9560-399a533c0fc9
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# System Requirements for the PHP SQL Driver
To access data in a SQL Server 2005 or later database using the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] \(SQL Server 2008 or later if using version 3.2 or 3.1\), you must have the following components installed on your computer:  
  
-   Supported operating systems for version 3.2 and 3.1 of the driver include:  
    -   Windows Server 2008 R2 SP1  
    -   Windows Vista SP2  
    -   Windows Server 2008 SP2  
    -   Windows 7 SP1  
    -   Windows Server 2012  
    -   Windows Server 2012 R2  
    -   Windows 8  
    -   Windows 8.1  
  
-   Supported operating systems for version 3.0 of the driver include:  
    -   Windows Server 2008 R2 SP1  
    -   Windows Vista SP2  
    -   Windows Server 2008 SP2  
    -   Windows 7 SP1  
  
-   Supported operating systems for version 2.0 of the driver include:  
    -   Supported operating systems for version 2.0 of the driver include:  
    -   [!INCLUDE[winxpsvr](../content/includes/winxpsvr_md.md)] Service Pack 1  
    -   Windows XP Service Pack 3  
    -   Windows Vista Service Pack 1 or later  
    -   Windows Server 2008  
    -   Windows Server 2008 R2  
    -   Windows 7  
  
-   SQL Azure Databases are supported. For information see [Connecting to Windows Azure SQL Database](../content/Connecting-to-Windows-Azure-SQL-Database.md).  
  
-   PHP 5.x is required. For information about how to download and install the latest stable binaries, see [http:\/\/php.net](http://go.microsoft.com/fwlink/?LinkId=101876).  
  
-   Microsoft Drivers for PHP for SQL Server, versions require PHP versions in the following table:  
  
|Microsoft Drivers for PHP for SQL Server Version|Supported PHP Versions|  
|----------------------------------------------------|--------------------------|  
|3.2|PHP 5.6.4\+ or<br /><br />PHP 5.5.16\+ or<br /><br />PHP 5.4.32|  
|3.1|PHP 5.5.16\+ or<br /><br />PHP 5.4.32|  
|3.0|PHP 5.4.32 or<br /><br />PHP 5.3.0|  
|2.0|PHP 5.3.0 or<br /><br />PHP 5.2.4 or<br /><br />PHP 5.2.13|  
  
-   A version of the driver file must be in your PHP extension directory. See Driver Versions later in this topic for information about the different driver files. See [Loading the PHP SQL Driver](../content/Loading-the-PHP-SQL-Driver.md)  for information on configuring the driver for the PHP runtime. To download the drivers, see [Microsoft Drivers for PHP for SQL Server](http://www.microsoft.com/download/details.aspx?id=20098).  
  
-   A Web server is required. Your Web server must be configured to run PHP. For information about hosting PHP applications with Internet Information Services \(IIS\) 6.0, see [Using FastCGI to Host PHP Applications on IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=117131). For information about hosting PHP applications with IIS 7.0, see [Using FastCGI to Host PHP Applications on IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=117132).  
  
    The [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] has been tested using IIS 6 and IIS 7 with FastCGI.  
  
    > [!NOTE]  
    > Microsoft provides support only for IIS.  
  
-   Versions 3.2 and 3.1 require Microsoft ODBC Driver 11 \(or higher\) for SQL Server. To download the Microsoft ODBC Driver 11 for PHP for SQL Server, see [Microsoft ODBC Driver 11 for SQL Server](http://www.microsoft.com/download/details.aspx?id=36434).  
  
    If you are using the SQLSRV driver, [sqlsrv_client_info](../content/sqlsrv_client_info.md) will return information about which version of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Native Client is being used by the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)]. If you are using the PDO\_SQLSRV driver, you can use [PDO::getAttribute](../Topic/PDO::getAttribute.md) to discover the version.  
  
-   For versions 3.0 and 2.0, the x86 version of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Native Client is required on the computer where PHP is running. If you are using a 64\-bit operating system, the x86 version of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Native Client will be installed with the x64 version of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Native Client \(do not install the x86 version of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Native Client on an x64 operating system\).  
  
    If you are using the SQLSRV driver, [sqlsrv_client_info](../content/sqlsrv_client_info.md) will return information about which version of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Native Client is being used by the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)]. If you are using the PDO\_SQLSRV driver, you can use [PDO::getAttribute](../Topic/PDO::getAttribute.md) to discover the version.  
  
    -   Version 3.0 of the driver requires Microsoft [!INCLUDE[ssSQL11](../content/includes/ssSQL11_md.md)] Native Client. You can download Microsoft [!INCLUDE[ssSQL11](../content/includes/ssSQL11_md.md)] Native Client from the [SQL Server 2012 feature pack page](http://go.microsoft.com/fwlink/?LinkID=236805).  
  
    -   Version 2.0 of the driver requires Microsoft [!INCLUDE[ssKilimanjaro](../content/includes/ssKilimanjaro_md.md)] Native Client. Click on the appropriate link below:  
  
        [Download the X86 package](http://go.microsoft.com/fwlink/?LinkID=188400&clcid=0x409)  
  
        [Download the X64 package](http://go.microsoft.com/fwlink/?LinkID=188401&clcid=0x409)  
  
## Driver Versions  
This section lists the drivers that are included with versions 3.2, 3.1, 3.0, and 2.0 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
Follow the installation instructions in [Loading the PHP SQL Driver](../content/Loading-the-PHP-SQL-Driver.md)  to configure the driver for use with the PHP runtime.  
  
**Microsoft Drivers 3.2 for PHP for SQL Server installs the following versions of the driver:**  
  
|Driver file|PHP version|Thread safe?|Use with PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|php\_sqlsrv\_54\_nts.dll<br /><br />php\_pdo\_sqlsrv\_54\_nts.dll|5.4|no|php5.dll|  
|php\_sqlsrv\_54\_ts.dll<br /><br />php\_pdo\_sqlsrv\_54\_ts.dll|5.4|yes|php5ts.dll|  
|php\_sqlsrv\_55\_nts.dll<br /><br />php\_pdo\_sqlsrv\_55\_nts.dll|5.5|no|php5.dll|  
|php\_sqlsrv\_55\_ts.dll<br /><br />php\_pdo\_sqlsrv\_55\_ts.dll|5.5|yes|php5ts.dll|  
|php\_sqlsrv\_56\_nts.dll<br /><br />php\_pdo\_sqlsrv\_56\_nts.dll|5.6|no|php5.dll|  
|php\_sqlsrv\_56\_ts.dll<br /><br />php\_pdo\_sqlsrv\_56\_ts.dll|5.6|yes|php5ts.dll|  
  
**Microsoft Drivers 3.1 for PHP for SQL Server installs the following versions of the driver:**  
  
|Driver file|PHP version|Thread safe?|Use with PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|php\_sqlsrv\_54\_nts.dll<br /><br />php\_pdo\_sqlsrv\_54\_nts.dll|5.4|no|php5.dll|  
|php\_sqlsrv\_54\_ts.dll<br /><br />php\_pdo\_sqlsrv\_54\_ts.dll|5.4|yes|php5ts.dll|  
|php\_sqlsrv\_55\_nts.dll<br /><br />php\_pdo\_sqlsrv\_55\_nts.dll|5.5|no|php5.dll|  
|php\_sqlsrv\_55\_ts.dll<br /><br />php\_pdo\_sqlsrv\_55\_ts.dll|5.5|yes|php5ts.dll|  
  
**Microsoft Drivers 3.0 for PHP for SQL Server installs the following versions of the driver:**  
  
|Driver file|PHP version|Thread safe?|Use with PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|php\_sqlsrv\_53\_nts.dll<br /><br />php\_pdo\_sqlsrv\_53\_nts.dll|5.3|no|php5.dll|  
|php\_sqlsrv\_53\_ts.dll<br /><br />php\_pdo\_sqlsrv\_53\_ts.dll|5.3|yes|php5ts.dll|  
|php\_sqlsrv\_54\_nts.dll<br /><br />php\_pdo\_sqlsrv\_54\_nts.dll|5.4|no|php5.dll|  
|php\_sqlsrv\_54\_ts.dll<br /><br />php\_pdo\_sqlsrv\_54\_ts.dll|5.4|yes|php5ts.dll|  
  
**Microsoft Drivers 2.0 for PHP for SQL Server installs the following versions of the driver:**  
  
|Driver file|PHP version|Thread safe?|Use with PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|php\_sqlsrv\_53\_nts\_vc6.dll<br /><br />php\_pdo\_sqlsrv\_53\_nts\_vc6.dll|5.3|no|php5.dll|  
|php\_sqlsrv\_53\_nts\_vc9.dll<br /><br />php\_pdo\_sqlsrv\_53\_nts\_vc9.dll|5.3|no|php5.dll|  
|php\_sqlsrv\_53\_ts\_vc6.dll<br /><br />php\_pdo\_sqlsrv\_53\_ts\_vc6.dll|5.3|yes|php5ts.dll|  
|php\_sqlsrv\_53\_ts\_vc9.dll<br /><br />php\_pdo\_sqlsrv\_53\_ts\_vc9.dll|5.3|yes|php5ts.dll|  
|php\_sqlsrv\_52\_nts\_vc6.dll<br /><br />php\_pdo\_sqlsrv\_52\_nts\_vc6.dll|5.2|no|php5.dll|  
|php\_sqlsrv\_52\_ts\_vc6.dll<br /><br />php\_pdo\_sqlsrv\_52\_ts\_vc6.dll|5.2|yes|php5ts.dll|  
  
If the name of the driver file contains "vc9", it should be used with a PHP version compiled with Visual C\+\+ 9.0.  
  
## See Also  
[Getting Started with the PHP SQL Driver](../content/Getting-Started-with-the-PHP-SQL-Driver.md)
[Programming Guide for PHP SQL Driver](../content/Programming-Guide-for-PHP-SQL-Driver.md)
[SQLSRV Driver API Reference](../content/SQLSRV-Driver-API-Reference.md)  
  
