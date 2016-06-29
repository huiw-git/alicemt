---
title: SET ANSI Command
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cf9a01b2-14bf-458c-a73c-2a58ddef32d8
translation.priority.ht: 
  - en-gb
---
# SET ANSI Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Determines how comparisons between strings of different lengths are made with the = operator in Visual FoxPro SQL commands.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SET ANSI ON | OFF</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>ON </definedTerm>
        <definition>
          <para>(Default for the driver; the default for Visual FoxPro is OFF.) Pads the shorter string with the blanks needed to make it equal to the longer string's length. The two strings are then compared character for character for their entire lengths. Consider this comparison:

</para>
          <code>'Tommy' = 'Tom'</code>
          <para>The result is False (.F.) if SET ANSI is on, because when padded, 'Tom' becomes 'Tom ' and the strings 'Tom ' and 'Tommy' don't match character for character.


</para>
          <para>The == operator uses this method for comparisons in Visual FoxPro SQL commands.
</para>
        </definition>
        <definedTerm>OFF </definedTerm>
        <definition>
          <para>Specifies that the shorter string not be padded with blanks. The two strings are compared character for character until the end of the shorter string is reached. Consider this comparison:

</para>
          <code>'Tommy' = 'Tom'</code>
          <para>The result is True (.T.) when SET ANSI is off, because the comparison stops after 'Tom'.
</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>SET ANSI determines whether the shorter of two strings is padded with blanks when an SQL string comparison is made. SET ANSI has no effect on the == operator; when you use the == operator, the shorter string is always padded with blanks for the comparison.</para>
    </content>
    <sections>
      <section>
        <title>String Order</title>
        <content>
          <para>In SQL commands, the left-to-right order of the two strings in a comparison is irrelevantswitching a string from one side of the = or == operator to the other doesn't affect the result of the comparison.</para>
        </content>
      </section>
    </sections>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="2149c3ca-3a71-446d-8d53-3d056e2f301a">SELECT - SQL</link>
<link xlink:href="9533d3e0-e7c1-49de-a3a3-0cc4373a91cb">SET EXACT</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>