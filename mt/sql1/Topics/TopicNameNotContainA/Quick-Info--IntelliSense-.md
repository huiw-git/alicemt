---
title: "Quick Info (IntelliSense)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c8b59f4-1922-4bde-844f-5f2306514d96
caps.latest.revision: 34
caps.handback.revision: 0
manager: jhubbard
---
# Quick Info (IntelliSense)
The [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] IntelliSense **Quick Info** option displays the complete declaration for any identifier in your code. When you move the mouse pointer over an identifier, its declaration is displayed in a yellow pop-up window. In [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], **Quick Info** is available in the Database Engine and XML Query Editors.  
  
## Transact-SQL Quick Info  
 **Quick Info** displays two types of information in the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] Query Editor. When not in debug mode, **Quick Info** displays the expression declaration. When in debug mode, **Quick Info** instead displays the name of the expression and its current value.  
  
 In the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] Query Editor, **Quick Info** is available only for those parts of the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] syntax that IntelliSense supports. For example, if you move the mouse pointer over the identifier for an object that has a data type that IntelliSense does not support, the **Quick Info** pop-up window contains a message that states that the data type is not supported.  
  
## See Also  
 [Transact-SQL Syntax Supported by IntelliSense](../../Topics/TopicNameNotContainA/Transact-SQL-Syntax-Supported-by-IntelliSense.md)