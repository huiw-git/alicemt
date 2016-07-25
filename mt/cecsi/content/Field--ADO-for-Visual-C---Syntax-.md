---
title: "Field (ADO for Visual C++ Syntax)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 04631b08-3937-440b-ac09-cd166f239908
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
# Field (ADO for Visual C++ Syntax)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <title>Methods</title>
    <content>
      <code>AppendChunk(VARIANT Data)
GetChunk(long Length, VARIANT *pvar)</code>
    </content>
  </section>
  <section>
    <title>Properties</title>
    <content>
      <code>get_ActualSize(long *pl)
get_Attributes(long *pl)
put_Attributes(long lAttributes)
get_DataFormat(IUnknown **ppiDF)
put_DataFormat(IUnknown *piDF)
get_DefinedSize(long *pl)
put_DefinedSize(long lSize)
get_Name(BSTR *pbstr)
get_NumericScale(BYTE *pbNumericScale)
put_NumericScale(BYTE bScale)
get_OriginalValue(VARIANT *pvar)
get_Precision(BYTE *pbPrecision)
put_Precision(BYTE bPrecision)
get_Type(DataTypeEnum *pDataType)
put_Type(DataTypeEnum DataType)
get_UnderlyingValue(VARIANT *pvar)
get_Value(VARIANT *pvar)
put_Value(VARIANT Val)</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>