---
title: "Address Book Data-Binding Object"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 080c1925-d453-4b89-92ac-c93591490518
caps.latest.revision: 12
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
# Address Book Data-Binding Object
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Address Book application uses the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object to bind data from the SQL Server database to a visual object (in this case, a DHTML table) in the application's client HTML page. The event-driven VBScript program logic uses the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> to:  </para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <list class="bullet">
      <listItem>
        <para>Query the database, send updates to the database, and refresh the data grid.</para>
      </listItem>
      <listItem>
        <para>Allow users to move to the first, next, previous, or last record in the data grid.</para>
      </listItem>
    </list>
    <para>The following code defines the <legacyBold>RDS.DataControl</legacyBold> component:</para>
    <code>&lt;OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"
   ID=DC1 Width=1 Height=1&gt;
   &lt;PARAM NAME="SERVER" VALUE="http://&lt;%=Request.ServerVariables("SERVER_NAME")%&gt;"&gt;
   &lt;PARAM NAME="CONNECT" VALUE="Provider=sqloledb;
Initial Catalog=AddrBookDb;Integrated Security=SSPI;"&gt;
&lt;/OBJECT&gt;</code>
    <para>The OBJECT tag defines the <legacyBold>RDS.DataControl</legacyBold> component in the program. The tag includes two types of parameters:  </para>
    <list class="bullet">
      <listItem>
        <para>Those associated with the generic OBJECT tag.</para>
      </listItem>
      <listItem>
        <para>Those specific to the <legacyBold>RDS.DataControl</legacyBold> object.</para>
      </listItem>
    </list>
  </introduction>
  <section>
    <title>Generic OBJECT Tag Parameters</title>
    <content>
      <para>The following table describes the parameters associated with the OBJECT tag.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Parameter</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>               <legacyBold>                 </legacyBold><legacyBold><legacyItalic>CLASSID</legacyItalic></legacyBold><legacyBold>               </legacyBold>             </para>
            </TD>
            <TD>
              <para>A unique, 128-bit number that identifies the type of embedded object to the system. This identifier is maintained in the local computer's system registry. (For the class IDs of the <legacyBold>RDS.DataControl</legacyBold> object, see <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl Object</legacyLink>.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>                 </legacyBold><legacyBold><legacyItalic>ID</legacyItalic></legacyBold><legacyBold>               </legacyBold>             </para>
            </TD>
            <TD>
              <para>Defines a document-wide identifier for the embedded object that is used to identify it in code.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>RDS.DataControl Tag Parameters</title>
    <content>
      <para>The following table describes the parameters specific to the <legacyBold>RDS.DataControl</legacyBold> object. (For a complete list of the <legacyBold>RDS.DataControl</legacyBold> object parameters, and when to implement them, see <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl object</legacyLink>.)</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Parameter</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="d2727ce7-da9f-4271-ae3c-9334ef477c14">SERVER</legacyLink>             </para>
            </TD>
            <TD>
              <para>If you are using HTTP, the value is the name of the server computer preceded by <codeInline>http://</codeInline>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="dbad5e77-b213-4eb8-aecf-d60f203fdb59">CONNECT</legacyLink>             </para>
            </TD>
            <TD>
              <para>Provides the necessary connection information for the <legacyBold>RDS.DataControl</legacyBold> to connect to SQL Server.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="e0dabf23-a159-4fe5-a962-3df544a21f5c">SQL</legacyLink>             </para>
            </TD>
            <TD>
              <para>Sets or returns the query string used to retrieve the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="80676831-6488-4dad-a558-c47c52256a22">Address Book Command Buttons</link>
</relatedTopics>
</developerConceptualDocument>