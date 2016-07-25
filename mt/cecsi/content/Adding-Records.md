---
title: "Adding Records"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dd34669e-6f06-403b-9241-1c85c82aecc2
caps.latest.revision: 9
manager: sonalm
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Adding Records
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Use the <legacyBold>AddNew</legacyBold> method to create and initialize a new record in an existing <legacyBold>Recordset</legacyBold>. You can use the <legacyBold>Supports</legacyBold> method with a <legacyBold>CursorOptionEnum</legacyBold> value of <legacyBold>adAddNew</legacyBold> to verify whether you can add records to the current <legacyBold>Recordset</legacyBold> object.</para>
    <para>After you call the <legacyBold>AddNew</legacyBold> method, the new record becomes the current record and remains current after you call the <legacyBold>Update</legacyBold> method. If the <legacyBold>Recordset</legacyBold> object does not support bookmarks, you might not be able to access the new record once you move to another record. Therefore, depending on your cursor type, you might need to call the <legacyBold>Requery</legacyBold> method to make the new record accessible.</para>
    <para>If you call <legacyBold>AddNew</legacyBold> while editing the current record or while adding a new record, ADO calls the <legacyBold>Update</legacyBold> method to save any changes and then creates the new record.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="cab4adff-f22f-4fb1-9217-f8138c795268">Adding Records Using AddNew</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="f3648ef4-9f36-4991-a868-83a617389844">Adding Multiple Fields</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="4c7e010d-08cd-4e22-9b32-23c36f02f88c">Determining Edit Mode</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="ed314bb9-e188-4658-a68c-a2abc49610be">Using AddNew in Immediate and Batch Modes</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>