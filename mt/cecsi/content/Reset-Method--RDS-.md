---
title: "Reset Method (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 3957197a-f543-4d6b-9e11-67a77c2063b7
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
# Reset Method (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Executes the sort or filter on a client-side <legacyBold>Recordset </legacyBold>based on the specified sort and filter properties.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>DataControl</parameterReference>.<legacyBold>Reset(</legacyBold><parameterReference>value</parameterReference><legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>DataControl</legacyItalic> </definedTerm>
        <definition>
          <para>An object variable that represents an <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object.</para>
        </definition>
        <definedTerm> <legacyItalic>value</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>Boolean</languageKeyword> value that is <languageKeyword>True</languageKeyword> (default) if you want to filter on the current "filtered" rowset. <languageKeyword>False</languageKeyword> indicates that you filter on the original rowset, removing any previous filter options.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyLink xlink:href="f6f80f67-f0fb-4e63-a5f5-8fdf312aac63">SortColumn</legacyLink>, <legacyLink xlink:href="1d9d8715-e4ad-4ff3-bf7f-f1dc0532d8c2">SortDirection</legacyLink>, <legacyLink xlink:href="28f17186-b842-4cf9-b320-a9bb941c481b">FilterValue</legacyLink>, <legacyLink xlink:href="24eb03ba-ccfd-4353-b6af-03586b2da6fd">FilterCriterion</legacyLink>, and <legacyLink xlink:href="0a5473e8-8ce6-4518-83fb-4920b827e285">FilterColumn</legacyLink> properties provide sorting and filtering functionality on the client-side cache. The sorting functionality orders records by values from one column. The filtering functionality displays a subset of records based on a find criteria, while the full <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> is maintained in the cache. The <legacyBold>Reset</legacyBold> method will execute the criteria and replace the current <legacyBold>Recordset</legacyBold> with an updatable <legacyBold>Recordset</legacyBold>.</para>
      <para>If there are changes to the original data that have not been submitted, the <legacyBold>Reset</legacyBold> method will fail. First, use the <legacyLink xlink:href="250062a4-13c4-4bed-807d-8b9ad81536d4">SubmitChanges</legacyLink> method to save any changes in a read/write <legacyBold>Recordset</legacyBold>, and then use the <legacyBold>Reset</legacyBold> method to sort or filter the records.</para>
      <para>If you want to perform more than one filter on your rowset, you can use the optional <legacyItalic>Boolean</legacyItalic> argument with the <legacyBold>Reset</legacyBold> method. The following example shows how to do this:</para>
      <code>ADC.SQL = "Select au_lname from authors"
ADC.Refresh    ' Get the new rowset.

ADC.FilterColumn = "au_lname"
ADC.FilterCriterion = "&lt;"
ADC.FilterValue = "'M'"
ADC.Reset         ' Rowset now has all Last Names &lt; "M".

ADC.FilterCriterion = "&gt;"
ADC.FilterValue = "'F'"
' Passing True is not necessary, because it is the 
' default filter on the current "filtered" rowset.
ADC.Reset(TRUE)     ' Rowset now has all Last 
                    ' Names &lt; "M" and &gt; "F".

ADC.FilterCriterion = "&gt;"
ADC.FilterValue = "'T'"
' Filter on the original rowset, throwing out the
' previous filter options.
ADC.Reset(FALSE)   ' Rowset now has all Last Names &gt; "T".</code>
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
<link xlink:href="250062a4-13c4-4bed-807d-8b9ad81536d4">SubmitChanges Method (RDS)</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>