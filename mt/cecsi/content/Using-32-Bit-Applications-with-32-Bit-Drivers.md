---
title: "Using 32-Bit Applications with 32-Bit Drivers"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0cdd5788-5642-4280-8d53-b4ec461aafa1
caps.latest.revision: 12
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Using 32-Bit Applications with 32-Bit Drivers
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>You can run 32-bit applications with 32-bit drivers. The 32-bit applications and the 32-bit drivers use the Win32® API.</para>
  </introduction>
  <section>
    <title>Architecture</title>
    <content>
      <para>The following illustration shows how 32-bit applications communicate with 32-bit drivers. The application calls the 32-bit Driver Manager, which in turn calls 32-bit drivers.</para>
      <mediaLink>
        <image xlink:href="140e158f-1e2f-478c-a972-afb6bcad57f5" />
      </mediaLink>
      <alert class="important">
        <para>Do not use the 32-bit thunking installer DLL on WindowsNT/Windows2000. Although it has the same file name as the 32-bit installer DLL, it is a different DLL.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>Administration</title>
    <content>
      <para>You can manage data sources for 32-bit drivers by using the ODBC Data Source Administrator. To open the ODBC Administrator on computers running Windows 2000, open the Windows Control Panel, double-click <legacyBold>Administrative Tools</legacyBold>, and then double-click <legacyBold>Data Sources (ODBC)</legacyBold>. On computers running previous versions of Microsoft Windows, the icon is named <legacyBold>32-bit ODBC</legacyBold> or simply <legacyBold>ODBC</legacyBold>.</para>
    </content>
  </section>
  <section>
    <title>Components</title>
    <content>
      <para>The ODBC component includes the following files for running 32-bit applications with 32-bit drivers. These components are in the \Redist directory.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>File name</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Odbc32.dll</para>
            </TD>
            <TD>
              <para>32-bit Driver Manager</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Odbccp32.dll</para>
            </TD>
            <TD>
              <para>32-bit Installer DLL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Odbcad32.exe</para>
            </TD>
            <TD>
              <para>32-bit ODBC Administrator program</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Odbcinst.hlp</para>
            </TD>
            <TD>
              <para>Installer Help file</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Msvcrt40.dll</para>
            </TD>
            <TD>
              <para>C run-time library</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>