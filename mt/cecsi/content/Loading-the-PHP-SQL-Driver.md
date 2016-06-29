---
title: Loading the PHP SQL Driver
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e5c114c5-8204-49c2-94eb-62ca63f5d3ec
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
# Loading the PHP SQL Driver
This topic provides instructions for loading the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] into the PHP process space.  
  
There are two options for loading a driver. The driver can be loaded when PHP is started or it can be loaded at PHP script runtime.  
  
## Moving the Driver File into Your Extension Directory  
Regardless of which procedure you use, the first step will be to put the driver file in a directory where the PHP runtime can find it. So, put the driver file in your PHP extension directory. See [System Requirements for the PHP SQL Driver](../content/System-Requirements-for-the-PHP-SQL-Driver.md) for a list of the driver files that are installed with the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
If necessary, specify the directory location of the driver file in the PHP configuration file \(php.ini\), using the **extension\_dir** option. For example, if you will put the driver file in your c:\\php\\ext directory, use this option:  
  
```  
extension_dir = "c:\PHP\ext"  
```  
  
## Loading the Driver at PHP Startup  
To load the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] when PHP is started, first move a driver file into your extension directory. Then, follow these steps:  
  
1.  To enable the SQLSRV driver, modify **php.ini** by adding the following line to the extension section, or modifying the line that is already there \(this example uses the version 3.2 thread safe driver for PHP 5.6\):  
  
    ```  
    extension=php_sqlsrv_56_ts.dll  
    ```  
  
    To enable the PDO\_SQLSRV driver, modify **php.ini** by adding the following line to the extension section, or modifying the line that is already there \(this example uses the version 3.2 thread safe driver for PHP 5.6\):  
  
    ```  
    extension=php_pdo_sqlsrv_56_ts.dll  
    ```  
  
2.  If you want to use the PDO\_SQLSRV driver, the php\_pdo.dll must be available, either as a built\-in extension, or as a dynamically\-loaded extension. If you need to load the PDO\_SQLSRV driver dynamically, the php\_pdo.dll must be present in the extension directory and the following line needs to be in the php.ini:  
  
    ```php  
    extension=php_pdo.dll  
    ```  
  
3.  Restart the Web server.  
  
> [!NOTE]  
> To determine whether the driver has been successfully loaded, run a script that calls [phpinfo\(\)](http://go.microsoft.com/fwlink/?LinkId=108678).  
  
For more information about **php.ini** directives, see [Description of core php.ini directives](http://go.microsoft.com/fwlink/?LinkId=105817).  
  
## Loading the Driver at PHP Script Runtime  
To load the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] at script runtime, first move a driver file into your extension directory. Then include the following line at the start of the PHP script that will use the driver:  
  
```  
dl('php_pdo_sqlsrv_56_ts.dll');  
```  
  
For more information about PHP functions related to dynamically loading extensions, see [dl](http://go.microsoft.com/fwlink/?LinkId=105818) and [extension\_loaded.](http://go.microsoft.com/fwlink/?LinkId=105819)  
  
## See Also  
[Getting Started with the PHP SQL Driver](../content/Getting-Started-with-the-PHP-SQL-Driver.md)
[System Requirements for the PHP SQL Driver](../content/System-Requirements-for-the-PHP-SQL-Driver.md)
[Programming Guide for PHP SQL Driver](../content/Programming-Guide-for-PHP-SQL-Driver.md)
[SQLSRV Driver API Reference](../content/SQLSRV-Driver-API-Reference.md)  
  
