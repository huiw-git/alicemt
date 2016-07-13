---
title: SET UNIQUE Command
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1f69e31e-4599-47cc-ac89-b86fba8703c5
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SET UNIQUE Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies whether records with duplicate index key values are maintained in an index file.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SET UNIQUE ON | OFF</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>ON </definedTerm>
        <definition>
          <para>Specifies that any record with a duplicate index key value not be included in the index file. Only the first record with the original index key value is included in the index file.</para>
        </definition>
        <definedTerm>OFF </definedTerm>
        <definition>
          <para>(Default.) Specifies that records with duplicate index key values be included in the index file.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>An index file retains its SET UNIQUE setting when you issue REINDEX. For more information, see <legacyLink xlink:href="694e8cf5-2f69-4001-9c1e-b735a4da3aff">INDEX</legacyLink>.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>