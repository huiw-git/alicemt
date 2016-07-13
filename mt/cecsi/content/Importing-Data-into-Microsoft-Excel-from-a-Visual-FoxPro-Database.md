---
title: Importing Data into Microsoft Excel from a Visual FoxPro Database
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3085bc4c-00a7-40e5-bffb-c3962cd3d509
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Importing Data into Microsoft Excel from a Visual FoxPro Database
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>You can import Visual FoxPro data into your Microsoft Excel worksheet if you have defined a data source for it. For information about creating a Visual FoxPro data source, see <legacyLink xlink:href="2c143020-0403-4592-80e0-84229f3d40be">Accessing a Visual FoxPro Data Source from Microsoft Excel</legacyLink>.</para>
    <procedure>
      <title>To import Visual FoxPro data into an Microsoft Excel worksheet</title>
      <steps class="ordered">
        <step>
          <content>
            <para>Open a Microsoft Excel spreadsheet.</para>
          </content>
        </step>
        <step>
          <content>
            <para>From the Data menu, choose Get External Data. Microsoft Query opens.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the Select Data Source dialog box, select a Visual FoxPro data source and then click Use.</para>
          </content>
        </step>
        <step>
          <content>
            <para>If the database accessed by your data source includes tables, select a table from the Add Tables dialog box. Microsoft Query displays the added table in the top half of the query designer. </para>
            <alert class="note">
              <para>The Owner list is not available in this dialog box because the driver does not support owners. The Database list is not available because the driver does not support multiple databases in a data source.</para>
            </alert>
          </content>
        </step>
        <step>
          <content>
            <para>Select fields for your query by dragging them from the table onto the lower half of the designer.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Close Microsoft Query. The data you selected is imported into your Microsoft Excel spreadsheet.</para>
          </content>
        </step>
      </steps>
    </procedure>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>