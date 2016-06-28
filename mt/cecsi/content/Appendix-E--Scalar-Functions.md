---
title: Appendix E: Scalar Functions
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 59c7cd5e-32d6-43ab-bac3-7010322d105a
translation.priority.ht: 
  - en-gb
---
# Appendix E: Scalar Functions
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC specifies the following types of scalar functions, with detailed information about each of these function types provided in the corresponding sections of this appendix. The function descriptions include associated syntax.</para>
    <para>This appendix contains the following topics.

</para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="270f669e-8aab-4db0-95a4-f2b3c69538b3">String Functions</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="4fa548dc-e8b0-4179-92ff-81d6a79d10c3">Numeric Functions</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="bdf054a0-7aba-4e99-a34a-799917376fd5">Time, Date, and Interval Functions</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="36614b4c-e037-43ef-8692-67f4861b144d">System Functions</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="d5789450-b668-4753-96c8-6789e955e7ed">Explicit Data Type Conversion Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="982f09e5-8205-41b9-98b3-8f898e24743f">SQL-92 CAST Function</legacyLink>
        </para>
      </listItem>
    </list>
    <para>ODBC does not mandate a data type for return values from scalar functions because the functions are often data source–specific. Applications should use the CONVERT scalar function whenever possible to force data type conversion.</para>
  </introduction>
  <section>
    <title>ODBC and SQL-92 Scalar Functions</title>
    <content>
      <para>The tables in this appendix include functions that have been added in ODBC 3.0 to align with SQL-92. Those functions added for a particular type of scalar function, as defined in ODBC, are indicated in each section.</para>
      <para>ODBC and SQL-92 classify their scalar functions differently. ODBC classifies scalar functions by argument type; SQL-92 classifies them by return value. For example, the EXTRACT function is classified as a timedate function by ODBC, because the extract-field argument is a datetime keyword and the extract-source argument is a datetime or interval expression. SQL-92, on the other hand, classifies EXTRACT as a numeric scalar function, because the return value is a numeric.</para>
      <para>An application can determine which scalar functions a driver supports by calling <legacyBold>SQLGetInfo</legacyBold>. Information types are included both for ODBC and for SQL-92 classifications of scalar functions. Because these classifications are different, the support for some scalar functions may be indicated in information types that do not correspond to ODBC and SQL-92. For example, support for EXTRACT in ODBC is indicated by the SQL_TIMEDATE_FUNCTIONS information type; support for EXTRACT in SQL-92, on the other hand, is indicated by the SQL_SQL92_NUMERIC_VALUE_FUNCTIONS information type.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>