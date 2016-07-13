---
title: Setting Parameter Values
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 13e5da79-b60c-48d0-b467-773f481ef2a4
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Setting Parameter Values
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>To set the value of a parameter, the application simply sets the value of the variable bound to the parameter. It is not important when this value is set, as long as it is set before the statement is executed. The application can set the value before or after binding the variable, and it can change the value as many times as it wants. When the statement is executed, the driver simply retrieves the current value of the variable. This is particularly useful when a prepared statement is executed more than once; the application sets new values for some or all of the variables each time the statement is executed. For an example of this, see <legacyLink xlink:href="f08c8a98-31ee-48b2-9dbf-6f31c2166dbb">Prepared Execution</legacyLink>, earlier in this section.</para>
    <para>If a length/indicator buffer was bound in the call to <legacyBold>SQLBindParameter</legacyBold>, it must be set to one of the following values before the statement is executed:  </para>
    <list class="bullet">
      <listItem>
        <para>The byte length of the data in the bound variable. The driver checks this length only if the variable is character or binary (<legacyItalic>ValueType</legacyItalic> is SQL_C_CHAR or SQL_C_BINARY).</para>
      </listItem>
      <listItem>
        <para>SQL_NTS. The data is a null-terminated string.</para>
      </listItem>
      <listItem>
        <para>SQL_NULL_DATA. The data value is NULL, and the driver ignores the value of the bound variable.</para>
      </listItem>
      <listItem>
        <para>SQL_DATA_AT_EXEC or the result of the SQL_LEN_DATA_AT_EXEC macro. The value of the parameter is to be sent with <legacyBold>SQLPutData</legacyBold>. For more information, see <legacyLink xlink:href="ea989084-a8e6-4737-892e-9ec99dd49caf">Sending Long Data</legacyLink>, later in this section.</para>
      </listItem>
    </list>
    <para>The following table shows the values of the bound variable and the length/indicator buffer that the application sets for a variety of parameter values.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Parameter</para>
            <para>value</para>
          </TD>
          <TD>
            <para>Parameter</para>
            <para>(SQL) </para>
            <para>data type</para>
          </TD>
          <TD>
            <para>Variable (C)</para>
            <para>data type</para>
          </TD>
          <TD>
            <para>Value in</para>
            <para>bound</para>
            <para>variable</para>
          </TD>
          <TD>
            <para>Value in</para>
            <para>length/indicator</para>
            <para>buffer[d]</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>"ABC"</para>
          </TD>
          <TD>
            <para>SQL_CHAR</para>
          </TD>
          <TD>
            <para>SQL_C_CHAR</para>
          </TD>
          <TD>
            <para>ABC\0[a]</para>
          </TD>
          <TD>
            <para>SQL_NTS or 3</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>10</para>
          </TD>
          <TD>
            <para>SQL_INTEGER</para>
          </TD>
          <TD>
            <para>SQL_C_SLONG</para>
          </TD>
          <TD>
            <para>10</para>
          </TD>
          <TD>
            <para>--</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>10</para>
          </TD>
          <TD>
            <para>SQL_INTEGER</para>
          </TD>
          <TD>
            <para>SQL_C_CHAR</para>
          </TD>
          <TD>
            <para>10\0[a]</para>
          </TD>
          <TD>
            <para>SQL_NTS or 2</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>1 P.M.</para>
          </TD>
          <TD>
            <para>SQL_TYPE_TIME</para>
          </TD>
          <TD>
            <para>SQL_C_TYPE_TIME</para>
          </TD>
          <TD>
            <para>13,0,0[b]</para>
          </TD>
          <TD>
            <para>--</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>1 P.M.</para>
          </TD>
          <TD>
            <para>SQL_TYPE_TIME</para>
          </TD>
          <TD>
            <para>SQL_C_CHAR</para>
          </TD>
          <TD>
            <para>{t '13:00:00'}\0[a], [c]</para>
          </TD>
          <TD>
            <para>SQL_NTS or 14</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>NULL</para>
          </TD>
          <TD>
            <para>SQL_SMALLINT</para>
          </TD>
          <TD>
            <para>SQL_C_SSHORT</para>
          </TD>
          <TD>
            <para>--</para>
          </TD>
          <TD>
            <para>SQL_NULL_DATA</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[a]   "\0" represents a null-termination character. The null-termination character is required only if the value in the length/indicator buffer is SQL_NTS.</para>
    <para>[b]   The numbers in this list are the numbers stored in the fields of the TIME_STRUCT structure.</para>
    <para>[c]   The string uses the ODBC date escape clause. For more information, see <legacyLink xlink:href="2b42a52a-6353-494c-a179-3a7533cd729f">Date, Time, and Timestamp Literals</legacyLink>.</para>
    <para>[d]   Drivers must always check this value to see whether it is a special value, such as SQL_NULL_DATA.</para>
    <para>What a driver does with a parameter value at execution time is driver-dependent. If necessary, the driver converts the value from the C data type and byte length of the bound variable to the SQL data type, precision, and scale of the parameter. In most cases, the driver then sends the value to the data source. In some cases, it formats the value as text and inserts it into the SQL statement before sending the statement to the data source.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>