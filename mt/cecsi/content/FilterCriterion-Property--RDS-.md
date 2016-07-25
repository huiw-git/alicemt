---
title: "FilterCriterion Property (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 24eb03ba-ccfd-4353-b6af-03586b2da6fd
caps.latest.revision: 15
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
# FilterCriterion Property (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the evaluation operator to use in the filter value.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>DataControl</parameterReference>.<legacyBold>FilterCriterion = </legacyBold><parameterReference>String</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>DataControl</legacyItalic>
        </definedTerm>
        <definition>
          <para>An object variable that represents an <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object.</para>
        </definition>
        <definedTerm>
          <legacyItalic>String</legacyItalic>
        </definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> value that specifies the evaluation operator of the <legacyLink xlink:href="28f17186-b842-4cf9-b320-a9bb941c481b">FilterValue</legacyLink> to the records. Can be any one of the following: &lt;, &lt;=, &gt;, &gt;=, =, or &lt;&gt;.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyLink xlink:href="f6f80f67-f0fb-4e63-a5f5-8fdf312aac63">SortColumn</legacyLink>, <legacyLink xlink:href="1d9d8715-e4ad-4ff3-bf7f-f1dc0532d8c2">SortDirection</legacyLink>, <legacyLink xlink:href="28f17186-b842-4cf9-b320-a9bb941c481b">FilterValue</legacyLink>, <unmanagedCodeEntityReference>FilterCriterion</unmanagedCodeEntityReference>, and <legacyLink xlink:href="0a5473e8-8ce6-4518-83fb-4920b827e285">FilterColumn</legacyLink> properties provide sorting and filtering functionality on the client-side cache. The sorting functionality orders records by values from one column. The filtering functionality displays a subset of records based on find criteria, while the full <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> is maintained in the cache. The <legacyLink xlink:href="3957197a-f543-4d6b-9e11-67a77c2063b7">Reset</legacyLink> method will execute the criteria and replace the current <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> with an updatable <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>.</para>
      <para>The "!=" operator is not valid for <unmanagedCodeEntityReference>FilterCriterion</unmanagedCodeEntityReference>; instead, use "&lt;&gt;".</para>
      <para>If both the filter and sort properties are set and you call the <legacyBold>Reset</legacyBold> method, the rowset is first filtered and then it is sorted. For ascending sorts, the null values are at the top; for descending sorts, null values are at the bottom (ascending is default behavior).</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="8a74802f-34d6-4676-bf94-07df5f8bff66">VBScript Example</link>
<link xlink:href="0a5473e8-8ce6-4518-83fb-4920b827e285">FilterColumn Property (RDS)</link>
<link xlink:href="28f17186-b842-4cf9-b320-a9bb941c481b">FilterValue Property (RDS)</link>
<link xlink:href="f6f80f67-f0fb-4e63-a5f5-8fdf312aac63">SortColumn Property (RDS)</link>
<link xlink:href="1d9d8715-e4ad-4ff3-bf7f-f1dc0532d8c2">SortDirection Property (RDS)</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>