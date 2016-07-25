---
title: "Stream (Visual C++ Syntax Index with #import)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: e59d0687-1f5a-45c5-9d0a-c1f27079495d
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
# Stream (Visual C++ Syntax Index with #import)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <title>Methods</title>
    <content>
      <code>HRESULT Cancel( );

HRESULT Close( );

HRESULT CopyTo( struct _Stream * DestStream, int CharNumber );

HRESULT Flush( );

HRESULT LoadFromFile( _bstr_t FileName );

HRESULT Open( const _variant_t &amp; Source, enum
    ConnectModeEnum Mode, enum     StreamOpenOptionsEnum Options, _bstr_t
    UserName, _bstr_t Password );

_variant_t Read( long NumBytes );

_bstr_t ReadText( long NumChars );

HRESULT SaveToFile( _bstr_t FileName, enum SaveOptionsEnum
    Options );

HRESULT SetEOS( );

HRESULT SkipLine( );

HRESULT Write( const _variant_t &amp; Buffer );

HRESULT WriteText( _bstr_t Data, enum StreamWriteEnum
    Options );</code>
    </content>
  </section>
  <section>
    <title>Properties</title>
    <content>
      <code>_bstr_t GetCharset( );
void PutCharset( _bstr_t pbstrCharset );
__declspec(property(get=GetCharset,put=PutCharset)) _bstr_t Charset;

VARIANT_BOOL GetEOS( );
__declspec(property(get=GetEOS)) VARIANT_BOOL EOS;

enum LineSeparatorEnum GetLineSeparator( );
void PutLineSeparator( enum LineSeparatorEnum pLS );
__declspec(property(get=GetLineSeparator,put=PutLineSeparator)) enum
    LineSeparatorEnum LineSeparator;

enum ConnectModeEnum GetMode( );
void PutMode( enum ConnectModeEnum pMode );
__declspec(property(get=GetMode,put=PutMode)) enum ConnectModeEnum Mode;

long GetPosition( );
void PutPosition( long pPos );
__declspec(property(get=GetPosition,put=PutPosition)) long Position;

long GetSize( );
__declspec(property(get=GetSize)) long Size;

enum ObjectStateEnum GetState( );
__declspec(property(get=GetState)) enum ObjectStateEnum State;

enum StreamTypeEnum GetType( );
void PutType( enum StreamTypeEnum ptype );
__declspec(property(get=GetType,put=PutType)) enum StreamTypeEnum Type;</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>