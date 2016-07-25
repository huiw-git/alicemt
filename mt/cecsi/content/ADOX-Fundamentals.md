---
title: "ADOX Fundamentals"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 954476fc-5f72-4ada-ace5-d9acb27d18f8
caps.latest.revision: 12
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
# ADOX Fundamentals
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Microsoft® ActiveX® Data Objects Extensions for Data Definition Language and Security (ADOX) is an extension to the ADO objects and programming model. ADOX includes objects for schema creation and modification, as well as security. Because it is an object-based approach to schema manipulation, you can write code that will work against various data sources regardless of differences in their native syntaxes.</para>
    <para>ADOX is a companion library to the core ADO objects. It exposes additional objects for creating, modifying, and deleting schema objects, such as tables and procedures. It also includes security objects to maintain users and groups and to grant and revoke permissions on objects.</para>
    <para>To use ADOX with your development tool, you should establish a reference to the ADOX type library. The description of the ADOX library is "Microsoft ADO Ext. for DDL and Security." The ADOX library file name is Msadox.dll, and the program ID (ProgID) is "ADOX". For more information about establishing references to libraries, see the documentation of your development tool.</para>
    <para>The Microsoft OLE DB Provider for the Microsoft Jet Database Engine fully supports ADOX. Certain features of ADOX may not be supported, depending on your data provider.</para>
    <para>This document assumes a working knowledge of the Microsoft® Visual Basic® programming language and a general knowledge of ADO. For more information about ADO, see the <legacyLink xlink:href="e3c50eee-964a-4abd-810d-1bd51978e814">ADO Programmer's Guide</legacyLink>. For more overview information about ADOX, see the following topics:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="31c0781c-96c8-4460-90ea-134066154fc7">ADOX Object Model</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="3f5287e9-f62c-40c4-bb59-985102be956e">ADOX Objects</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="c0c90ba9-0471-4381-96f1-376de22fa2ee">ADOX Collections</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="2ddf19e4-312e-4d21-8053-a6fc4b738ad4">ADOX Properties</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="8de11ef7-034c-4613-91df-2244171f0b9a">ADOX Methods</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="438e4369-f7e8-4dca-a709-dd501a3ca83f">ADOX Examples</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics>
<link xlink:href="ef700465-2e97-46e8-8213-2d662501e540">ADOX API Reference</link>
<link xlink:href="438e4369-f7e8-4dca-a709-dd501a3ca83f">ADOX Code Examples</link>
<link xlink:href="c0c90ba9-0471-4381-96f1-376de22fa2ee">ADOX Collections</link>
<link xlink:href="9d91f511-d46f-44ef-97ef-77bf93836186">ADOX Enumerated Constants</link>
<link xlink:href="8de11ef7-034c-4613-91df-2244171f0b9a">ADOX Methods</link>
<link xlink:href="31c0781c-96c8-4460-90ea-134066154fc7">ADOX Object Model</link>
<link xlink:href="3f5287e9-f62c-40c4-bb59-985102be956e">ADOX Objects</link>
<link xlink:href="2ddf19e4-312e-4d21-8053-a6fc4b738ad4">ADOX Properties</link>
<link xlink:href="75b774a5-fa94-490a-b521-b2b8f7d48919">Microsoft ADO MD Programmer's Reference</link>
<link xlink:href="e3c50eee-964a-4abd-810d-1bd51978e814">ADO Programmer's Guide</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>