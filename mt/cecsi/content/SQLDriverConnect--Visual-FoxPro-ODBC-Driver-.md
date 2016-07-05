---
title: SQLDriverConnect (Visual FoxPro ODBC Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 10492c8f-3a18-4971-9db8-879e878083b9
translation.priority.ht: 
  - en-gb
---
# SQLDriverConnect (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic contains Visual FoxPro ODBC Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>Support: Full </para>
    <para>ODBC API Conformance: Level 1</para>
    <para>Connects to an existing data source, which can be either a <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">database</legacyLink> or a directory of <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">free tables</legacyLink>. The ODBC attribute keywords UID and PWD are ignored. The following table lists the additional supported attribute keywords.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>ODBC attribute keyword</para>
          </TD>
          <TD>
            <para>Attribute value</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>DSN</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>UID</para>
          </TD>
          <TD>
            <para>Ignored by the Visual FoxPro ODBC Driver but does not generate an error.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>PWD</para>
          </TD>
          <TD>
            <para>Ignored by the Visual FoxPro ODBC Driver but does not generate an error.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Driver</para>
          </TD>
          <TD>
            <para>The name and location of the Visual FoxPro ODBC Driver; implemented by the Driver Manager. </para>
          </TD>
        </tr>
      </tbody>
    </table>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Visual FoxPro ODBC Driver attribute keyword</para>
          </TD>
          <TD>
            <para>Attribute value</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>BackgroundFetch</para>
          </TD>
          <TD>
            <para>"Yes" or "No"</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Collate</para>
          </TD>
          <TD>
            <para>"Machine" or other collating sequence. For a list of supported collating sequences, see <legacyLink xlink:href="00efbcd4-fea8-4061-86a5-82de413cb753">SET COLLATE</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Description</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Exclusive</para>
          </TD>
          <TD>
            <para>"Yes" or "No"</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SourceDB</para>
          </TD>
          <TD>
            <para>A fully qualified path to a directory containing zero or more <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">free tables</legacyLink>, or the absolute path and file name for a <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">database</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SourceType</para>
          </TD>
          <TD>
            <para>"DBC" or "DBF"</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Version</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>If the data source name is not specified, the Driver Manager prompts the user for the information (depending on the setting of the <legacyItalic>fDriverCompletion</legacyItalic> argument) and then continues. If more information is required, the Visual FoxPro ODBC Driver displays the prompt dialog.</para>
    <para>For more information, see <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink> in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>