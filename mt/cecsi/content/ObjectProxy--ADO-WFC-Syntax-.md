---
title: "ObjectProxy (ADO/WFC Syntax)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: f68f58bc-ad28-46cc-9fb3-099e1a678397
caps.latest.revision: 8
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
# ObjectProxy (ADO/WFC Syntax)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>An <legacyBold>ObjectProxy</legacyBold> object represents a server, and is returned by the <legacyBold>createObject</legacyBold> method of the <legacyLink xlink:href="9194bffa-5bdf-4dff-af86-f7158c23bfa7">DataSpace</legacyLink> object. The ObjectProxy class has one method, <legacyBold>call</legacyBold>, which can invoke a method on the server and return an object resulting from that invocation.</para>
    <para>
      <legacyBold>package com.ms.wfc.data</legacyBold>
    </para>
  </introduction>
  <section>
    <title>Methods</title>
    <content>
      <para />
    </content>
    <sections>
      <section>
        <title>Call Method (ADO/WFC Syntax)</title>
        <content>
          <para>Invokes a method on the server represented by the ObjectProxy. Optionally, method arguments may be passed as an array of objects.</para>
        </content>
        <sections>
          <section>
            <title>Syntax</title>
            <content>
              <code>public Object <legacyItalic>ObjectProxy</legacyItalic>.( String <legacyItalic>method</legacyItalic> )
public Object <legacyItalic>ObjectProxy</legacyItalic>.( String <legacyItalic>method</legacyItalic>, Object[] <legacyItalic>args</legacyItalic>)</code>
            </content>
          </section>
          <section>
            <title>Returns</title>
            <content>
              <definitionTable>
                <definedTerm>Object </definedTerm>
                <definition>
                  <para>An object resulting from invoking the method.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Parameters</title>
            <content>
              <definitionTable>
                <definedTerm> <legacyItalic>ObjectProxy</legacyItalic> </definedTerm>
                <definition>
                  <para>An <legacyBold>ObjectProxy</legacyBold> object that represents the server.</para>
                </definition>
                <definedTerm> <legacyItalic>method</legacyItalic> </definedTerm>
                <definition>
                  <para>A String, containing the name of the method to invoke on the server.</para>
                </definition>
                <definedTerm> <legacyItalic>args</legacyItalic> </definedTerm>
                <definition>
                  <para>Optional. An array of objects that are arguments to the method on the server. Java data types are automatically converted to data types suitable for use on the server.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>