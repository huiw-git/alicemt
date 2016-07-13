---
title: Declaring the Application&#39;s ODBC Version
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 083a1ef5-580a-4979-9cf3-50f4549a080a
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Declaring the Application&#39;s ODBC Version
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Before an application allocates a connection, it must set the SQL_ATTR_ODBC_VERSION environment attribute. This attribute states that the application follows the ODBC 2.<legacyItalic>x</legacyItalic> or ODBC 3.<legacyItalic>x</legacyItalic> specification when using the following items:  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyBold>SQLSTATEs</legacyBold>. Many SQLSTATE values are different in ODBC 2.<legacyItalic>x</legacyItalic> and ODBC 3.<legacyItalic>x</legacyItalic>.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Date, Time, and Timestamp Type Identifiers</legacyBold>. The following table shows the type identifiers for date, time, and timestamp data in ODBC 2.<legacyItalic>x</legacyItalic> and ODBC 3.<legacyItalic>x</legacyItalic>.</para>
        <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
          <thead>
            <tr>
              <TD>
                <para>ODBC 2.<legacyItalic>x</legacyItalic></para>
              </TD>
              <TD>
                <para>ODBC 3.<legacyItalic>x</legacyItalic></para>
              </TD>
            </tr>
          </thead>
          <tbody>
            <tr>
              <TD>
                <para>                   <legacyBold>SQL Type Identifiers</legacyBold>                 </para>
              </TD>
              <TD>
                <para> </para>
              </TD>
            </tr>
            <tr>
              <TD>
                <para>     SQL_DATE</para>
              </TD>
              <TD>
                <para>SQL_TYPE_DATE</para>
              </TD>
            </tr>
            <tr>
              <TD>
                <para>     SQL_TIME</para>
              </TD>
              <TD>
                <para>SQL_TYPE_TIME</para>
              </TD>
            </tr>
            <tr>
              <TD>
                <para>     SQL_TIMESTAMP</para>
              </TD>
              <TD>
                <para>SQL_TYPE_TIMESTAMP</para>
              </TD>
            </tr>
            <tr>
              <TD>
                <para>                   <legacyBold>C Type Identifiers</legacyBold>                 </para>
              </TD>
              <TD>
                <para> </para>
              </TD>
            </tr>
            <tr>
              <TD>
                <para>     SQL_C_DATE</para>
              </TD>
              <TD>
                <para>SQL_C_TYPE_DATE</para>
              </TD>
            </tr>
            <tr>
              <TD>
                <para>     SQL_C_TIME</para>
              </TD>
              <TD>
                <para>SQL_C_TYPE_TIME</para>
              </TD>
            </tr>
            <tr>
              <TD>
                <para>     SQL_C_TIMESTAMP</para>
              </TD>
              <TD>
                <para>SQL_C_TYPE_TIMESTAMP</para>
              </TD>
            </tr>
          </tbody>
        </table>
      </listItem>
      <listItem>
        <para>             <legacyItalic>CatalogName</legacyItalic>             <legacyBold> Argument in SQLTables</legacyBold>. In ODBC 2.<legacyItalic>x</legacyItalic>, the wildcard characters ("%" and "_") in the <legacyItalic>CatalogName</legacyItalic> argument are treated literally. In ODBC 3.<legacyItalic>x</legacyItalic>, they are treated as wildcard characters. Thus, an application that follows the ODBC 2.<legacyItalic>x</legacyItalic> specification cannot use these as wildcard characters and does not escape them when using them as literals. An application that follows the ODBC 3.<legacyItalic>x</legacyItalic> specification can use these as wildcard characters or escape them and use them as literals. For more information, see <legacyLink xlink:href="f5e0abec-8f24-42e0-b94f-16dd1f2004fd">Arguments in Catalog Functions</legacyLink>.</para>
      </listItem>
    </list>
    <para>The ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager and ODBC 3<legacyItalic>.x</legacyItalic> drivers check the version of the ODBC specification to which an application is written and respond accordingly. For example, if the application follows the ODBC 2.<legacyItalic>x</legacyItalic> specification and calls <legacyBold>SQLExecute</legacyBold> before calling <legacyBold>SQLPrepare</legacyBold>, the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager returns SQLSTATE S1010 (Function sequence error). If the application follows the ODBC 3<legacyItalic>.x</legacyItalic> specification, the Driver Manager returns SQLSTATE HY010 (Function sequence error). For more information, see <legacyLink xlink:href="b5eee7be-28ed-4467-8cf1-2205e2010a53">Backward Compatibility and Standards Compliance</legacyLink>.</para>
    <alert class="important">
      <para>Applications that follow the ODBC 3.<legacyItalic>x</legacyItalic> specification must use conditional code to avoid using functionality new to ODBC 3.<legacyItalic>x</legacyItalic> when working with ODBC 2.<legacyItalic>x</legacyItalic> drivers. ODBC 2.<legacyItalic>x</legacyItalic> drivers do not support functionality new to ODBC 3.<legacyItalic>x</legacyItalic> just because the application declares that it follows the ODBC 3.<legacyItalic>x</legacyItalic> specification. Furthermore, ODBC 3.<legacyItalic>x</legacyItalic> drivers do not cease to support functionality new to ODBC 3.<legacyItalic>x</legacyItalic> just because the application declares that it follows the ODBC 2.<legacyItalic>x</legacyItalic> specification.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>