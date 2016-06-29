---
title: SQLDriverConnect (dBASE Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c837aa31-068e-4fa3-bc00-aae09bec21de
translation.priority.ht: 
  - en-gb
---
# SQLDriverConnect (dBASE Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic provides dBASE Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>         <legacyBold>SQLDriverConnect</legacyBold> enables you to connect to a driver without creating a data source (DSN).</para>
    <para>The following keywords are supported in the connection string for all drivers: <legacyBold>DSN</legacyBold>, <legacyBold>DBQ</legacyBold>, and <legacyBold>FIL</legacyBold>. </para>
    <para>When the Paradox driver is used, after a password-protected file has been opened by a user, other users are not allowed to open the same file.</para>
    <para>The following table shows the minimum keywords required to connect to each driver, and provides an example of keyword/value pairs used with <legacyBold>SQLDriverConnect</legacyBold>. For a full list of DRIVERID values, see <legacyLink xlink:href="19909902-054c-4e19-9c06-a212aace13fe">SQLConfigDataSource</legacyLink>.</para>
    <alert class="note">
      <para>If DBQ or DefaultDir is not specified for the dBASEdriver, the driver will connect to the current directory.</para>
    </alert>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Driver</para>
          </TD>
          <TD>
            <para>Keywords required</para>
          </TD>
          <TD>
            <para>Examples</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>dBASE</para>
          </TD>
          <TD>
            <para>Driver, DriverID</para>
          </TD>
          <TD>
            <para>Driver={Microsoft dBASE Driver (*.dbf)}; DBQ=c:\temp; DriverID=277</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>