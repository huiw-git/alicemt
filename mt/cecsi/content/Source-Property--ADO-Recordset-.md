---
title: "Source Property (ADO Recordset)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: a05ba2c9-2821-4343-8607-4de9b764ec91
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
# Source Property (ADO Recordset)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the data source for a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets a <legacyBold>String</legacyBold> value or <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object reference; returns only a <legacyBold>String</legacyBold> value that indicates the source of the <legacyBold>Recordset</legacyBold>.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>Source</legacyBold> property to specify a data source for a <legacyBold>Recordset</legacyBold> object using one of the following: a <legacyBold>Command</legacyBold> object variable, an SQL statement, a stored procedure, or a table name.</para>
      <para>If you set the <legacyBold>Source</legacyBold> property to a <legacyBold>Command</legacyBold> object, the <legacyLink xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection</legacyLink> property of the <legacyBold>Recordset</legacyBold> object will inherit the value of the <legacyBold>ActiveConnection</legacyBold> property for the specified <legacyBold>Command</legacyBold> object. However, reading the <legacyBold>Source</legacyBold> property does not return a <legacyBold>Command</legacyBold> object; instead, it returns the <legacyLink xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText</legacyLink> property of the <legacyBold>Command</legacyBold> object to which you set the <legacyBold>Source</legacyBold> property.</para>
      <para>If the <legacyBold>Source</legacyBold> property is an SQL statement, a stored procedure, or a table name, you can optimize performance by passing the appropriate <legacyItalic>Options</legacyItalic> argument with the <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> method call.</para>
      <para>The <legacyBold>Source</legacyBold> property is read/write for closed <legacyBold>Recordset</legacyBold> objects and read-only for open <legacyBold>Recordset</legacyBold> objects.</para>
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
<link xlink:href="7c83eb01-71c7-4c5d-9778-6270471c8164">Visual Basic Example</link>
<link xlink:href="4044ba15-f013-4c4c-9fe1-b4410fe9a778">Source Property (ADO Error)</link>
<link xlink:href="2c18279e-6f35-4af0-b12e-8f1543d9ed20">Source Property (ADO Record)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>