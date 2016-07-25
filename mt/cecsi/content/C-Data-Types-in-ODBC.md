---
title: "C Data Types in ODBC"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c91bef31-3794-4736-966a-d50997b2233c
caps.latest.revision: 25
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# C Data Types in ODBC
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC defines the C data types that are used by application variables and their corresponding type identifiers. These are used by the buffers that are bound to result set columns and statement parameters. For example, suppose an application wants to retrieve data from a result set column in character format. It declares a variable with the SQLCHAR * data type and binds this variable to the result set column with a type identifier of SQL_C_CHAR. For a complete list of C data types and type identifiers, see <legacyLink xlink:href="981d49c3-3531-4543-aa75-5bd9e4f67000">Appendix D: Data Types</legacyLink>.</para>
    <para>ODBC also defines a default mapping from each SQL data type to a C data type. For example, a 2-byte integer in the data source is mapped to a 2-byte integer in the application. To use the default mapping, an application specifies the SQL_C_DEFAULT type identifier. However, use of this identifier is discouraged for interoperability reasons.</para>
    <para>All integer C data types defined in ODBC 1<legacyItalic>.x</legacyItalic> were signed. Unsigned C data types and their corresponding type identifiers were added in ODBC 2.0. Because of this, applications and drivers need to be particularly careful when dealing with 1<legacyItalic>.x</legacyItalic> versions.</para>
  </introduction>
  <section>
    <title>C Data Type Extensibility</title>
    <content>
      <para>In ODBC 3.8, you can specify driver-specific C data types. This enables you to bind a SQL type as a driver-specific C type in ODBC applications when you call <legacyLink xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol</legacyLink>, <legacyLink xlink:href="e3c1356a-5db7-4186-85fd-8b74633317e8">SQLGetData</legacyLink>, or <legacyLink xlink:href="38349d4b-be03-46f9-9d6a-e50dd144e225">SQLBindParameter</legacyLink>. This can be useful for supporting new server types, because existing C data types might not correctly represent the new server data types. Using driver-specific C types can increase the number of conversions that drivers can perform.</para>
      <para>For example, suppose a database management system (DBMS) introduced a new SQL type, <languageKeyword>DATETIMEOFFSET</languageKeyword>, to represent the date and time with time zone information. There would be no specific C type in ODBC that corresponded to <languageKeyword>DATETIMEOFFSET</languageKeyword>. An application would have to bind <languageKeyword>DATETIMEOFFSET</languageKeyword> as SQL_C_BINARY and cast it to a user-defined data type. Beginning in ODBC 3.8 with C data type extensibility, a driver can define a new corresponding C type. For example, for the new SQL type DATETIMEOFFSET, the driver can define a new corresponding C type such as SQL_C_DATETIMEOFFSET. Then, an application can bind the new SQL type as a driver-specific C type.</para>
      <para>A C data type is defined in the driver as follows: </para>
      <list class="bullet">
        <listItem>
          <para>The ODBC compliance level for an application, ODBC driver, and Driver Manager is 3.8 (or higher).</para>
        </listItem>
        <listItem>
          <para>The data range of a driver-specific C type is between 0x4000 and 0x7FFF.</para>
        </listItem>
        <listItem>
          <para>The driver defines the structure of the data corresponding to the C type.  This can be done in the driver-specific SDK.</para>
        </listItem>
      </list>
      <para>The driver manager will not validate a C type defined in the range of 0x4000 and 0x7FFF; the driver will perform the validation and any data type conversion. But if the data range of a C type passed to the driver manager is between 0x0000 and 0x3FFF or between 0x8000 and 0xFFFF, the driver manager will validate the C data type.</para>
      <alert class="note">
        <para>Driver-specific C data types should be described in the driver documentation.</para>
      </alert>
      <para>To specify an ODBC compliance level of 3.8, an application calls <legacyLink xlink:href="0343241c-4b15-4d4b-aa2b-2e8ab5215cd2">SQLSetEnvAttr</legacyLink> with the SQL_ATTR_ODBC_VERSION attribute set to <languageKeyword>SQL_OV_ODBC3_80</languageKeyword>. To determine the version of the driver, an application calls <unmanagedCodeEntityReference>SQLGetInfo</unmanagedCodeEntityReference> with SQL_DRIVER_ODBC_VER.</para>
      <para>For more information about ODBC 3.8, see <link xlink:href="854f0bb4-17e9-489b-9595-eefffb8ba99f">What's New in ODBC 3.8</link>. </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b681d260-3dbb-47df-a616-4910d727add7">C Data Types</link>
</relatedTopics>
</developerConceptualDocument>