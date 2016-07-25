---
title: "Error Handling"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4909e413-f3b0-4183-8ad3-67b1434df742
caps.latest.revision: 4
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
# Error Handling
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ADO uses several different methods to notify an application of errors that occur. This section discusses the types of errors that can occur when you are using ADO and how your application is notified. It concludes by making suggestions about how to handle those errors.</para>
  </introduction>
  <section>
    <title>How Does ADO Report Errors?</title>
    <content>
      <para>ADO notifies you about errors in several ways:  </para>
      <list class="bullet">
        <listItem>
          <para>ADO errors generate a run-time error. Handle an ADO error the same way you would any other run-time error, such as using an <legacyBold>On Error</legacyBold> statement in Visual Basic.</para>
        </listItem>
        <listItem>
          <para>Your program can receive errors from OLE DB. An OLE DB error generates a run-time error as well.</para>
        </listItem>
        <listItem>
          <para>If the error is specific to your data provider, one or more <legacyBold>Error</legacyBold> objects are placed in the <legacyBold>Errors</legacyBold> collection of the <legacyBold>Connection</legacyBold> object that was used to access the data store when the error occurred.</para>
        </listItem>
        <listItem>
          <para>If the process that raised an event also produced an error, error information is placed in an <legacyBold>Error</legacyBold> object and passed as a parameter to the event. See <legacyLink xlink:href="e9003457-0762-48b3-942f-0820266b158f">Handling ADO Events</legacyLink> for more information about events.</para>
        </listItem>
        <listItem>
          <para>Problems that occur when processing batch updates or other bulk operations involving a <legacyBold>Recordset</legacyBold> can be indicated by the <legacyBold>Status</legacyBold> property of the <legacyBold>Recordset</legacyBold>. For example, schema constraint violations or insufficient permissions can be specified by <legacyBold>RecordStatusEnum</legacyBold> values.</para>
        </listItem>
        <listItem>
          <para>Problems that occur involving a particular <legacyBold>Field</legacyBold> in the current record are also indicated by the <legacyBold>Status</legacyBold> property of each <legacyBold>Field</legacyBold> in the <legacyBold>Fields</legacyBold> collection of the <legacyBold>Record</legacyBold> or <legacyBold>Recordset</legacyBold>. For example, updates that could not be completed or incompatible data types can be specified by <legacyBold>FieldStatusEnum</legacyBold> values.</para>
        </listItem>
      </list>
      <para>This section contains the following topics.  </para>
      <list class="bullet">
        <listItem>
          <para>             <legacyLink xlink:href="9bb84114-a1df-4122-a1b8-ad98dcd85cc3">ADO Errors</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="cc7d6ff9-2034-45c6-9d61-90b177010054">Provider Errors</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="5e7b1af4-996b-47c5-9161-c5575ad4fec9">Field-Related Error Information</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="7e103574-59ad-4790-b5f9-fa8d715e711e">Recordset-Related Error Information</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="8c57f35e-3c04-4f17-bf3e-3ad053951530">Handling Errors In Other Languages</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="ea1d4a97-58c3-476b-a496-cc80db2a90d5">Anticipating Errors</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>