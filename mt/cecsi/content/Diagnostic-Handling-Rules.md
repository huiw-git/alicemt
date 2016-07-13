---
title: Diagnostic Handling Rules
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 74387c3a-d6b3-4c35-b209-b9612602b20a
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Diagnostic Handling Rules
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following rules govern diagnostic handling in <legacyBold>SQLGetDiagRec</legacyBold> and <legacyBold>SQLGetDiagField</legacyBold>.</para>
    <para>For all ODBC components:  </para>
    <list class="bullet">
      <listItem>
        <para>Must not replace, alter, or mask errors or warnings received from another ODBC component.</para>
      </listItem>
      <listItem>
        <para>May add an additional status record when they receive a diagnostic message from another ODBC component. The added record must add real information value to the original message.</para>
      </listItem>
    </list>
    <para>For the ODBC component that directly interfaces a data source:  </para>
    <list class="bullet">
      <listItem>
        <para>Must prefix its vendor identifier, its component identifier, and the data source's identifier to the diagnostic message it receives from the data source.</para>
      </listItem>
      <listItem>
        <para>Must preserve the data source's native error code.</para>
      </listItem>
      <listItem>
        <para>Must preserve the data source's diagnostic message.</para>
      </listItem>
    </list>
    <para>For any ODBC component that generates an error or warning independent of the data source:  </para>
    <list class="bullet">
      <listItem>
        <para>Must supply the correct SQLSTATE for the error or warning.</para>
      </listItem>
      <listItem>
        <para>Must generate the text of the diagnostic message.</para>
      </listItem>
      <listItem>
        <para>Must prefix its vendor identifier and its component identifier to the diagnostic message.</para>
      </listItem>
      <listItem>
        <para>Must return a native error code, if one is available and meaningful.</para>
      </listItem>
    </list>
    <para>For the ODBC component that interfaces with the Driver Manager:  </para>
    <list class="bullet">
      <listItem>
        <para>Must initialize the output arguments of <legacyBold>SQLGetDiagRec</legacyBold> and <legacyBold>SQLGetDiagField</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>Must format and return the diagnostic information as output arguments of <legacyBold>SQLGetDiagRec</legacyBold> and <legacyBold>SQLGetDiagField</legacyBold> when that function is called.</para>
      </listItem>
    </list>
    <para>For one ODBC component other than the Driver Manager:  </para>
    <list class="bullet">
      <listItem>
        <para>Must set the SQLSTATE based on the native error. For file-based drivers and DBMS-based drivers that do not use a gateway, the driver must set the SQLSTATE. For DBMS-based drivers that use a gateway, either the driver or a gateway that supports ODBC may set the SQLSTATE.</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>