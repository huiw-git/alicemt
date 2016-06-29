---
title: Features of the Microsoft ODBC Driver for SQL Server on Windows
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
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
# Features of the Microsoft ODBC Driver for SQL Server on Windows
    
## Microsoft ODBC Driver 13 \(Preview\) for SQL Server on Windows  
 The ODBC Driver 13 \(Preview\) for SQL Server contains all the functionality of the previous version \(11\) and adds support for Always Encrypted, a new feature found in Microsoft SQL Server 2016 \(Preview\).  
  
 Always Encrypted allows clients to encrypt sensitive data inside client applications and never reveal the encryption keys to SQL Server. An Always Encrypted enabled driver installed on the client computer achieves this by automatically encrypting and decrypting sensitive data in the SQL Server client application. The driver encrypts the data in sensitive columns before passing the data to SQL Server, and automatically rewrites queries so that the semantics to the application are preserved. Similarly, the driver transparently decrypts data stored in encrypted database columns that are contained in query results. For more information, see [Using Always Encrypted with the Windows ODBC Driver](../content/Using-Always-Encrypted-with-the-Windows-ODBC-Driver.md).  
  
## Microsoft ODBC Driver 11 for SQL Server on Windows  
 The ODBC Driver for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] contains all the functionality of the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Native Client ODBC driver that shipped in [!INCLUDE[ssSQL11](../content/includes/ssSQL11_md.md)]. For more information, see [SQL Server Native Client Programming](http://msdn.microsoft.com/library/ms130892.aspx). The [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Native Client ODBC driver is based on the ODBC driver that ships in the Windows operating system. For more information, see [Windows Data Access Components SDK](http://msdn.microsoft.com/library/aa968814(VS.85).aspx).  
  
 This release of the ODBC Driver for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] contains the following new features:  
  
 The –l option, which specifies a login timeout, has been added to BCP.exe.  
 The –l option specifies the number of seconds before a Bcp.exe login to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] times out when you try to connect to a server. The default Bcp.exe timeout for login to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] is 15 seconds. The login time\-out must be a number between 0 and 65534. If the value supplied is not numeric or does not fall into that range, Bcp.exe generates an error message. A value of 0 specifies time\-out to be infinite.  
  
 A login timeout of less than \(approximately\) 10 seconds are not reliable.  
  
 Driver\-Aware Connection Pooling  
 The ODBC Driver for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] supports [Driver\-Aware Connection Pooling](http://msdn.microsoft.com/library/hh405031(VS.85).aspx). For more information, see [Driver-Aware Connection Pooling in the ODBC Driver for SQL Server](../content/Driver-Aware-Connection-Pooling-in-the-ODBC-Driver-for-SQL-Server.md).  
  
 Asynchronous Execution \(Notification Method\)  
 The ODBC Driver for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] supports [Asynchronous Execution \(Notification Method\)](http://msdn.microsoft.com/library/hh405038(VS.85).aspx). For a usage sample, see [Asynchronous Execution &#40;Notification Method&#41; Sample](../content/Asynchronous-Execution--Notification-Method--Sample.md).  
  
 Connection Resiliency  
 To ensure that applications remain connected to a Microsoft Azure SQL Database, the ODBC driver on Windows can restore idle connections. For more information, see [Connection Resiliency in the Windows ODBC Driver](../content/Connection-Resiliency-in-the-Windows-ODBC-Driver.md).  
  
## Behavior Changes  
 In [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], the **\-y0** option for Sqlcmd.exe caused output is truncated at 1 MB if display\_width was 0.  
  
 Beginning in the ODBC Driver 11 for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], there is no limit on the amount of data that retrieved in a single column when **–y0** is specified. Sqlcmd.exe now streams columns as large as 2 GB \([!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data type maximum\).  
  
 Another difference is that a combination of **\-h \-y0** now produces an error that reports the options are incompatible. **\-h**, which specifies the number of rows to print between the column headings and has never been compatible with **\-y0**, and was ignored, though no headers were printed.  
  
 **\-y0** can cause performance issues on both the server and the network, depending on the size of data returned.  
  
## See Also  
 [Microsoft ODBC Driver for SQL Server on Windows](../content/Microsoft-ODBC-Driver-for-SQL-Server-on-Windows.md)  
  
  