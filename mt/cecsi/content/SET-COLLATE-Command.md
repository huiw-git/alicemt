---
title: SET COLLATE Command
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 00efbcd4-fea8-4061-86a5-82de413cb753
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SET COLLATE Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies a collation sequence for character fields in subsequent indexing and sorting operations.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SET COLLATE TO <parameterReference>cSequenceName</parameterReference></legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>cSequenceName</legacyItalic> </definedTerm>
        <definition>
          <para>Specifies a collation sequence. The available collation sequence options are described in the following table.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Options</para>
                </TD>
                <TD>
                  <para>Language</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>DUTCH</para>
                </TD>
                <TD>
                  <para>Dutch </para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>GENERAL</para>
                </TD>
                <TD>
                  <para>English, French, German, Modern Spanish, Portuguese, and other Western European languages</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>GERMAN</para>
                </TD>
                <TD>
                  <para>German phone book order (DIN)</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>ICELAND</para>
                </TD>
                <TD>
                  <para>Icelandic</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>MACHINE</para>
                </TD>
                <TD>
                  <para>Machine (the default collation sequence for earlier FoxPro versions)</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>NORDAN</para>
                </TD>
                <TD>
                  <para>Norwegian, Danish</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SPANISH</para>
                </TD>
                <TD>
                  <para>Traditional Spanish</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SWEFIN</para>
                </TD>
                <TD>
                  <para>Swedish, Finnish</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>UNIQWT</para>
                </TD>
                <TD>
                  <para>Unique Weight</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <alert class="note">
            <para>When you specify the SPANISH option, <legacyItalic>ch</legacyItalic> is a single letter that sorts between <legacyItalic>c</legacyItalic> and <legacyItalic>d</legacyItalic>, and <legacyItalic>ll</legacyItalic> sorts between <legacyItalic>l</legacyItalic> and <legacyItalic>m</legacyItalic>.</para>
          </alert>
          <para>If you specify a collation sequence option as a literal character string, be sure to enclose the option in quotation marks:


</para>
          <code>SET COLLATE TO "SWEFIN"</code>
          <para>MACHINE is the default collation sequence option and is the sequence Xbase users are familiar with. Characters are ordered as they appear in the current code page.


</para>
          <para>GENERAL may be preferable for U.S. and Western European users. Characters are ordered as they appear in the current code page. In FoxPro versions earlier than 2.5, indexes might have been created using the <legacyBold>UPPER</legacyBold>( ) or <legacyBold>LOWER</legacyBold>( ) functions to convert character fields to a consistent case. In FoxPro versions later than 2.5, you can instead specify the GENERAL collation sequence option and omit the <legacyBold>UPPER</legacyBold>( ) conversion.


</para>
          <para>If you specify a collation sequence option other than MACHINE and if you create an .idx file, a compact .idx is always created.


</para>
          <para>Use SET("COLLATE") to return the current collation sequence.


</para>
          <para>You can specify a collating sequence for a data source by using the <legacyLink xlink:href="de020197-7f53-4643-9cbf-b7887ba88de9">ODBC Visual FoxPro Setup Dialog Box</legacyLink> or by using the Collate keyword in your connection string with <legacyLink xlink:href="10492c8f-3a18-4971-9db8-879e878083b9">SQLDriverConnect</legacyLink>. This is identical to issuing the following command:


</para>
          <code>SET COLLATE TO <legacyItalic>cSequenceName</legacyItalic></code>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>SET COLLATE enables you to order tables containing accented characters for any of the supported languages. Changing the setting of SET COLLATE doesn't affect the collating sequence of previously opened indexes. Visual FoxPro automatically maintains existing indexes, providing the flexibility to create many different types of indexes, even for the same field.</para>
      <para>For example, if an index is created with SET COLLATE set to GENERAL and the SET COLLATE setting is later changed to SPANISH, the index retains the GENERAL collation sequence.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="de020197-7f53-4643-9cbf-b7887ba88de9">ODBC Visual FoxPro Setup Dialog Box</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>