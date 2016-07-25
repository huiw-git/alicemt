---
title: "Receiving Results"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 791aa26e-7aae-477e-9f05-5cd46e1de095
caps.latest.revision: 10
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
# Receiving Results
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>In ADO most commands result in some information returned to the caller. For commands returning rowset, the results are received in a <legacyBold>Recordset</legacyBold> object, which is probably the most used of the ADO objects. </para>
    <para>There are several ways to receive data in a <legacyBold>Recordset </legacyBold>object from a data source, including calling the following:  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="0b81af6f-b9ae-4f7c-b59b-b5bdd775036f">Connection.Execute method</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="0b81af6f-b9ae-4f7c-b59b-b5bdd775036f">Command.Execute method</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="0b81af6f-b9ae-4f7c-b59b-b5bdd775036f">Recordset.Open method</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="5a0ec8f9-5ba3-4f9f-b80d-2073aa049586">Connection.NamedCommand</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="35ffdb79-a931-4271-a3bb-0cd804cf173e">Connection.StoredProcedure</legacyLink>           </para>
      </listItem>
    </list>
    <para>Receiving data in a <legacyBold>Recordset</legacyBold> object concludes the process of getting data, with the participation of a <legacyBold>Connection</legacyBold> object and a <legacyBold>Command</legacyBold> object, implicitly or explicitly. In a typical client/server application system, the whole process of getting data requires a round trip over the network for each filled <legacyBold>Recordset</legacyBold>. </para>
    <para>To receive more than one result sets means you would need to make several round trips over the network, one for each data set encapsulated in a <legacyBold>Recordset</legacyBold> object. For slow or congested networks, reducing the number of round trips may help improve the application's performances. Therefore, some providers offer support to receive multiple <legacyBold>Recordset</legacyBold>s in a single round trip. This is discussed in the following topic:  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="2a7ad7a6-f00d-4355-b0b5-d0ab957b0566">Receiving Multiple Recordsets</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>