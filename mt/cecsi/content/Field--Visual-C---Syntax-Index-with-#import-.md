---
title: "Field (Visual C++ Syntax Index with #import)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 90cb636a-9416-48a4-b4eb-bb11bbd40950
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
# Field (Visual C++ Syntax Index with #import)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <title>Methods</title>
    <content>
      <code>HRESULT AppendChunk( const _variant_t &amp; Data );

_variant_t GetChunk( long Length );</code>
    </content>
  </section>
  <section>
    <title>Properties</title>
    <content>
      <code>long GetActualSize( );
__declspec(property(get=GetActualSize)) long ActualSize;

long GetAttributes( );
void PutAttributes( long pl );
__declspec(property(get=GetAttributes,put=PutAttributes)) long     Attributes;

IUnknownPtr GetDataFormat( );
void PutRefDataFormat( IUnknown * ppiDF );
__declspec(property(get=GetDataFormat,put=PutRefDataFormat)) IunknownPtr
    DataFormat;

long GetDefinedSize( );
void PutDefinedSize( long pl );
__declspec(property(get=GetDefinedSize,put=PutDefinedSize)) long
    DefinedSize;

_bstr_t GetName( );
__declspec(property(get=GetName)) _bstr_t Name;

unsigned char GetNumericScale( );
void PutNumericScale( unsigned char pbNumericScale );
__declspec(property(get=GetNumericScale,put=PutNumericScale)) unsigned
    char NumericScale;

_variant_t GetOriginalValue( );
__declspec(property(get=GetOriginalValue)) _variant_t OriginalValue;

unsigned char GetPrecision( );
void PutPrecision( unsigned char pbPrecision );
__declspec(property(get=GetPrecision,put=PutPrecision)) unsigned char
    Precision;

enum DataTypeEnum GetType( );
void PutType( enum DataTypeEnum pDataType );
__declspec(property(get=GetType,put=PutType)) enum DataTypeEnum Type;

_variant_t GetUnderlyingValue( );
__declspec(property(get=GetUnderlyingValue)) _variant_t UnderlyingValue;

_variant_t GetValue( );
void PutValue( const _variant_t &amp; pvar );
__declspec(property(get=GetValue,put=PutValue)) _variant_t Value;</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>