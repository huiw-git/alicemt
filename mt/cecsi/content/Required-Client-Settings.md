---
title: "Required Client Settings"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e776b4e3-fcc4-4bfb-a7e8-5ffae1d83833
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
# Required Client Settings
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>Specify the following settings to use a custom <legacyBold>DataFactory</legacyBold> handler. </para>
    <list class="bullet">
      <listItem>
        <para>Specify "Provider=MS Remote" in the <link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object_ADO</link> object <link xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider Property (ADO)</link> property or the <legacyBold>Connection</legacyBold> object connection string "<legacyBold>Provider</legacyBold>=" keyword.</para>
      </listItem>
      <listItem>
        <para>Set the <link xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation Property (ADO)</link> property to <legacyBold>adUseClient</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>Specify the name of the handler to use in the <link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link> object's <legacyBold>Handler</legacyBold> property, or the <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object_ADO</link> object's connection string "<legacyBold>Handler</legacyBold>=" keyword. (You cannot set the handler in the <legacyBold>Connection</legacyBold> object connect string.) </para>
      </listItem>
    </list>
    <para>RDS provides a default handler on the server named <legacyBold>MSDFMAP.Handler</legacyBold>. (The default customization file is named MSDFMAP.INI.)</para>
    <para>
      <legacyBold>Example</legacyBold>
    </para>
    <para>Assume that the following sections in <legacyBold>MSDFMAP.INI</legacyBold> and the data source name, AdvWorks, have been previously defined:</para>
    <code>[connect CustomerDataBase]
Access=ReadWrite
Connect="DSN=AdvWorks"

[sql CustomerById]
SQL="SELECT * FROM Customers WHERE CustomerID = ?"</code>
    <para>The following code snippets are written in Visual Basic:</para>
  </introduction>
  <section>
    <title>RDS.DataControl Version</title>
    <content>
      <code>Dim dc as New RDS.DataControl
Set dc.Handler = "MSDFMAP.Handler"
Set dc.Server = "http://yourServer"
Set dc.Connect = "Data Source=CustomerDatabase"
Set dc.SQL = "CustomerById(4)"
dc.Refresh</code>
    </content>
  </section>
  <section>
    <title>Recordset Version</title>
    <content>
      <code>Dim rs as New ADODB.Recordset
rs.CursorLocation = adUseClient</code>
      <para>Specify either the <link xlink:href="fdc34362-6d47-4727-b171-8d033159408e">Handler Property (RDS)</link> property or keyword; the <link xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider Property (ADO)</link> property or keyword; and the <legacyItalic>CustomerById</legacyItalic> and <legacyItalic>CustomerDatabase</legacyItalic> identifiers. Then open the <legacyBold>Recordset</legacyBold> object</para>
      <para>rs.Open "CustomerById(4)", "Handler=MSDFMAP.Handler;" &amp; _</para>
      <code>   "Provider=MS Remote;Data Source=CustomerDatabase;" &amp; _
   "Remote Server=http://yourServer"</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="d50eb3cc-a822-486f-b80b-65bb50547ecd">Customization File Connect Section</link>
<link xlink:href="e65c2871-9986-44ff-b8b7-7f5eda91b3fa">Customization File SQL Section</link>
<link xlink:href="42e8ec20-eaac-4a95-8cb8-4bba93a75bcb">Customization File UserList Section</link>
<link xlink:href="86d77985-a0d0-405a-8587-c85a20540a0e">DataFactory Customization</link>
<link xlink:href="e776b4e3-fcc4-4bfb-a7e8-5ffae1d83833">Required Client Settings</link>
<link xlink:href="136f74bf-8d86-4a41-be66-c86cbcf81548">Understanding the Customization File</link>
<link xlink:href="d447712a-e123-47b5-a3a4-5d366cfe8d72">Writing Your Own Customized Handler</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>