---
title: "Desktop Database Drivers Architecture"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8b4d13f7-ab37-40b4-a9c6-145e7385352f
caps.latest.revision: 6
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Desktop Database Drivers Architecture
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>These drivers are designed for use on Microsoft Windows 95 or later, or Windows NT 4.0 and Windows 2000. Only 32-bit applications are supported on Windows 95 or later; 16-bit and 32-bit applications are supported on Windows NT 4.0 and Windows 2000. </para>
  </introduction>
  <section>
    <content>
      <alert class="note">
        <para>   For information about the version of ODBC to be used with these drivers, refer to the <legacyItalic>ODBC Programmer's Reference</legacyItalic>, and past and current release notes. Except for noted areas, these drivers conform to the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
      </alert>
      <para>The ODBC Desktop Database Drivers include 32-bit drivers for Microsoft Access, dBASE, Microsoft Excel, Paradox, and Text. No 16-bit drivers are included. (A driver for Microsoft FoxPro is available separately.)</para>
      <para>The application/driver architecture on Windows 95 or later is:</para>
      <mediaLink>
        <image xlink:href="f65408a7-47e8-4251-ac78-9a07b506f03e" />
      </mediaLink>
      <para>The use of these drivers by 16-bit applications on Windows 95 is not supported.</para>
      <para>The application/driver architecture on Windows NT 4.0 and Windows 2000 is:</para>
      <mediaLink>
        <image xlink:href="7e650492-f804-4d09-8491-8ad1426c6a59" />
      </mediaLink>
      <para>The Desktop Database Drivers are two-tier drivers. In a two-tier configuration, the driver does not perform the process of parsing, validating, optimizing, and executing the query. Instead, Microsoft Jet performs these tasks. It processes ODBC API calls and acts as an SQL engine. Microsoft Jet has become an integral, inseparable part of the drivers: It is shipped with the drivers and resides with the drivers, even if no other application on the computer uses it.</para>
      <para>The Desktop Database Drivers consist of six different drivers — or, more precisely, one driver file (Odbcjt32.dll) that the ODBC <legacyLink xlink:href="559e4de1-16c9-4998-94f5-6431122040cd">Driver Manager</legacyLink> uses in six different ways. The DRIVERID flag in the registry entry for a data source determines which driver in Odbcjt32.dll the Driver Manager uses. An application passes this flag in the connection string included in a call to <legacyBold>SQLDriverConnect</legacyBold>. By default, the flag is the ID of the Microsoft Access driver.</para>
      <para>The driver setup file changes the DRIVERID flag at setup time. All drivers except the Microsoft Access driver have an associated setup DLL. When you click <legacyBold>Setup</legacyBold> in the <legacyLink xlink:href="a2f66b4c-a4ac-401b-8e95-d8f96332e0b5">Microsoft ODBC Data Source Administrator</legacyLink> for a data source, the ODBC installer DLL (Odbcinst.dll) loads the setup DLL. The setup DLL exports the ODBC installer function <legacyBold>SQLConfigDataSource</legacyBold>. If a window handle is passed to <legacyBold>SQLConfigDataSource</legacyBold>, this function displays a setup window and changes the DRIVERID flag according to the driver selected from the user interface.</para>
      <para>When a file is created programmatically, a NULL window handle is passed to <legacyBold>SQLConfigDataSource</legacyBold>, and the function creates a data source dynamically, changing the DRIVERID flag according to the <legacyItalic>lpszDriver</legacyItalic> argument in the function call. </para>
      <para>Odbcjt32.dll implements ODBC functions on top of the Microsoft Jet API. There is no direct mapping between ODBC and Microsoft Jet functions, however. Many factors, such as the cursor models and SQL mapping, prevent a direct correlation of the functions.</para>
      <para>The ODBC driver resides between the Microsoft Jet engine and the ODBC Driver Manager. Some ODBC functions called by an application are handled by the Driver Manager and not passed to the driver. For these functions, Microsoft Jet never sees the function call because it does not have a direct connection to the Driver Manager.</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>