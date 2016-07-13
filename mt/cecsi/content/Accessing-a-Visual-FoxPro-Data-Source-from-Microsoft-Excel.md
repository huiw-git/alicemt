---
title: Accessing a Visual FoxPro Data Source from Microsoft Excel
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2c143020-0403-4592-80e0-84229f3d40be
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Accessing a Visual FoxPro Data Source from Microsoft Excel
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>If you have Microsoft Query installed, you can create a data source in Microsoft Excel that connects to Visual FoxPro data.</para>
    <procedure>
      <title>To access Visual FoxPro data from Microsoft Excel</title>
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
            <para>In the Select Data Source dialog box, click Other.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the ODBC Data Sources dialog box, click New.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the Add Data Source dialog box, select Microsoft Visual FoxPro Driver from the Installed ODBC Drivers list box and click OK.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the <legacyLink xlink:href="de020197-7f53-4643-9cbf-b7887ba88de9">ODBC Visual FoxPro Setup dialog box</legacyLink>, enter the data source name, select the Database type, enter the path to the database or directory, and click OK. </para>
            <para>The new data source name is displayed in the Enter Data Source text box of the ODBC Data Sources dialog box. </para>
          </content>
        </step>
        <step>
          <content>
            <para>Click OK. </para>
            <para>The new data source name is selected in the Available Data Sources text box of the Select Data Source dialog box. </para>
          </content>
        </step>
        <step>
          <content>
            <para>Click Use.</para>
          </content>
        </step>
      </steps>
      <conclusion>
        <content>
          <para>You can now add tables to the open query. For more information about building a query, see <legacyLink xlink:href="3085bc4c-00a7-40e5-bffb-c3962cd3d509">Importing Data into Microsoft Excel from a Visual FoxPro Database</legacyLink>.</para>
        </content>
      </conclusion>
    </procedure>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>