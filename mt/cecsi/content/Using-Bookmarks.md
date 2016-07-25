---
title: "Using Bookmarks"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cca244e6-84f8-4394-bca9-f7a819b8f4df
caps.latest.revision: 9
manager: sonalm
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
# Using Bookmarks
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>It is often useful to return directly to a specific record after having moved around in the <legacyBold>Recordset</legacyBold> without having to scroll through every record and compare values. For example, if you attempt to search for a record using the <legacyBold>Find</legacyBold> method but the search returns no records, you are automatically placed at either end of the <legacyBold>Recordset</legacyBold>. If your provider supports them, bookmarks can be used to mark your place before using the <legacyBold>Find</legacyBold> method so you can return to your location. A bookmark is a <legacyBold>Variant</legacyBold> type value that uniquely identifies a record in a <legacyBold>Recordset</legacyBold> object. </para>
    <para>You can also use a variant array of bookmarks with the <legacyBold>Recordset</legacyBold> <legacyBold>Filter</legacyBold> method to filter on a selected set of records. For details about this technique, see Filtering the Results in the topic, <legacyLink xlink:href="bdf9a56a-de4a-44de-9111-2f11ab7b16ea">Working with Recordsets</legacyLink>, later in this section.</para>
    <para>You can use the <legacyBold>Bookmark</legacyBold> property to get a bookmark for a record, or set the current record in a <legacyBold>Recordset</legacyBold> object to the record identified by a valid bookmark. The following code uses the <legacyBold>Bookmark</legacyBold> property to set a bookmark and then return to the bookmarked record after moving on to other records. To determine if your <legacyBold>Recordset</legacyBold> supports bookmarks, use the <legacyBold>Supports</legacyBold> method. </para>
    <code>    'BeginBookmarkEg
    Dim varBookmark As Variant
    Dim blnCanBkmrk As Boolean
    
    objRs.Open strSQL, strConnStr, adOpenStatic, adLockOptimistic, adCmdText
    
    If objRs.RecordCount &gt; 4 Then
        objRs.Move 4                       ' move to the fifth record
        blnCanBkmrk = objRs.Supports(adBookmark)
        If blnCanBkmrk = True Then
            varBookmark = objRs.Bookmark   ' record the bookmark
            objRs.MoveLast                 ' move to a different record
            objRs.Bookmark = varBookmark   ' return to the bookmarked (sixth) record
        End If
    End If
    'EndBookmarkEg</code>
    <para>The <legacyLink xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports</legacyLink> method is covered in more detail later. </para>
    <para>Except for the case of cloned <legacyBold>Recordsets</legacyBold>, bookmarks are unique to the <legacyBold>Recordset</legacyBold> in which they were created, even if the same command is used. This means that you cannot use a <legacyBold>Bookmark</legacyBold> obtained from one <legacyBold>Recordset</legacyBold> to move to the same record in a second <legacyBold>Recordset</legacyBold> opened with the same command.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>