---
title: ODBC API Reference
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apitype: dllExport
ms.assetid: b7a49774-f458-44ce-9a04-a0457501405b
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC API Reference
<?xml version="1.0" encoding="utf-8"?>
<developerOrientationDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The topics in this section describe each ODBC function in alphabetical order. Each function is defined as a C programming language function. Descriptions include the following:  </para>
    <list class="bullet">
      <listItem>
        <para>Purpose</para>
      </listItem>
      <listItem>
        <para>ODBC version</para>
      </listItem>
      <listItem>
        <para>Standard CLI conformance level</para>
      </listItem>
      <listItem>
        <para>Syntax</para>
      </listItem>
      <listItem>
        <para>Arguments</para>
      </listItem>
      <listItem>
        <para>Return values</para>
      </listItem>
      <listItem>
        <para>Diagnostics</para>
      </listItem>
      <listItem>
        <para>Comments about usage and implementation</para>
      </listItem>
      <listItem>
        <para>Code example</para>
      </listItem>
      <listItem>
        <para>References to related functions</para>
      </listItem>
    </list>
    <para>The standard CLI conformance level can be one of the following: ISO 92, Open Group, ODBC, or Deprecated. A function tagged as ISO 92–conformant also appears in Open Group version 1, because Open Group is a pure superset of ISO 92. A function tagged as Open Group-compliant also appears in ODBC 3.<legacyItalic>x</legacyItalic>, because ODBC 3.<legacyItalic>x</legacyItalic> is a pure superset of Open Group version 1. A function tagged as ODBC-compliant appears in neither standard. A function tagged as deprecated has been deprecated in ODBC 3.<legacyItalic>x</legacyItalic>.</para>
    <para>Handling of diagnostic information is described in the <legacyLink xlink:href="1dbc4398-97a8-4585-bb77-1f7ea75e24c4">SQLGetDiagField</legacyLink> function description. The text associated with SQLSTATE values is included to provide a description of the condition but is not intended to prescribe specific text.</para>
    <alert class="note">
      <para>For driver-specific information about ODBC functions, see the section for the driver.</para>
    </alert>
    <para>This section contains topics for the following functions:</para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="ca119958-ff72-42d4-b0ac-b1ca3212c705">SQLAllocConnect Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="00bac0c1-346b-4e48-901a-06ba4557b944">SQLAllocEnv Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="6e7fe420-8cf4-4e72-8dad-212affaff317">SQLAllocHandle Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="7bb38a06-e3d5-4c9a-a0e8-7b59b2ec6927">SQLAllocStmt Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="38349d4b-be03-46f9-9d6a-e50dd144e225">SQLBindParameter Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="b7f1be66-e6c7-4790-88ec-62b7662103c0">SQLBrowseConnect Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="7029d0da-b0f2-44e6-9114-50bd96f47196">SQLBulkOperations Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="ac0b5972-627f-4440-8c5a-0e8da728726d">SQLCancel Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="16049b5b-22a7-4640-9897-c25dd0f19d21">SQLCancelHandle Function</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="05b0a054-e28d-4e16-b5b0-07418486b372">SQLCloseCursor Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="8c45c598-cb01-4789-a571-e93619a18ed9">SQLColAttribute Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="3ece37af-db56-47fc-bc9d-6a7d0d8a00ec">SQLColAttributes Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="ef233d9a-6ed5-4986-9d42-5e0b1a79fb6e">SQLColumnPrivileges Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="4a3618b7-d2b8-43c6-a1fd-7a4e6fa8c7d0">SQLColumns Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="1b97c46a-d2e5-4540-8239-9d975e5321c6">SQLCompleteAsync Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="d5450895-3824-44c4-8aa4-d4f9752a9602">SQLCopyDesc Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="3f63b1b4-e70e-44cd-96c6-6878d50d0117">SQLDataSources Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="eddef353-83f3-4a3c-8f24-f9ed888890a4">SQLDescribeCol Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="1f5b63c4-2f3e-44da-b155-876405302281">SQLDescribeParam Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="9e84a58e-db48-4821-a0cd-5c711fcbe36b">SQLDisconnect Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="6b5b7514-e9cb-4cfd-8b7a-ab51dfab9efa">SQLDrivers Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="ff375ce1-eb50-4693-b1e6-70181a6dbf9f">SQLEndTran Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="ee5c90de-3c61-4f63-8b57-1543d1704a0e">SQLError Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="985fcee1-f204-425c-bdd1-deb0e7d7bbd9">SQLExecDirect Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="9286a01d-cde2-4b90-af94-9fd7f8da48bf">SQLExecute Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="940b5cf7-581c-4ede-8533-c67d5e9ef488">SQLExtendedFetch Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="c0243667-428c-4dda-ae91-3c307616a1ac">SQLFetchScroll Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="07f3f645-f643-4d39-9a10-70a72f24e608">SQLForeignKeys Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="0d22eaeb-3c75-47fb-af9a-6f7397e61b9c">SQLFreeConnect Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="32000150-e120-445e-b269-43200f813b2a">SQLFreeEnv Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="17a6fcdc-b05a-4de7-be93-a316f39696a1">SQLFreeHandle Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="03408162-8b63-4470-90c4-e6c7d8d33892">SQLFreeStmt Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="2cb4ffa8-19d3-4664-8c2f-6682cdcc3f33">SQLGetConnectAttr Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="59cde899-7957-4b5e-8677-f34d3b859bfd">SQLGetConnectOption Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="e6e92199-7bb6-447c-8987-049a4c6ce05d">SQLGetCursorName Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="e3c1356a-5db7-4186-85fd-8b74633317e8">SQLGetData Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="f09ff660-1e4a-4370-be85-90d4da0487d3">SQLGetDescField Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="325e0907-8e87-44e8-a111-f39e636a9cbc">SQLGetDescRec Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="1dbc4398-97a8-4585-bb77-1f7ea75e24c4">SQLGetDiagField Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="ebdbac93-3d68-438f-8416-ef1f08e04269">SQLGetDiagRec Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="01f4590f-427a-4280-a1c3-18de9f7d86c1">SQLGetEnvAttr Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="0451d2f9-0f4f-46ba-b252-670956a52183">SQLGetFunctions Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="e321d460-e997-4527-aee6-207cf5a498e9">SQLGetStmtAttr Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="d69c2668-4260-4722-8c34-1c51caac307f">SQLGetStmtOption Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="bdedb044-8924-4ca4-85f3-8b37578e0257">SQLGetTypeInfo Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="bf169ed5-4d55-412c-b184-12065a726e89">SQLMoreResults Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="b8efc247-27ab-4a00-92b6-1400785783fe">SQLNativeSql Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="dbf2da44-253b-4094-bd6b-29bafc23c7a3">SQLNumParams Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="d863179f-12a9-4b55-ac6b-7d84202d3da3">SQLNumResultCols Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="68fe010d-9539-4e5b-a260-c8d32423b1db">SQLParamData Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="ee08e987-0243-4060-ab21-64da11fe444f">SQLParamOptions Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="332e1b4b-b0ed-4e7a-aa4d-4f35f4f4476b">SQLPrepare Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="3f809b09-3c1b-415e-80c5-a603e8e25d5b">SQLPrimaryKeys Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="4ca37b28-a6df-465b-8988-d422d37fc025">SQLProcedureColumns Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="d0d9ef10-2fd4-44a5-9334-649f186f4ba0">SQLProcedures Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="9a60f004-1477-4c54-a20c-7378e1116713">SQLPutData Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="61e00a8a-9b3b-45b9-b397-7fe818822416">SQLRowCount Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="8cd2c2a2-25c8-4aff-951c-b593bbfc90ad">SQLSetConnectOption Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="4e055946-12d4-4589-9891-41617a50f34e">SQLSetCursorName Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="bf55256c-7eb7-4e3f-97ef-b0fee09ba829">SQLSetDescRec Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="0343241c-4b15-4d4b-aa2b-2e8ab5215cd2">SQLSetEnvAttr Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="2ebdc303-3802-443a-8895-69c93dff5618">SQLSetParam Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="80190ee7-ae3b-45e5-92a9-693eb558f322">SQLSetPos Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="2a825ba7-7942-4c23-bcdb-c80dc12f8c86">SQLSetScrollOptions Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="7abc5260-733a-48d4-9974-2d1a6a9ea5f6">SQLSetStmtAttr Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="9cbe2b62-4cf7-43ab-8fb4-9a53df2c6b3f">SQLSetStmtOption Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="bb2d9f21-bda0-4e50-a8be-f710db660034">SQLSpecialColumns Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="45210682-cfea-4e5d-9951-bcf1cbe10f41">SQLStatistics Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="8cfdb64f-64c5-47e6-ad57-0533ac630afa">SQLTablePrivileges Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="60d5068a-7d7c-447c-acc6-f3f2cf73440c">SQLTables Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="496249e0-8eff-4c60-8358-5543bc3ead9c">SQLTransact Function</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerOrientationDocument>