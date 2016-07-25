---
title: "Step 5: DataControl is Made Usable (RDS Tutorial)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed5c4a24-9804-4c85-817e-317652acb9b4
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
# Step 5: DataControl is Made Usable (RDS Tutorial)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The returned <legacyBold>Recordset</legacyBold> object is available for use. You can examine, navigate, or edit it as you would any other <legacyBold>Recordset</legacyBold>. What you can do with the <legacyBold>Recordset</legacyBold> depends on your environment. Visual Basic and Visual C++ have visual controls that can use a <legacyBold>Recordset</legacyBold> directly or indirectly with the aid of an enabling data control.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>For example, if you are displaying a Web page in Microsoft Internet Explorer, you might want to display the <legacyBold>Recordset</legacyBold> object data in a visual control. Visual controls on a Web page cannot access a <legacyBold>Recordset</legacyBold> object directly. However, they can access the <legacyBold>Recordset</legacyBold> object through the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink>. The <legacyBold>RDS.DataControl</legacyBold> becomes usable by a visual control when its <legacyLink xlink:href="a29e3fb9-306d-497a-9a59-1856a914e5e9">SourceRecordset</legacyLink> property is set to the <legacyBold>Recordset</legacyBold> object.</para>
    <para>The visual control object must have its <legacyBold>DATASRC</legacyBold> parameter set to the <legacyBold>RDS.DataControl</legacyBold>, and its <legacyBold>DATAFLD</legacyBold> property set to a <legacyBold>Recordset</legacyBold> object field (column).</para>
    <para>In this tutorial, set the <legacyBold>SourceRecordset</legacyBold> property:</para>
    <code>Sub RDSTutorial5()
   Dim DS as New RDS.DataSpace
   Dim RS as ADODB.Recordset
   Dim DC as New RDS.DataControl
   Dim DF as Object
   Set DF = DS.<codeFeaturedElement>CreateObject</codeFeaturedElement>("RDSServer.DataFactory", "http://yourServer")
   Set RS = DF.<codeFeaturedElement>Query</codeFeaturedElement> ("DSN=Pubs", "SELECT * FROM Authors")
   DC.<codeFeaturedElement>SourceRecordset</codeFeaturedElement> = RS         ' Visual controls can now bind to DC.
...</code>
  </introduction>
  <relatedTopics>
<link xlink:href="b1e927d6-7d50-4978-9eef-045043cdce7a">Step 6: Changes are Sent to the Server (RDS Tutorial)</link>
<link xlink:href="e2a48c4d-88b1-43ff-a202-9cdec54997d2">RDS Tutorial (VBScript)</link>
<link xlink:href="d0d735e0-669a-41e7-ada2-8dd80924e349">RDS Tutorial (Visual J++)</link>
</relatedTopics>
</developerConceptualDocument>