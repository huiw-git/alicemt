---
title: Converting Data from SQL to C Data Types
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 029727f6-d3f0-499a-911c-bcaf9714e43b
translation.priority.ht: 
  - en-gb
---
# Converting Data from SQL to C Data Types
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an application calls <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLGetData</legacyBold>, the driver retrieves the data from the data source. If necessary, it converts the data from the data type in which the driver retrieved it to the data type specified by the <legacyItalic>TargetType</legacyItalic> argument in <legacyBold>SQLBindCol</legacyBold> or <legacyBold>SQLGetData.</legacyBold> Finally, it stores the data in the location pointed to by the <legacyItalic>TargetValuePtr</legacyItalic> argument in <legacyBold>SQLBindCol</legacyBold> or <legacyBold>SQLGetData</legacyBold> (and the SQL_DESC_DATA_PTR field of the ARD).</para>
    <para>The following table shows the supported conversions from ODBC SQL data types to ODBC C data types. A filled circle indicates the default conversion for an SQL data type (the C data type to which the data will be converted when the value of <legacyItalic>TargetType</legacyItalic> is SQL_C_DEFAULT). A hollow circle indicates a supported conversion.</para>
    <para>For an ODBC 3<legacyItalic>.x</legacyItalic> application working with an ODBC 2.<legacyItalic>x</legacyItalic> driver, conversion from driver-specific data types might not be supported.</para>
    <para>The format of the converted data is not affected by the Windows® country setting.</para>
    <para>The tables in the following sections describe how the driver or data source converts data retrieved from the data source; drivers are required to support conversions to all ODBC C data types from the ODBC SQL data types that they support. For a given ODBC SQL data type, the first column of the table lists the legal input values of the <legacyItalic>TargetType</legacyItalic> argument in <legacyBold>SQLBindCol</legacyBold> and <legacyBold>SQLGetData</legacyBold>. The second column lists the outcomes of a test, often using the <legacyItalic>BufferLength</legacyItalic> argument specified in <legacyBold>SQLBindCol</legacyBold> or <legacyBold>SQLGetData</legacyBold>, which the driver performs to determine whether it can convert the data. For each outcome, the third and fourth columns list the values placed in the buffers specified by the <legacyItalic>TargetValuePtr</legacyItalic> and <legacyItalic>StrLen_or_IndPtr</legacyItalic> arguments specified in <legacyBold>SQLBindCol</legacyBold> or <legacyBold>SQLGetData</legacyBold> after the driver has attempted to convert the data. (The <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument corresponds to the SQL_DESC_OCTET_LENGTH_PTR field of the ARD.) The last column lists the SQLSTATE returned for each outcome by <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLGetData</legacyBold>.</para>
    <para>If the <legacyItalic>TargetType</legacyItalic> argument in <legacyBold>SQLBindCol</legacyBold> or <legacyBold>SQLGetData</legacyBold> contains an identifier for an ODBC C data type not shown in the table for a given ODBC SQL data type, <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLGetData</legacyBold> returns SQLSTATE 07006 (Restricted data type attribute violation). If the <legacyItalic>TargetType</legacyItalic> argument contains an identifier that specifies a conversion from a driver-specific SQL data type to an ODBC C data type and this conversion is not supported by the driver, <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLGetData</legacyBold> returns SQLSTATE HYC00 (Optional feature not implemented).</para>
    <para>Although it is not shown in the tables, the driver returns SQL_NULL_DATA in the buffer specified by the <legacyItalic>StrLen_or_IndPtr </legacyItalic>argument when the SQL data value is NULL. For an explanation of the use of <legacyItalic>StrLen_or_IndPtr </legacyItalic>when multiple calls are made to retrieve data, see the <legacyLink xlink:href="e3c1356a-5db7-4186-85fd-8b74633317e8">SQLGetData</legacyLink>function description. When SQL data is converted to character C data, the character count returned in *<legacyItalic>StrLen_or_IndPtr </legacyItalic>does not include the null-termination byte. If <legacyItalic>TargetValuePtr</legacyItalic> is a null pointer, <legacyBold>SQLGetData</legacyBold> returns SQLSTATE HY009 (Invalid use of null pointer); in <legacyBold>SQLBindCol</legacyBold>, this unbinds the column.</para>
    <para>The following terms and conventions are used in the tables:  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyBold>Byte length of data</legacyBold> is the number of bytes of C data available to return in *<legacyItalic>TargetValuePtr</legacyItalic>, whether or not the data will be truncated before it is returned to the application. For string data, this does not include the space for the null-termination character.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Character byte length</legacyBold> is the total number of bytes needed to display the data in character format. This is as defined for each C data type in the section <legacyLink xlink:href="9f7f766f-2492-463c-aab7-f2476e222042">Display Size</legacyLink>, except that character byte length is in bytes while the display size is in characters.</para>
      </listItem>
      <listItem>
        <para>Words in <legacyItalic>italics</legacyItalic> represent function arguments or elements of the SQL grammar. For the syntax of grammar elements, see <legacyLink xlink:href="0ee36f09-59e7-4b94-88ca-7ebc0952a3be">Appendix C: SQL Grammar</legacyLink>.</para>
      </listItem>
    </list>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="7fdb7f38-b64d-48f2-bcb4-1ca96b2bbdb6">SQL to C: Character</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="76f8b5d5-4bd0-4dcb-a90a-698340e0d36e">SQL to C: Numeric</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="0eeaab8b-ad82-4a36-b464-9a1211d5f72c">SQL to C: Bit</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="8c519072-ae4c-4d32-9d4e-775e3d3d6389">SQL to C: Binary</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="703c7960-9cf4-4d7a-9920-53b29c184f97">SQL to C: Date</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="cf56c684-c261-4b89-994a-db14ab2241d6">SQL to C: GUID</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="6dc59973-7bb5-40f1-87c8-5bf68b3bf2ee">SQL to C: Time</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="6a0617cf-d8c0-4316-8bb4-e6ddb45d7bf1">SQL to C: Timestamp</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="1233634b-8214-420f-b872-3b2630105ba4">SQL to C: Year-Month Intervals</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="8ea84d69-2292-4128-89a0-f184f68abb98">SQL to C: Day-Time Intervals</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="0190c76c-7f9b-42f4-be9d-cef7284840fd">SQL to C Data Conversion Examples</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>