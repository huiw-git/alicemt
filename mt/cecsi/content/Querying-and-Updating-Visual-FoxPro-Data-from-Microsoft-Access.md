---
title: Querying and Updating Visual FoxPro Data from Microsoft Access
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2d314e78-9edf-44b2-bd8b-96784236bcbe
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Querying and Updating Visual FoxPro Data from Microsoft Access
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>You can query and update data stored in a Visual FoxPro database from a Microsoft Access database by using the Link Table option.</para>
    <procedure>
      <title>To link a Visual FoxPro database to a Microsoft Access database</title>
      <steps class="ordered">
        <step>
          <content>
            <para>Open a Microsoft Access database.</para>
          </content>
        </step>
        <step>
          <content>
            <para>From the Tables tab, click New.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the New Table dialog box, select Link Table and click OK.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the Link Dialog box, select ODBC Database in the Files of type list.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the SQL Data Sources dialog box, select the data source that connects to the Visual FoxPro data you want to query and click OK.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the Link Tables dialog box, select the tables you want to query and update and click OK. The linked Visual FoxPro tables are displayed in the Tables tab of the Microsoft Access database.</para>
          </content>
        </step>
      </steps>
      <conclusion>
        <content>
          <para>You can now use Microsoft Access to query and update data in the linked Visual FoxPro tables. Changes you make to linked data are sent back to the Visual FoxPro data source.</para>
          <para>If you do not want changes you make in Microsoft Access to affect the data on the Visual FoxPro data source, see <legacyLink xlink:href="a3591295-0a76-4e3c-b4fa-8bd4f1cde705">Importing Visual FoxPro Data into Microsoft Access</legacyLink>.</para>
        </content>
      </conclusion>
    </procedure>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>