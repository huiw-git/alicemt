---
title: "Record (Visual C++ Syntax Index with #import)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: ba6dd186-9552-4b6c-960b-3ee6cd589afd
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
# Record (Visual C++ Syntax Index with #import)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <title>Methods</title>
    <content>
      <code>HRESULT Cancel( );

HRESULT Close( );

_bstr_t CopyRecord( _bstr_t Source, _bstr_t Destination,
    _bstr_t     UserName, _bstr_t Password, enum CopyRecordOptionsEnum
    Options,     VARIANT_BOOL Async );

HRESULT DeleteRecord( _bstr_t Source, VARIANT_BOOL Async );

_RecordsetPtr GetChildren( );

_bstr_t MoveRecord( _bstr_t Source, _bstr_t Destination,
    _bstr_t     UserName, _bstr_t Password, enum MoveRecordOptionsEnum
    Options,     VARIANT_BOOL Async );

HRESULT Open( const _variant_t &amp; Source, const _variant_t
&amp;     ActiveConnection, enum ConnectModeEnum Mode, enum
    RecordCreateOptionsEnum CreateOptions, enum RecordOpenOptionsEnum
    Options, _bstr_t UserName, _bstr_t Password );</code>
    </content>
  </section>
  <section>
    <title>Properties</title>
    <content>
      <code>_variant_t GetActiveConnection( );
void PutActiveConnection( _bstr_t pvar );
void PutRefActiveConnection( struct _Connection * pvar );

FieldsPtr GetFields( );
__declspec(property(get=GetFields)) FieldsPtr Fields;

enum ConnectModeEnum GetMode( );
void PutMode( enum ConnectModeEnum pMode );
__declspec(property(get=GetMode,put=PutMode)) enum ConnectModeEnum Mode;

_bstr_t GetParentURL( );
__declspec(property(get=GetParentURL)) _bstr_t ParentURL;

enum RecordTypeEnum GetRecordType( );
__declspec(property(get=GetRecordType)) enum RecordTypeEnum
    RecordType;

_variant_t GetSource( );
void PutSource( _bstr_t pvar );
void PutRefSource( IDispatch * pvar );

enum ObjectStateEnum GetState( );
__declspec(property(get=GetState)) enum ObjectStateEnum State;</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>