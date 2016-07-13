---
title: Processing SQL Statements
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 54dad6a3-e86c-477b-ba7c-4e95e0385ec1
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Processing SQL Statements
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>The ODBC cursor library passes all SQL statements directly to the driver except the following:  </para>
  </introduction>
  <section>
    <content>
      <list class="bullet">
        <listItem>
          <para>Positioned update and delete statements</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>SELECT FOR UPDATE </legacyBold>statements</para>
        </listItem>
        <listItem>
          <para>Batched SQL statements</para>
        </listItem>
      </list>
      <para>To execute positioned update and delete statements and to position the cursor on a row to call <legacyBold>SQLGetData</legacyBold> for that row, the cursor library constructs a searched statement that identifies the row.</para>
      <para>This section contains the following topics.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="2975dd97-48e6-4d0a-a9c7-40759a7d94c8">Processing Positioned Update and Delete Statements</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="8d2e79a4-5daf-458e-a536-d8b6e588753e">Processing SELECT FOR UPDATE Statements</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="04b93ef9-11de-47a3-8bd8-ba963c42f182">Processing Batches of SQL Statements</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="e429254c-c43f-4fbf-98b2-5f1ed53501ff">Constructing Searched Statements</legacyLink>
          </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>