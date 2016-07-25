---
title: "Considering Database Features to Use"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 59760114-508e-46c5-81d2-8f2498c0d778
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Considering Database Features to Use
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>After the basic level of interoperability is known, the database features used by the application must be considered. For example, what SQL statements will the application execute? Will the application use scrollable cursors? Transactions? Procedures? Long data? For ideas about what features might not be supported by all DBMSs, see the <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo</legacyLink>, <legacyLink xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr</legacyLink>, and <legacyLink xlink:href="7abc5260-733a-48d4-9974-2d1a6a9ea5f6">SQLSetStmtAttr</legacyLink> function descriptions, and <legacyLink xlink:href="0ee36f09-59e7-4b94-88ca-7ebc0952a3be">Appendix C: SQL Grammar</legacyLink>. The features required by an application might eliminate some DBMSs from the list of target DBMSs. They might also show that the application can easily target many DBMSs.</para>
    <para>For example, if the required features are simple, they can usually be implemented with a high degree of interoperability. An application that executes a simple <legacyBold>SELECT</legacyBold> statement and retrieves results with a forward-only cursor is likely to be highly interoperable by virtue of its simplicity: Almost all drivers and DBMSs support the functionality it needs.</para>
    <para>However, if the required features are more complex, such as scrollable cursors, positioned update and delete statements, and procedures, trade-offs must often be made. There are several possibilities:  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyBold>Lower interoperability, more features.</legacyBold> The application includes the features but works only with DBMSs that support them.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Higher interoperability, fewer features.</legacyBold> The application drops the features but works with more DBMSs.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Higher interoperability, optional features.</legacyBold> The application includes the features but makes them available only with those DBMSs that support them.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Higher interoperability, more features.</legacyBold> The application uses the features with DBMSs that support them and emulates them for DBMSs that do not.</para>
      </listItem>
    </list>
    <para>The first two cases are relatively simple to implement, because the features are used either with all supported DBMSs or with none. The latter two cases, on the other hand, are more complex. It is necessary in both cases to check whether the DBMS supports the features and in the last case to write a potentially large amount of code to emulate these features. Therefore, these schemes are likely to require more development time and may be slower at run time.</para>
    <para>Consider a generic query application that can connect to a single data source. The application accepts a query from the user and displays the results in a window. Now suppose this application has one feature that allows users to display the results of multiple queries simultaneously. That is, they can execute a query and look at some of the results, execute a different query and look at some of its results, and then return to the first query. This presents an interoperability problem because some drivers support only a single active statement.</para>
    <para>The application has a number of choices, based on what the driver returns for the SQL_MAX_CONCURRENT_ACTIVITIES option in <legacyBold>SQLGetInfo</legacyBold>:  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyBold>Always support multiple queries.</legacyBold> After connecting to a driver, the application checks the number of active statements. If the driver supports only one active statement, the application closes the connection and informs the user that the driver does not support required functionality. The application is easy to implement and has full functionality but has lower interoperability.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Never support multiple queries.</legacyBold> The application drops the feature altogether. It is easy to implement and has high interoperability but has less functionality.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Support multiple queries only if the driver does.</legacyBold> After connecting to a driver, the application checks the number of active statements. The application allows the user to start a new statement when one is already active only if the driver supports multiple active statements. The application has higher functionality and interoperability but is harder to implement.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Always support multiple queries and emulate them when necessary.</legacyBold> After connecting to a driver, the application checks the number of active statements. The application always allows the user to start a new statement when one is already active. If the driver supports only one active statement, the application opens an additional connection to that driver and executes the new statement on that connection. The application has full functionality and high interoperability but is harder to implement.</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>