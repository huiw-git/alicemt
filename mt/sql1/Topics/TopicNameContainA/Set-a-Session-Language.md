---
title: "Set a Session Language"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: de7f2c90-8f4f-4cfc-94cc-4933a7fd2bde
caps.latest.revision: 40
caps.handback.revision: 0
manager: jhubbard
---
# Set a Session Language
The session language can be used to set how the following elements are displayed on the server, based on language and cultural preference:  
  
-   The language that will be used for error and other system messages. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] supports having multiple copies of all system error strings and messages in all the languages in which [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is available. These messages can be viewed in the [sys.messages](assetId:///8c16ecdf-68f4-4a2a-b594-086e3344e58a) catalog view. When you install a localized version of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], these system messages are translated for the language version that you install. By default, you also obtain the U.S. English set of these messages. Additionally, you can add user-defined messages in a specific language by using [sp_addmessage](assetId:///54746d30-f944-40e5-a707-f2d9be0fb9eb).  
  
-   The format of date and time data.  
  
-   The names of days and months, including abbreviations.  
  
-   The first day of the week.  
  
-   Currency data.  
  
 There are 33 languages available for use as session settings. For a list of languages, see [sys.syslanguages](assetId:///f216d1cd-997c-42f0-a737-abbdfcd88383).  
  
## Setting the Session Language from the Server  
 To set the session language from the server side, use [SET LANGUAGE](assetId:///0ec0e5cf-e115-4be9-a0db-e65837d6fa45).  
  
## Setting the Session Language from the Client  
 The session language can be set on the client side by using OLE DB, ODBC or ADO.NET. For OLE DB, use the SSPROP_INIT_CURRENTLANGUAGE property. For more information, see [Working with Languages in the User Interface](assetId:///913ab38c-e443-446c-b326-7447e95aa7f9).  
  
 For ODBC, use the Language keyword. For more information, see [SQLConfigDataSource](assetId:///003e75b1-54e5-4b36-a6f7-11e1f14cf98f).  
  
 For ADO.NET, use the **Current Language** parameter of the **ConnectionString** object. For more information, see the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Data Access Components (MDAC) software development kit (SDK) documentation.