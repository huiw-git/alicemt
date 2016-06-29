---
title: Mapping Deprecated Functions
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ee462617-1d79-4c88-afeb-b129cff34cc6
translation.priority.ht: 
  - en-gb
---
# Mapping Deprecated Functions
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This section describes how deprecated functions are mapped by the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager to guarantee backward compatibility of ODBC 3<legacyItalic>.x</legacyItalic> drivers that are used with ODBC 2.<legacyItalic>x</legacyItalic> applications. The Driver Manager performs this mapping regardless of the version of the application. Because each of the ODBC 2.<legacyItalic>x</legacyItalic> functions in the following list is mapped to the corresponding ODBC 3<legacyItalic>.x</legacyItalic> function when called in an ODBC 3<legacyItalic>.x</legacyItalic> driver, the ODBC 3<legacyItalic>.x</legacyItalic> driver does not have to implement the ODBC 2.<legacyItalic>x</legacyItalic> functions. </para>
  </introduction>
  <section>
    <content>
      <para>The mapping in the list is triggered when the driver is an ODBC 3<legacyItalic>.x</legacyItalic> driver and the driver does not support the function that is being mapped.</para>
      <para>The following table lists all duplicated functionality that was introduced in ODBC 3<legacyItalic>.x</legacyItalic>.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>ODBC 2.<legacyItalic>x</legacyItalic> function</para>
            </TD>
            <TD>
              <para>ODBC 3<legacyItalic>.x</legacyItalic> function</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLAllocConnect</legacyBold>
            </para>
            </TD>
            <TD>
              <para>
              <legacyBold>SQLAllocHandle</legacyBold>
            </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLAllocEnv</legacyBold>
            </para>
            </TD>
            <TD>
              <para>
              <legacyBold>SQLAllocHandle</legacyBold>
            </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLAllocStmt</legacyBold>
            </para>
            </TD>
            <TD>
              <para>
              <legacyBold>SQLAllocHandle</legacyBold>
            </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLBindParam</legacyBold>[1]</para>
            </TD>
            <TD>
              <para>
              <legacyBold>SQLBindParameter</legacyBold>
            </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLColAttributes</legacyBold>
            </para>
            </TD>
            <TD>
              <para>
              <legacyBold>SQLColAttribute</legacyBold>
            </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLError</legacyBold>
            </para>
            </TD>
            <TD>
              <para>
              <legacyBold>SQLGetDiagRec</legacyBold>
            </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLFreeConnect</legacyBold>
            </para>
            </TD>
            <TD>
              <para>
              <legacyBold>SQLFreeHandle</legacyBold>
            </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLFreeEnv</legacyBold>
            </para>
            </TD>
            <TD>
              <para>
              <legacyBold>SQLFreeHandle</legacyBold>
            </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLFreeStmt</legacyBold> with an <legacyItalic>Option</legacyItalic> of SQL_DROP</para>
            </TD>
            <TD>
              <para>
              <legacyBold>SQLFreeHandle</legacyBold>
            </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLGetConnectOption</legacyBold>
            </para>
            </TD>
            <TD>
              <para>
              <legacyBold>SQLGetConnectAttr</legacyBold>
            </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLGetStmtOption</legacyBold>
            </para>
            </TD>
            <TD>
              <para>
              <legacyBold>SQLGetStmtAttr</legacyBold>
            </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLParamOptions</legacyBold>
            </para>
            </TD>
            <TD>
              <para>
              <legacyBold>SQLSetStmtAttr</legacyBold>
            </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLSetConnectOption</legacyBold>
            </para>
            </TD>
            <TD>
              <para>
              <legacyBold>SQLSetConnectAttr</legacyBold>
            </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLSetParam</legacyBold>[2]</para>
            </TD>
            <TD>
              <para>
              <legacyBold>SQLBindParameter</legacyBold>
            </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLSetScrollOption</legacyBold>
            </para>
            </TD>
            <TD>
              <para>
              <legacyBold>SQLSetStmtAttr</legacyBold>
            </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLSetStmtOption</legacyBold>
            </para>
            </TD>
            <TD>
              <para>
              <legacyBold>SQLSetStmtAttr</legacyBold>
            </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>SQLTransact</legacyBold>
            </para>
            </TD>
            <TD>
              <para>
              <legacyBold>SQLEndTran</legacyBold>
            </para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   Even though this function did not exist in ODBC 2<legacyItalic>.x</legacyItalic>, it is in the Open Group and ISO standards.</para>
      <para>[2]   This is an ODBC 1.0 function.</para>
      <para>This section contains the following topics.

</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="ac89dd1f-c565-47cc-8fa3-6fa5f80b5d63">SQLAllocConnect Mapping</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="4bb51845-ee91-4b97-9dd4-2fab977f2aec">SQLAllocEnv Mapping</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="a2449dbb-1b6c-4b49-81b9-ebdddd4442fd">SQLAllocStmt Mapping</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="375f8f24-36de-4946-916e-c75abc6f070d">SQLBindParam Mapping</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="30e25719-176b-4c48-97d4-920766b22412">SQLColAttributes Mapping</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="802ac711-7e5d-4152-9698-db0cafcf6047">SQLError Mapping</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="8a844538-93c0-4709-bab6-35c45e771d80">SQLFreeConnect Mapping</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="c0f76455-d072-4bae-bee7-452277dfa479">SQLFreeEnv Mapping</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="267d95f2-4f0c-47ab-9411-5afe105215a2">SQLFreeStmt Mapping</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="e3792fe4-a955-473a-a297-c1b2403660c4">SQLGetConnectOption Mapping</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="fa599517-3f3e-4dad-a65a-b8596ae3f330">SQLGetStmtOption Mapping</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="bcd9ba4f-7834-4bc4-876e-c7478998e524">SQLInstallTranslator Mapping</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="57ed65f6-9620-4738-b331-19d2a2b5cae4">SQLParamOptions Mapping</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="a1b325cf-0c42-41c1-b141-b5a4fee7e708">SQLSetConnectOption Mapping</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="022dfbc0-8d18-4c35-8a28-d9eb16063188">SQLSetParam Mapping</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="a0fa4510-8891-4a61-a867-b2555bc35f05">SQLSetScrollOptions Mapping</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="6a9921aa-8a53-4668-9b13-87164062f1e5">SQLSetStmtOption Mapping</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="8a01041f-3572-46f9-8213-b817f3cf929c">SQLTransact Mapping</legacyLink>
          </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>