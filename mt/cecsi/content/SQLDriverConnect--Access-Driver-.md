---
title: SQLDriverConnect (Access Driver)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9d133e9b-7545-464d-aa3c-677fa7e2a41d
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLDriverConnect (Access Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic provides Access Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>         <legacyBold>SQLDriverConnect</legacyBold> enables you to connect to a driver without creating a data source (DSN).</para>
    <para>The following keywords are supported in the connection string for all drivers: <legacyBold>DSN</legacyBold>, <legacyBold>DBQ</legacyBold>, and <legacyBold>FIL</legacyBold>. </para>
    <para>The <legacyBold>UID</legacyBold> and <legacyBold>PWD</legacyBold> keywords are also supported. </para>
    <para>The PWD keyword should not include any of the special characters (see SQL_SPECIAL_CHARACTERS in <legacyBold>SQLGetInfo</legacyBold> Returned Values).</para>
    <para>The following table shows the minimum keywords required to connect to each driver, and provides an example of keyword/value pairs used with <legacyBold>SQLDriverConnect</legacyBold>. For a full list of DRIVERID values, see <legacyLink xlink:href="1b152fb7-fa12-46b9-b168-006bb1355e77">SQLConfigDataSource</legacyLink>.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Driver</para>
          </TD>
          <TD>
            <para>Keywords Required</para>
          </TD>
          <TD>
            <para>Examples</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Microsoft Access</para>
          </TD>
          <TD>
            <para>Driver, DBQ</para>
          </TD>
          <TD>
            <para>Driver={Microsoft Access Driver (*.mdb)}; DBQ=c:\\temp\\sample.mdb</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>