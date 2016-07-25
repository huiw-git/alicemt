---
title: "Collections (Visual C++ Syntax Index with #import)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 36fbca8e-1884-44b5-806b-d15e30f42fe6
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
# Collections (Visual C++ Syntax Index with #import)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>It is useful to know that collections inherit certain common methods and properties.</para>
    <para>All collections inherit the <legacyBold>Count</legacyBold> property and <legacyBold>Refresh</legacyBold> method, and all collections add the <legacyBold>Item</legacyBold> property. The <legacyBold>Errors</legacyBold> collection adds the <legacyBold>Clear</legacyBold> method. The <legacyBold>Parameters</legacyBold> collection inherits the <legacyBold>Append</legacyBold> and <legacyBold>Delete</legacyBold> methods, while the <legacyBold>Fields</legacyBold> collection adds the <legacyBold>Append</legacyBold>, <legacyBold>Delete</legacyBold>, and <legacyBold>Update</legacyBold> methods.</para>
  </introduction>
  <section>
    <title>Properties Collection</title>
    <content />
    <sections>
      <section>
        <title>Methods</title>
        <content>
          <code>HRESULT Refresh( );</code>
        </content>
      </section>
      <section>
        <title>Properties</title>
        <content>
          <code>long GetCount( ); __declspec(property(get=GetCount)) long Count;
PropertyPtr GetItem( const _variant_t &amp; Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];</code>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Errors Collection</title>
    <content />
    <sections>
      <section>
        <title>Methods</title>
        <content>
          <code>HRESULT Clear( );
HRESULT Refresh( );</code>
        </content>
      </section>
      <section>
        <title>Properties</title>
        <content>
          <code>long GetCount( ); __declspec(property(get=GetCount)) long Count;
PropertyPtr GetItem( const _variant_t &amp; Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];</code>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Parameters Collection</title>
    <content />
    <sections>
      <section>
        <title>Methods</title>
        <content>
          <code>HRESULT Append( IDispatch * Object );
HRESULT Delete( const _variant_t &amp; Index );
HRESULT Refresh( );</code>
        </content>
      </section>
      <section>
        <title>Properties</title>
        <content>
          <code>long GetCount( ); __declspec(property(get=GetCount)) long Count;
PropertyPtr GetItem( const _variant_t &amp; Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];</code>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Fields Collection</title>
    <content />
    <sections>
      <section>
        <title>Methods</title>
        <content>
          <code>HRESULT Append( _bstr_t Name, enum DataTypeEnum Type, long DefinedSize, enum FieldAttributeEnum Attrib, const _variant_t &amp; FieldValue = vtMissing );
HRESULT Delete( const _variant_t &amp; Index );
HRESULT Refresh( );
HRESULT Update( );</code>
        </content>
      </section>
      <section>
        <title>Properties</title>
        <content>
          <code>long GetCount( ); __declspec(property(get=GetCount)) long Count;
PropertyPtr GetItem( const _variant_t &amp; Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];</code>
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