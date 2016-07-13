---
title: Types of Applications
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d346a64e-a32c-4153-a40f-5b53c2f57ef2
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Types of Applications
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC applications can be classified as follows:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>Pure ODBC 2.</legacyBold>
          <legacyBold>
            <legacyItalic>x</legacyItalic>
          </legacyBold>
          <legacyBold> Application</legacyBold> A 32-bit application that: </para>
        <list class="bullet">
          <listItem>
            <para>Calls only ODBC 2.<legacyItalic>x </legacyItalic>functions (including the ODBC 1.0 function <legacyBold>SQLSetParam</legacyBold>). These include ODBC 1.<legacyItalic>x </legacyItalic>applications that have been ported to 32-bit.</para>
          </listItem>
          <listItem>
            <para>Expects ODBC 2.<legacyItalic>x </legacyItalic>behavior for features that have had behavioral changes. (See <legacyLink xlink:href="a17ae701-6ab6-4eaf-9e46-d3b9cd0a3a67">Behavioral Changes</legacyLink> for more information.)</para>
          </listItem>
          <listItem>
            <para>Has not been recompiled with ODBC 3.5 headers.</para>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Pure ODBC 2.</legacyBold>
          <legacyBold>
            <legacyItalic>x</legacyItalic>
          </legacyBold>
          <legacyBold> Recompiled Application</legacyBold> A pure ODBC 2.<legacyItalic>x</legacyItalic> application that has been recompiled using the ODBC 3.5 header files, by setting ODBCVER=0x0250.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Pure ODBC 2.</legacyBold>
          <legacyBold>
            <legacyItalic>x</legacyItalic>
          </legacyBold>
          <legacyBold> Unicode Application</legacyBold> A pure ODBC 2.<legacyItalic>x </legacyItalic>recompiled application that is Unicode-compliant and uses the SQL_WCHAR data type.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Pure Open Group and ISO</legacyBold>–<legacyBold>compliant ODBC Application</legacyBold> A 32-bit application that: </para>
        <list class="bullet">
          <listItem>
            <para>Calls functions defined in the Open Group or ISO CLI standards. (These functions may include deprecated 3.0 functions.)</para>
          </listItem>
          <listItem>
            <para>Does not use the Unicode data types.</para>
          </listItem>
          <listItem>
            <para>Expects ODBC 3.0 behavior for features that have had behavioral changes.</para>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Pure ODBC 3.0 Application</legacyBold> A 32-bit application that: </para>
        <list class="bullet">
          <listItem>
            <para>Is compiled with 3.0 headers.</para>
          </listItem>
          <listItem>
            <para>Calls any ODBC 3.0 function, possibly including those that are deprecated.</para>
          </listItem>
          <listItem>
            <para>Expects ODBC 3.0 behavior for features that have had behavioral changes.</para>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Pure ODBC 3.5 Application</legacyBold> A 32 or 64-bit application that:</para>
        <list class="bullet">
          <listItem>
            <para>May use Unicode data types.</para>
          </listItem>
          <listItem>
            <para>Calls any ODBC 3.5 function, possibly including those that are deprecated.</para>
          </listItem>
          <listItem>
            <para>Expects ODBC 3.5 behavior for features that have had behavioral changes.</para>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Pure ODBC 3.8 (or later) Application</legacyBold> A 32-bit or 64-bit application that:</para>
        <list class="bullet">
          <listItem>
            <para>May use Unicode data types.</para>
          </listItem>
          <listItem>
            <para>Calls any ODBC 3.8 function, possibly including those that are deprecated.</para>
          </listItem>
          <listItem>
            <para>Expects ODBC 3.8 behavior for features that have had behavioral changes.</para>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Replaced Application</legacyBold> A 32 or 64-bit application that:</para>
        <list class="bullet">
          <listItem>
            <para>Implements new behavior for duplicated functionality.</para>
          </listItem>
          <listItem>
            <para>Uses any new features in a later version of ODBC only within conditional code.</para>
          </listItem>
          <listItem>
            <para>Has limited conditional code to handle behavioral changes or has registered itself to be an earlier version of ODBC application.</para>
          </listItem>
        </list>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>