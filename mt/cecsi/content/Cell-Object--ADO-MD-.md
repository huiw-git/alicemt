---
title: "Cell Object (ADO MD)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: dcc2f044-b785-4a29-9bc5-b673f66eedf9
caps.latest.revision: 9
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
# Cell Object (ADO MD)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Represents the data at the intersection of axis coordinates contained in a cellset.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>A <legacyBold>Cell</legacyBold> object is returned by the <legacyLink xlink:href="0e93d79b-b12e-4e98-889e-c2dfcca20fd0">Item</legacyLink> property of a <legacyLink xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset</legacyLink> object.</para>
      <para>With the collections and properties of a <legacyBold>Cell</legacyBold> object, you can do the following:  </para>
      <list class="bullet">
        <listItem>
          <para>Return the data in the <legacyBold>Cell</legacyBold> with the <legacyLink xlink:href="70dc5cff-0b05-456d-b86b-2686fe4e7ce6">Value</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return the string representing the formatted display of the <legacyBold>Value</legacyBold> property with the <legacyLink xlink:href="5c06451e-06ec-4da6-9a87-2d043469248a">FormattedValue</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return the ordinal value of the <legacyBold>Cell</legacyBold> within the <legacyBold>Cellset</legacyBold> with the <legacyLink xlink:href="a6001168-b954-47f0-ba0d-c05c4cc40c58">Ordinal</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Determine the position of the <legacyBold>Cell</legacyBold> within the <legacyLink xlink:href="feb2581c-fc41-471c-bb69-29f8a55fda70">CubeDef</legacyLink> with the <legacyLink xlink:href="5b9e7545-cf30-464d-80ef-5c99c8306bab">Positions</legacyLink> collection.</para>
        </listItem>
        <listItem>
          <para>Retrieve other information about the <legacyBold>Cell</legacyBold> with the standard ADO <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection.</para>
        </listItem>
      </list>
      <para>The <legacyBold>Properties</legacyBold> collection contains provider-supplied properties. The following table lists properties that might be available. The actual property list may differ depending upon the implementation of the provider. See the documentation for your provider for a more complete list of available properties.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Name</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>BackColor</para>
            </TD>
            <TD>
              <para>Background color used when displaying the cell.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FontFlags</para>
            </TD>
            <TD>
              <para>Bitmask detailing effects on the font.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FontName</para>
            </TD>
            <TD>
              <para>Font used to display the cell value.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FontSize</para>
            </TD>
            <TD>
              <para>Font size used to display the cell value.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ForeColor</para>
            </TD>
            <TD>
              <para>Foreground color used when displaying the cell.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FormatString</para>
            </TD>
            <TD>
              <para>Value in a formatted string.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="c45d795b-3272-4df4-a54c-7cd4fcb187fd">Properties, Methods, and Events</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="b4647211-2566-4657-ae7b-3dd761457d7b">VBScript Example</link>
<link xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset Object</link>
<link xlink:href="5b9e7545-cf30-464d-80ef-5c99c8306bab">Positions Collection</link>
<link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>