---
title: "ADO Objects and Collections"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7a745aae-9372-49b6-8dae-b9c93e5f3216
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
# ADO Objects and Collections
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ADO consists of the following nine objects and four collections. </para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Object or Collection</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>               <legacyBold>Connection</legacyBold> object</para>
          </TD>
          <TD>
            <para>Represents a unique session with a data source. In the case of a client/server database system, it may be equivalent to an actual network connection to the server. Depending on the functionality supported by the provider, some collections, methods, or properties of a <legacyBold>Connection</legacyBold> object may not be available.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Command</legacyBold> object</para>
          </TD>
          <TD>
            <para>Used to define a specific command, such as a SQL query, intended to run against a data source.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Recordset</legacyBold> object</para>
          </TD>
          <TD>
            <para>Represents the entire set of records from a base table or the results of an executed command. All <legacyBold>Recordset</legacyBold> objects consist of records (rows) and fields (columns).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Record</legacyBold> object</para>
          </TD>
          <TD>
            <para>Represents a single row of data, either from a <legacyBold>Recordset</legacyBold> or from the provider. This record could represent a database record or some other type of object such as a file or directory, depending upon your provider.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Stream</legacyBold> object</para>
          </TD>
          <TD>
            <para>Represents a stream of binary or text data. For example, an XML document can be loaded into a stream for command input or returned from certain providers as the results of a query. A <legacyBold>Stream</legacyBold> object can be used to manipulate fields or records containing these streams of data.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Parameter</legacyBold> object</para>
          </TD>
          <TD>
            <para>Represents a parameter or argument associated with a <legacyBold>Command</legacyBold> object, based on a parameterized query or stored procedure.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Field</legacyBold> object</para>
          </TD>
          <TD>
            <para>Represents a column of data with a common data type. Each <legacyBold>Field</legacyBold> object corresponds to a column in the <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Property</legacyBold> object</para>
          </TD>
          <TD>
            <para>Represents a characteristic of an ADO object that is defined by the provider. ADO objects have two types of properties: built-in and dynamic. Built-in properties are those properties implemented in ADO and immediately available to any new object. The <legacyBold>Property</legacyBold> object is a container for dynamic properties, defined by the underlying provider. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Error</legacyBold> object</para>
          </TD>
          <TD>
            <para>Contains details about data access errors that pertain to a single operation involving the provider.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Fields</legacyBold> collection</para>
          </TD>
          <TD>
            <para>Contains all the <legacyBold>Field</legacyBold> objects of a <legacyBold>Recordset</legacyBold> or <legacyBold>Record</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Properties</legacyBold> collection</para>
          </TD>
          <TD>
            <para>Contains all the <legacyBold>Property</legacyBold> objects for a specific instance of an object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Parameters</legacyBold> collection</para>
          </TD>
          <TD>
            <para>Contains all the <legacyBold>Parameter</legacyBold> objects of a <legacyBold>Command</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Errors</legacyBold> collection</para>
          </TD>
          <TD>
            <para>Contains all the <legacyBold>Error</legacyBold> objects created in response to a single provider-related failure.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics>
<link xlink:href="4aca9838-1ec6-4084-bd63-dc2d17d8ab7d">ADO Object Model</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>