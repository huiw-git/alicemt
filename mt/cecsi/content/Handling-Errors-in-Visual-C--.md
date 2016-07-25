---
title: "Handling Errors in Visual C++"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b7576f07-020a-45f7-9e79-b5756f33f7ab
caps.latest.revision: 4
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
# Handling Errors in Visual C++
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>In COM, most operations return an HRESULT return code that indicates whether a function completed successfully. The #import directive generates wrapper code around each "raw" method or property and checks the returned HRESULT. If the HRESULT indicates failure, the wrapper code throws a COM error by calling _com_issue_errorex() with the HRESULT return code as an argument. COM error objects can be caught in a <legacyBold>try-catch</legacyBold> block. (For efficiency's sake, catch a reference to a _com_error object.)</para>
    <para>Remember, these are ADO errors: they result from the ADO operation failing. Errors returned by the underlying provider appear as <legacyBold>Error</legacyBold> objects in the <legacyBold>Connection</legacyBold> object's <legacyBold>Errors</legacyBold> collection.</para>
    <para>The #import directive only creates error-handling routines for methods and properties declared in the ADO .dll. However, you can take advantage of this same error-handling mechanism by writing your own error-checking macro or inline function. See the topic Visual C++® Extensions for examples.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>