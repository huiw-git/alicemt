---
title: "DataFactory Object (RDSServer) Properties, Methods, and Events"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 36a1f49b-91f4-44f4-b6e2-52fc7ed06d7e
caps.latest.revision: 13
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
# DataFactory Object (RDSServer) Properties, Methods, and Events
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <section>
    <title>Properties</title>
    <content>
      <para>None.</para>
    </content>
  </section>
  <section>
    <title>Methods</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="b3f36bc8-6f69-49b0-83cd-2ccd3afebfbe">ConvertToString Method (RDS)</link>
              </para>
            </TD>
            <TD>
              <para>Converts a recordset into a MIME64 string.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="6840b1e5-c04d-4d3e-9dcc-42128c83492f">CreateRecordset Method (RDS)</link>
              </para>
            </TD>
            <TD>
              <para>Creates and returns an empty recordset.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="2d9c30e9-ab5b-4920-91b8-48454c2fb5d8">Execute Method (RDS)</link>
              </para>
            </TD>
            <TD>
              <para>Execute the request and create an advanced data rowset (for use with ADO 2.5 or later).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="9f131c8d-1497-416d-8209-abb481c38f7b">Execute21 Method (RDS)</link>
              </para>
            </TD>
            <TD>
              <para>Execute the request and create an advanced data rowset (for use with ADO 2.1).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="20f2480f-3758-405d-a379-05a0dce74796">Query Method (RDS)</link>
              </para>
            </TD>
            <TD>
              <para>Execute the request and create an advanced data rowset.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="250062a4-13c4-4bed-807d-8b9ad81536d4">SubmitChanges Method (RDS)</link>
              </para>
            </TD>
            <TD>
              <para>Given a recordset with pending changes, this method submits them to the database identified in the connection string.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="7af42866-7db2-4174-8251-388a2cf741f2">Synchronize Method (RDS)</link>
              </para>
            </TD>
            <TD>
              <para>Synchronize the given recordset with the database specified by the connection string (for use with ADO 2.5 or later).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="6b35f136-9d9a-4bdd-8144-67decfd3c4e9">Synchronize21 Method (RDS)</link>
              </para>
            </TD>
            <TD>
              <para>Synchronize the given recordset with the database specified by the connection string (for use with ADO 2.1).</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Events</title>
    <content>
      <para>None.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">DataFactory Object (RDSServer)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>