---
title: "Recordset (Visual C++ Syntax Index with #import)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: fe41da71-b607-4329-94da-60964b8efcdc
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
# Recordset (Visual C++ Syntax Index with #import)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <title>Methods</title>
    <content>
      <code>HRESULT AddNew( const _variant_t &amp; FieldList = vtMissing,
    const    _variant_t &amp; Values = vtMissing );

HRESULT Cancel( );

HRESULT CancelBatch( enum AffectEnum AffectRecords );

HRESULT CancelUpdate( );

_RecordsetPtr Clone( enum LockTypeEnum LockType );

HRESULT Close( );

enum CompareEnum CompareBookmarks( const _variant_t
    &amp; Bookmark1, const     _variant_t &amp; Bookmark2 );

HRESULT Delete( enum AffectEnum AffectRecords );

HRESULT Find( _bstr_t Criteria, long SkipRecords, enum
    SearchDirectionEnum SearchDirection, const _variant_t &amp; Start =
    vtMissing );

_variant_t GetRows( long Rows, const _variant_t &amp; Start =
    vtMissing, const _variant_t &amp; Fields = vtMissing );

_bstr_t GetString( enum
    StringFormatEnum StringFormat, long NumRows,     _bstr_t 
    ColumnDelimeter, _bstr_t RowDelimeter, _bstr_t NullExpr );

HRESULT Move( long NumRecords, const _variant_t &amp; Start = 
    vtMissing );

HRESULT MoveFirst( );
HRESULT MoveLast( );
HRESULT MoveNext( );
HRESULT MovePrevious( );

_RecordsetPtr NextRecordset( VARIANT * RecordsAffected );

HRESULT Open( const _variant_t &amp; Source, const _variant_t &amp;
    ActiveConnection, enum CursorTypeEnum CursorType, enum LockTypeEnum
    LockType, long Options );

HRESULT Requery( long Options );

HRESULT Update( const _variant_t &amp; Fields = vtMissing, const
    _variant_t &amp;     Values = vtMissing );

HRESULT UpdateBatch( enum AffectEnum AffectRecords );

HRESULT Resync( enum AffectEnum AffectRecords, enum
    ResyncEnum     ResyncValues );

HRESULT Save( const _variant_t &amp; Destination, enum
    PersistFormatEnum     PersistFormat );

HRESULT Seek( const _variant_t &amp; KeyValues, enum SeekEnum
    SeekOption );

VARIANT_BOOL Supports( enum CursorOptionEnum CursorOptions );</code>
    </content>
  </section>
  <section>
    <title>Properties</title>
    <content>
      <code>enum PositionEnum GetAbsolutePage( );
void PutAbsolutePage( enum PositionEnum pl );
__declspec(property(get=GetAbsolutePage,put=PutAbsolutePage)) enum
    PositionEnum AbsolutePage;

enum PositionEnum GetAbsolutePosition( );
void PutAbsolutePosition( enum PositionEnum pl );
__declspec(property(get=GetAbsolutePosition,put=PutAbsolutePosition))
    enum PositionEnum AbsolutePosition;

IDispatchPtr GetActiveCommand( );
__declspec(property(get=GetActiveCommand)) IDispatchPtr ActiveCommand;

void PutRefActiveConnection( IDispatch * pvar );
void PutActiveConnection( const _variant_t &amp; pvar );
_variant_t GetActiveConnection( );

enum CursorLocationEnum GetCursorLocation( );
void PutCursorLocation( enum CursorLocationEnum plCursorLoc );
__declspec(property(get=GetCursorLocation,put=PutCursorLocation)) enum
    CursorLocationEnum CursorLocation;

VARIANT_BOOL GetBOF( );
__declspec(property(get=GetBOF)) VARIANT_BOOL BOF;

VARIANT_BOOL GetEndOfFile( ); // Actually, GetEOF. Renamed in #import.
__declspec(property(get=GetEndOfFile)) VARIANT_BOOL EndOfFile;

_variant_t GetBookmark( );
void PutBookmark( const _variant_t &amp; pvBookmark );
__declspec(property(get=GetBookmark,put=PutBookmark)) _variant_t
    Bookmark;

long GetCacheSize( );
void PutCacheSize( long pl );
__declspec(property(get=GetCacheSize,put=PutCacheSize)) long
    CacheSize;

enum CursorTypeEnum GetCursorType( );
void PutCursorType( enum CursorTypeEnum plCursorType );
__declspec(property(get=GetCursorType,put=PutCursorType)) enum
    CursorTypeEnum CursorType;

_bstr_t GetDataMember( );
void PutDataMember( _bstr_t pbstrDataMember );
__declspec(property(get=GetDataMember,put=PutDataMember)) _bstr_t
    DataMember;

IUnknownPtr GetDataSource( );
void PutRefDataSource( IUnknown * ppunkDataSource );
__declspec(property(get=GetDataSource,put=PutRefDataSource)) IUnknownPtr
    DataSource;

enum EditModeEnum GetEditMode( );
__declspec(property(get=GetEditMode)) enum EditModeEnum EditMode;

FieldsPtr GetFields( );
__declspec(property(get=GetFields)) FieldsPtr Fields;

_variant_t GetFilter( );
void PutFilter( const _variant_t &amp; Criteria );
__declspec(property(get=GetFilter,put=PutFilter)) _variant_t Filter;

_bstr_t GetIndex( );
void PutIndex( _bstr_t pbstrIndex );
__declspec(property(get=GetIndex,put=PutIndex)) _bstr_t Index;

enum LockTypeEnum GetLockType( );
void PutLockType( enum LockTypeEnum plLockType );
__declspec(property(get=GetLockType,put=PutLockType)) enum LockTypeEnum
    LockType;

enum MarshalOptionsEnum GetMarshalOptions( );
void PutMarshalOptions( enum MarshalOptionsEnum peMarshal );
__declspec(property(get=GetMarshalOptions,put=PutMarshalOptions)) enum
    MarshalOptionsEnum MarshalOptions;

long GetMaxRecords( );
void PutMaxRecords( long plMaxRecords );
__declspec(property(get=GetMaxRecords,put=PutMaxRecords)) long
    MaxRecords;

long GetPageCount( );
__declspec(property(get=GetPageCount)) long PageCount;

long GetPageSize( );
void PutPageSize( long pl );
__declspec(property(get=GetPageSize,put=PutPageSize)) long PageSize;

long GetRecordCount( );
__declspec(property(get=GetRecordCount)) long RecordCount;

_bstr_t GetSort( );
void PutSort( _bstr_t Criteria );
__declspec(property(get=GetSort,put=PutSort)) _bstr_t Sort;

void PutRefSource( IDispatch * pvSource );
void PutSource( _bstr_t pvSource );
_variant_t GetSource( );

long GetState( );
__declspec(property(get=GetState)) long State;

long GetStatus( );
__declspec(property(get=GetStatus)) long Status;

VARIANT_BOOL GetStayInSync( );
void PutStayInSync( VARIANT_BOOL pbStayInSync );
__declspec(property(get=GetStayInSync,put=PutStayInSync)) VARIANT_BOOL
    StayInSync;</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>