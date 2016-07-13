---
title: Visual FoxPro Field Data Types
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 50b733dc-679a-4b10-bc5d-98bb474dead2
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Visual FoxPro Field Data Types
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table lists the values for the <legacyItalic>FieldType</legacyItalic> argument in ALTER TABLE and CREATE TABLE and indicates whether <legacyItalic>nFieldWidth </legacyItalic>and <legacyItalic>nPrecision</legacyItalic> arguments are required.</para>
  </introduction>
  <section>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>
                <legacyItalic>FieldType</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>NFieldWidth</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>
                <legacyItalic>nPrecision</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>B</para>
            </TD>
            <TD>
              <para>-</para>
            </TD>
            <TD>
              <para>d</para>
            </TD>
            <TD>
              <para>Double</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>C</para>
            </TD>
            <TD>
              <para>N</para>
            </TD>
            <TD>
              <para>-</para>
            </TD>
            <TD>
              <para>Character field of width <legacyItalic>n</legacyItalic></para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>D</para>
            </TD>
            <TD>
              <para>-</para>
            </TD>
            <TD>
              <para>-</para>
            </TD>
            <TD>
              <para>Date</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>F</para>
            </TD>
            <TD>
              <para>N</para>
            </TD>
            <TD>
              <para>d</para>
            </TD>
            <TD>
              <para>Floating numeric field of width <legacyItalic>n</legacyItalic> with <legacyItalic>d</legacyItalic> decimal places</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>G</para>
            </TD>
            <TD>
              <para>-</para>
            </TD>
            <TD>
              <para>-</para>
            </TD>
            <TD>
              <para>General</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>I</para>
            </TD>
            <TD>
              <para>-</para>
            </TD>
            <TD>
              <para>-</para>
            </TD>
            <TD>
              <para>Integer</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>L</para>
            </TD>
            <TD>
              <para>-</para>
            </TD>
            <TD>
              <para>-</para>
            </TD>
            <TD>
              <para>Logical</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>M</para>
            </TD>
            <TD>
              <para>-</para>
            </TD>
            <TD>
              <para>-</para>
            </TD>
            <TD>
              <para>Memo</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>N</para>
            </TD>
            <TD>
              <para>N</para>
            </TD>
            <TD>
              <para>d</para>
            </TD>
            <TD>
              <para>Numeric field of width <legacyItalic>n</legacyItalic> with <legacyItalic>d</legacyItalic> decimal places</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>T</para>
            </TD>
            <TD>
              <para>-</para>
            </TD>
            <TD>
              <para>-</para>
            </TD>
            <TD>
              <para>DateTime</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Y</para>
            </TD>
            <TD>
              <para>-</para>
            </TD>
            <TD>
              <para>-</para>
            </TD>
            <TD>
              <para>Currency</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>