---
title: "Stream (ADO for Visual C++ Syntax)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: dddcceef-9296-4fb3-8eca-94b17d0148de
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
# Stream (ADO for Visual C++ Syntax)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <title>Methods</title>
    <content>
      <code>Cancel(void)
Close(void)
CopyTo(_ADOStream *DestStream, LONG CharNumber = -1)
Flush(void)
LoadFromFile(BSTR FileName)
Open(VARIANT Source, ConnectModeEnum Mode, StreamOpenOptionsEnum Options, BSTR UserName, BSTR Password)
Read(long NumBytes, VARIANT *pVal)
ReadText(long NumChars, BSTR *pbstr)
SaveToFile(BSTR FileName, SaveOptionsEnum Options = adSaveCreateNotExist)
SetEOS(void)
SkipLine(void)
Write(VARIANT Buffer)
WriteText(BSTR Data, StreamWriteEnum Options = adWriteChar)</code>
    </content>
  </section>
  <section>
    <title>Properties</title>
    <content>
      <code>get_Charset(BSTR *pbstrCharset)
put_Charset(BSTR Charset)
get_EOS(VARIANT_BOOL *pEOS)
get_LineSeparator(LineSeparatorEnum *pLS)
put_LineSeparator(LineSeparatorEnum LineSeparator)
get_Mode(ConnectModeEnum *pMode)
put_Mode(ConnectModeEnum Mode)
get_Position(LONG *pPos)
put_Position(LONG Position)
get_Size(LONG *pSize)
get_State(ObjectStateEnum *pState)
get_Type(StreamTypeEnum *pType)
put_Type(StreamTypeEnum Type)</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>