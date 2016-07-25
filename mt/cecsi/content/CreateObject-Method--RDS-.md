---
title: "CreateObject Method (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: dec96be6-0b31-4953-9c9a-e962b5afcd18
caps.latest.revision: 14
manager: sonalm
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# CreateObject Method (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Creates the proxy for the target business object and returns a pointer to it. The proxy packages and marshals data to the server-side stub for communications with the business object to send requests and data over the Internet. For in-process component objects, no proxies are used, just a pointer to the object is provided.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <section>
    <title>Syntax</title>
    <content>
      <para>Remote Data Service supports the following protocols: HTTP, HTTPS (HTTP over Secure Socket Layer), DCOM, and in-process.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Protocol</para>
            </TD>
            <TD>
              <para>Syntax</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>HTTP</para>
            </TD>
            <TD>
              <para>Set object = DataSpace.CreateObject("ProgId", "http://awebsrvr")</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HTTPS</para>
            </TD>
            <TD>
              <para>Set object = DataSpace.CreateObject("ProgId", "https://awebsrvr")</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DCOM</para>
            </TD>
            <TD>
              <para>Set object = DataSpace.CreateObject("ProgId", "computername")</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>In-process</para>
            </TD>
            <TD>
              <para>Set object = DataSpace.CreateObject("ProgId", "")</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Parameters</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>Object</legacyItalic>
        </definedTerm>
        <definition>
          <para>An object variable that evaluates to an object that is the type specified in <legacyItalic>ProgID</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>DataSpace</legacyItalic>
        </definedTerm>
        <definition>
          <para>An object variable that represents an <legacyLink xlink:href="9194bffa-5bdf-4dff-af86-f7158c23bfa7">RDS.DataSpace</legacyLink> object used to create an instance of the new object.</para>
        </definition>
        <definedTerm>
          <legacyItalic>ProgID</legacyItalic>
        </definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> value that contains the programmatic identifier specifying a server-side business object that implements your application's business rules.</para>
        </definition>
        <definedTerm>
          <legacyItalic>awebsrvr </legacyItalic>or <legacyItalic>computername</legacyItalic></definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> value that represents a URL identifying the Internet Information Services (IIS) Web server where an instance of the server business object is created.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyItalic>HTTP protocol</legacyItalic> is the standard Web protocol; <legacyItalic>HTTPS</legacyItalic> is a secure Web protocol. Use the <legacyItalic>DCOM protocol</legacyItalic> when running a local-area network without HTTP. The <legacyItalic>in-process</legacyItalic> protocol is a local dynamic-link library (DLL); it does not use a network.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="9194bffa-5bdf-4dff-af86-f7158c23bfa7">DataSpace Object (RDS)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b4e2844a-120a-4513-860b-f1b6e4b5dda4">DataFactory Object, Query Method, and CreateObject Method Example (VBScript)</link>
<link xlink:href="12b0e160-5e5c-441f-bed7-ac0bd061e003">DataSpace Object and CreateObject Method Example (VBScript)</link>
<link xlink:href="6840b1e5-c04d-4d3e-9dcc-42128c83492f">CreateRecordset Method (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>