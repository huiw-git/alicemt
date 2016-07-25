---
title: "DataSpace (ADO/WFC Syntax)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 950d45d8-07de-467b-b255-f9a7b997204c
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
# DataSpace (ADO/WFC Syntax)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>createObject</legacyBold> method of the <legacyBold>DataSpace</legacyBold> class specifies both a business object to process client application requests (<legacyItalic>progid</legacyItalic>) and the communications protocol and server (<legacyItalic>connection</legacyItalic>). <legacyBold>createObject</legacyBold> returns an <legacyLink xlink:href="f68f58bc-ad28-46cc-9fb3-099e1a678397">ObjectProxy</legacyLink> object that represents the server.</para>
  </introduction>
  <section>
    <title>package com.ms.wfc.data</title>
    <content />
    <sections>
      <section>
        <title>Constructor</title>
        <content>
          <code>public DataSpace()</code>
        </content>
      </section>
      <section>
        <title>Methods</title>
        <content>
          <code>public static ObjectProxy DataSpace.createObject(String
    progid, String connection)</code>
        </content>
      </section>
      <section>
        <title>Properties</title>
        <content>
          <code>public static int getInternetTimeout()
public static void setInternetTimeout(int plInetTimeout)</code>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics>
<link xlink:href="9194bffa-5bdf-4dff-af86-f7158c23bfa7">DataSpace Object (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>