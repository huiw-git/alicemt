---
title: Using 16-Bit Applications with 32-Bit Drivers
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68feb3b7-c01a-4f42-8df9-f9c182d89325
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Using 16-Bit Applications with 32-Bit Drivers
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Use 32-bit or 64-bit driver manager instead.</para>
    </alert>
    <para>You can run 16-bit applications with 32-bit drivers on your Windows-based system as long as the 32-bit driver does not explicitly call Win32 API functions that create threads. The Windows on Windows (WOW) subsystem runs the applications in 16-bit mode and resolves 16-bit calls to the operating system. ODBC thunking DLLs resolve 16-bit calls from the application to 32-bit drivers. The 16-bit applications use the Windows API, and 32-bit drivers use the Win32 API.</para>
  </introduction>
  <section>
    <title>Architecture</title>
    <content>
      <para>The following illustration shows how 16-bit applications communicate with 32-bit drivers. Between the 16-bit Driver Manager and the 32-bit drivers are generic thunking DLLs that convert 16-bit ODBC calls to 32-bit ODBC calls.</para>
      <mediaLink>
        <image xlink:href="e00def60-5da2-427e-b623-c5379cc7b743" />
      </mediaLink>
      <alert class="note">
        <para>Anytime a 16-bit application interacts with a 32-bit driver, the 32-bit Driver Manager always returns "2.0" as the version of ODBC supported by the driver.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>Administration</title>
    <content>
      <para>You can manage data sources for 32-bit drivers by using the ODBC Data Source Administrator. To open the ODBC Administrator on computers running Microsoft® Windows® 2000, open the Windows Control Panel, double-click <legacyBold>Administrative Tools</legacyBold>, and then double-click <legacyBold>Data Sources (ODBC)</legacyBold>. On computers running previous versions of Microsoft Windows, the icon is named <legacyBold>32-bit ODBC</legacyBold> or simply <legacyBold>ODBC</legacyBold>.</para>
      <para>The following illustration shows how a 16-bit application calls a 32-bit driver setup DLL. Between the 16-bit installer DLL and the 32-bit driver setup DLL is a generic thunking DLL that converts 16-bit installer DLL calls to 32-bit installer DLL calls.</para>
      <mediaLink>
        <image xlink:href="e0856fbc-525d-4be6-9668-d4c6f6cf1a46" />
      </mediaLink>
      <para>In Windows on Windows (16-bit to 32-bit thunking), an additional thunking DLL named Ds32gt.dll converts 16-bit argument values passed through a 32-bit setup DLL back to 16-bit.</para>
    </content>
  </section>
  <section>
    <title>Components</title>
    <content>
      <para>The ODBC component of the MDAC 2.8 SP1 SDK includes the following files for running 16-bit applications with 32-bit drivers. These components are in the \Redist directory.</para>
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
              <para>Odbc16gt.dll</para>
            </TD>
            <TD>
              <para>16-bit ODBC generic thunking DLL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Odbc32gt.dll</para>
            </TD>
            <TD>
              <para>32-bit ODBC generic thunking DLL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Odbccp32.dll</para>
            </TD>
            <TD>
              <para>32-bit installer DLL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Odbcad32.exe</para>
            </TD>
            <TD>
              <para>32-bit Administrator program</para>
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
              <para>Ds16gt.dll</para>
            </TD>
            <TD>
              <para>16-bit driver setup generic thunking DLL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Ctl3d32.dll</para>
            </TD>
            <TD>
              <para>32-bit three-dimensional window style library</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>In addition, the following files along with the 16-bit ODBC 2.10 Driver Manager, which are not part of ODBC 3.51, are required by and should be installed with the 16-bit application. </para>
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
              <para>Odbc.dll</para>
            </TD>
            <TD>
              <para>16-bit Driver Manager</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Odbcinst.dll</para>
            </TD>
            <TD>
              <para>16-bit Installer DLL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Odbcadm.exe</para>
            </TD>
            <TD>
              <para>16-bit ODBC Administrator program</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>