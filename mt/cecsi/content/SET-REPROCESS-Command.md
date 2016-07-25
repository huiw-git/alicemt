---
title: "SET REPROCESS Command"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b0708757-b1d7-42f3-8988-787f2a806b8b
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SET REPROCESS Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies how many times or for how long to lock a file or record after an unsuccessful locking attempt.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SET REPROCESS TO <parameterReference>nAttempts</parameterReference> [SECONDS] | TO AUTOMATIC</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>TO <legacyItalic>nAttempts</legacyItalic>[SECONDS] </definedTerm>
        <definition>
          <para>Specifies the number of times or number of seconds to try to lock a record or file after an initial unsuccessful attempt. The default value is 0; the maximum value is 32,000.</para>
          <para>SECONDS specifies that Visual FoxPro attempts to lock a file or record for <legacyItalic>nAttempts</legacyItalic> seconds. It's available only when <legacyItalic>nAttempts</legacyItalic> is greater than zero.


</para>
          <para>For example, if <legacyItalic>nAttempts</legacyItalic> is 30, Visual FoxPro attempts to lock a record or file up to 30 times. If you also include SECONDS (SET REPROCESS TO 30 SECONDS), Visual FoxPro continuously attempts to lock a record or file for up to 30 seconds.


</para>
          <para>If an ON ERROR routine is in effect and if attempts by a command to lock the record or file are unsuccessful, the ON ERROR routine is executed. However, if a function attempts the lock, an ON ERROR routine isn't executed and the function returns False (.F.).


</para>
          <para>If an ON ERROR routine isn't in effect, a command attempts to lock the record or file, and the lock can't be placed, an error is generated. If a function attempts to place the lock, the alert isn't displayed and the function returns False (.F.).


</para>
          <para>If <legacyItalic>nAttempts</legacyItalic> is 0 (the default value) and you issue a command or function that attempts to lock a record or file, Visual FoxPro tries to lock the record or file indefinitely. If the record or file becomes available for locking while you wait, the lock is placed and the system message is cleared. If a function attempted to place the lock, the function returns True (.T.).


</para>
          <para>If an ON ERROR routine is in effect and a command is attempting to lock the record or file, the ON ERROR routine takes precedence over additional attempts to lock the record or file. The ON ERROR routine is immediately executed. Visual FoxPro does not attempt additional record or file locks and does not display the system message.


</para>
          <para>If <legacyItalic>nAttempts</legacyItalic> is 1, Visual FoxPro attempts to lock the record or file indefinitely and an ON ERROR routine isn't executed.


</para>
          <para>If a lock has been placed by another user on the record or file you are attempting to lock, you must wait until the user releases the lock.
</para>
        </definition>
        <definedTerm>TO AUTOMATIC </definedTerm>
        <definition>
          <para>Specifies that Visual FoxPro attempts to lock the record or file indefinitely. (SET REPROCESS TO -2 is an equivalent command.)</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The first attempt to lock a record or file isn't always successful. Frequently, a record or file is locked by another user on the network. SET REPROCESS determines whether Visual FoxPro makes additional attempts to lock the record or file when the initial attempt is unsuccessful. You can specify either how many times additional attempts are made or for how long the attempts are made. An ON ERROR routine affects how unsuccessful lock attempts are handled.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>