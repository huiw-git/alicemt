---
title: "Item Property (ADO MD Cellset)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 0e93d79b-b12e-4e98-889e-c2dfcca20fd0
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
# Item Property (ADO MD Cellset)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Retrieves a cell from a <legacyLink xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">cellset</legacyLink> using its coordinates.</para>
  </introduction>
  <section>
    <title>Syntax</title>
    <content>
      <code>
        <codeFeaturedElement>Set</codeFeaturedElement> <legacyItalic>Cell</legacyItalic> = <legacyItalic>Cellset</legacyItalic>.<codeFeaturedElement>Item ( </codeFeaturedElement><legacyItalic>Positions</legacyItalic><codeFeaturedElement>)</codeFeaturedElement></code>
    </content>
  </section>
  <section>
    <title>Parameters</title>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Positions</legacyItalic> </definedTerm>
        <definition>
          <para>A <languageKeyword>VariantArray</languageKeyword> of values that uniquely specify a cell. <legacyItalic>Positions</legacyItalic> can be one of the following:</para>
          <list class="bullet">
            <listItem>
              <para>An array of position numbers</para>
            </listItem>
            <listItem>
              <para>An array of member names</para>
            </listItem>
            <listItem>
              <para>The ordinal position</para>
            </listItem>
          </list>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>Item</unmanagedCodeEntityReference> property to return a <legacyLink xlink:href="dcc2f044-b785-4a29-9bc5-b673f66eedf9">Cell</legacyLink> object within a <legacyLink xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset</legacyLink> object. If the <unmanagedCodeEntityReference>Item</unmanagedCodeEntityReference> property cannot find the cell corresponding to the <legacyItalic>Positions</legacyItalic> argument, an error occurs.</para>
      <para>The <unmanagedCodeEntityReference>Item</unmanagedCodeEntityReference> property is the default property for the <unmanagedCodeEntityReference>Cellset</unmanagedCodeEntityReference> object. The following syntax forms are interchangeable:</para>
      <code>
        <legacyItalic>Cellset</legacyItalic>.Item ( <legacyItalic>Positions</legacyItalic> )<legacyItalic>Cellset</legacyItalic> ( <legacyItalic>Positions</legacyItalic> )</code>
    </content>
  </languageReferenceRemarks>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyItalic>Positions </legacyItalic>argument specifies which cell to return. You can specify the cell by ordinal position or by the position along each axis. When specifying the cell by position along each axis, you can specify the numeric value of the position or the names of the members for each position.</para>
      <para>The ordinal position is a number that uniquely identifies one cell within the <unmanagedCodeEntityReference>Cellset</unmanagedCodeEntityReference>. Conceptually, cells are numbered in a <unmanagedCodeEntityReference>Cellset</unmanagedCodeEntityReference> as if the <unmanagedCodeEntityReference>Cellset</unmanagedCodeEntityReference> were a <legacyItalic>p</legacyItalic>-dimensional array, where <legacyItalic>p</legacyItalic> is the number of axes. Cells are addressed in row-major order. Below is the formula for calculating the ordinal number of a cell:</para>
      <para>If member names are passed as strings to <unmanagedCodeEntityReference>Item</unmanagedCodeEntityReference>, the members must be listed in increasing order of the numeric axis identifiers. Within an axis, the members must be listed in increasing order of dimension nesting — that is, the outermost dimension's member comes first, followed by members of inner dimensions. Each dimension should be represented by a separate string, and the list of member strings should be separated by commas.</para>
      <alert class="note">
        <para>Retrieving cells by member name may not be supported by your data provider. See the documentation for your provider for more information.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset Object (ADO MD)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="dcc2f044-b785-4a29-9bc5-b673f66eedf9">Cell Object</link>
<link xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>