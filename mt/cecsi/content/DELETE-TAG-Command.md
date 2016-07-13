---
title: DELETE TAG Command
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4f4e1362-a5f3-4b15-8a3c-d4e96605f221
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# DELETE TAG Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Removes a tag or tags from a compound index (.cdx) file.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
DELETE TAG <parameterReference>TagName1</parameterReference> [OF <parameterReference>CDXFileName1</parameterReference>]
   [, <parameterReference>TagName2</parameterReference> [OF <parameterReference>CDXFileName2</parameterReference>]] ...
  Or 
DELETE TAG ALL [OF <parameterReference>CDXFileName</parameterReference>]</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>TagName1</legacyItalic>OF <legacyItalic>CDXFileName1</legacyItalic>[, <legacyItalic>TagName2</legacyItalic>[OF <legacyItalic>CDXFileName2</legacyItalic>]] ... </definedTerm>
        <definition>
          <para>Specifies a tag to remove from a compound index file. You can delete multiple tags with one DELETE TAG by including a list of tag names separated by commas. If two or more tags with the same name exist in the open index files, you can remove a tag from a specific index file by including OF <legacyItalic>CDXFileName</legacyItalic>.</para>
        </definition>
        <definedTerm>ALL [OF <legacyItalic>CDXFileName</legacyItalic>] </definedTerm>
        <definition>
          <para>Removes every tag from a compound index file. If the current table has a structural compound index file, all tags are removed from the index file, the index file is deleted from the disk, and the flag in the table's header indicating the presence of an associated structural compound index file is removed. Use ALL with OF <legacyItalic>CDXFileName</legacyItalic> to remove all tags from an open compound index file other than the structural compound index file.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Compound index files, created with INDEX, contain tags corresponding to index entries. DELETE TAG is used to remove a tag or tags from open compound index files. You can delete only tags from compound index files open in the current work area. If you remove all the tags from a compound index file, the file is deleted from the disk.</para>
      <para>Visual FoxPro looks first for a tag in the structural compound index file (if one is open). If the tag isn't in the structural compound index file, Visual FoxPro then looks for the tag in the other open compound index files.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="694e8cf5-2f69-4001-9c1e-b735a4da3aff">INDEX</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>