---
title: Types of Drivers
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 864c53c1-b68a-48b6-b6bc-5ecb520bb9dc
translation.priority.ht: 
  - en-gb
---
# Types of Drivers
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC drivers can be classified as follows:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>32-bit ODBC 2.</legacyBold>
          <legacyBold>
            <legacyItalic>x</legacyItalic>
          </legacyBold>
          <legacyBold> Driver</legacyBold> A 32-bit driver that: </para>
        <list class="bullet">
          <listItem>
            <para>Exports only ODBC 2<legacyItalic>.x</legacyItalic> functions.</para>
          </listItem>
          <listItem>
            <para>Exhibits ODBC 2.<legacyItalic>x </legacyItalic>behavior for behavioral changes.</para>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>
          <legacyBold>ISO and Open Group-Compliant Driver</legacyBold> A 32-bit driver that: </para>
        <list class="bullet">
          <listItem>
            <para>Exports all functions that are documented in the Open Group or ISO CLI documents. This will include some of functions that are deprecated in ODBC.</para>
          </listItem>
          <listItem>
            <para>Exhibits ODBC 3.0 behavior for behavioral changes.</para>
          </listItem>
          <listItem>
            <para>Does not necessarily go through the ODBC 3.0 Driver Manager.</para>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>
          <legacyBold>ODBC 3.0 Driver</legacyBold> A 32-bit driver that: </para>
        <list class="bullet">
          <listItem>
            <para>Exports only functions that are in ODBC 3.0 minus deprecated functions.</para>
          </listItem>
          <listItem>
            <para>Is capable of exhibiting ODBC 2.<legacyItalic>x </legacyItalic>behavior or ODBC 3.0 behavior with respect to behavioral changes, based on the SQL_ATTR_APP_ODBC_VERSION environment attribute.</para>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>
          <legacyBold>ODBC 3.5 (or later) ANSI Driver</legacyBold> A 32-bit driver that: </para>
        <list class="bullet">
          <listItem>
            <para>Exports only functions that are in ODBC 3.5 minus deprecated functions.</para>
          </listItem>
          <listItem>
            <para>Is capable of exhibiting ODBC 2.<legacyItalic>x </legacyItalic>behavior or ODBC 3.0 behavior, or ODBC 3.5 behavior with respect to behavioral changes, based on the SQL_ATTR_APP_ODBC_VERSION environment attribute.</para>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>
          <legacyBold>ODBC 3.5 (or later) Unicode Driver</legacyBold> A 32-bit driver that: </para>
        <list class="bullet">
          <listItem>
            <para>Supports all the features of an ODBC 3.5 ANSI driver.</para>
          </listItem>
          <listItem>
            <para>Exports Unicode versions of all ODBC string APIs.</para>
          </listItem>
          <listItem>
            <para>Can store and process Unicode data on the data source.</para>
          </listItem>
        </list>
      </listItem>
    </list>
    <alert class="note">
      <para>16-bit ODBC drivers will not work directly with the ODBC 3.<legacyItalic>x</legacyItalic> Driver Manager. However, it is possible for 16-bit drivers to work with the 2.0 ODBC Driver Manager, which subsequently thunks up to the 3.<legacyItalic>x </legacyItalic>Driver Manager.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>