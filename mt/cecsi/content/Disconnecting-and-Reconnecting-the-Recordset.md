---
title: "Disconnecting and Reconnecting the Recordset"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c5134af7-81d6-4de4-9fd1-cfe29973545e
caps.latest.revision: 3
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
# Disconnecting and Reconnecting the Recordset
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>One of the most powerful features found in ADO is the capability to open a client-side Recordset from a data source and then disconnect the Recordset from the data source. Once the Recordset has been disconnected, the connection to the data source can be closed, thereby releasing the resources on the server used to maintain it. You can continue to view and edit the data in the Recordset while it is disconnected and later reconnect to the data source and send your updates in batch mode.</para>
    <para>To disconnect a Recordset, open it with a cursor location of adUseClient, and then set the ActiveConnection property equal to Nothing. (C++ users should set the ActiveConnection equal to NULL to disconnect.)</para>
    <para>We will use a disconnected Recordset later in this section when we discuss Recordset persistence to address a scenario in which we need to have the data in a Recordset available to an application while the client computer is not connected to a network.</para>
  </introduction>
  <relatedTopics>
<link xlink:href="0cb548e0-fcb4-4c49-98c8-be287911f826">Batch Mode</link>
</relatedTopics>
</developerConceptualDocument>