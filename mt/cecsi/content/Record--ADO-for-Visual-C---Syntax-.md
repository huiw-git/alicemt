---
title: "Record (ADO for Visual C++ Syntax)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: c4ce8532-a4d8-4f74-9488-9389b6695958
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
# Record (ADO for Visual C++ Syntax)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <title>Methods</title>
    <content>
      <code>Cancel(void)
Close(void)
CopyRecord(BSTR Source, BSTR Destination, BSTR UserName, BSTR Password, CopyRecordOptionsEnum Options, VARIANT_BOOL Async, BSTR *pbstrNewURL)
DeleteRecord(BSTR Source, VARIANT_BOOL Async)
GetChildren(_ADORecordset **ppRSet)
MoveRecord(BSTR Source, BSTR Destination, BSTR UserName, BSTR Password, MoveRecordOptionsEnum Options, VARIANT_BOOL Async, BSTR *pbstrNewURL)
Open(VARIANT Source, VARIANT ActiveConnection, ConnectModeEnum Mode, RecordCreateOptionsEnum CreateOptions, RecordOpenOptionsEnum Options, BSTR UserName, BSTR Password)</code>
    </content>
  </section>
  <section>
    <title>Properties</title>
    <content>
      <code>get_ActiveConnection(VARIANT *pvar)
put_ActiveConnection(BSTR bstrConn)
putref_ActiveConnection(_ADOConnection *Con)
get_Fields(ADOFields **ppFlds)
get_Mode(ConnectModeEnum *pMode)
put_Mode(ConnectModeEnum Mode)
get_ParentURL(BSTR *pbstrParentURL)
get_RecordType(RecordTypeEnum *pType)
get_Source(VARIANT *pvar)
put_Source(BSTR Source)
putref_Source(IDispatch *Source)
get_State(ObjectStateEnum *pState)</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>