---
title: Installing the Microsoft ODBC Driver for SQL Server on Linux
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
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
# Installing the Microsoft ODBC Driver for SQL Server on Linux
This topic explains how to install the [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] ODBC Driver 13 \(Preview\) and 11 for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] on Linux. Before you can begin to use the driver, install the unixODBC driver manager. See [Installing the Driver Manager](../content/Installing-the-Driver-Manager.md) for more information.  
  
## Installing the Microsoft ODBC Driver 13 \(Preview\) for SQL Server on Linux  
**Installation Steps**  
  
To install the driver:  
  
1.  Make sure that you have root permission.  
  
2.  Change to the directory where the ODBC driver on Linux placed the file called msodbcsql\-13.0.0.0.tar.gz. Make sure that you have the \*.tar.gz file that matches your version of Linux. To extract the files, execute the following command, **tar xvzf msodbcsql\-13.0.0.0.tar.gz**  
  
3.  Change to the msodbcsql\-13.0.0.0.tar.gz directory and there you should see a file called install.sh  
  
4.  To see a list of the available installation options, execute the following command: **.\/install.sh**  
  
5.  Make a backup of **odbcinst.ini**. The driver installation updates **odbcinst.ini**. odbcinst.ini contains the list of drivers that are registered with the unixODBC Driver Manager. To discover the location of odbcinst.ini on your computer, execute the following command: **odbc\_config \-\-odbcinstini**  
  
6.  Before you install the driver, execute the following command: **.\/install.sh verify**. The output of **.\/install.sh verify** reports if your computer has the required software to support the ODBC driver on Linux  
  
7.  When you are ready to install the ODBC driver on Linux, execute the command: **.\/install.sh install**. If you need to specify an install command \(**bin\-dir** or **lib\-dir**\), specify the command after the **install** option  
  
8.  After reviewing the license agreement, type **YES** to continue with the installation  
  
9. Verify that the ODBC Driver Manager library location is part the ld path as follows:   a\) 	Edit \/etc\/ld.so.conf \(using your editor of choice\) b\) If not already present, add **\/usr\/lib64** to the last line of the file, save, and return to the terminal c\) Run **ldconfig** \(type ldconfig\) to force the ld configuration file to be reloaded  
  
Installation puts the driver in \/opt\/microsoft\/msodbcsql\/13.0.0.0. The driver and its support files must be in \/opt\/microsoft\/msodbcsql\/13.0.0.0.  
  
To verify that the ODBC driver on Linux was registered successfully, execute the following command: **odbcinst \-q \-d \-n "ODBC Driver 13 for SQL Server"**.  
  
