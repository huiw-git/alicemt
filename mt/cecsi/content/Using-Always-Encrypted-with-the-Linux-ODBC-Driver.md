---
title: Using Always Encrypted with the Linux ODBC Driver
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f44299a0-fd80-47d3-ac0c-bb471250a54a
manager: jhubbard
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
# Using Always Encrypted with the Linux ODBC Driver
Always Encrypted allows clients to encrypt sensitive data inside client applications and never reveal the encryption keys to SQL Server. An Always Encrypted enabled driver installed on the client computer achieves this by automatically encrypting and decrypting sensitive data in the SQL Server client application. The driver encrypts the data in sensitive columns before passing the data to SQL Server, and automatically rewrites queries so that the semantics to the application are preserved. Similarly, the driver transparently decrypts data stored in encrypted database columns that are contained in query results. For more information, see [Always Encrypted \(Database Engine\)](https://msdn.microsoft.com/en-us/library/mt163865.aspx).  
  
**Limitations of the Preview release**  
  
> [!NOTE]  
> Always Encrypted is supported only by Microsoft ODBC Driver 13 \(Preview\) for SQL Server with SQL Server 2016 \(Preview 3.4\+\). This preview release does **not** support the following:  
>   
> -   Bulk Operations via BCP or ODBC bulk functions  
> -   Locales other than EN\-US  
> -   Azure Key Vault and custom Key Store Providers \(Note: Local machine Key Store Providers **are** supported\)  
  
## Developing client applications for accessing Always Encrypted data  
Querying a database using Always Encrypted from a client application requires minimal development effort. The following summarizes the prerequisites and steps you must take for your application to read and write Always Encrypted data.  
  
### Prerequisites  
  
-   Configure the server by following the directions in the **Getting Started with Always Encrypted** section of the [Always Encrypted \(Database Engine\)](https://msdn.microsoft.com/en-us/library/mt163865.aspx) topic.  
  
-   Install **Microsoft ODBC Driver 13 \(Preview\) for SQL Server on Linux** on the client computer  
  
### Set up the client application  
The client application must be configured to have access to a key store containing a Column Master Key \(CMK\) protecting the data the application is going to access. For information about master keys, see [Always Encrypted \(Database Engine\)](https://msdn.microsoft.com/en-us/library/mt163865.aspx). The ODBC driver supports storing CMKs in the local machine key stores: local user and local machine.  
  
### Using the local machine key store providers  
The ODBC driver comes with a built in key store provider implementation for the local machine and local user Key Stores. Client applications should ensure that OpenSSL is installed and configured as recommended by their distribution. The creator\/administrator of certificates \(usually the DBA\) will need to distribute the CMK to each client machine that will work with encrypted columns. Specifically you will need to install the Column Master Key in the location specified when you created it on SQL Server.  On Linux Systems, the LOCALMACHINE location corresponds to the "\/etc\/ssl\/private" directory, and the CURRENTUSER location corresponds to the path “~\/ssl\/private".   You can read more about how to do this on the [Always Encrypted \(Database Engine\)](https://msdn.microsoft.com/en-us/library/mt163865.aspx) page.  
  
### Enabling Always Encrypted for a client connection  
Modify the connection string in your client application by adding the **ColumnEncryption\=Enabled** parameter to the connection string.  
  
The following is an example of a connection string for the Microsoft ODBC Driver 13 for SQL Server that enables Always Encrypted:  
  
```  
SQLWCHAR *connString = L"DRIVER=ODBC Driver 13 for SQL Server;SERVER=.;ColumnEncryption=Enabled";   
```  
  
### Inserting\/Retrieving data example  
Insert data into encrypted columns by using **SQLPrepare**\/**SQLExecute** or **SQLExecDirect** functions in conjunction with the **SQLBindParam** function. The application passes plaintext SQL with parameter markers in the function arguments, and binds buffers with plaintext values for all marked parameters. The driver then transparently encrypts these parameters and passes the encrypted values to the server. Similarly when encrypted columns are retrieved via BindCol or GetData functions, the driver transparently decrypts the values before sending the values to the cound buffers in the application. When a column is encrypted no plaintext data is available to the SQL Server; it only sends\/receives encrypted data.  
  
There is no difference in regular operation when using the ODBC driver with encrypted columns from a developer’s perspective. See the [ODBC sample code](https://code.msdn.microsoft.com/windowsapps/ODBC-sample-191624ae/sourcecode?fileId=51137&pathId=1980325953) for an example of how to interact with the driver.  
  
> [!NOTE]  
> The Preview release of the Microsoft ODBC Driver 13 for SQL Server has limited support for Always Encrypted with stored procedures. It does not yet support operations with stored procedures when Always Encrypted is enabled.  
  
> [!NOTE]  
> Queries can perform equality comparisons on columns if they are encrypted using deterministic encryption. For more information, see the **Selecting Deterministic or Randomized encryption** section of the [Always Encrypted \(Database Engine\)](https://msdn.microsoft.com/en-us/library/mt163865.aspx) topic.  
  
### Always Encrypted API reference  
There is a modification to the ODBC driver API for use in client applications that use Always Encrypted.  
  
> [!NOTE]  
> This update is available only in Microsoft ODBC Driver 13 \(Preview\) for SQL Server.  
  
**SQLServerConnection Class**  
  
|Name|Description|  
|--------|---------------|  
|New connection string keyword:<br /><br />ColumnEncryption|ColumnEncryption\=Enabled enables Always Encrypted functionality for the connection and ColumnEncryption\=Disabled disables it. Accepted values are Enabled\/Disabled. The default is Disabled.|  
  
## See Also  
[Microsoft ODBC Driver for SQL Server on Linux](../content/Microsoft-ODBC-Driver-for-SQL-Server-on-Linux.md)  
[Always Encrypted \(Database Engine\)](https://msdn.microsoft.com/en-us/library/mt163865.aspx)  
  
