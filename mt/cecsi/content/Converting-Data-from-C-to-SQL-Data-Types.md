---
title: "Converting Data from C to SQL Data Types"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ee0afe78-b58f-4d34-ad9b-616bb23653bd
caps.latest.revision: 8
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Converting Data from C to SQL Data Types
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an application calls <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold>, the driver retrieves the data for any parameters bound with <legacyBold>SQLBindParameter</legacyBold> from storage locations in the application. When an application calls <legacyBold>SQLSetPos</legacyBold>, the driver retrieves the data for an update or add operation from columns bound with <legacyBold>SQLBindCol</legacyBold>. For data-at-execution parameters, the application sends the parameter data with <legacyBold>SQLPutData</legacyBold>. If necessary, the driver converts the data from the data type specified by the <legacyItalic>ValueType</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold> to the data type specified by the <legacyItalic>ParameterType</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>,and then sends the data to the data source.</para>
    <para>The following table shows the supported conversions from ODBC C data types to ODBC SQL data types. A filled circle indicates the default conversion for an SQL data type (the C data type from which the data will be converted when the value of <legacyItalic>ValueType</legacyItalic> or the SQL_DESC_CONCISE_TYPE descriptor field is SQL_C_DEFAULT). A hollow circle indicates a supported conversion.</para>
    <para>The format of the converted data is not affected by the Windows® country setting.</para>
    <mediaLink>
      <image xlink:href="9b2cdbae-5a9d-44cf-881f-8cbd8932c131" />
    </mediaLink>
    <para>The tables in the following sections describe how the driver or data source converts data sent to the data source; drivers are required to support conversions from all ODBC C data types to the ODBC SQL data types that they support. For a given ODBC C data type, the first column of the table lists the legal input values of the <legacyItalic>ParameterType</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>. The second column lists the outcomes of a test that the driver performs to determine if it can convert the data. The third column lists the SQLSTATE returned for each outcome by <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, <legacyBold>SQLSetPos</legacyBold>, or <legacyBold>SQLPutData</legacyBold>. Data is sent to the data source only if SQL_SUCCESS is returned.</para>
    <para>If the <legacyItalic>ParameterType</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold> contains the identifier of an ODBC SQL data type that is not shown in the table for a given C data type, <legacyBold>SQLBindParameter</legacyBold> returns SQLSTATE 07006 (Restricted data type attribute violation). If the <legacyItalic>ParameterType</legacyItalic> argument contains a driver-specific identifier and the driver does not support the conversion from the specific ODBC C data type to that driver-specific SQL data type, <legacyBold>SQLBindParameter</legacyBold> returns SQLSTATE HYC00 (Optional feature not implemented).</para>
    <para>If the <legacyItalic>ParameterValuePtr</legacyItalic> and <legacyItalic>StrLen_or_IndPtr</legacyItalic> arguments specified in <legacyBold>SQLBindParameter</legacyBold> are both null pointers, that function returns SQLSTATE HY009 (Invalid use of null pointer). Although it is not shown in the tables, an application sets the value of the length/indicator buffer pointed to by the <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument of <legacyBold>SQLBindParameter</legacyBold> or the value of the <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument of <legacyBold>SQLPutData</legacyBold> to SQL_NULL_DATA to specify a NULL SQL data value. (The <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument corresponds to the SQL_DESC_OCTET_LENGTH_PTR field of the APD.) The application sets these values to SQL_NTS to specify that the value in *<legacyItalic>ParameterValuePtr</legacyItalic> in <legacyBold>SQLBindParameter</legacyBold> or *<legacyItalic>DataPtr</legacyItalic> in <legacyBold>SQLPutData</legacyBold> (pointed to by the SQL_DESC_DATA_PTR field of the APD) is a null-terminated string.</para>
    <para>The following terms are used in the tables:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>Byte length of data</legacyBold> — Number of bytes of SQL data available to send to the data source, whether or not the data will be truncated before it is sent to the data source. For string data, this does not include space for the null-termination character.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Column byte length</legacyBold> — Number of bytes required to store the data at the data source.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Character byte length</legacyBold> — Maximum number of bytes needed to display data in character form. This is as defined for each SQL data type in <legacyLink xlink:href="9f7f766f-2492-463c-aab7-f2476e222042">Display Size</legacyLink>, except character byte length is in bytes, while the display size is in characters.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Number of digits</legacyBold> — Number of characters used to represent a number, including the minus sign, decimal point, and exponent (if needed).</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Words in </legacyBold>
          <legacyBold>
            <legacyItalic>italics</legacyItalic>
          </legacyBold> — Elements of the SQL grammar. For the syntax of grammar elements, see <legacyLink xlink:href="0ee36f09-59e7-4b94-88ca-7ebc0952a3be">Appendix C: SQL Grammar</legacyLink>.</para>
      </listItem>
    </list>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="be66188a-ebdb-4c9e-af72-c379886766fa">C to SQL: Character</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="af4095ff-06c3-4b04-83bf-19f9ee098dc2">C to SQL: Numeric</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="267c9fa9-599e-4ee6-b51b-0cae43f09183">C to SQL: Bit</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="3e9083f3-357b-41aa-833c-2c8aac2226cd">C to SQL: Binary</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="bea087d3-911f-418b-b483-d2b5b334da19">C to SQL: Date</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="9168b0b6-a828-4fef-b8cd-bdf439776f23">C to SQL: GUID</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="a8da43c9-d9a5-45e5-bd9a-1dd633db2ee0">C to SQL: Time</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="0e08bfff-68f9-4648-9558-09b57fea08ad">C to SQL: Timestamp</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="a0eb7b55-9db0-4375-9210-bddec4593880">C to SQL: Year-Month Intervals</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="f9ee1ddb-dec7-4f78-b6e2-5ba34e7d6f59">C to SQL: Day-Time Intervals</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="9f390afc-d8b8-4286-b559-98b3b8781f3d">C to SQL Data Conversion Examples</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>