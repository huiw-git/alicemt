---
title: "Delete Method (ADOX Collections)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: e6b6e3a4-8952-4d79-81f4-51019c338374
caps.latest.revision: 11
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
# Delete Method (ADOX Collections)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Removes an object from a collection.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Collection</parameterReference><legacyBold>.Delete </legacyBold><parameterReference>Name</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <parameterReference>Name </parameterReference></definedTerm>
        <definition>
          <para>A <languageKeyword>Variant</languageKeyword> that specifies the name or ordinal position (index) of the object to delete.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>An error will occur if the <legacyItalic>Name</legacyItalic> does not exist in the collection.</para>
      <para>For <legacyLink xlink:href="38d750e7-f3fb-426e-b4b4-55eea4f1a654">Tables</legacyLink> and <legacyLink xlink:href="0a30fa74-6f10-4410-bd70-882e7c43cd46">Users</legacyLink> collections, an error will occur if the provider does not support deleting tables or users, respectively. For <legacyLink xlink:href="dc7a38e1-93b9-4034-9af2-ff419e8fb2a3">Procedures</legacyLink> and <legacyLink xlink:href="a55d380c-2b7b-4b57-af74-8ba0b3de0db9">Views</legacyLink> collections, <legacyBold>Delete</legacyBold> will fail if the provider does not support persisting commands.</para>
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
                <link xlink:href="23b9fea8-4f76-4a51-95ce-1a6ce4560b34">Columns Collection</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="09aa7b0a-69d5-4564-80a7-20ad8189670f">Groups Collection</link>
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
                <link xlink:href="dc7a38e1-93b9-4034-9af2-ff419e8fb2a3">Procedures Collection</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="38d750e7-f3fb-426e-b4b4-55eea4f1a654">Tables Collection</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="0a30fa74-6f10-4410-bd70-882e7c43cd46">Users Collection</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="a55d380c-2b7b-4b57-af74-8ba0b3de0db9">Views Collection</link>
              </para>
            </TD>
            <TD />
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="94f1ac93-e778-4a40-a85e-94bce5316ac7">Procedures Delete Method Example (VB)</link>
<link xlink:href="17df2a83-4166-4df8-8c17-0a33aaac8582">Views Delete Method Example (VB)</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>