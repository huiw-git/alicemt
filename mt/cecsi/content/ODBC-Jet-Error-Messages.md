---
title: ODBC Jet Error Messages
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f8d2a8f2-0316-42c4-bc34-5367661634ae
translation.priority.ht: 
  - en-gb
---
# ODBC Jet Error Messages
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>For errors that occur in the data source, the ODBC driver returns an error message returned to it by the ODBC File Library. For errors that occur in the ODBC driver or the Driver Manager, the driver returns an error message based on the text associated with the SQLSTATE.</para>
    <para>Error messages have the following format:</para>
    <code>[vendor][ODBC-component][data-source]message-text</code>
    <para>The prefixes in brackets ([ ]) identify the location of the error. When the error occurs in the Driver Manager, <legacyItalic>data-source</legacyItalic> is not given. When the error occurs in the data source, the [<legacyItalic>vendor</legacyItalic>] and [<legacyItalic>ODBC-component</legacyItalic>] prefixes identify the vendor and name of the ODBC component that received the error from the data source. </para>
    <para>The following table shows the error messages returned by the Driver Manager and driver ISAM: </para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Error message</para>
          </TD>
          <TD>
            <para>Error location</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>[Microsoft][ODBC Driver Manager] <legacyItalic>message-text</legacyItalic></para>
          </TD>
          <TD>
            <para>Driver Manager (Odbc32.dll)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>[Microsoft][ODBC <legacyItalic>driver-name</legacyItalic>]<legacyItalic>message-text</legacyItalic></para>
          </TD>
          <TD>
            <para>Driver ISAM (see Driver ISAMs)</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>