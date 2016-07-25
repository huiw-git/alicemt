---
title: "RDS Methods"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c2c6af1a-3c44-4c9d-ad33-b381552c71af
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
# RDS Methods
<?xml version="1.0" encoding="utf-8"?>
<developerOrientationDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <tbody>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="560b5b3d-fba9-4275-8920-9c3e186134f7">Cancel (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Cancels execution of a pending, asynchronous method call.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="76d8a6e9-bc6c-4ea0-8e7a-2bae5ed06650">CancelUpdate (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Cancels any changes made to the current or new row of a <legacyBold>Recordset</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="b3f36bc8-6f69-49b0-83cd-2ccd3afebfbe">ConvertToString (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Converts a <legacyBold>Recordset</legacyBold> to a MIME string that represents the recordset data.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="dec96be6-0b31-4953-9c9a-e962b5afcd18">CreateObject (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Creates the proxy for the target business object and returns a pointer to it.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="6840b1e5-c04d-4d3e-9dcc-42128c83492f">CreateRecordset (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Creates an empty, disconnected <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="2d9c30e9-ab5b-4920-91b8-48454c2fb5d8">Execute Method (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Execute the request and create an advanced data rowset (for use with ADO 2.5 and later).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="9f131c8d-1497-416d-8209-abb481c38f7b">Execute21 Method (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Execute the request and create an advanced data rowset (for use with ADO 2.1).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <link xlink:href="ad45c676-ec7e-4a3a-9a6b-a54f75eb3012">InvokeService</link>
            </para>
          </TD>
          <TD>
            <para>Returns a pointer to the requested interface on a more capable version of the object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="45c80bb5-136f-4204-9df2-78740fa55574">MoveFirst, MoveLast, MoveNext, MovePrevious (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Moves to the first, last, next, or previous record in a specified <legacyBold>Recordset</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="20f2480f-3758-405d-a379-05a0dce74796">Query (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Uses a valid SQL query string to return a <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="c90a8050-0ff4-4c83-9925-261f2f2ccfe9">Refresh (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Requeries the data source specified in the <legacyBold>Connect</legacyBold> property and updates the query results.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="3957197a-f543-4d6b-9e11-67a77c2063b7">Reset (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Executes the sort or filter on a client-side <legacyBold>Recordset</legacyBold>, based on the specified sort and filter properties.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="250062a4-13c4-4bed-807d-8b9ad81536d4">SubmitChanges (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Submits pending changes of the locally cached and updatable <legacyBold>Recordset</legacyBold> to the data source specified in the <legacyBold>Connect</legacyBold> property.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="7af42866-7db2-4174-8251-388a2cf741f2">Synchronize Method (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Synchronize the given recordset with the database specified by the connection string (for use with ADO 2.5 and later).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="6b35f136-9d9a-4bdd-8144-67decfd3c4e9">Synchronize21 Method (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Synchronize the given recordset with the database specified by the connection string (for use with ADO 2.1).</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerOrientationDocument>