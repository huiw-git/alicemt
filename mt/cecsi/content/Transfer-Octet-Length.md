---
title: Transfer Octet Length
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9fdc9762-e203-4cff-9212-54f450bf18d9
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Transfer Octet Length
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The transfer octet length of a column is the maximum number of bytes returned to the application when data is transferred to its default C data type. For character data, the transfer octet length does not include space for the null-termination character. The transfer octet length of a column may be different than the number of bytes required to store the data on the data source.</para>
  </introduction>
  <section>
    <content>
      <para>The transfer octet length defined for each ODBC SQL data type is shown in the following table.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>SQL type identifier</para>
            </TD>
            <TD>
              <para>Length</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>All character types[a]</para>
            </TD>
            <TD>
              <para>The defined or the maximum (for variable type) length of the column in bytes. This is the same value as the descriptor field SQL_DESC_OCTET_LENGTH.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DECIMAL
SQL_NUMERIC</para>
            </TD>
            <TD>
              <para>The number of bytes required to hold the character representation of this data if the character set is ANSI, and twice this number if the character set is UNICODE. This is the maximum number of digits plus two, because the data is returned as a character string and characters are needed for the digits, a sign, and a decimal point. For example, the transfer length of a column defined as NUMERIC(10,3) is 12.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_TINYINT</para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_SMALLINT</para>
            </TD>
            <TD>
              <para>2</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_INTEGER</para>
            </TD>
            <TD>
              <para>4</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_BIGINT</para>
            </TD>
            <TD>
              <para>The number of bytes required to hold the character representation of this data if the character set is ANSI, and twice this number if the character set is UNICODE, because this data type is returned as a character string by default. The character representation consists of 20 characters: 19 for digits and a sign, if signed, or 20 digits, if unsigned. Therefore, the length is 20.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_REAL</para>
            </TD>
            <TD>
              <para>4</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_FLOAT</para>
            </TD>
            <TD>
              <para>8</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DOUBLE</para>
            </TD>
            <TD>
              <para>8</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_BIT</para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>All binary types[a]</para>
            </TD>
            <TD>
              <para>The number of bytes required to hold the defined (for fixed types) or maximum (for variable types) number of characters.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_TYPE_DATE
SQL_TYPE_TIME</para>
            </TD>
            <TD>
              <para>6 (the size of the SQL_DATE_STRUCT or SQL_TIME_STRUCT structure).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_TYPE_TIMESTAMP</para>
            </TD>
            <TD>
              <para>16 (the size of the SQL_TIMESTAMP_STRUCT structure).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>All interval data types</para>
            </TD>
            <TD>
              <para>34 (the size of the interval structure).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_GUID</para>
            </TD>
            <TD>
              <para>16 (the size of the GUID structure).</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[a]   If the driver cannot determine the column or parameter length for variable types, it returns SQL_NO_TOTAL.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>