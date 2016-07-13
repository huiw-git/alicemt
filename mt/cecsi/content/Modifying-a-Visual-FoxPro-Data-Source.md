---
title: Modifying a Visual FoxPro Data Source
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9c30b5a-9ddf-4044-a7c5-0bdb983fdda4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Modifying a Visual FoxPro Data Source
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <procedure>
      <title>To modify a Visual FoxPro data source</title>
      <steps class="ordered">
        <step>
          <content>
            <para>On computers running Windows 2000, open the Windows Control Panel and double-click Administrative Tools.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Double-click Data Sources (ODBC) to open the ODBC Data Source Administrator dialog box.This icon is available after you've installed the Visual FoxPro ODBC Driver or any ODBC driver software. </para>
            <alert class="note">
              <para>If you are running a previous version of Windows, open the Windows Control Panel and double-click 32-bit ODBC or ODBC to open the ODBC Data Source Administrator dialog box.</para>
            </alert>
          </content>
        </step>
        <step>
          <content>
            <para>In the User DSN or System DSN tab, select the name of the data source you want to modify and click Configure.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the <legacyLink xlink:href="de020197-7f53-4643-9cbf-b7887ba88de9">ODBC Visual FoxPro Setup dialog box</legacyLink>, select and change the items you want to modify and then click OK.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Click OK to save changes and close the ODBC Data Source Administrator dialog box.</para>
          </content>
        </step>
      </steps>
      <conclusion>
        <content>
          <para>Your changes will take effect the next time you access the data source from your application.</para>
        </content>
      </conclusion>
    </procedure>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>