---
title: "SET EXACT Command"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9533d3e0-e7c1-49de-a3a3-0cc4373a91cb
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SET EXACT Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the rules for comparing two strings of different lengths.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SET EXACT ON | OFF</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>ON </definedTerm>
        <definition>
          <para>Specifies that expressions must match character for character to be equivalent. Any trailing blanks in the expressions are ignored for the comparison. For the comparison, the shorter of the two expressions is padded on the right with blanks to match the length of the longer expression.</para>
        </definition>
        <definedTerm>OFF </definedTerm>
        <definition>
          <para>(Default.) Specifies that, to be equivalent, expressions must match character for character until the end of the expression on the right side is reached.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The SET EXACT setting has no effect if both strings are the same length.</para>
    </content>
    <sections>
      <section>
        <title>String Comparisons</title>
        <content>
          <para>Visual FoxPro has two relational operators that test for equality.</para>
          <para>The = operator performs a comparison between two values of the same type. This operator is suited for comparing character, numeric, date, and logical data.</para>
          <para>However, when you compare character expressions with the = operator, the results might not be exactly what you expect. Character expressions are compared character for character from left to right until one of the expressions isn't equal to the other, until the end of the expression on the right side of the = operator is reached (SET EXACT OFF), or until the ends of both expressions are reached (SET EXACT ON).</para>
          <para>The == operator can be used when an exact comparison of character data is needed. If two character expressions are compared with the == operator, the expressions on both sides of the == operator must contain exactly the same characters, including blanks, to be considered equal. The SET EXACT setting is ignored when character strings are compared using ==.</para>
          <para>The following table shows how the choice of operator and the SET EXACT setting affect comparisons. (An underscore represents a blank space.)</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Comparison</para>
                </TD>
                <TD>
                  <para>= EXACT OFF</para>
                </TD>
                <TD>
                  <para>= EXACT ON</para>
                </TD>
                <TD>
                  <para>== EXACT ON or OFF</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>"abc" = "abc"</para>
                </TD>
                <TD>
                  <para>Match</para>
                </TD>
                <TD>
                  <para>Match</para>
                </TD>
                <TD>
                  <para>Match</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>"ab" = "abc"</para>
                </TD>
                <TD>
                  <para>No match</para>
                </TD>
                <TD>
                  <para>No match</para>
                </TD>
                <TD>
                  <para>No match</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>"abc" = "ab"</para>
                </TD>
                <TD>
                  <para>Match</para>
                </TD>
                <TD>
                  <para>No match</para>
                </TD>
                <TD>
                  <para>No match</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>"abc" = "ab_"</para>
                </TD>
                <TD>
                  <para>No match</para>
                </TD>
                <TD>
                  <para>No match</para>
                </TD>
                <TD>
                  <para>No match</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>"ab" = "ab_"</para>
                </TD>
                <TD>
                  <para>No match</para>
                </TD>
                <TD>
                  <para>Match</para>
                </TD>
                <TD>
                  <para>No match</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>"ab_" = "ab"</para>
                </TD>
                <TD>
                  <para>Match</para>
                </TD>
                <TD>
                  <para>Match</para>
                </TD>
                <TD>
                  <para>No match</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>"" = "ab"</para>
                </TD>
                <TD>
                  <para>No match</para>
                </TD>
                <TD>
                  <para>No match</para>
                </TD>
                <TD>
                  <para>No match</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>"ab" = ""</para>
                </TD>
                <TD>
                  <para>Match</para>
                </TD>
                <TD>
                  <para>No match</para>
                </TD>
                <TD>
                  <para>No match</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>"__" = ""</para>
                </TD>
                <TD>
                  <para>Match</para>
                </TD>
                <TD>
                  <para>Match</para>
                </TD>
                <TD>
                  <para>No match</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>"" = "___"</para>
                </TD>
                <TD>
                  <para>No match</para>
                </TD>
                <TD>
                  <para>Match</para>
                </TD>
                <TD>
                  <para>No match</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>TRIM("___") = ""</para>
                </TD>
                <TD>
                  <para>Match</para>
                </TD>
                <TD>
                  <para>Match</para>
                </TD>
                <TD>
                  <para>Match</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>"" = TRIM("___")</para>
                </TD>
                <TD>
                  <para>Match</para>
                </TD>
                <TD>
                  <para>Match</para>
                </TD>
                <TD>
                  <para>Match</para>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
      </section>
    </sections>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="cf9a01b2-14bf-458c-a73c-2a58ddef32d8">SET ANSI</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>