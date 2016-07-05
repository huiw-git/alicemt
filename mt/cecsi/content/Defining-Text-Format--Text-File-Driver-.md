---
title: Defining Text Format (Text File Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3af46dad-52cc-4d5c-a27e-6315d65a74e6
translation.priority.ht: 
  - en-gb
---
# Defining Text Format (Text File Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When the Text driver is used, you can use the <legacyBold>Define Text Format</legacyBold> dialog box to define the format for columns in a selected file. This dialog box enables you to specify the schema for each data table. This information is written to a Schema.ini file in the data source directory. A separate Schema.ini file is created for each text data source directory.</para>
    <alert class="note">
      <para>The same default file format applies to all new text data tables. All files created by the CREATE TABLE statement inherit those same default format values, which are set by selecting file format values in the <legacyBold>Define Text Format</legacyBold> dialog box with &lt;default&gt; chosen in the <legacyBold>Tables</legacyBold> list. The Text driver does not change the format of an existing text file to match the format defined in this dialog box, but returns an error when it uses the format, such as when it attempts to retrieve data from the text file. </para>
    </alert>
    <para>The following options are available in the <legacyBold>Define Text Format</legacyBold> dialog box:</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Option</para>
          </TD>
          <TD>
            <para>Information</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>               <legacyBold>Add</legacyBold>             </para>
          </TD>
          <TD>
            <para>Adds a column using the values in <legacyBold>Data Type</legacyBold>, <legacyBold>Name</legacyBold>, and <legacyBold>Width</legacyBold> from the dialog box, and if applicable, the Date Separator value from Schema.ini.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Characters</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>ANSI</legacyBold> or <legacyBold>OEM</legacyBold>. OEM specifies a non-ANSI character set. This defaults to OEM if the format of the item selected in the <legacyBold>Tables</legacyBold> list has not been previously defined by this dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Column Name Header</legacyBold>             </para>
          </TD>
          <TD>
            <para>Indicates whether the columns of the first row of the selected table are to be used as column names. Either <legacyBold>TRUE</legacyBold> or <legacyBold>FALSE</legacyBold>. Defaults to FALSE if the format of the item selected in the <legacyBold>Tables</legacyBold> list has not been previously defined by this dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Columns</legacyBold>             </para>
          </TD>
          <TD>
            <para>Lists the column names for each column in the selected table. The order of the columns reflects the order of the columns in the table. This list is enabled if a file has been selected in the <legacyBold>Tables</legacyBold> list.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Data Type</legacyBold>             </para>
          </TD>
          <TD>
            <para>Can be BIT, BYTE, CHAR, CURRENCY, DATE, FLOAT, INTEGER, LONGCHAR, SHORT, or SINGLE. Date data types can be in the following formats: "dd-mmm-yy", "mm-dd-yy", "mmm-dd-yy", "yyyy-mm-dd", or "yyyy-mmm-dd". "mm" denotes numbers for months; "mmm" denotes letters for months.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Delimiter</legacyBold>             </para>
          </TD>
          <TD>
            <para>Specifies the custom delimiter character to be used to separate columns. Enabled when the <legacyBold>Custom Delimited</legacyBold> format is selected. The delimiter can be only one character in length, and double quotation marks (") cannot be used as the delimiter character. (The delimiter cannot be specified in hexadecimal or decimal format.)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Format</legacyBold>             </para>
          </TD>
          <TD>
            <para>Either delimited or fixed length. If delimited, indicates the type of delimiter used: comma (CSV), tab, or special character (custom). This defaults to <legacyBold>CSV Delimited</legacyBold> if the format of the item selected in the <legacyBold>Tables</legacyBold> list has not been previously defined by this dialog box.</para>
            <para>If <legacyBold>Format</legacyBold> is fixed-length and <legacyBold>Column Name Header</legacyBold> is TRUE, the first line must be comma-delimited.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Guess</legacyBold>             </para>
          </TD>
          <TD>
            <para>Automatically generates the column's data type, name, and width values for the columns in the selected table by scanning the table's contents according to the <legacyBold>Format</legacyBold> box selection. Enabled when the table format is delimited. Any previously defined columns in the <legacyBold>Columns</legacyBold> list are cleared and replaced with new entries. If <legacyBold>Column Name Header</legacyBold> is not selected, column names are generated automatically as "F1", "F2", and so on. No default value is shown in the <legacyBold>Data Type</legacyBold> box.</para>
            <para>This functionality works only on columns that are less than 64,513 bytes.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Modify</legacyBold>             </para>
          </TD>
          <TD>
            <para>Modifies the selected column using the values in <legacyBold>Data</legacyBold> <legacyBold>Type</legacyBold>, <legacyBold>Name</legacyBold>, and <legacyBold>Width</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Name</legacyBold>             </para>
          </TD>
          <TD>
            <para>Displays the name of the selected column. Can be used to specify a new column name for either an existing column or a new column.</para>
            <para>If <legacyBold>Column Name Header</legacyBold> is TRUE, the column name displayed is ignored.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Remove</legacyBold>             </para>
          </TD>
          <TD>
            <para>Deletes the selected column.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Rows to Scan</legacyBold>             </para>
          </TD>
          <TD>
            <para>The number of rows that Setup or the driver will scan when setting the columns and column data types based upon existing data.</para>
            <para>You can enter a number from 1 to 32767 for the number of rows to scan. This defaults to 25 if the format of the item selected in the <legacyBold>Tables</legacyBold> list has not been previously defined by this dialog box. (A number outside the limit will return an error.)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Tables</legacyBold>             </para>
          </TD>
          <TD>
            <para>Contains a list of all files in the directory selected in the <legacyBold>Text</legacyBold> <legacyBold>Setup</legacyBold> dialog box that match the list of extensions specified.</para>
            <para>When &lt;default&gt; is selected, and one of the following is true, the values of the table attributes in the <legacyBold>Tables</legacyBold> group are written to Schema.ini (no other entries in Schema.ini are touched):  </para>
            <list class="bullet">
              <listItem>
                <para>There is no Schema.ini in the specified directory.</para>
              </listItem>
              <listItem>
                <para>The Schema.ini file exists, but there is no section in Schema.ini for one of the Text files (with the specified extension) in the directory.</para>
              </listItem>
              <listItem>
                <para>The section for a Text file exists in Schema.ini, but the body is empty.</para>
              </listItem>
            </list>
            <para>When &lt;default&gt; is selected, the <legacyBold>Columns</legacyBold> group is disabled.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Width</legacyBold>             </para>
          </TD>
          <TD>
            <para>The width of the column can be changed for CHAR or LONGCHAR columns. The width defaults to 1 if the format of the item selected in the <legacyBold>Tables</legacyBold> list has not been previously defined by this dialog box.</para>
            <para>For other data types, the width control is disabled and no value is displayed.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>