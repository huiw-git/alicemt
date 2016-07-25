---
title: "Connect Property (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: dbad5e77-b213-4eb8-aecf-d60f203fdb59
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
# Connect Property (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the database name from which the query and update operations are run.</para>
    <para>You can set the <legacyBold>Connect</legacyBold> property at design time in the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object's OBJECT tags, or at run time in scripting code (for instance, VBScript).</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <syntaxSection>
    <legacySyntax>
Design time: <legacyBold>&lt;PARAM NAME="Connect" VALUE="</legacyBold><parameterReference>ConnectionString</parameterReference><legacyBold>"&gt;</legacyBold>
Run time: <parameterReference>DataControl</parameterReference>.<legacyBold>Connect</legacyBold> = <legacyBold>"</legacyBold><parameterReference>ConnectionString</parameterReference><legacyBold>"</legacyBold></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>ConnectionString</legacyItalic> </definedTerm>
        <definition>
          <para>A valid connection string. For more general information about connection strings, see the <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString</legacyLink> property or your provider documentation.</para>
          <alert class="note">
            <para>Specifying MS Remote as the provider for the <legacyBold>RDS.DataControl</legacyBold> would create a four-tier scenario. Scenarios greater than three tiers have not been tested and should not be needed.</para>
          </alert>
        </definition>
        <definedTerm> <legacyItalic>DataControl</legacyItalic> </definedTerm>
        <definition>
          <para>An object variable that represents an <legacyBold>RDS.DataControl</legacyBold> object.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="06297993-fe72-4446-aa76-3b8bc25444f6">VBScript Example</link>
<link xlink:href="20f2480f-3758-405d-a379-05a0dce74796">Query Method (RDS)</link>
<link xlink:href="c90a8050-0ff4-4c83-9925-261f2f2ccfe9">Refresh Method (RDS)</link>
<link xlink:href="250062a4-13c4-4bed-807d-8b9ad81536d4">SubmitChanges Method (RDS)</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>