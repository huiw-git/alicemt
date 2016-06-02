---
title: Search an Active Document Incrementally
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 490bb36c-dd43-4219-9e2a-ff27046b9395
---
# Search an Active Document Incrementally
  You can search a single document or window incrementally by entering text. The search operation highlights the first set of characters that matches the characters entered during the incremental search in the document or window. Incremental search automatically searches all of the text within a document or window except for text that has been hidden.  
  
 For the **Match case** option, incremental search uses the criteria from your previous search. For example, if you searched across multiple files using the **Find in Files** dialog box and select **Match Case**, and you next search incrementally, the search will be case\-sensitive.  
  
### To search incrementally  
  
1.  Open the file or window to you want to search.  
  
2.  On the **Edit** menu, point to **Advanced**, and then click **Incremental Search**.  
  
     The cursor icon changes to a binocular with an arrow, indicating the search direction, and the status bar displays "Incremental Search."  
  
3.  Begin typing the text string.  
  
     The status bar displays the text you are entering while the editor highlights the first occurrence that matches the text. As you continue typing, the editor moves to the next match and highlights it. If no matches are available, the status bar displays the following.  
  
    ```  
    Incremental Search: <text> (not found)  
    ```  
  
 Incremental searches are performed from the current location in the document downwards from left to right. Incremental searches can be done using keyboard shortcut keys.  
  
> [!NOTE]  
>  For a complete list of keyboard shortcut keys, see [SQL Server Management Studio Keyboard Shortcuts](../../Topics\TopicNameNotContainA/SQL-Server-Management-Studio-Keyboard-Shortcuts.md).  
  
## See Also  
 [Search and Replace](../../Topics\TopicNameNotContainA/Search-and-Replace.md)   
 [Search Documents Interactively](../../Topics\TopicNameNotContainA/Search-Documents-Interactively.md)   
 [Search Documents Using Results Lists](../../Topics\TopicNameNotContainA/Search-Documents-Using-Results-Lists.md)   
 [Search Text with Wildcards](../../Topics\TopicNameNotContainA/Search-Text-with-Wildcards.md)   
 [Search Text with Regular Expressions](../../Topics\TopicNameNotContainA/Search-Text-with-Regular-Expressions.md)  
  
  