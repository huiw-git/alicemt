---
title: Overview of SQL Server Drivers
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57f13a0e-f966-43f8-8188-9d66a15376f2
manager: jhubbard
---
# Overview of SQL Server Drivers
SQL Server supports a wide variety of drivers, which are used by client applications or services to connect and query for data.  Please see below for a summary of the different drivers, both current and legacy.  
  
## Current SQL Drivers  
The following SQL Drivers are actively developed. Each driver has a support statement that can be found by following the links.  
  
### ADO.NET  
ADO.NET is a library that is a standard part of the .Net framework.  It is a C\# implementation of the TDS protocol, which is supported by all modern versions of SQL Server.    
						  This driver is developed, tested, and supported by Microsoft.  
  
[SQL Server and ADO.NET](https://msdn.microsoft.com/library/kb9s9ks0.aspx)  
  
### JDBC  
The JDBC SQL driver is a Java implementation of the TDS protocol, which is supported by all modern versions of SQL Server.  This driver is developed, tested, and supported by Microsoft.  
  
[Microsoft JDBC Driver for SQL Server](../content/Microsoft-JDBC-Driver-for-SQL-Server.md)  
  
### ODBC  
The ODBC SQL driver is a C\+\+ implementation of the TDS protocol, which is supported by all modern versions of SQL Server.  This driver is developed, tested, and supported by Microsoft.  
  
[Microsoft ODBC Driver for SQL Server](../content/Microsoft-ODBC-Driver-for-SQL-Server.md)  
  
### PHP  
The PHP SQL driver relies on the Microsoft SQL Server ODBC Driver to handle the low\-level communication with SQL Server.  This driver is developed, tested, and supported by Microsoft.  
  
[Microsoft PHP Driver for SQL Server](../content/Microsoft-PHP-Driver-for-SQL-Server.md)  
  
### Node.js  
The Node.js SQL driver is hosted and supported by the Node.js Foundation, a collaborative project at the Linux Foundation.  
  
[Node.js](https://nodejs.org)  
  
### Python  
The Python SQL driver is hosted and supported by the Python Software Foundation.  
  
[Python](https://www.python.org/)  
  
### Ruby  
The Ruby SQL driver is hosted at the following location.  
  
[Ruby](https://www.ruby-lang.org/)  
  
## Legacy SQL Drivers  
The following SQL Drivers were developed and tested by Microsoft, but are not recommended to be used for new development. Each driver has a support statement that can be found by following the links.  
  
### OLEDB  
The OLE DB provider will not be included after SQL Server 2012.  
  
[Microsoft OLE DB](https://msdn.microsoft.com/library/ms722784.aspx)  
  
### ADO  
The ADO SQL driver has a direct dependency on the OLE DB provider.  As such, it will not be supported after SQL Server 2012.  
  
[ActiveX Data Objects &#40;ADO&#41;](../content/ActiveX-Data-Objects--ADO-.md)  
  
