---
title: "Step 2: Invoke the Server Program (RDS Tutorial)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5e74c2da-65ee-4de4-8b41-6eac45c3632e
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
# Step 2: Invoke the Server Program (RDS Tutorial)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When you invoke a method on the client <legacyItalic>proxy</legacyItalic>, the actual program on the server executes the method. In this step, you'll execute a query on the server.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>
      <legacyBold>Part A</legacyBold>   If you weren't using <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">RDSServer.DataFactory</legacyLink> in this tutorial, the most convenient way to perform this step would be to use the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object. The <legacyBold>RDS.DataControl</legacyBold> combines the previous step of creating a proxy, with this step, issuing the query.</para>
    <para>Set the <legacyBold>RDS.DataControl</legacyBold> object <legacyLink xlink:href="d2727ce7-da9f-4271-ae3c-9334ef477c14">Server</legacyLink> property to identify where the server program should be instantiated; the <legacyLink xlink:href="dbad5e77-b213-4eb8-aecf-d60f203fdb59">Connect</legacyLink> property to specify the connect string to access the data source; and the <legacyLink xlink:href="e0dabf23-a159-4fe5-a962-3df544a21f5c">SQL</legacyLink> property to specify the query command text. Then issue the <legacyLink xlink:href="c90a8050-0ff4-4c83-9925-261f2f2ccfe9">Refresh</legacyLink> method to cause the server program to connect to the data source, retrieve rows specified by the query, and return a <legacyBold>Recordset</legacyBold> object to the client.</para>
    <para>This tutorial does not use the <legacyBold>RDS.DataControl</legacyBold>, but this is how it would look if it did:</para>
    <code>Sub RDSTutorial2A()
   Dim DC as New RDS.DataControl
   DC.<codeFeaturedElement>Server</codeFeaturedElement> = "http://yourServer"
   DC.<codeFeaturedElement>Connect</codeFeaturedElement> = "DSN=Pubs"
   DC.<codeFeaturedElement>SQL</codeFeaturedElement> = "SELECT * FROM Authors"
   DC.<codeFeaturedElement>Refresh</codeFeaturedElement>
...</code>
    <para>Nor does the tutorial invoke RDS with ADO objects, but this is how it would look if it did:</para>
    <code>Dim rs as New ADODB.Recordset
rs.Open "SELECT * FROM Authors","<codeFeaturedElement>Provider</codeFeaturedElement>=MS Remote;<codeFeaturedElement>Data Source</codeFeaturedElement>=Pubs;" &amp; _
        "<codeFeaturedElement>Remote Server</codeFeaturedElement>=http://yourServer;<codeFeaturedElement>Remote Provider</codeFeaturedElement>=SQLOLEDB;"</code>
    <para>         <legacyBold>Part B</legacyBold>   The general method of performing this step is to invoke the <legacyBold>RDSServer.DataFactory</legacyBold> object <legacyLink xlink:href="20f2480f-3758-405d-a379-05a0dce74796">Query</legacyLink> method. That method takes a connect string, which is used to connect to a data source, and a command text, which is used to specify the rows to be returned from the data source.</para>
    <para>This tutorial uses the <legacyBold>DataFactory</legacyBold> object <legacyBold>Query</legacyBold> method:</para>
    <code>Sub RDSTutorial2B()
   Dim DS as New RDS.DataSpace
   Dim DF
   Dim RS as ADODB.Recordset
   Set DF = DS.<codeFeaturedElement>CreateObject</codeFeaturedElement>("RDSServer.DataFactory", "http://yourServer")
   Set RS = DF.<codeFeaturedElement>Query</codeFeaturedElement> ("DSN=Pubs", "SELECT * FROM Authors")
...</code>
  </introduction>
  <relatedTopics>
<link xlink:href="9c6779c9-1208-4696-ac51-c39f3a6d9240">Step 3: Server Obtains a Recordset (RDS Tutorial)</link>
<link xlink:href="e2a48c4d-88b1-43ff-a202-9cdec54997d2">RDS Tutorial (VBScript)</link>
<link xlink:href="d0d735e0-669a-41e7-ada2-8dd80924e349">RDS Tutorial (Visual J++)</link>
</relatedTopics>
</developerConceptualDocument>