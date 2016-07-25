---
title: "Microsoft OLE DB Remoting Provider (ADO Service Provider)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a4360ed4-b70f-4734-9041-4025d033346b
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
# Microsoft OLE DB Remoting Provider (ADO Service Provider)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Microsoft OLE DB Remoting Provider enables a local user on a client machine to invoke data providers on a remote machine. Specify the data provider parameters for the remote machine as you would if you were a local user on the remote machine. Then specify the parameters used by the Remoting Provider to access the remote machine. You can then access the remote machine as if you were a local user.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to  <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <section>
    <title>Provider Keyword</title>
    <content>
      <para>To invoke the OLE DB Remoting Provider, specify the following keyword and value in the connection string. (Note the blank space in the provider name.)</para>
      <code>"Provider=<codeFeaturedElement>MS Remote</codeFeaturedElement>"</code>
    </content>
  </section>
  <section>
    <title>Additional Keywords</title>
    <content>
      <para>When this service provider is invoked, the following additional keywords are relevant.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Keyword</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyBold>Data Source</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the name of the remote data source. It is passed to the OLE DB Remoting Provider for processing.</para>
              <para>This keyword is equivalent to the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object's <legacyLink xlink:href="dbad5e77-b213-4eb8-aecf-d60f203fdb59">Connect</legacyLink> property.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Dynamic Properties</title>
    <content>
      <para>When this service provider is invoked, the following dynamic properties are added to the <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink>object's <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Dynamic Property Name</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyBold>DFMode</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Indicates the DataFactory Mode. A string that specifies the desired version of the <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">DataFactory</legacyLink> object on the server. Set this property before opening a connection to request a particular version of the <legacyBold>DataFactory</legacyBold>. If the requested version is not available, an attempt will be made to use the preceding version. If there is no preceding version, an error will occur. If <legacyBold>DFMode</legacyBold> is less than the available version, an error will occur. This property is read-only after a connection is made.</para>
              <para>Can be one of the following valid string values:  </para>
              <list class="bullet">
                <listItem>
                  <para>"25"—Version 2.5 (Default)</para>
                </listItem>
                <listItem>
                  <para>"21"—Version 2.1</para>
                </listItem>
                <listItem>
                  <para>"20"—Version 2.0</para>
                </listItem>
                <listItem>
                  <para>"15"—Version 1.5</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Command Properties</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Indicates values that will be added to the string of command (rowset) properties sent to the server by the MS Remote provider. The default value for this string is vt_empty.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Current DFMode</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Indicates the actual version number of the <legacyBold>DataFactory</legacyBold> on the server. Check this property to see if the version requested in the <legacyBold>DFMode</legacyBold> property was honored.</para>
              <para>Can be one of the following valid Long integer values:  </para>
              <list class="bullet">
                <listItem>
                  <para>25—Version 2.5 (Default)</para>
                </listItem>
                <listItem>
                  <para>21—Version 2.1</para>
                </listItem>
                <listItem>
                  <para>20—Version 2.0</para>
                </listItem>
                <listItem>
                  <para>15—Version 1.5</para>
                </listItem>
              </list>
              <para>Adding "DFMode=20;" to your connection string when using the <legacyBold>MSRemote</legacyBold> provider can improve your server's performance when updating data. With this setting, the <legacyBold>RDSServer.DataFactory</legacyBold> object on the server uses a less resource-intensive mode. However, the following features are not available in this configuration:   </para>
              <list class="bullet">
                <listItem>
                  <para>Using parameterized queries.</para>
                </listItem>
                <listItem>
                  <para>Getting parameter or column information before calling the <legacyBold>Execute</legacyBold> method.</para>
                </listItem>
                <listItem>
                  <para>Setting <legacyBold>Transact Updates</legacyBold> to <languageKeyword>True</languageKeyword>.</para>
                </listItem>
                <listItem>
                  <para>Getting row status.</para>
                </listItem>
                <listItem>
                  <para>Calling the <legacyBold>Resync</legacyBold> method.</para>
                </listItem>
                <listItem>
                  <para>Refreshing (explicitly or automatically) via the <legacyBold>Update Resync</legacyBold> property.</para>
                </listItem>
                <listItem>
                  <para>Setting <legacyBold>Command</legacyBold> or <legacyBold>Recordset</legacyBold> properties.</para>
                </listItem>
                <listItem>
                  <para>Using <legacyBold>adCmdTableDirect</legacyBold>.</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Handler</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Indicates the name of a server-side customization program (or handler) that extends the functionality of the <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">RDSServer.DataFactory</legacyLink>, and any parameters used by the handler<legacyItalic>,</legacyItalic> all separated by commas (","). A <languageKeyword>String</languageKeyword> value.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Internet Timeout</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Indicates the maximum number of milliseconds to wait for a request to travel to and from the server. (The default is 5 minutes.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Remote Provider</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Indicates the name of the data provider to be used on the remote server.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Remote Server</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Indicates the server name and communication protocol to be used by this connection. This property is equivalent to the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataContro</legacyLink> object <legacyLink xlink:href="d2727ce7-da9f-4271-ae3c-9334ef477c14">Server</legacyLink> property.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Transact Updates</legacyBold>
              </para>
            </TD>
            <TD>
              <para>When set to <languageKeyword>True</languageKeyword>, this value indicates that when <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink> is performed on the server, it will be done inside a transaction. The default value for this Boolean dynamic property is <languageKeyword>False</languageKeyword>.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>You may also set writable dynamic properties by specifying their names as keywords in the connection string. For example, set the <legacyBold>Internet Timeout</legacyBold> dynamic property to five seconds by specifying:</para>
      <code>Dim cn as New ADODB.Connection
