---
title: "Referencing the ADO Libraries In a Visual C++ Application"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d3ea12ec-bca8-48c3-af57-ce14576108c9
caps.latest.revision: 11
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
# Referencing the ADO Libraries In a Visual C++ Application
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>To use the latest version of ADO in a Visual C++ application, use the following <codeInline>#import</codeInline> directive:</para>
    <code>#import "msado15.dll" \
    no_namespace rename("EOF", "EndOfFile")</code>
    <para>To use ADO MD or ADOX, you must import <legacyItalic>msadomd.dll</legacyItalic> or <legacyItalic>msadox.dll</legacyItalic>, by using the syntax above.</para>
  </introduction>
  <section>
    <title>Backward Compatibility</title>
    <content>
      <para>To use any earlier version of ADO, replace <legacyItalic>msado15.dll</legacyItalic> above with one of the following type libraries.  </para>
      <list class="bullet">
        <listItem>
          <para>             <legacyItalic>msado27.tlb</legacyItalic>, ADO 2.7 Type Library</para>
        </listItem>
        <listItem>
          <para>             <legacyItalic>msado26.tlb</legacyItalic>, ADO 2.6 Type Library</para>
        </listItem>
        <listItem>
          <para>             <legacyItalic>msado25.tlb</legacyItalic>, ADO 2.5 Type Library</para>
        </listItem>
        <listItem>
          <para>             <legacyItalic>msado21.tlb</legacyItalic>, ADO 2.1 Type Library</para>
        </listItem>
        <listItem>
          <para>             <legacyItalic>msado20.tlb</legacyItalic>, ADO 2.0 Type Library</para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>