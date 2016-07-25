---
title: "Step 6: Changes are Sent to the Server (RDS Tutorial)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b1e927d6-7d50-4978-9eef-045043cdce7a
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
# Step 6: Changes are Sent to the Server (RDS Tutorial)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>If the <legacyBold>Recordset</legacyBold> object is edited, any changes (that is, rows that are added, changed, or deleted) can be sent back to the server.</para>
    <alert class="note">
      <para>The default behavior of RDS can be invoked implicitly with ADO objects and the Microsoft OLE DB Remoting Provider. Queries can return <legacyBold>Recordset</legacyBold>s, and edited <legacyBold>Recordset</legacyBold>s can update the data source. This tutorial does not invoke RDS with ADO objects, but this is how it would look if it did:</para>
    </alert>
    <code>Dim rs as New ADODB.Recordset
rs. "SELECT * FROM Authors","=MS Remote;=Pubs;" &amp; _
=http://yourServer;=SQLOLEDB;"
...              ' Edit the Recordset.
rs.   ' The equivalent of 
...</code>
    <para>         <legacyBold>Part A</legacyBold>   Assume for this case that you have only used the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> and that a <legacyBold>Recordset</legacyBold> object is now associated with the <legacyBold>RDS.DataControl</legacyBold>. The <legacyLink xlink:href="250062a4-13c4-4bed-807d-8b9ad81536d4">SubmitChanges</legacyLink> method updates the data source with any changes to the <legacyBold>Recordset</legacyBold> object if the <legacyLink xlink:href="d2727ce7-da9f-4271-ae3c-9334ef477c14">Server</legacyLink> and <legacyLink xlink:href="dbad5e77-b213-4eb8-aecf-d60f203fdb59">Connect</legacyLink> properties are still set.</para>
    <code>Sub RDSTutorial6A()
Dim DC as New RDS.DataControl
Dim RS as ADODB.Recordset
DC. = "http://yourServer"
DC. = "DSN=Pubs"
DC. = "SELECT * FROM Authors"
DC.
...
Set RS = DC.
   ' Edit the Recordset.
...
DC.
...</code>
    <para>         <legacyBold>Part B</legacyBold>   Alternatively, you could update the server with the <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">RDSServer.DataFactory</legacyLink> object, specifying a connection and a <legacyBold>Recordset</legacyBold> object.</para>
    <code>Sub RDSTutorial6B()
Dim DS As New RDS.DataSpace
Dim RS As ADODB.Recordset
Dim DC As New RDS.DataControl
Dim DF As Object
Dim blnStatus As Boolean
Set DF = DS.("RDSServer.DataFactory", "http://yourServer")
Set RS = DF. ("DSN=Pubs", "SELECT * FROM Authors")
DC. = RS    ' Visual controls can now bind to DC.
    ' Edit the Recordset.
blnStatus = DF."DSN=Pubs", RS
End Sub</code>
    <para>
      <legacyBold>This is the end of the tutorial.</legacyBold>
    </para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <relatedTopics>
<link xlink:href="a4360ed4-b70f-4734-9041-4025d033346b">Microsoft OLE DB Remoting Provider</link>
<link xlink:href="6e3305a0-7bc7-40d1-9122-235c15d23ab2">RDS Tutorial</link>
<link xlink:href="e2a48c4d-88b1-43ff-a202-9cdec54997d2">RDS Tutorial (VBScript)</link>
<link xlink:href="d0d735e0-669a-41e7-ada2-8dd80924e349">RDS Tutorial (Visual J++)</link>
</relatedTopics>
</developerConceptualDocument>