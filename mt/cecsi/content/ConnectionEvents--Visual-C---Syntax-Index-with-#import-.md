---
title: "ConnectionEvents (Visual C++ Syntax Index with #import)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: dd052d36-7730-4400-822b-0544fb1992b4
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
# ConnectionEvents (Visual C++ Syntax Index with #import)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <title>Events</title>
    <content>
      <code>HRESULT InfoMessage( struct Error * pError, enum
    EventStatusEnum *     adStatus, struct _Connection * pConnection );

HRESULT BeginTransComplete( long TransactionLevel,
    struct Error * pError, enum EventStatusEnum * adStatus, struct
    _Connection * pConnection );

HRESULT CommitTransComplete( struct Error *
    pError, enum EventStatusEnum     * adStatus, struct _Connection *
    pConnection );

HRESULT RollbackTransComplete( struct Error *
    pError, enum     EventStatusEnum * adStatus, struct _Connection *
    pConnection );

HRESULT WillExecute( BSTR * Source, enum
    CursorTypeEnum * CursorType,
    enum LockTypeEnum * LockType, long * Options, enum EventStatusEnum *
    adStatus, struct _Command * pCommand, struct _Recordset * pRecordset,
    struct _Connection * pConnection );

HRESULT ExecuteComplete( long RecordsAffected, struct
    Error * pError,     enum EventStatusEnum * adStatus, struct _Command
    * pCommand, struct     _Recordset * pRecordset, struct _Connection *
    pConnection );

HRESULT WillConnect( BSTR * ConnectionString, BSTR *
    UserID, BSTR *     Password, long * Options, enum EventStatusEnum *
    adStatus, struct     _Connection * pConnection );

HRESULT ConnectComplete( struct Error *
    pError, enum EventStatusEnum *     adStatus, struct _Connection *
    pConnection );

HRESULT Disconnect( enum EventStatusEnum *
    adStatus, struct _Connection *     pConnection );</code>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>