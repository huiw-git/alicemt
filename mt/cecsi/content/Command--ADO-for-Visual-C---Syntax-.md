---
title: "Command (ADO for Visual C++ Syntax)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: cf12cbd1-25f7-4bb5-aa94-0fe823b3b6d6
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
# Command (ADO for Visual C++ Syntax)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <title>Methods</title>
    <content>
      <code>Cancel(void)
CreateParameter(BSTR Name, DataTypeEnum Type, ParameterDirectionEnum Direction, long Size, VARIANT Value, _ADOParameter **ppiprm)
Execute(VARIANT *RecordsAffected, VARIANT *Parameters, long Options, _ADORecordset **ppirs)</code>
    </content>
  </section>
  <section>
    <title>Properties</title>
    <content>
      <code>get_ActiveConnection(_ADOConnection **ppvObject)
put_ActiveConnection(VARIANT vConn)
putref_ActiveConnection(_ADOConnection *pCon)
get_CommandText(BSTR *pbstr)
put_CommandText(BSTR bstr)
get_CommandTimeout(LONG *pl)
put_CommandTimeout(LONG Timeout)
get_CommandType(CommandTypeEnum *plCmdType)
put_CommandType(CommandTypeEnum lCmdType)
get_Name(BSTR *pbstrName)
put_Name(BSTR bstrName)
get_Prepared(VARIANT_BOOL *pfPrepared)
put_Prepared(VARIANT_BOOL fPrepared)
get_State(LONG *plObjState)
get_Parameters(ADOParameters **ppvObject)</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>