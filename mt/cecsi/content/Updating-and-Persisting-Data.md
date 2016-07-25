---
title: "Updating and Persisting Data"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8dc27274-4f96-43d1-913c-4ff7d01b9a27
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
# Updating and Persisting Data
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The preceding chapters have discussed how to use ADO to get to data in a data source, how to move around in the data, and even how to edit the data. Of course, if the goal of your application is to allow users to make changes to the data, you will need to understand how to save those changes. You can either persist the <legacyBold>Recordset</legacyBold> changes to a file using the <legacyBold>Save</legacyBold> method, or you can send the changes back to the data source for storage using the <legacyBold>Update</legacyBold> or <legacyBold>UpdateBatch</legacyBold> methods.</para>
    <para>In the preceding chapters, you changed the data in several rows of the <legacyBold>Recordset</legacyBold>. ADO supports two basic notions relating to the addition, deletion, and modification of rows of data.</para>
    <para>The first notion is that changes aren't immediately made to the <legacyBold>Recordset</legacyBold>; instead, they are made to an internal <legacyItalic>copy buffer</legacyItalic>. If you decide you don't want the changes, the modifications in the copy buffer are discarded. If you decide to keep the changes, the changes in the copy buffer are applied to the <legacyBold>Recordset</legacyBold>.</para>
    <para>The second notion is that changes are either propagated to the data source as soon as you declare the work on a row complete (that is, <legacyItalic>immediate</legacyItalic> mode), or all changes to a set of rows are collected until you declare the work for the set complete (that is, <legacyItalic>batch</legacyItalic> mode). The <legacyBold>LockType</legacyBold> property determines when the changes are made to the underlying data source. <legacyBold>adLockOptimistic</legacyBold> or <legacyBold>adLockPessimistic</legacyBold> specifies immediate mode, while <legacyBold>adLockBatchOptimistic</legacyBold> specifies batch mode. The <legacyBold>CursorLocation</legacyBold> property can affect which <legacyBold>LockType</legacyBold> settings are available. For instance, the <legacyBold>adLockPessimistic</legacyBold> setting is not supported if the <legacyBold>CursorLocation</legacyBold> property is set to <legacyBold>adUseClient</legacyBold>.</para>
    <para>In immediate mode, each invocation of the <legacyBold>Update</legacyBold> method propagates the changes to the data source. In batch mode, each invocation of <legacyBold>Update</legacyBold> or movement of the current row position saves the changes to the copy buffer, but only the <legacyBold>UpdateBatch</legacyBold> method propagates the changes to the data source.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="6508e4e9-e33a-4dad-b340-5d632fd78a91">Updating Data</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="21c162ca-2845-4dd8-a49d-e715aba8c461">Persisting Data</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>