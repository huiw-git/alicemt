---
title: "ADO Fundamentals"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d6a66928-e68f-4c38-b87a-838c5de50a28
caps.latest.revision: 9
manager: sonalm
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# ADO Fundamentals
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ADO gives developers a powerful, logical object model for programmatically accessing, editing, and updating data from a wide variety of data sources through OLE DB system interfaces. The most common usage of ADO is to query a table or tables in a relational database, retrieve and display the results in an application, and perhaps let users make and save changes to the data. Other tasks include the following:  </para>
    <list class="bullet">
      <listItem>
        <para>Querying a database using SQL and displaying the results.</para>
      </listItem>
      <listItem>
        <para>Accessing information in a file store over the Internet.</para>
      </listItem>
      <listItem>
        <para>Manipulating messages and folders in an e-mail system.</para>
      </listItem>
      <listItem>
        <para>Saving data from a database into an XML file.</para>
      </listItem>
      <listItem>
        <para>Executing commands described with XML and retrieving an XML stream.</para>
      </listItem>
      <listItem>
        <para>Saving data into a binary or XML stream.</para>
      </listItem>
      <listItem>
        <para>Allowing a user to review and change data in database tables.</para>
      </listItem>
      <listItem>
        <para>Creating and reusing parameterized database commands.</para>
      </listItem>
      <listItem>
        <para>Executing stored procedures.</para>
      </listItem>
      <listItem>
        <para>Dynamically creating a flexible structure, which is named a <legacyBold>Recordset</legacyBold>, to hold, navigate, and manipulate data.</para>
      </listItem>
      <listItem>
        <para>Performing transactional database operations.</para>
      </listItem>
      <listItem>
        <para>Filtering and sorting local copies of database information based on run-time criteria.</para>
      </listItem>
      <listItem>
        <para>Creating and manipulating hierarchical results from databases.</para>
      </listItem>
      <listItem>
        <para>Binding database fields to data-aware components.</para>
      </listItem>
      <listItem>
        <para>Creating remote, disconnected <legacyBold>Recordsets</legacyBold>.</para>
      </listItem>
    </list>
    <para>ADO exposes a wide variety of options and settings to provide such flexibility. Therefore, it is important to take a methodical approach to learning how to use ADO in an application, breaking down each of your goals into manageable pieces.</para>
    <para>Four primary operations are involved in most applications that use ADO: getting data, examining data, editing data, and updating data. These operations are examined in more detail later in this section.</para>
    <para>However, before we discuss these details, we will present an overview of the ADO object model and a simple ADO application, which is written in Microsoft® Visual Basic® and performs each of the four primary ADO operations:  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="7a745aae-9372-49b6-8dae-b9c93e5f3216">ADO Objects and Collections</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="de4bcd56-dac2-45e6-95ab-9fd7f25878fc">HelloData: A Simple ADO Application</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="6e0488c3-934d-4976-99dc-65c580dc7a3c">OLE DB Providers</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="8ae6611b-3069-4155-b014-c0c9da37be39">Errors</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>