---
title: Set a Session Language
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: de7f2c90-8f4f-4cfc-94cc-4933a7fd2bde
---
# Set a Session Language
  The session language can be used to set how the following elements are displayed on the server, based on language and cultural preference:  
  
-   The language that will be used for error and other system messages. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] supports having multiple copies of all system error strings and messages in all the languages in which [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is available. These messages can be viewed in the [sys.messages](../Topic/sys.messages%20\(Transact-SQL\).md) catalog view. When you install a localized version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], these system messages are translated for the language version that you install. By default, you also obtain the U.S. English set of these messages. Additionally, you can add user\-defined messages in a specific language by using [sp\_addmessage](../Topic/sp_addmessage%20\(Transact-SQL\).md).  
  
-   The format of date and time data.  
  
-   The names of days and months, including abbreviations.  
  
-   The first day of the week.  
  
-   Currency data.  
  
 There are 33 languages available for use as session settings. For a list of languages, see [sys.syslanguages](../Topic/sys.syslanguages%20\(Transact-SQL\).md).  
  
## Setting the Session Language from the Server  
 To set the session language from the server side, use [SET LANGUAGE](../Topic/SET%20LANGUAGE%20\(Transact-SQL\).md).  
  
## Setting the Session Language from the Client  
 The session language can be set on the client side by using OLE DB, ODBC or ADO.NET. For OLE DB, use the SSPROP\_INIT\_CURRENTLANGUAGE property. For more information, see [Initialization and Authorization Properties](../Topic/Initialization%20and%20Authorization%20Properties.md).  
  
 For ODBC, use the Language keyword. For more information, see [SQLConfigDataSource](../Topic/SQLConfigDataSource.md).  
  
 For ADO.NET, use the **Current Language** parameter of the **ConnectionString** object. For more information, see the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Data Access Components \(MDAC\) software development kit \(SDK\) documentation.  
  
  