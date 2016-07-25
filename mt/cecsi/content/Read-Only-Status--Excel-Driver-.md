---
title: "Read-Only Status (Excel Driver)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef5d773b-4f8f-4005-b985-84b53d8e9f9b
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Read-Only Status (Excel Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When the Microsoft Excel driver is used, data source tables are opened as read-only by default, and can be opened by only one user at a time. Even though tables have read-only status, however, applications can perform insertions and updates for Microsoft Excel tables. </para>
  </introduction>
  <section>
    <content>
      <para>When an application performs a Save As command on Microsoft Excel data through the Microsoft Excel driver, the application should create a new table and insert the data to be saved into the new table. Inserts result in an append to the table. No other operations can be performed on the table until it is closed and reopened. Once the table is closed, no subsequent insert can be performed because the table is then a read-only table.</para>
      <para>It is possible to update values when using the Microsoft Excel driver, but a row cannot be deleted from a table based on a Microsoft Excel spreadsheet, so updates are not considered officially supported by the Microsoft Excel driver.</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>