---
title: Schema.ini File (Text File Driver)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0c4625c4-c730-4984-b430-9051b7bc0451
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Schema.ini File (Text File Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When the Text driver is used, the format of the text file is determined by using a schema information file. The schema information file is always named Schema.ini and always kept in the same directory as the text data source. The schema information file provides the IISAM with information about the general format of the file, the column name and data type information, and several other data characteristics. A Schema.ini file is always required for accessing fixed-length data. You should use a Schema.ini file when your text table contains DateTime, Currency, or Decimal data, or any time that you want more control over the handling of the data in the table.</para>
    <alert class="note">
      <para>The Text ISAM will obtain initial values from the registry, not from Schema.ini. The same default file format applies to all new text data tables. All files that were created by the CREATE TABLE statement inherit those same default format values, which are set by selecting file format values in the <legacyBold>Define Text Format</legacyBold> dialog box with &lt;default&gt; chosen in the <legacyBold>Tables</legacyBold> list. If the values in the registry differ from the values in Schema.ini, the values in the registry will be overwritten by the values from Schema.ini.</para>
    </alert>
  </introduction>
  <section>
    <title>Understanding Schema.ini Files</title>
    <content>
      <para>Schema.ini files provide schema information about the records in a text file. Each Schema.ini entry specifies one of five characteristics of the table:  </para>
      <list class="bullet">
        <listItem>
          <para>The text file name</para>
        </listItem>
        <listItem>
          <para>The file format</para>
        </listItem>
        <listItem>
          <para>The field names, widths, and types</para>
        </listItem>
        <listItem>
          <para>The character set</para>
        </listItem>
        <listItem>
          <para>Special data type conversions</para>
        </listItem>
      </list>
      <para>The following sections discuss these characteristics.</para>
    </content>
  </section>
  <section>
    <title>Specifying the File Name</title>
    <content>
      <para>The first entry in Schema.ini is always the name of the text source file enclosed in square brackets. The following example illustrates the entry for the file Sample.txt:</para>
      <code>[Sample.txt]</code>
    </content>
  </section>
  <section>
    <title>Specifying the File Format</title>
    <content>
      <para>The <legacyBold>Format</legacyBold> option in Schema.ini specifies the format of the text file. The Text IISAM can read the format automatically from most character-delimited files. You can use any single character as a delimiter in the file except the double quotation mark ("). The <legacyBold>Format</legacyBold> setting in Schema.ini overrides the setting in the Windows Registry, file by file. The following table lists the valid values for the <legacyBold>Format</legacyBold> option.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Format specifier</para>
            </TD>
            <TD>
              <para>Table format</para>
            </TD>
            <TD>
              <para>Schema.ini Format statement</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>               <legacyBold>Tab Delimited</legacyBold>             </para>
            </TD>
            <TD>
              <para>Fields in the file are delimited by tabs.</para>
            </TD>
            <TD>
              <para>Format=TabDelimited</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>CSV Delimited</legacyBold>             </para>
            </TD>
            <TD>
              <para>Fields in the file are delimited by commas (comma-separated values).</para>
            </TD>
            <TD>
              <para>Format=CSVDelimited</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Custom Delimited</legacyBold>             </para>
            </TD>
            <TD>
              <para>Fields in the file are delimited by any character you choose to input into the dialog box. All except the double quotation marks (") are allowed, including blank.</para>
            </TD>
            <TD>
              <para>Format=Delimited(<legacyItalic>custom character</legacyItalic>)</para>
              <para>-or-</para>
              <para>With no delimiter specified:</para>
              <para>Format=Delimited( )</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Fixed Length</legacyBold>             </para>
            </TD>
            <TD>
              <para>Fields in the file are of a fixed length.</para>
            </TD>
            <TD>
              <para>Format=FixedLength</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Specifying the Fields</title>
    <content>
      <para>You can specify field names in a character-delimited text file in two ways:   </para>
      <list class="bullet">
        <listItem>
          <para>Include the field names in the first row of the table and set <legacyBold>ColNameHeader</legacyBold> to <legacyBold>True.</legacyBold></para>
        </listItem>
        <listItem>
          <para>Specify each column by number and designate the column name and data type. </para>
        </listItem>
      </list>
      <para>You must specify each column by number and designate the column name, data type, and width for fixed-length files.</para>
      <alert class="note">
        <para>The <legacyBold>ColNameHeader</legacyBold> setting in Schema.ini overrides the <legacyBold>FirstRowHasNames</legacyBold> setting in the Windows Registry, file by file.</para>
      </alert>
      <para>The data types of the fields can also be determined. Use the <legacyBold>MaxScanRows</legacyBold> option to indicate how many rows should be scanned when determining the column types. If you set <legacyBold>MaxScanRows</legacyBold> to 0, the whole file is scanned. The <legacyBold>MaxScanRows</legacyBold> setting in Schema.ini overrides the setting in the Windows Registry, file by file.</para>
      <para>The following entry indicates that Microsoft Jet should use the data in the first row of the table to determine field names and should examine the whole file to determine the data types used:</para>
      <code>ColNameHeader=True
MaxScanRows=0</code>
      <para>The next entry designates fields in a table by using the column number (<legacyBold>Col</legacyBold><legacyItalic>n</legacyItalic>) option, which is optional for character-delimited files and required for fixed-length files. The example shows the Schema.ini entries for two fields, a 10-character CustomerNumber text field and a 30-character CustomerName text field:</para>
      <code>Col1=CustomerNumber Text Width 10
Col2=CustomerName Text Width 30</code>
      <para>The syntax of <legacyBold>Col</legacyBold><legacyItalic>n</legacyItalic> is:</para>
      <code>
        
        <legacyItalic>n</legacyItalic>=<legacyItalic>ColumnNametype</legacyItalic> [<legacyItalic>#</legacyItalic>]</code>
    </content>
  </section>
  <section>
    <title>Remarks</title>
    <content>
      <para>The following table describes each part of the <legacyBold>Col</legacyBold><legacyItalic>n</legacyItalic> entry.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Parameter</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>               <legacyItalic>ColumnName</legacyItalic>             </para>
            </TD>
            <TD>
              <para>The text name of the column. If the column name contains embedded spaces, you must enclose it in double quotation marks.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyItalic>type</legacyItalic>             </para>
            </TD>
            <TD>
              <para>Data types are as follows:</para>
              <para>
                <legacyBold>Microsoft Jet data types</legacyBold> </para>
              <para>Bit</para>
              <para>Byte</para>
              <para>Short</para>
              <para>Long</para>
              <para>Currency</para>
              <para>Single</para>
              <para>Double</para>
              <para>DateTime</para>
              <para>Text</para>
              <para>Memo</para>
              <para>
                <legacyBold>ODBC data types</legacyBold> Char (same as Text)</para>
              <para>Float (same as Double)</para>
              <para>Integer (same as Short)</para>
              <para>LongChar (same as Memo)</para>
              <para>Date <legacyItalic>date format</legacyItalic></para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Width</legacyBold>             </para>
            </TD>
            <TD>
              <para>The literal string value <codeInline>Width</codeInline>. Indicates that the following number designates the width of the column (optional for character-delimited files; required for fixed-length files).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyItalic>#</legacyItalic>             </para>
            </TD>
            <TD>
              <para>The integer value that designates the width of the column (required if <legacyBold>Width</legacyBold> is specified).</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Selecting a Character Set</title>
    <content>
      <para>You can select from two character sets: ANSI and OEM. The <legacyBold>CharacterSet</legacyBold> setting in Schema.ini overrides the setting in the Windows Registry, file by file. The following example shows the Schema.ini entry that sets the character set to ANSI:</para>
      <code>CharacterSet=ANSI</code>
    </content>
  </section>
  <section>
    <title>Specifying Data Type Formats and Conversions</title>
    <content>
      <para>The Schema.ini file contains several options that you can use to specify how data is converted or displayed. The following table lists each of these options.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Option</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>               <legacyBold>DateTimeFormat</legacyBold>             </para>
            </TD>
            <TD>
              <para>Can be set to a format string that indicates dates and times. You should specify this entry if all date/time fields in the import/export are handled with the same format. All Microsoft Jet formats except A.M. and P.M. are supported. If there is no format string, the Windows Control Panel short date picture and time options are used.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>DecimalSymbol</legacyBold>             </para>
            </TD>
            <TD>
              <para>Can be set to any single character that is used to separate the integer from the fractional part of a number. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>NumberDigits</legacyBold>             </para>
            </TD>
            <TD>
              <para>Indicates the number of decimal digits in the fractional portion of a number. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>NumberLeadingZeros</legacyBold>             </para>
            </TD>
            <TD>
              <para>Specifies whether a decimal value less than 1 and more than –1 should contain leading zeros; this value can be either False (no leading zeros) or True. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>CurrencySymbol</legacyBold>             </para>
            </TD>
            <TD>
              <para>Indicates the currency symbol that can be used for currency values in the text file. Examples include the dollar sign ($) and Dm.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>CurrencyPosFormat</legacyBold>             </para>
            </TD>
            <TD>
              <para>Can be set to any of the following values:</para>
              <list class="bullet">
                <listItem>
                  <para>Currency symbol prefix with no separation ($1)</para>
                </listItem>
                <listItem>
                  <para>Currency symbol suffix with no separation (1$)</para>
                </listItem>
                <listItem>
                  <para>Currency symbol prefix with one character separation ($ 1)</para>
                </listItem>
                <listItem>
                  <para>Currency symbol suffix with one character separation (1 $)</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>CurrencyDigits</legacyBold>             </para>
            </TD>
            <TD>
              <para>Specifies the number of digits used for the fractional part of a currency amount. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>CurrencyNegFormat</legacyBold>             </para>
            </TD>
            <TD>
              <para>Can be one of the following values:</para>
              <list class="bullet">
                <listItem>
                  <para>($1)</para>
                </listItem>
                <listItem>
                  <para>–$1</para>
                </listItem>
                <listItem>
                  <para>$–1</para>
                </listItem>
                <listItem>
                  <para>$1–</para>
                </listItem>
                <listItem>
                  <para>(1$)</para>
                </listItem>
                <listItem>
                  <para>–1$</para>
                </listItem>
                <listItem>
                  <para>1–$</para>
                </listItem>
                <listItem>
                  <para>1$–</para>
                </listItem>
                <listItem>
                  <para>–1 $</para>
                </listItem>
                <listItem>
                  <para>–$ 1</para>
                </listItem>
                <listItem>
                  <para>1 $–</para>
                </listItem>
                <listItem>
                  <para>$ 1–</para>
                </listItem>
                <listItem>
                  <para>$ –1</para>
                </listItem>
                <listItem>
                  <para>1– $</para>
                </listItem>
                <listItem>
                  <para>($ 1) </para>
                </listItem>
                <listItem>
                  <para>(1 $)</para>
                </listItem>
              </list>
              <para>This example shows the dollar sign, but you should replace it with the appropriate <legacyBold>CurrencySymbol</legacyBold> value in the actual program. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>CurrencyThousandSymbol</legacyBold>             </para>
            </TD>
            <TD>
              <para>Indicates the single-character symbol that can be used for separating currency values in the text file by thousands.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>CurrencyDecimalSymbol</legacyBold>             </para>
            </TD>
            <TD>
              <para>Can be set to any single character that is used to separate the whole from the fractional part of a currency amount. </para>
            </TD>
          </tr>
        </tbody>
      </table>
      <alert class="note">
        <para>If you omit an entry, the default value in the Windows Control Panel is used.</para>
      </alert>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>