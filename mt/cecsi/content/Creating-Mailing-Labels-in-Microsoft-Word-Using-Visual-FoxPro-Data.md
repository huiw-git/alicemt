---
title: "Creating Mailing Labels in Microsoft Word Using Visual FoxPro Data"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c901b60c-9f84-407a-b3d1-b4d301a71370
caps.latest.revision: 6
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Creating Mailing Labels in Microsoft Word Using Visual FoxPro Data
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>You can use Visual FoxPro data in a Microsoft Word for Windows 95 or Windows 98 document. For example, you might want to create mailing labels from the customer information stored in a Visual FoxPro table.</para>
    <procedure>
      <title>To create mailing labels</title>
      <steps class="ordered">
        <step>
          <content>
            <para>In Microsoft Word, create a new blank document.</para>
          </content>
        </step>
        <step>
          <content>
            <para>From the Tools menu, choose Mail Merge.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the Mail Merge Helper, choose Create and then select Mailing Labels.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Under Main Document, choose Active Window.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Under Data Source, choose Get Data and then select Open Data Source.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the Open Data Source dialog box, choose MS Query.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the Select Data Source dialog box, select a Visual FoxPro data source and then click Use.</para>
          </content>
        </step>
        <step>
          <content>
            <para>If the database accessed by your data source includes tables, select a table from the Add Tables dialog box. Microsoft Query displays the added table in the top half of the query designer.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Select fields for your query by dragging them from the table onto the lower half of the designer.</para>
          </content>
        </step>
        <step>
          <content>
            <para>From the File menu, choose Return Data to Microsoft Word. Microsoft Query closes, and the data you selected is available for use in your mail merge document.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Under Main Document, choose Setup.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the Label Options dialog box, select the printer and label information you want and then click OK.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the Create Labels dialog box, select the fields you want to print on the mailing labels and then click OK.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the Mail Merge Helper, under the Merge the Data with the Document, click Merge.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the Merge dialog box, select the options you want and then click Merge.</para>
          </content>
        </step>
      </steps>
    </procedure>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>