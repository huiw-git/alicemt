---
title: "Collections (ADO/WFC Syntax)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 073f9a0e-c755-42dd-9f71-4647d68e331a
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
# Collections (ADO/WFC Syntax)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>       <legacyBold>package com.ms.wfc.data</legacyBold>     </para>
  </introduction>
  <section>
    <title>Parameters</title>
    <content />
    <sections>
      <section>
        <title>Methods</title>
        <content>
          <code>public void append(com.ms.wfc.data.Parameter param)
public void delete(int n)
public void delete(String s)
public void refresh()
public Parameter getItem(int n)
public Parameter getItem(String s)</code>
        </content>
      </section>
      <section>
        <title>Properties</title>
        <content>
          <code>public int getCount()</code>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Fields</title>
    <content />
    <sections>
      <section>
        <title>Methods</title>
        <content>
          <code>public void append(String name, int type)
public void append(String name, int type, int definedSize)
public void append(String name, int type, int definedSize, int attrib)
public void delete(int n)
public void delete(String s)
public void refresh()
public com.ms.wfc.data.Field getItem(int n)
public com.ms.wfc.data.Field getItem(String s)</code>
        </content>
      </section>
      <section>
        <title>Properties</title>
        <content>
          <code>public int getCount()</code>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Errors</title>
    <content />
    <sections>
      <section>
        <title>Methods</title>
        <content>
          <code>public void clear()
public void refresh()
public com.ms.wfc.data.Error getItem(int n)
public com.ms.wfc.data.Error getItem(String s)</code>
        </content>
      </section>
      <section>
        <title>Properties</title>
        <content>
          <code>public int getCount()</code>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics>
<link xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors Collection</link>
<link xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields Collection</link>
<link xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>