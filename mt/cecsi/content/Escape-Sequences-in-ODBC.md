---
title: Escape Sequences in ODBC
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cf229f21-6c38-4b5b-aca8-f1be0dfeb3d0
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Escape Sequences in ODBC
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A number of language features, such as outer joins and scalar function calls, are commonly implemented by DBMSs. However, the syntaxes for these features tend to be DBMS-specific, even when standard syntaxes are defined by the various standards bodies. Because of this, ODBC defines escape sequences that contain standard syntaxes for the following language features:  </para>
    <list class="bullet">
      <listItem>
        <para>Date, time, timestamp, and datetime interval literals</para>
      </listItem>
      <listItem>
        <para>Scalar functions such as numeric, string, and data type conversion functions</para>
      </listItem>
      <listItem>
        <para>LIKE predicate escape character</para>
      </listItem>
      <listItem>
        <para>Outer joins</para>
      </listItem>
      <listItem>
        <para>Procedure calls</para>
      </listItem>
    </list>
    <para>The escape sequence used by ODBC is as follows:</para>
    <code>
        <legacyItalic>(extension)</legacyItalic>
        </code>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>The escape sequence is recognized and parsed by drivers, which replace the escape sequences with DBMS-specific grammar. For more information about escape sequence syntax, see <legacyLink xlink:href="646d5f0b-df0c-47a6-a630-99cac1026a4c">ODBC Escape Sequences</legacyLink> in Appendix C: SQL Grammar.</para>
      <alert class="note">
        <para>In ODBC 2.<legacyItalic>x</legacyItalic>, this was the standard syntax of the escape sequence:           <legacyBold>   --(*vendor(</legacyBold><legacyItalic>vendor-name</legacyItalic><legacyBold>), product(</legacyBold><legacyItalic>product-name</legacyItalic><legacyBold>)</legacyBold> <legacyItalic>extension</legacyItalic><legacyBold> *)--</legacyBold>         </para>
        <para>In addition to this syntax, a shorthand syntax was defined of the form:           <legacyBold>   {</legacyBold><legacyItalic>extension</legacyItalic><legacyBold>}</legacyBold>         </para>
        <para>In ODBC 3.<legacyItalic>x</legacyItalic>, the long form of the escape sequence has been deprecated, and the shorthand form is used exclusively.</para>
      </alert>
      <para>Because the escape sequences are mapped by the driver to DBMS-specific syntaxes, an application can use either the escape sequence or DBMS-specific syntax. However, applications that use the DBMS-specific syntax will not be interoperable. When using the escape sequence, applications should make sure that the SQL_ATTR_NOSCAN statement attribute is turned off, which it is by default. Otherwise, the escape sequence will be sent directly to the data source, where it will generally cause a syntax error.</para>
      <para>Drivers support only those escape sequences that they can map to underlying language features. For example, if the data source does not support outer joins, neither will the driver. To determine which escape sequences are supported, an application calls <legacyBold>SQLGetTypeInfo</legacyBold> and <legacyBold>SQLGetInfo</legacyBold>. For more information, see the next section, <legacyLink xlink:href="2b42a52a-6353-494c-a179-3a7533cd729f">Date, Time, and Timestamp Literals</legacyLink>.</para>
      <para>This section contains the following topics.  </para>
      <list class="bullet">
        <listItem>
          <para>             <legacyLink xlink:href="2b42a52a-6353-494c-a179-3a7533cd729f">Date, Time, and Timestamp Literals</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="10cb4dcf-4cd8-4a56-8725-d080bd3ffe47">Scalar Function Calls</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="185d6109-48cf-4981-bc40-ec2a4a90cafc">LIKE Predicate Escape Character</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="be1a0203-5da9-4871-9566-4bd3fbc0895c">Outer Joins</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="145130cc-40e7-4722-8417-dff131084752">Procedure Calls</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>