[Use Existing MSDN C\+\+ ODBC Samples for the ODBC Driver on Linux](http://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) shows a code sample that connects to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] using the ODBC driver on Linux.  
  
**Uninstalling**  
  
You can uninstall the ODBC driver on Linux, by executing the following commands:  
  
1.  rm \-f \/usr\/bin\/sqlcmd  
  
2.  rm \-f \/usr\/bin\/bcp  
  
3.  rm \-rf \/opt\/microsoft\/msodbcsql  
  
4.  odbcinst \-u \-d \-n "ODBC Driver 13 for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]"  
  
## Installing the Microsoft ODBC Driver 11 for SQL Server on Linux  
**Installation Steps**  
  
> [!IMPORTANT]  
> These instructions refer to msodbcsql\-11.0.2270.0.tar.gz, which is installation file for Red Hat Linux. If you are installing the Preview for SUSE Linux, the file name is msodbcsql\-11.0.2260.0.tar.gz.  
  
To install the driver:  
  
1.  Make sure that you have root permission.  
  
2.  Change to the directory where the ODBC driver on Linux placed the file called msodbcsql\-11.0.2270.0.tar.gz. Make sure that you have the \*.tar.gz file that matches your version of Linux. To extract the files, execute the following command, **tar xvzf msodbcsql\-11.0.2270.0.tar.gz**.  
  
3.  Change to the msodbcsql\-11.0.2270.0 directory and there you should see a file called install.sh.  
  
4.  To see a list of the available installation options, execute the following command: **.\/install.sh**.  
  
5.  Make a backup of **odbcinst.ini**. The driver installation updates **odbcinst.ini**. odbcinst.ini contains the list of drivers that are registered with the unixODBC Driver Manager. To discover the location of odbcinst.ini on your computer, execute the following command: **odbc\_config \-\-odbcinstini**.  
  
6.  Before you install the driver, execute the following command: **.\/install.sh verify**. The output of **.\/install.sh verify** reports if your computer has the required software to support the ODBC driver on Linux.  
  
7.  When you are ready to install the ODBC driver on Linux, execute the command: **.\/install.sh install**. If you need to specify an install command \(**bin\-dir** or **lib\-dir**\), specify the command after the **install** option.  
  
8.  After reviewing the license agreement, type **YES** to continue with the installation.  
  
Installation puts the driver in \/opt\/microsoft\/msodbcsql\/11.0.2270.0. The driver and its support files must be in \/opt\/microsoft\/msodbcsql\/11.0.2270.0.  
  
To verify that the ODBC driver on Linux was registered successfully, execute the following command: **odbcinst \-q \-d \-n "ODBC Driver 11 for SQL Server"**.  
  
[Use Existing MSDN C\+\+ ODBC Samples for the ODBC Driver on Linux](http://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) shows a code sample that connects to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] using the ODBC driver on Linux.  
  
**Uninstalling**  
  
You can uninstall the ODBC driver on Linux, by executing the following commands:  
  
1.  rm \-f \/usr\/bin\/sqlcmd  
  
2.  rm \-f \/usr\/bin\/bcp  
  
3.  rm \-rf \/opt\/microsoft\/msodbcsql  
  
4.  odbcinst \-u \-d \-n "ODBC Driver 11 for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]"  
  
## Troubleshooting Connection Problems  
If you are unable to make a connection to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] using the ODBC driver on Linux, use the following information to identify the problem.  
  
The most common connection problem is to have two copies of the UnixODBC Driver Manager installed. Search \/usr for libodbc\*.so\*. If you see more than one version of the file, you \(possibly\) have more than one driver manager installed. Your application might use the wrong version. If you see the UnixODBC Driver Manager installed package when you execute \(on Red Hat\) the command **yum list unixODBC**, delete the package.  
  
Enable the connection log by verifying that your odbcinst.ini file contains the section and these items:  
  
```  
[ODBC]  
Trace = Yes  
TraceFile = (your log file)  
```  
  
If you get another connection failure and do not see a log file, there \(possibly\) are two copies of the driver manager on your computer. Otherwise, the log output should be similar to the following:  
  
```  
[ODBC][28783][1321576347.077780][SQLDriverConnectW.c][290]  
        Entry:  
            Connection = 0x17c858e0  
            Window Hdl = (nil)  
            Str In = [DRIVER={ODBC Driver 11 for SQL Server};SERVER={contoso.com};Trusted_Connection={YES};WSID={mydb.contoso.com};AP...][length = 139 (SQL_NTS)]  
            Str Out = (nil)  
            Str Out Max = 0  
            Str Out Ptr = (nil)  
            Completion = 0  
        UNICODE Using encoding ASCII 'UTF8' and UNICODE 'UTF16LE'  
```  
  
If the character encoding is not UTF\-8, for example:  
  
```  
UNICODE Using encoding ASCII 'ISO8859-1' and UNICODE 'UCS-2LE'  
```  
  
There is more than one Driver Manager installed and your application is using the wrong one. Or, the Driver Manager was not built correctly.  
  
For more information about resolving connection failures, see:  
  
-   [Steps to troubleshoot SQL connectivity issues](http://blogs.msdn.com/b/sql_protocols/archive/2008/04/30/steps-to-troubleshoot-connectivity-issues.aspx)  
  
-   [SQL Server 2005 Connectivity Issue Troubleshoot \- Part I](http://blogs.msdn.com/b/sql_protocols/archive/2005/10/22/sql-server-2005-connectivity-issue-troubleshoot-part-i.aspx)  
  
-   [Connectivity troubleshooting in SQL Server 2008 with the Connectivity Ring Buffer](http://blogs.msdn.com/b/sql_protocols/archive/2008/05/20/connectivity-troubleshooting-in-sql-server-2008-with-the-connectivity-ring-buffer.aspx)  
  
-   [SQL Server Authentication Troubleshooter](http://blogs.msdn.com/b/sqlsecurity/archive/2010/03/29/sql-server-authentication-troubleshooter.aspx)  
  
-   [Error details \(http:\/\/www.microsoft.com\/products\/ee\/transform.aspx?ProdName\=Microsoft\+SQL\+Server&EvtSrc\=MSSQLServer&EvtID\=11001\)](http://www.microsoft.com/products/ee/transform.aspx?ProdName=Microsoft+SQL+Server&EvtSrc=MSSQLServer&EvtID=001)  
  
    The error number specified in the URL \(11001\) should be changed to match the error that you see.  
  
## See Also  
[Microsoft ODBC Driver for SQL Server on Linux](../content/Microsoft-ODBC-Driver-for-SQL-Server-on-Linux.md)  
  
