---
title: "Records and Streams"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d68868e-2611-4b5c-9a89-7caa5f753151
caps.latest.revision: 11
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
# Records and Streams
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ADO currently provides the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object as the primary means of accessing information in data sources, such as relational databases. However, some providers support the <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> and <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> objects as alternative or complementary objects with which data from providers can be manipulated. For specifics on <legacyBold>Record</legacyBold> behavior, see your provider's documentation.</para>
  </introduction>
  <section>
    <title>Records</title>
    <content>
      <para>
        <legacyBold>Record</legacyBold> objects essentially function as one-row <legacyBold>Recordset</legacyBold>s. However, <legacyBold>Records</legacyBold> have limited functionality compared to <legacyBold>Recordsets</legacyBold> and they have different properties and methods.The source for the data in a <legacyBold>Record</legacyBold> object can be a command which returns one row of data from the provider. Using <legacyBold>Record</legacyBold> objects rather than <legacyBold>Recordset</legacyBold> objects to receive the results from a query that returns one row of data eliminates the overhead of instantiating the more complex <legacyBold>Recordset</legacyBold> object.</para>
      <para>
        <legacyBold>Record</legacyBold> objects can serve another purpose, particularly with providers for data sources other than traditional relational databases, such as the <legacyLink xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Microsoft OLE DB Provider for Internet Publishing</legacyLink>. Much of the information that must be processed exists, not as tables in databases, but as messages in electronic mail systems and files in modern file systems. The <legacyBold>Record</legacyBold> and <legacyBold>Stream</legacyBold> objects facilitate access to information stored in sources other than relational databases.</para>
      <para>The <legacyBold>Record</legacyBold> object can represent and manage data such as directories and files in a file system or folders and messages in an e-mail system. For these purposes, the source for the <legacyBold>Record</legacyBold> can be the current row of an open <legacyBold>Recordset</legacyBold>, an absolute URL, or a relative URL in conjunction with an open <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object.</para>
      <para>Typically, a <legacyBold>Recordset</legacyBold> can be used to represent a container or parent in a hierarchy such as a folder or directory. A <legacyBold>Record</legacyBold> can be used to return specific information about one node in the parent container, such as a file or document. The primary reason <legacyBold>Records</legacyBold> are used to represent this type of information is that these sources of data are heterogeneous. This means that each <legacyBold>Record</legacyBold> may have a different set and number of fields. Traditional <legacyBold>Recordsets</legacyBold> containing rows from a database are homogenous, which means that each row has the same number and type of fields.</para>
      <para>For more information about using the <legacyBold>Record</legacyBold> object for processing this heterogeneous data from providers such as the Internet Publishing Provider, see <legacyLink xlink:href="d399fce4-b70b-418f-8110-3deb3448863c">Using ADO for Internet Publishing</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Streams</title>
    <content>
      <para>The <legacyBold>Stream</legacyBold> object provides the means to read, write, and manage a stream of bytes. This byte stream may be text or binary and is limited in size only by system resources. Typically, ADO <legacyBold>Stream</legacyBold> objects are used for the following purposes:  </para>
      <list class="bullet">
        <listItem>
          <para>To contain the data of a <legacyBold>Recordset</legacyBold> saved in XML format. These XML streams from saved <legacyBold>Recordset</legacyBold>s can be used as the source when opening a new <legacyBold>Recordset</legacyBold>. For more information, see <legacyLink xlink:href="ad5bf52c-fd10-4cfa-bf7d-fcedcaa41eea">Streams and Persistence</legacyLink>.</para>
        </listItem>
        <listItem>
          <para>To contain <legacyLink xlink:href="f78f61b6-87e0-48dc-961e-83d0e20da58e">CommandStreams</legacyLink> to be executed against the provider as an alternative to <legacyLink xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText</legacyLink>. For example, XML UpdateGrams can be used as the source for a command against the Microsoft OLE DB Provider for SQL Server.</para>
        </listItem>
        <listItem>
          <para>To receive results from the provider in a format other than a <legacyBold>Recordset</legacyBold>, such as XML results from the Microsoft OLE DB Provider for SQL Server. For more information, see <legacyLink xlink:href="996c1321-c926-4f57-8297-85c8c20de974">Retrieving Resultsets into Streams</legacyLink>.</para>
        </listItem>
        <listItem>
          <para>To contain the text or bytes that comprise a file or message, typically used with providers such as the Microsoft OLE DB Provider for Internet Publishing. For more information about this use of <legacyBold>Stream</legacyBold> objects, see <legacyLink xlink:href="d399fce4-b70b-418f-8110-3deb3448863c">Using ADO for Internet Publishing</legacyLink>.</para>
        </listItem>
      </list>
      <para>A <legacyBold>Stream</legacyBold> object can be opened on:  </para>
      <list class="bullet">
        <listItem>
          <para>A simple file specified with a URL.</para>
        </listItem>
        <listItem>
          <para>A field of a <legacyBold>Record</legacyBold> or <legacyBold>Recordset</legacyBold> containing a <legacyBold>Stream</legacyBold> object.</para>
        </listItem>
        <listItem>
          <para>The default stream of a <legacyBold>Record</legacyBold> or <legacyBold>Recordset</legacyBold> object representing a directory or compound file.</para>
        </listItem>
        <listItem>
          <para>A resource field containing the URL of a simple file.</para>
        </listItem>
        <listItem>
          <para>No particular source at all. In this case, a <legacyBold>Stream</legacyBold> object is opened in memory. Data can be written to it and then saved in another <legacyBold>Stream</legacyBold> or file.</para>
        </listItem>
        <listItem>
          <para>A BLOB field in a <legacyBold>Recordset</legacyBold>.</para>
        </listItem>
      </list>
      <para>This section contains the following topics.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="ad5bf52c-fd10-4cfa-bf7d-fcedcaa41eea">Streams and Persistence</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="0ac09dbe-2665-411e-8fbb-d1efe6c777be">Command Streams</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="996c1321-c926-4f57-8297-85c8c20de974">Retrieving Resultsets into Streams</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="d399fce4-b70b-418f-8110-3deb3448863c">Using ADO for Internet Publishing</legacyLink>
          </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>