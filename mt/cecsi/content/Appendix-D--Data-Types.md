---
title: Appendix D: Data Types
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 981d49c3-3531-4543-aa75-5bd9e4f67000
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Appendix D: Data Types
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC defines two sets of data types: SQL data types and C data types. SQL data types indicate the data type of data stored at the data source. C data types indicate the data type of data stored in application buffers.</para>
  </introduction>
  <section>
    <content>
      <para>SQL data types are defined by each DBMS in accordance with the SQL-92 standard. For each SQL data type specified in the SQL-92 standard, ODBC defines a type identifier, which is a <legacyBold>#define</legacyBold> value that is passed as an argument in ODBC functions or returned in the metadata of a result set. The only SQL-92 data types not supported by ODBC are BIT (the ODBC SQL_BIT type has different characteristics), BIT_VARYING, TIME_WITH_TIMEZONE, TIMESTAMP_WITH_TIMEZONE, and NATIONAL_CHARACTER. Drivers are responsible for mapping data source–specific SQL data types to ODBC SQL data type identifiers and driver-specific SQL data type identifiers. The SQL data type is specified in the SQL_DESC_CONCISE_TYPE field of an implementation descriptor.</para>
      <para>ODBC defines the C data types and their corresponding ODBC type identifiers. An application specifies the C data type of the buffer that will receive result set data by passing the appropriate C type identifier in the <legacyItalic>TargetType</legacyItalic> argument in a call to <legacyBold>SQLBindCol</legacyBold> or <legacyBold>SQLGetData</legacyBold>. It specifies the C type of the buffer containing a statement parameter by passing the appropriate C type identifier in the <legacyItalic>ValueType</legacyItalic> argument in a call to <legacyBold>SQLBindParameter</legacyBold>. The C data type is specified in the SQL_DESC_CONCISE_TYPE field of an application descriptor.</para>
      <alert class="note">
        <para>There are no driver-specific C data types.</para>
      </alert>
      <para>Each SQL data type corresponds to an ODBC C data type. Before returning data from the data source, the driver converts it to the specified C data type. Before sending data to the data source, the driver converts it from the specified C data type.</para>
      <para>This appendix contains the following topics.

</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="467e0c0c-a818-4737-8a24-3d8e15c7e162">Using Data Type Identifiers</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="1b22f985-f5e4-4779-87eb-e43329a442b1">SQL Data Types</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="b681d260-3dbb-47df-a616-4910d727add7">C Data Types</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="f0077c9b-8eb2-4b5f-8c4c-7436fdef37ab">Data Type Identifiers and Descriptors</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="8fa365d2-9de0-40c6-bcd2-a85613061baf">Pseudo-Type Identifiers</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="4b12a9de-51d0-416a-87f4-9bf84959cad9">Transferring Data in Its Binary Form</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="28a879a1-666e-4183-b731-d36b584d5d86">Guidelines for Interval and Numeric Data Types</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="70667410-c582-4369-8e06-9d98e21cd2bf">Constraints of the Gregorian Calendar</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="723107a1-be08-4ea3-a8c0-b2c45d38d1aa">Column Size, Decimal Digits, Transfer Octet Length, and Display Size</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="029727f6-d3f0-499a-911c-bcaf9714e43b">Converting Data from SQL to C Data Types</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="ee0afe78-b58f-4d34-ad9b-616bb23653bd">Converting Data from C to SQL Data Types</legacyLink>
          </para>
        </listItem>
      </list>
      <para>For an explanation of ODBC data types, see <legacyLink xlink:href="7332d93e-44db-4132-9c10-988dbc13369e">Data Types in ODBC</legacyLink>. For information about driver-specific SQL data types, see the driver's documentation.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>