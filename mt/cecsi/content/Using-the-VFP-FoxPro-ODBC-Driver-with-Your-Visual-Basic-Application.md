---
title: Using the VFP FoxPro ODBC Driver with Your Visual Basic Application
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5223ca23-5df6-4ebc-aa3b-70682ff27a8c
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Using the VFP FoxPro ODBC Driver with Your Visual Basic Application
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Your Microsoft® Visual Basic® application can communicate with Visual FoxPro data by creating a data control that connects to a Visual FoxPro data source.</para>
  </introduction>
  <section>
    <content>
      <procedure>
        <title>To connect to Visual FoxPro data using the Data Control in Visual Basic</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Create a data source named "test" that connects to the TasTrade sample database included in Visual FoxPro. The default Visual FoxPro installation places the TasTrade sample database in the location:
</para>
              <code>c:\vfp\samples\mainsamp\data\tastrade.dbc</code>
            </content>
          </step>
          <step>
            <content>
              <para>In Visual Basic, create a new form and place a text box and a Data control on it.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Change the Data control's Connect property as follows:
</para>
              <code>ODBC;DATABASE=tastrade;DSN=test</code>
            </content>
          </step>
          <step>
            <content>
              <para>Change the RecordsetType property to the following:
</para>
              <code>2 - Snapshot</code>
            </content>
          </step>
          <step>
            <content>
              <para>Change the RecordSource property to the following:
</para>
              <code>customer</code>
            </content>
          </step>
          <step>
            <content>
              <para>Change the DataSource property for the text box to the default name for the Data control to the following:
</para>
              <code>data1</code>
            </content>
          </step>
          <step>
            <content>
              <para>Change the text box's DataField property to the following:
</para>
              <code>customer_id</code>
            </content>
          </step>
          <step>
            <content>
              <para>Run the form, and use the Data control to skip through the customer id fields from the Visual FoxPro TasTrade sample database.</para>
            </content>
          </step>
        </steps>
      </procedure>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>