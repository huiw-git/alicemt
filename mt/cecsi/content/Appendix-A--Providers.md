---
title: "Appendix A: Providers"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2581b47-b11e-4e1e-b96c-d39c77c5b48a
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
# Appendix A: Providers
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This section addresses three kinds of providers: data providers, service providers, and service components. Providers fall into two categories: those providing data and those providing services. A <legacyItalic>data provider</legacyItalic> owns its own data and exposes it in tabular form to your application. A <legacyItalic>service provider</legacyItalic> encapsulates a service by producing and consuming data, augmenting features in your ADO applications. A service provider may also be further defined as a <legacyItalic>service component</legacyItalic>, which must work together with other service providers or components.</para>
  </introduction>
  <section>
    <title>Data Providers</title>
    <content>
      <para>ADO is powerful and flexible because it can connect to any of several different data providers and still expose the same programming model, regardless of the specific features of any given provider.</para>
      <para>However, because each data provider is unique, how your application interacts with ADO will vary slightly by data provider. The differences usually fall into one of three categories:  </para>
      <list class="bullet">
        <listItem>
          <para>Connection parameters in the <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object usage.</para>
        </listItem>
        <listItem>
          <para>Provider-specific <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> behavior.</para>
        </listItem>
      </list>
      <para>Details for each of the data providers currently available from Microsoft are listed as follows.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Area</para>
            </TD>
            <TD>
              <para>Topic</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>ODBC databases</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="2dc0372d-e74d-4d0f-9c8c-04e5a168c148">Microsoft OLE DB Provider for ODBC</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Microsoft Indexing Service</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="f86a0598-5097-471b-8318-d2c859d085f2">Microsoft OLE DB Provider for Microsoft Indexing Service</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Active Directory Service</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="f9e81452-5675-4cfc-9949-cfbd2fe57534">Microsoft OLE DB Provider for Microsoft Active Directory Service</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Microsoft Jet databases</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="fd956da1-5203-40af-aa7e-fc13a6c6581f">OLE DB Provider for Microsoft Jet</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Microsoft SQL Server</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="99bc40c4-9181-4ca1-a06f-9a1a914a0b7b">Microsoft OLE DB Provider for SQL Server</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Oracle databases</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="44fae9dd-5585-4cd6-8bbd-3248a78931b4">Microsoft OLE DB Provider for Oracle</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Internet Publishing</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Microsoft OLE DB Provider for Internet Publishing</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Simple data sources</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="1e7dc6f0-482c-4103-8187-f890865e40fc">Microsoft OLE DB Simple Provider</legacyLink>             </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Provider-Specific Dynamic Properties</title>
    <content>
      <para>The <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collections of the <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink>, <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink>, and <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> objects include dynamic properties specific to the provider. These properties provide information about functionality specific to the provider beyond the built-in properties that ADO supports.</para>
      <para>After establishing the connection and creating these objects, use the <legacyLink xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh</legacyLink> method on the <legacyBold>Properties</legacyBold> collection of the object to obtain the provider-specific properties. Refer to the provider documentation and the <legacyLink xlink:href="3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8">OLE DB Programmer's Guide</legacyLink> for detailed information about these dynamic properties.</para>
    </content>
  </section>
  <section>
    <title>Service Providers</title>
    <content>
      <para>To use a service provider, you must supply a keyword. You should also be aware of the provider-specific dynamic properties associated with each service provider. Provider-specific details are listed for each service provider that is currently available from Microsoft:  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="523009ce-e01b-4e2d-a7df-816d7688aff0">Microsoft Data Shaping Service for OLE DB</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="e75ef0dc-2016-4fcc-8918-23311c0d4e02">Microsoft OLE DB Persistence Provider</legacyLink>   </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="a4360ed4-b70f-4734-9041-4025d033346b">Microsoft OLE DB Remoting Provider</legacyLink> </para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Service Components</title>
    <content>
      <para>The <legacyLink xlink:href="420d0989-7cfb-4c66-a7b5-f4199d13165d">Cursor Service for OLE DB</legacyLink> service component supplements the cursor support functions of data providers. It also requires a keyword and has dynamic properties.</para>
      <para>For more information about OLE DB Providers, see <externalLink><linkText>Microsoft OLE DB</linkText><linkUri>https://msdn.microsoft.com/library/windows/desktop/ms722784.aspx</linkUri></externalLink>.</para>
    </content>
  </section>
  <section>
    <title>Provider Commands</title>
    <content>
      <para>For each provider listed here, if your applications allow users to enter SQL statements as the provider commands, you must always validate the user input and be vigilant of possible hacker attacks using potentially dangerous SQL statements, such as <codeInline>DROP TABLE t1</codeInline>, as part of the user input.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Microsoft OLE DB Provider for Internet Publishing</link>
<link xlink:href="f9e81452-5675-4cfc-9949-cfbd2fe57534">Microsoft OLE DB Provider for Microsoft Active Directory Service</link>
<link xlink:href="f86a0598-5097-471b-8318-d2c859d085f2">Microsoft OLE DB Provider for Microsoft Indexing Service</link>
<link xlink:href="2dc0372d-e74d-4d0f-9c8c-04e5a168c148">Microsoft OLE DB Provider for ODBC</link>
<link xlink:href="44fae9dd-5585-4cd6-8bbd-3248a78931b4">Microsoft OLE DB Provider for Oracle</link>
<link xlink:href="99bc40c4-9181-4ca1-a06f-9a1a914a0b7b">Microsoft OLE DB Provider for SQL Server</link>
<link xlink:href="fd956da1-5203-40af-aa7e-fc13a6c6581f">OLE DB Provider for Microsoft Jet</link>
<link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="c90a8050-0ff4-4c83-9925-261f2f2ccfe9">Refresh Method (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>