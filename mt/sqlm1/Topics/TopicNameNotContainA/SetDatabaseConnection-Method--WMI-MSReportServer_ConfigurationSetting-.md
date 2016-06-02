---
title: SetDatabaseConnection Method (WMI MSReportServer_ConfigurationSetting)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SetDatabaseConnection (WMI MSReportServer_ConfigurationSetting Class)
apilocation: 
  - reportingservices.mof
apitype: MOFDef
ms.assetid: c040aa78-92b8-41e4-9ae2-eff9fcdddc5b
---
# SetDatabaseConnection Method (WMI MSReportServer_ConfigurationSetting)
  Sets the report server database connection to a particular report server database.  
  
## Syntax  
  
```vb#  
Public Sub SetDatabaseConnection(Server as String, _  
    DatabaseName as string, CredentialsType as Integer, _  
    Username as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```c#  
public void BackupEncryptionKey(string Server,   
    string DatabaseName, Int32 CredentialsType,   
    string UserName, string Password, out Int32 HRESULT);  
```  
  
## Parameters  
 *Server*  
 The name of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance that is used to host the report server database.  
  
 *DatabaseName*  
 The name of the report server database.  
  
 *CredentialsType*  
 The type of credentials to use for the connection. Values can be:  
  
-   0 \- Windows  
  
-   1 – [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]  
  
-   2 \- Windows Service  
  
 *UserName*  
 The account name used to connect to the report server database.  
  
 *Password*  
 The password used to connect to the report server database.  
  
 *HRESULT*  
 \[out\] Value indicating whether the call succeeded or failed.  
  
## Return Value  
 Returns an *HRESULT* indicating success or failure of the method call. A value of 0 indicates that the method call was successful. A non\-zero value indicates that an error has occurred.  
  
## Remarks  
 When the *CredentialsType* parameter is set to 0 \(Windows\), the *UserName* and *Password* parameters must be set. The *UserName* parameter must be in the form "domain\\username", and the value must represent a valid Windows logon.  
  
 When the *CredentialsType* parameter is set to 1 \([!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\), the value passed in the *UserName* parameter must conform to the requirements of a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login name.  
  
 When the *CredentialsType* parameter is set to 2 \(Windows Service\), the report server uses integrated security to connect to the report server database and the *UserName* and *Password* parameters are ignored. The Reporting Server Web service will use either the [!INCLUDE[vstecasp](../../Token\Other/vstecasp_md.md)] account or an application pool’s account and the Windows service account to access the report server database.  
  
 When called, the SetDatabaseConnection method encrypts and stores the credentials and database information in the configuration file for the specified report server.  
  
 The SetDatabaseConnection method does not check that the report server can connect to the report server database using the data specified.  
  
 When set for the first time, the ConnectionPoolSize property is set based on the following processors: ConnectionPoolSize \= \#Processors \* 75.  
  
 The SetDatabaseConnection method does not grant permissions to the specified account\(s\). You must call the [GenerateDatabaseRightsScript](../Topic/GenerateDatabaseRightsScript%20Method%20\(WMI%20MSReportServer_ConfigurationSetting\).md) method for each account that requires access to the report server database and run the resulting script.  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Token\Other/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)  
  
  