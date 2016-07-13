---
title: Importing Visual FoxPro Data into Microsoft Access
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a3591295-0a76-4e3c-b4fa-8bd4f1cde705
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Importing Visual FoxPro Data into Microsoft Access
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>You can import data stored in a Visual FoxPro database into a Microsoft Access database using the Import option.</para>
    <procedure>
      <title>To import Visual FoxPro data into a Microsoft Access database</title>
      <steps class="ordered">
        <step>
          <content>
            <para>Open a Microsoft Access database.</para>
          </content>
        </step>
        <step>
          <content>
            <para>From the File menu, choose Get External Data then Import.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the Import dialog box, select ODBC Databases in the Files of type list.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the SQL Data Sources dialog box, select the Visual FoxPro data source that connects to the FoxPro data you want to query and click OK.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the Import Objects dialog box, select one or more tables you want to import and click OK. The names of the Visual FoxPro tables you imported are displayed in the Tables tab of the Microsoft Access database.</para>
          </content>
        </step>
      </steps>
      <conclusion>
        <content>
          <para>You can now use Microsoft Access to manipulate the data in the imported Visual FoxPro tables. The data you import is a snapshot of the data stored in Visual FoxPro; changes you make to imported data are not sent back to the Visual FoxPro data source.</para>
          <para>If you want changes you make in Microsoft Access to change the data on the Visual FoxPro data source, see <legacyLink xlink:href="2d314e78-9edf-44b2-bd8b-96784236bcbe">Querying and Updating Visual FoxPro Data from Microsoft Access</legacyLink>.</para>
        </content>
      </conclusion>
    </procedure>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>