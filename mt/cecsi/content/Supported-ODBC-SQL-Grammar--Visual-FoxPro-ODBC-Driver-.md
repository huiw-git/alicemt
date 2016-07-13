---
title: Supported ODBC SQL Grammar (Visual FoxPro ODBC Driver)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f41a38c2-e22e-4c65-a32e-9a6777435160
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Supported ODBC SQL Grammar (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Microsoft Visual FoxPro ODBC Driver supports the following:

</para>
  </introduction>
  <section>
    <content>
      <list class="bullet">
        <listItem>
          <para>All SQL statements and clauses in the ODBC minimum SQL grammar</para>
        </listItem>
        <listItem>
          <para>An additional SQL statement from the ODBC core SQL grammar</para>
        </listItem>
      </list>
      <para>The following table lists the items supported by the driver, by ODBC SQL Grammar level.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Level</para>
            </TD>
            <TD>
              <para>Elements</para>
            </TD>
            <TD>
              <para>Item</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Minimum</para>
            </TD>
            <TD>
              <para>Data Definition Language (DDL)</para>
            </TD>
            <TD>
              <para>CREATE TABLE and DROP TABLE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para>Data Manipulation Language (DML)</para>
            </TD>
            <TD>
              <para>SELECT, INSERT, UPDATE, and DELETE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para>Expressions</para>
            </TD>
            <TD>
              <para>Simple (such as A&gt;B+C)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para>Data types</para>
            </TD>
            <TD>
              <para>CHAR, VARCHAR, or LONG VARCHAR</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>In addition to the supported ODBC SQL grammar, the Visual FoxPro ODBC Driver supports the complete native Visual FoxPro language syntax for the following Visual FoxPro commands:</para>
      <para>
        <legacyLink xlink:href="3a01a291-f4d9-43bc-a725-5a95546ff364">ALTER TABLE</legacyLink>
      </para>
      <para>
        <legacyLink xlink:href="be2143ba-fc16-42c9-84f7-8985cd924860">CREATE TABLE</legacyLink>
      </para>
      <para>
        <legacyLink xlink:href="0d5bd477-626f-4f22-a05a-f531d9f8c5e7">DELETE</legacyLink>
      </para>
      <para>
        <legacyLink xlink:href="4f4e1362-a5f3-4b15-8a3c-d4e96605f221">DELETE TAG</legacyLink>
      </para>
      <para>
        <legacyLink xlink:href="bc50459b-8861-4889-84a9-129ae9065aa8">DROP TABLE</legacyLink>
      </para>
      <para>
        <legacyLink xlink:href="694e8cf5-2f69-4001-9c1e-b735a4da3aff">INDEX</legacyLink>
      </para>
      <para>
        <legacyLink xlink:href="9b648198-349f-46f6-b869-13d129945971">INSERT</legacyLink>
      </para>
      <para>
        <legacyLink xlink:href="2149c3ca-3a71-446d-8d53-3d056e2f301a">SELECT</legacyLink>
      </para>
      <para>
        <legacyLink xlink:href="ff1e0331-c060-4304-b280-039725b45f63">UPDATE</legacyLink>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>