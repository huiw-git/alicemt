---
title: "Determining What is Supported"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 65090cba-6d46-4775-8d61-f6838e7752a6
caps.latest.revision: 10
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
# Determining What is Supported
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>Supports</legacyBold> method is used to determine whether a specified <legacyBold>Recordset</legacyBold> object supports a particular type of functionality. It has the following syntax:</para>
    <code>
        boolean = recordset.Supports(CursorOptions )</code>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyBold>Supports</legacyBold> method returns a Boolean value that indicates whether the provider supports all of the features identified by the CursorOptions argument. You can use the <legacyBold>Supports</legacyBold> method to determine what types of functionality a <legacyBold>Recordset</legacyBold> object supports. If the <legacyBold>Recordset</legacyBold> object supports the features whose corresponding constants are in <legacyItalic>CursorOptions</legacyItalic>, the <legacyBold>Supports</legacyBold> method returns <legacyBold>True</legacyBold>. Otherwise, it returns <legacyBold>False</legacyBold>.</para>
      <para>Using the <legacyBold>Supports</legacyBold> method, you can check for the ability of the <legacyBold>Recordset</legacyBold> object to add new records, use bookmarks, use the <legacyBold>Find</legacyBold> method, use scrolling, use the <legacyBold>Index</legacyBold> property, and to perform batch updates. For a complete list of constants and their meanings, see <legacyLink xlink:href="4e10cda7-ce81-4466-94c2-844d38191cf1">CursorOptionEnum</legacyLink>.</para>
      <para>Although the <legacyBold>Supports</legacyBold> method may return <legacyBold>True</legacyBold> for a given functionality, it does not guarantee that the provider can make the feature available under all circumstances. The <legacyBold>Supports</legacyBold> method simply returns whether the provider can support the specified functionality, assuming certain conditions are met. For example, the <legacyBold>Supports</legacyBold> method may indicate that a <legacyBold>Recordset</legacyBold> object supports updates, even though the cursor is based on a multiple table join — some columns of which are not updateable.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>