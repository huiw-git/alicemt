---
title: SQLWriteDSNToIni Function
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLWriteDSNToIni
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: dc7018b2-18d4-4657-96d0-086479a47474
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLWriteDSNToIni Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 1.0</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLWriteDSNToIni</legacyBold> adds a data source to the system information.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL <legacyBold>SQLWriteDSNToIni</legacyBold>(
     LPCSTR   <parameterReference>lpszDSN</parameterReference>,
     LPCSTR   <parameterReference>lpszDriver</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>lpszDSN</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Name of the data source to add.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszDriver</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Driver description (usually the name of the associated DBMS) presented to users instead of the physical driver name.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>The function returns TRUE if it is successful, FALSE if it fails.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLWriteDSNToIni</legacyBold> returns FALSE, an associated <legacyItalic>*pfErrorCode</legacyItalic> value can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError </legacyBold>and explains each one in the context of this function.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>
                <legacyItalic>*pfErrorCode</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>Error</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>ODBC_ERROR_GENERAL_ERR</para>
            </TD>
            <TD>
              <para>General installer error</para>
            </TD>
            <TD>
              <para>An error occurred for which there was no specific installer error.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_INVALID_DSN</para>
            </TD>
            <TD>
              <para>Invalid DSN</para>
            </TD>
            <TD>
              <para>The <legacyItalic>lpszDSN</legacyItalic> argument contained a string that was invalid for a DSN.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_INVALID_NAME</para>
            </TD>
            <TD>
              <para>Invalid driver or translator name</para>
            </TD>
            <TD>
              <para>The <legacyItalic>lpszDriver</legacyItalic> argument was invalid.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_REQUEST_FAILED</para>
            </TD>
            <TD>
              <para>Request failed</para>
            </TD>
            <TD>
              <para>The installer failed to create a DSN in the registry.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_OUT_OF_MEM</para>
            </TD>
            <TD>
              <para>Out of memory</para>
            </TD>
            <TD>
              <para>The installer could not perform the function because of a lack of memory.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>
        <legacyBold>SQLWriteDSNToIni</legacyBold> adds the data source to the [ODBC Data Sources] section of the system information. It then creates a specification section for the data source and adds a single keyword (<legacyBold>Driver</legacyBold>) with the name of the driver DLL as its value. If the data source specification section already exists, <legacyBold>SQLWriteDSNToIni</legacyBold> removes the old section before creating the new one.</para>
      <para>The caller of this function must add any driver-specific keywords and values to the data source specification section of the system information.</para>
      <para>If the name of the data source is Default, <legacyBold>SQLWriteDSNToIni</legacyBold> also creates the default driver specification section in the system information.</para>
      <para>This function should be called only from a setup DLL.</para>
    </content>
  </section>
  <section>
    <title>Related Functions</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>For information about</para>
            </TD>
            <TD>
              <para>See</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Adding, modifying, or removing a data source</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="01ced74e-c575-4a25-83f5-bd7d918123f8">ConfigDSN</legacyLink>(in the Setup DLL)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Adding, modifying, or removing a data source</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="f8d6e342-c010-434e-b1cd-f5371fb50a14">SQLConfigDataSource</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Removing a data source name from the system information</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="bb2e8273-7b61-4113-bfc8-f7ccc607c811">SQLRemoveDSNFromIni</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>