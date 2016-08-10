---
title: "New Search Property List"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-search
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ffca78e9-8608-4b15-bd38-b2d78da4247a
caps.latest.revision: 23
caps.handback.revision: 0
manager: jhubbard
---
# New Search Property List
Use this dialog box to create a search property list.  
  
## Options  
 **Search property list name**  
 Enter the name of the search property list.  
  
 **Owner**  
 Specify the owner of the search property list. If you want ownership to be assigned to yourself, that is, to the current user, leave this field empty. To specify a different user, click the browse button.  
  
### Create Search Property List Options  
 Click one of the following options:  
  
 **Create an empty search property list**  
 Creates a search property list without any properties.  
  
 **Create from an existing search property list**  
 Copies the properties of an existing search property list into the new property list. Search property lists are database objects, so you must specify the database that contains the property list that you want to copy.  
  
 **Source database**  
 Specify the name of the database to which the existing search property list belongs. The current database is selected by default. Optionally, you can use the list box to select another database, if your current connection is associated with a user ID in that database.  
  
 **Source search property list**  
 Select the name of an existing search property list from those belonging to the selected database.  
  
## Permissions  
 See [CREATE SEARCH PROPERTY LIST (Transact-SQL)](assetId:///5440cbb8-3403-4d27-a2f9-8e1f5a1bc12b).  
  
## To Use SQL Server Management Studio to Manage Search Property Lists  
 For information about how to create, view, change, or delete a search property list, and about how to configure a full-text index for property searching, see [Search Document Properties with Search Property Lists](../../Topics/TopicNameNotContainA/Search-Document-Properties-with-Search-Property-Lists.md).  
  
## See Also  
 [CREATE SEARCH PROPERTY LIST (Transact-SQL)](assetId:///5440cbb8-3403-4d27-a2f9-8e1f5a1bc12b)   
 [Search Document Properties with Search Property Lists](../../Topics/TopicNameNotContainA/Search-Document-Properties-with-Search-Property-Lists.md)   
 [sys.registered_search_property_lists (Transact-SQL)](assetId:///630d4caa-9bea-4cd3-a5b1-01098b0855fc)