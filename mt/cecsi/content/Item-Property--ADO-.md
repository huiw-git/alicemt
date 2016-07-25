---
title: "Item Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: e11484bb-c5c7-42d8-9bb8-21572125d727
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
# Item Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates a specific member of a collection, by name or ordinal number.</para>
  </introduction>
  <section>
    <title>Syntax</title>
    <content>
      <code>Set object = collection.Item ( Index )</code>
    </content>
  </section>
  <section>
    <title>Return Value</title>
    <content>
      <para>Returns an object reference.</para>
    </content>
  </section>
  <section>
    <title>Parameters</title>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Index</legacyItalic> </definedTerm>
        <definition>
          <para>A <languageKeyword>Variant</languageKeyword> expression that evaluates either to the name or to the ordinal number of an object in a collection.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>Item</legacyBold> property to return a specific object in a collection. If <legacyBold>Item</legacyBold> cannot find an object in the collection corresponding to the <legacyItalic>Index</legacyItalic> argument, an error occurs. Also, some collections don't support named objects; for these collections, you must use ordinal number references.</para>
      <para>The <legacyBold>Item</legacyBold> property is the default property for all collections; therefore, the following syntax forms are interchangeable:</para>
      <code>collection.Item (Index)
collection (Index)</code>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="072fb21a-ec0f-4b02-9022-1cef3ad4bfff">Axes Collection</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="23b9fea8-4f76-4a51-95ce-1a6ce4560b34">Columns Collection</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="c79a5e36-71fd-44c4-948d-d6a7a89bb3b5">CubeDefs Collection</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="eaf6f4e7-2ea0-49a3-89ee-e219e025257c">Dimensions Collection</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors Collection</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields Collection</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="09aa7b0a-69d5-4564-80a7-20ad8189670f">Groups Collection</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="bef0fcb1-8060-4faa-84f0-3d52e9c4526f">Hierarchies Collection</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="184cf536-455c-42be-bf1c-a5c25bade961">Indexes Collection</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="cdb31c76-e559-475c-b33a-aac24f73e70e">Keys Collection</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="fed8684a-b428-4ee4-8f8d-928abe4ad9ad">Levels Collection</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="3a647cde-efdc-4394-b1b9-8cbb1b9d689f">Members Collection</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters Collection</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="5b9e7545-cf30-464d-80ef-5c99c8306bab">Positions Collection</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="dc7a38e1-93b9-4034-9af2-ff419e8fb2a3">Procedures Collection</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="38d750e7-f3fb-426e-b4b4-55eea4f1a654">Tables Collection</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="0a30fa74-6f10-4410-bd70-882e7c43cd46">Users Collection</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="a55d380c-2b7b-4b57-af74-8ba0b3de0db9">Views Collection</link>
              </para>
            </TD>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b4476603-691b-4081-8797-a3d0b331dce5">Visual Basic Example</link>
<link xlink:href="05ae3f5a-a0c1-459d-aa7d-ed7f3b2ecd60">Visual C++ Example</link>
<link xlink:href="e1426a08-71b8-4af2-9f57-97ceb90ccef2">Visual J++ Example</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>