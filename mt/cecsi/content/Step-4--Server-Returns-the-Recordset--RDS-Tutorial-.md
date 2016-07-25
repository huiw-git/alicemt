---
title: "Step 4: Server Returns the Recordset (RDS Tutorial)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3d1855c4-419c-4810-b5ea-6c874b5e2905
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
# Step 4: Server Returns the Recordset (RDS Tutorial)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>RDS converts the retrieved <legacyBold>Recordset</legacyBold> object to a form that can be sent back to the client (that is, it <legacyItalic>marshals</legacyItalic> the <legacyBold>Recordset</legacyBold>). The exact form of the conversion and how it is sent depends on whether the server is on the Internet or an intranet, a local area network, or is a dynamic-link library. However, this detail is not critical; all that matters is that RDS sends the <legacyBold>Recordset</legacyBold> back to the client.</para>
    <para>On the client side, a <legacyBold>Recordset</legacyBold> object is returned and assigned to a local variable.</para>
    <code>Sub RDSTutorial4()
   Dim DS as New RDS.DataSpace
   Dim RS as ADODB.Recordset
   Dim DF as Object
   Set DF = DS.<codeFeaturedElement>CreateObject</codeFeaturedElement>("RDSServer.DataFactory", "http://yourServer")
   Set RS = DF.<codeFeaturedElement>Query</codeFeaturedElement>("DSN=Pubs", "SELECT * FROM Authors")
...</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ed5c4a24-9804-4c85-817e-317652acb9b4">Step 5: DataControl is Made Usable (RDS Tutorial)</link>
<link xlink:href="e2a48c4d-88b1-43ff-a202-9cdec54997d2">RDS Tutorial (VBScript)</link>
<link xlink:href="d0d735e0-669a-41e7-ada2-8dd80924e349">RDS Tutorial (Visual J++)</link>
</relatedTopics>
</developerConceptualDocument>