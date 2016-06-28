---
title: Troubleshooting (Visual FoxPro ODBC Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fd478dd8-666a-4f0a-a2d6-b94e81cbbe4b
translation.priority.ht: 
  - en-gb
---
# Troubleshooting (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following sections discuss how to improve performance and solve problems you might encounter while using the Visual FoxPro ODBC Driver.</para>
  </introduction>
  <section>
    <title>Accessing Parameterized Views</title>
    <content>
      <para>You can't access parameterized views in a Visual FoxPro database using the driver. A parameterized view creates a WHERE clause in the view's SQL <legacyBold>SELECT</legacyBold> statement that limits the records downloaded to those records that meet the conditions of the WHERE clause built using the value supplied for the parameter. Because the driver doesn't support passing parameters to the view, attempts to access a parameterized view by using the driver will fail.</para>
      <para>The parameter value can be supplied at run time or passed programmatically to the view.</para>
    </content>
  </section>
  <section>
    <title>Accessing Remote Views</title>
    <content>
      <para>You can't access remote views in a Visual FoxPro database using the driver. Remote views are views that access either non-FoxPro data or a combination of FoxPro and non-FoxPro data. To access remote views, use Visual FoxPro.</para>
    </content>
  </section>
  <section>
    <title>Deleting Records</title>
    <content>
      <para>You can mark records for deletion using the driver, but you can't permanently remove records from the database. To permanently remove records from a table, use Visual FoxPro.</para>
    </content>
  </section>
  <section>
    <title>Increasing Performance Using Background Fetching</title>
    <content>
      <para>You can improve performance on large fetches by using the background fetching feature of the driver. Background fetching uses a separate thread to fetch data requested from a specific data source.</para>
      <para>You can employ background fetching for a data source in one of the following ways:

</para>
      <list class="bullet">
        <listItem>
          <para>Check the <legacyBold>Fetch data in background</legacyBold> checkbox on the <legacyLink xlink:href="de020197-7f53-4643-9cbf-b7887ba88de9">ODBC Visual FoxPro Setup dialog box</legacyLink>.</para>
        </listItem>
        <listItem>
          <para>Use the BackgroundFetch attribute keyword in your connection string.</para>
        </listItem>
      </list>
      <para>For information on connection string attribute keywords, see <legacyLink xlink:href="57634960-47e9-49bf-95c1-6e3702ac8166">Using Connection Strings</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Updating Multitiered Views</title>
    <content>
      <para>A multitiered view is a view based on one or more views rather than on a base table. When you update data in a multitiered view, the updates go down only one level, to the view on which the top-level view is based; base tables are not updated.</para>
    </content>
  </section>
  <section>
    <title>Using Data Definition Language (DDL) in Stored Procedures</title>
    <content>
      <para>You can't use DDL, such as CREATE TABLE or ALTER TABLE, in Visual FoxPro stored procedures.</para>
      <para>For information on language you can use in stored procedures, see <legacyLink xlink:href="e449de20-d6ca-4902-9f8e-814eb6e86650">Support for Rules, Triggers, Default Values, and Stored Procedures</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Using Positioned Updates</title>
    <content>
      <para>The driver doesn't support positioned updates. Use the SQL WHERE clause to identify the rows you want to update.</para>
    </content>
  </section>
  <section>
    <title>Using the SET ANSI Command</title>
    <content>
      <para>If you're a Visual FoxPro developer, you should be aware that the default setting for SET ANSI is ON for the driver, in contrast to a default setting of OFF for Visual FoxPro. The default ON setting for SET ANSI allows Visual FoxPro data sources to behave consistently with other ODBC data sources that typically perform exact comparisons. You can change the default setting. For more information, see <legacyLink xlink:href="cf9a01b2-14bf-458c-a73c-2a58ddef32d8">SET ANSI</legacyLink>.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>