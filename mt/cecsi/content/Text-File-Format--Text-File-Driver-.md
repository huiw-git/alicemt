---
title: Text File Format (Text File Driver)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f53cd4b5-0721-4562-a90f-4c55e6030cb9
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Text File Format (Text File Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The ODBC Text driver supports both delimited and fixed-width text files. A text file consists of an optional header line and zero or more text lines.</para>
    <para>Although the header line uses the same format as the other lines in the text file, the ODBC Text driver interprets the header line entries as column names, not data.</para>
    <para>A delimited text line contains one or more data values separated by delimiters: commas, tabs, or a custom delimiter. The same delimiter must be used throughout the file. Null data values are denoted by two delimiters in a row with no data between them. Character strings in a delimited text line can be enclosed in double quotation marks (""). No blanks can occur before or after delimited values.</para>
    <para>The width of each data entry in a fixed-width text line is specified in a schema. Null data values are denoted by blanks.</para>
    <para>Tables are limited to a maximum of 255 fields. Field names are limited to 64 characters, and field widths are limited to 32,766 characters. Records are limited to 65,000 bytes.</para>
    <para>A text file can be opened only for a single user. Multiple users are not supported.</para>
    <para>The following grammar, written for programmers, defines the format of a text file that can be read by the ODBC text driver: </para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Format</para>
          </TD>
          <TD>
            <para>Representation</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Non-italics</para>
          </TD>
          <TD>
            <para>Characters that must be entered as shown</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyItalic>italics</legacyItalic>             </para>
          </TD>
          <TD>
            <para>Arguments that are defined elsewhere in the grammar</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>brackets ([])</para>
          </TD>
          <TD>
            <para>Optional items</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>braces ({})</para>
          </TD>
          <TD>
            <para>A list of mutually exclusive choices</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>vertical bars (|)</para>
          </TD>
          <TD>
            <para>Separate mutually exclusive choices</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>ellipses (...)</para>
          </TD>
          <TD>
            <para>Items that can be repeated one or more times</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>The format of a text file is:</para>
    <code>text-file ::=
   [delimited-header-line] [delimited-text-line]... end-of-file |
   [fixed-width-header-line] [fixed-width-text-line]... end-of-file
delimited-header-line ::= delimited-text-line
delimited-text-line ::=
   blank-line |
   delimited-data [delimiter delimited-data]... end-of-line
fixed-width-header-line ::= fixed-width-text-line
fixed-width-text-line ::=
   blank-line |
   fixed-width-data [fixed-width-data]... end-of-line
end-of-file ::= &lt;EOF&gt;
blank-line ::= end-of-line
delimited-data ::= delimited-string | number | date | delimited-null
fixed-width-data ::= fixed-width-string | number | date | fixed-width-null</code>
    <alert class="note">
      <para>The width of each column in a fixed-width text file is specified in the Schema.ini file.</para>
    </alert>
    <code>
<legacyItalic>end-of-line</legacyItalic> ::= &lt;CR&gt; | &lt;LF&gt; | &lt;CR&gt;&lt;LF&gt;
<legacyItalic>delimited-string</legacyItalic> ::= <legacyItalic>unquoted-string</legacyItalic> | <legacyItalic>quoted-string</legacyItalic>
<legacyItalic>unquoted-string</legacyItalic> ::= [<legacyItalic>character</legacyItalic> | <legacyItalic>digit</legacyItalic>] [<legacyItalic>character</legacyItalic> | <legacyItalic>digit</legacyItalic> | <legacyItalic>quote-character</legacyItalic>]...
<legacyItalic>quoted-string</legacyItalic> ::=
   <legacyItalic>quote-character</legacyItalic>
   [<legacyItalic>character</legacyItalic> | <legacyItalic>digit</legacyItalic> | <legacyItalic>delimiter</legacyItalic> | <legacyItalic>end-of-line</legacyItalic> | <legacyItalic>embedded-quoted-string</legacyItalic>]...
   <legacyItalic>quote-character</legacyItalic>
<legacyItalic>embedded-quoted-string ::=</legacyItalic>
<legacyItalic>   quote-characterquote-character</legacyItalic>
   [<legacyItalic>character</legacyItalic> | <legacyItalic>digit</legacyItalic> | <legacyItalic>delimiter</legacyItalic> | <legacyItalic>end-of-line</legacyItalic>]
   <legacyItalic>quote-characterquote-character</legacyItalic>
<legacyItalic>fixed-width-string</legacyItalic> ::= [<legacyItalic>character</legacyItalic> | <legacyItalic>digit</legacyItalic> | <legacyItalic>delimiter</legacyItalic> | <legacyItalic>quote-character</legacyItalic>] ...
<legacyItalic>character</legacyItalic> ::= any character except:
   <legacyItalic>delimiter</legacyItalic>
   <legacyItalic>digit</legacyItalic>
   <legacyItalic>end-of-file</legacyItalic>
   <legacyItalic>end-of-line</legacyItalic>
   <legacyItalic>quote-character</legacyItalic>
<legacyItalic>digit</legacyItalic> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
<legacyItalic>delimiter</legacyItalic> ::= , | &lt;TAB&gt; | 
<legacyItalic>custom-delimitercustom-delimiter</legacyItalic> ::= any character except:
   <legacyItalic>end-of-file</legacyItalic>
   <legacyItalic>end-of-line</legacyItalic>
   <legacyItalic>quote-character</legacyItalic></code>
    <alert class="note">
      <para>The delimiter in a custom-delimited text file is specified in the Schema.ini file.</para>
    </alert>
    <code>quote-character ::= "
number ::= exact-number | approximate-number
exact-number ::= [+ | -] {unsigned-integer[.unsigned-integer] |
   unsigned-integer. |
   .unsigned-integer}
approximate-number ::= exact-number{e | E}[+ | -]unsigned-integer
unsigned-integer ::= {digit}...
date ::=
   mm date-separator dd date-separator yy |
   mmm date-separator dd date-separator yy |
   dd date-separator mmm date-separator yy |
   yyyy date-separator mm date-separator dd |
   yyyy date-separator mmm date-separator dd
mm ::= digit [digit]
dd ::= digit [digit]
yy ::= digit digit
yyyy ::= digit digit digit digit
mmm ::= Jan | Feb | Mar | Apr | May | Jun | Jul | Aug | Sep | Oct | Nov | Dec
date-separator ::= - | / | .
delimited-null ::=</code>
    <alert class="note">
      <para>For delimited files, a NULL is represented by no data between two delimiters.</para>
    </alert>
    <code>fixed-width-null ::= &lt;SPACE&gt;...</code>
    <alert class="note">
      <para>For fixed-width files, a NULL is represented by spaces.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>