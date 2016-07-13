---
title: SET EXCLUSIVE Command
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d4fe12c5-7e8b-4d20-9ea4-2bcaffb271f2
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SET EXCLUSIVE Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies whether table files are opened for exclusive or shared use on a network.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SET EXCLUSIVE ON | OFF</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>ON </definedTerm>
        <definition>
          <para>Limits accessibility of a table opened on a network to the user who opened it. The table isn't accessible to other users on the network. SET EXCLUSIVE ON also prevents all other users from having read-only access.</para>
        </definition>
        <definedTerm>OFF </definedTerm>
        <definition>
          <para>(Default for the driver; the defaults for Visual FoxPro are ON for the global data session and OFF for a private data session.) Allows a table opened on a network to be shared and modified by any user on the network.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Changing the setting of SET EXCLUSIVE doesn't change the status of previously opened tables. For example, if a table is opened with SET EXCLUSIVE set to ON and SET EXCLUSIVE is later changed to OFF, the table retains its exclusive-use status.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="de020197-7f53-4643-9cbf-b7887ba88de9">ODBC Visual FoxPro Setup Dialog Box</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>