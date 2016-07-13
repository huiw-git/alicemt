---
title: SET BLOCKSIZE Command
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0c11580f-37f5-4a8e-99be-9fb9c44bb433
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SET BLOCKSIZE Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies how disk space is allocated for the storage of memo fields.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SET BLOCKSIZE TO <parameterReference>nBytes</parameterReference></legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>nBytes</legacyItalic> </definedTerm>
        <definition>
          <para>Specifies the block size in which disk space for memo fields is allocated. If <legacyItalic>nBytes</legacyItalic> is 0, disk space is allocated in single bytes (blocks of 1 byte). If <legacyItalic>nBytes</legacyItalic> is an integer between 1 and 32, disk space is allocated in blocks of <legacyItalic>nBytes</legacyItalic> bytes multiplied by 512. If <legacyItalic>nBytes</legacyItalic> is greater than 32, disk space is allocated in blocks of <legacyItalic>nBytes</legacyItalic> bytes. If you specify a block size value greater than 32, you can save substantial disk space.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The default value for SET BLOCKSIZE is 64. To reset the block size to a different value after the file has been created, set it to a new value and then use COPY to create a new table. The new table has the specified block size.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>