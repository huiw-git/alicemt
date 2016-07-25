---
title: "Collections (ADO for Visual C++ Syntax)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 6a0109a0-f2d9-4f7c-8e1e-42763f9acaea
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
# Collections (ADO for Visual C++ Syntax)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <title>Parameters</title>
    <content />
    <sections>
      <section>
        <title>Methods</title>
        <content>
          <code>Append(IDispatch *Object);
Delete(VARIANT Index);
Refresh(void);</code>
          <para>For more information, see </para>
          <list class="bullet">
            <listItem>
              <para>
                <link xlink:href="f8a9bbed-ba9c-4698-945d-317ad22d2e92">Append Method (ADO)</link>
              </para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="160c575e-df63-4ade-a2d3-5fd8f72e70cc">Delete Method (ADO Parameters Collection)</link>
              </para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh Method (ADO)</link>
              </para>
            </listItem>
          </list>
        </content>
      </section>
      <section>
        <title>Properties</title>
        <content>
          <code>get_Count(long *c);
get_Item(VARIANT Index, _ADOParameter **ppvObject);</code>
          <para>For more information, see </para>
          <list class="bullet">
            <listItem>
              <para>
                <link xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count Property (ADO)</link>
              </para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="e11484bb-c5c7-42d8-9bb8-21572125d727">Item Property (ADO)</link>
              </para>
            </listItem>
          </list>
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
          <code>Append(BSTR bstrName, DataTypeEnum Type, long DefinedSize, FieldAttributeEnum Attrib);
Delete(VARIANT Index);
Refresh(void);</code>
          <para>For more information, see </para>
          <list class="bullet">
            <listItem>
              <para>
                <link xlink:href="f8a9bbed-ba9c-4698-945d-317ad22d2e92">Append Method (ADO)</link>
              </para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="160c575e-df63-4ade-a2d3-5fd8f72e70cc">Delete Method (ADO Parameters Collection)</link>
              </para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh Method (ADO)</link>
              </para>
            </listItem>
          </list>
        </content>
      </section>
      <section>
        <title>Properties</title>
        <content>
          <code>get_Count(long *c);
get_Item(VARIANT Index, ADOField **ppvObject);</code>
          <para>For more information, see </para>
          <list class="bullet">
            <listItem>
              <para>
                <link xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count Property (ADO)</link>
              </para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="e11484bb-c5c7-42d8-9bb8-21572125d727">Item Property (ADO)</link>
              </para>
            </listItem>
          </list>
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
          <code>Clear(void);
Refresh(void);</code>
          <para>For more information, see </para>
          <list class="bullet">
            <listItem>
              <para>
                <link xlink:href="0a61ba7a-20b8-426a-91a0-9040e7c5a98a">Clear Method (ADO)</link>
              </para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh Method (ADO)</link>
              </para>
            </listItem>
          </list>
        </content>
      </section>
      <section>
        <title>Properties</title>
        <content>
          <code>get_Count(long *c);
get_Item(VARIANT Index, ADOError **ppvObject);</code>
          <para>For more information, see </para>
          <list class="bullet">
            <listItem>
              <para>
                <link xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count Property (ADO)</link>
              </para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="e11484bb-c5c7-42d8-9bb8-21572125d727">Item Property (ADO)</link>
              </para>
            </listItem>
          </list>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Properties</title>
    <content />
    <sections>
      <section>
        <title>Methods</title>
        <content>
          <code>Refresh(void);</code>
          <para>For more information, see </para>
          <list class="bullet">
            <listItem>
              <para>
                <link xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh Method (ADO)</link>
              </para>
            </listItem>
          </list>
        </content>
      </section>
      <section>
        <title>Properties</title>
        <content>
          <code>get_Count(long *c);
get_Item(VARIANT Index, ADOProperty **ppvObject);</code>
          <para>For more information, see </para>
          <list class="bullet">
            <listItem>
              <para>
                <link xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count Property (ADO)</link>
              </para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="e11484bb-c5c7-42d8-9bb8-21572125d727">Item Property (ADO)</link>
              </para>
            </listItem>
          </list>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics>
<link xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors Collection</link>
<link xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields Collection</link>
<link xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters Collection</link>
<link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>