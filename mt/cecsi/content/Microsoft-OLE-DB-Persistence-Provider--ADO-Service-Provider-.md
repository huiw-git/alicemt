---
title: "Microsoft OLE DB Persistence Provider (ADO Service Provider)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e75ef0dc-2016-4fcc-8918-23311c0d4e02
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
# Microsoft OLE DB Persistence Provider (ADO Service Provider)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Microsoft OLE DB Persistence Provider enables you to save a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object into a file, and later restore that <legacyBold>Recordset</legacyBold> object from the file. Schema information, data, and pending changes are preserved.</para>
    <para>You can save the <legacyBold>Recordset</legacyBold> in either the proprietary Advanced Data Table Gram (ADTG) format, or the open Extensible Markup Language (XML) format.</para>
  </introduction>
  <section>
    <title>Provider Keyword</title>
    <content>
      <para>To invoke this provider, specify the following keyword and value in the connection string.</para>
      <code>"Provider=<codeFeaturedElement>MSPersist</codeFeaturedElement>"</code>
    </content>
  </section>
  <section>
    <title>Errors</title>
    <content>
      <para>The following errors issued by this provider can be detected in your application.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Constant</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>E_BADSTREAM</para>
            </TD>
            <TD>
              <para>The file opened does not have a valid format (that is, the format is not ADTG or XML).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>E_CANTPERSISTROWSET</para>
            </TD>
            <TD>
              <para>The <legacyBold>Recordset</legacyBold> object saved has characteristics that prevent it from being stored.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The Microsoft OLE DB Persistence Provider exposes no dynamic properties.</para>
      <para>Currently, only parameterized hierarchical <legacyBold>Recordset</legacyBold> objects cannot be saved.</para>
      <para>For more information about persistently storing <legacyBold>Recordset</legacyBold> objects, see <legacyLink xlink:href="a9b287f5-04b0-4514-8143-f67879ca9842">Recordset Persistence</legacyLink>.</para>
      <para>When a stream is used to open a <legacyBold>Recordset,</legacyBold> there should be no parameters specified other than the <legacyItalic>Source</legacyItalic> parameter of the <legacyBold>Open</legacyBold> method.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="e75ef0dc-2016-4fcc-8918-23311c0d4e02">Microsoft OLE DB Persistence Provider (ADO Service Provider)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>