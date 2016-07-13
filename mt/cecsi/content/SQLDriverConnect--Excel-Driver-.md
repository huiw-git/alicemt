---
title: SQLDriverConnect (Excel Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 285cb1ea-f461-4596-97f2-fc57af05dede
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLDriverConnect (Excel Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic provides Excel Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>
      <legacyBold>SQLDriverConnect</legacyBold> enables you to connect to a driver without creating a data source (DSN).</para>
    <para>The following keywords are supported in the connection string for all drivers: <legacyBold>DSN</legacyBold>, <legacyBold>DBQ</legacyBold>, and <legacyBold>FIL</legacyBold>. </para>
    <para>The following table shows the minimum keywords required to connect to each driver, and provides an example of keyword/value pairs used with <legacyBold>SQLDriverConnect</legacyBold>. For a full list of DRIVERID values, see <legacyLink xlink:href="885b3bea-f4b6-4902-b994-f78a912b612f">SQLConfigDataSource</legacyLink>.</para>
    <alert class="note">
      <para>If DBQ or DefaultDir is not specified for the Microsoft Excel 3.0 or 4.0 driver, the driver will connect to the current directory.</para>
    </alert>
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
            <para>Microsoft Excel 3.0 or 4.0</para>
          </TD>
          <TD>
            <para>Driver, DriverID</para>
          </TD>
          <TD>
            <para>Driver={Microsoft Excel Driver (*.xls)}; DBQ=c:\temp; DriverID=278</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Microsoft Excel 5.0/7.0</para>
          </TD>
          <TD>
            <para>Driver, DriverID,  DBQ</para>
          </TD>
          <TD>
            <para>Driver={Microsoft Excel Driver (*.xls)}; DBQ=c:\temp\sample.xls; DriverID=22</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Microsoft Excel 97 and later</para>
          </TD>
          <TD>
            <para>Driver, DriverID,  DBQ</para>
          </TD>
          <TD>
            <para>Driver={Microsoft Excel Driver (*.xls)}; DBQ=c:\temp\sample.xls; DriverID=790</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>