---
title: "Visual C++ Extensions for ADO"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2952ece0-7217-4448-bb09-f6b64f43b7e2
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
# Visual C++ Extensions for ADO
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The preferred method of programming ADO with Visual C++ is using the <legacyBold>#import </legacyBold>directive, as discussed in <legacyLink xlink:href="11233b96-e05c-4221-9aed-5f20944b0f1c">Microsoft Visual C++ ADO Programming</legacyLink>. However, earlier versions of ADO shipped with an alternate method of programming using Visual C++: the Visual C++ Extensions. This section documents this feature for those who must maintain Visual C++ Extensions code, but new ADO code should be written using #<legacyBold>import</legacyBold>.</para>
    <para>One of the most tedious jobs Visual C++ programmers face when retrieving data with ADO is converting data returned as a VARIANT data type into a C++ data type, and then storing the converted data in a class or structure. In addition to being cumbersome, retrieving C++ data through a VARIANT data type diminishes performance.</para>
    <para>ADO provides an interface that supports retrieving data into native C/C++ data types without going through a VARIANT, and also provides preprocessor macros that simplify using the interface. The result is a flexible tool that is easier to use and has great performance.</para>
    <para>A common C/C++ client scenario is to bind a record in a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> to a C/C++ struct or class containing native C/C++ types. When going through VARIANTs, this involves writing conversion code from VARIANT to C/C++ native types. The Visual C++ Extensions for ADO are targeted at making this scenario much easier for the Visual C++ programmer.</para>
    <para>See the following topics to learn more about the Visual C++ Extensions for ADO.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="ff759185-df41-4507-8d12-0921894ffbd9">Using Visual C++ Extensions for ADO</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="e492d307-24cb-489c-a5b0-99cdc09b07da">Visual C++ Extensions Header</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="9739c278-582c-402b-a158-7f68a1b2c293">ADO with Visual C++ Extensions Example</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics>
<link xlink:href="d02b199e-1e52-4cc9-b118-750952ae7f63">ADO for Visual C++ Syntax Index for COM</link>
<link xlink:href="9739c278-582c-402b-a158-7f68a1b2c293">ADO with Visual C++ Extensions Example</link>
<link xlink:href="ff759185-df41-4507-8d12-0921894ffbd9">Using Visual C++ Extensions for ADO</link>
<link xlink:href="e492d307-24cb-489c-a5b0-99cdc09b07da">Visual C++ Extensions Header</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>