cn.Open "Provider=MS Remote;Internet Timeout=5000"</code>
      <para>You may also set or retrieve a dynamic property by specifying its name as the index to the <legacyBold>Properties</legacyBold> property. The following example shows how to get and print the current value of the <legacyBold>Internet Timeout</legacyBold> dynamic property, and then set a new value:</para>
      <code>Debug.Print cn.Properties("Internet Timeout")
cn.Properties("Internet Timeout") = 5000</code>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>In ADO 2.0, the OLE DB Remoting Provider could only be specified in the <legacyItalic>ActiveConnection</legacyItalic> parameter of the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object <legacyBold>Open</legacyBold> method. Starting with ADO 2.1, the provider may also be specified in the <legacyItalic>ConnectionString </legacyItalic>parameter of the <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object <legacyBold>Open</legacyBold> method.</para>
      <para>The equivalent of the <legacyBold>RDS.DataControl</legacyBold> object <legacyLink xlink:href="e0dabf23-a159-4fe5-a962-3df544a21f5c">SQL</legacyLink> property is not available. The <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object <legacyBold>Open</legacyBold> method <legacyItalic>Source </legacyItalic>argument is used instead.</para>
      <para>
        <embeddedLabel>Note</embeddedLabel>   Specifying "...;Remote Provider=MS Remote;..." would create a four-tier scenario. Scenarios beyond three tiers have not been tested and should not be needed.</para>
    </content>
  </languageReferenceRemarks>
  <codeExample>
    <description>
      <content>
        <para>This example performs a query on the <legacyBold>Authors</legacyBold> table of the <legacyBold>Pubs</legacyBold> database on a server named <legacyItalic>YourServer</legacyItalic>. The names of the remote data source and remote server are provided in the <legacyLink xlink:href="663defab-5545-4973-9036-24d5882c9737">Open</legacyLink> method of the<legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d"> Connection</legacyLink> object, and the SQL query is specified in the<legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d"> Open</legacyLink> method of the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object. A <legacyBold>Recordset</legacyBold> object is returned, edited, and used to update the data source.</para>
      </content>
    </description>
    <code>Dim rs as New ADODB.Recordset
Dim cn as New ADODB.Connection
cn.Open  "<codeFeaturedElement>Provider</codeFeaturedElement>=MS Remote;<codeFeaturedElement>Data Source</codeFeaturedElement>=pubs;" &amp; _
         "<codeFeaturedElement>Remote Server</codeFeaturedElement>=http://YourServer"
rs.<codeFeaturedElement>Open</codeFeaturedElement> "SELECT * FROM authors", cn
...                'Edit the recordset
rs.<codeFeaturedElement>UpdateBatch</codeFeaturedElement>     'Equivalent of RDS <codeFeaturedElement>SubmitChanges</codeFeaturedElement>
...</code>
  </codeExample>
  <relatedTopics>
<legacyLink xlink:href="4083b72f-68c4-4252-b366-abb70db5ca2b">Overview of the OLE DB Remoting Provider</legacyLink>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>