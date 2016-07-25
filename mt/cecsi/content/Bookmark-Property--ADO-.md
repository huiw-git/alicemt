---
title: "Bookmark Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 481dcc93-487b-490e-ac58-a1e9b2ebfd43
caps.latest.revision: 11
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
# Bookmark Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates a bookmark that uniquely identifies the current record in a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object or sets the current record in a <legacyBold>Recordset</legacyBold> object to the record identified by a valid bookmark.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>Variant</languageKeyword> expression that evaluates to a valid bookmark.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>Bookmark</legacyBold> property to save the position of the current record and return to that record at any time. Bookmarks are available only in <legacyBold>Recordset</legacyBold> objects that support bookmark functionality.</para>
      <para>When you open a <legacyBold>Recordset</legacyBold> object, each of its records has a unique bookmark. To save the bookmark for the current record, assign the value of the <legacyBold>Bookmark</legacyBold> property to a variable. To quickly return to that record at any time after moving to a different record, set the <legacyBold>Recordset</legacyBold> object's <legacyBold>Bookmark</legacyBold> property to the value of that variable.</para>
      <para>The user may not be able to view the value of the bookmark. Also, users should not expect bookmarks to be directly comparable — two bookmarks that refer to the same record may have different values.</para>
      <para>If you use the <legacyLink xlink:href="ad49265f-1c05-4271-9bbf-7c00010ac18c">Clone</legacyLink> method to create a copy of a <legacyBold>Recordset</legacyBold> object, the <legacyBold>Bookmark</legacyBold> property settings for the original and the duplicate <legacyBold>Recordset</legacyBold> objects are identical and you can use them interchangeably. However, you cannot use bookmarks from different <legacyBold>Recordset</legacyBold> objects interchangeably, even if they were created from the same source or command.</para>
      <alert class="note">
        <para>
          <legacyBold>Remote Data Service Usage</legacyBold>   When used on a client-side <legacyBold>Recordset</legacyBold> object, the <legacyBold>Bookmark</legacyBold> property is always available.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b6573c6e-fee8-4267-a722-fadaec6eafe6">Visual Basic Example</link>
<link xlink:href="bd2b9d85-e75e-4fc8-a392-076582019caa">Visual C++ Example</link>
<link xlink:href="eecd75a8-3e4f-4a18-b1c1-4c053dd7833f">Visual J++ Example</link>
<link xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>