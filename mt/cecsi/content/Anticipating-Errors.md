---
title: "Anticipating Errors"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ea1d4a97-58c3-476b-a496-cc80db2a90d5
caps.latest.revision: 5
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
# Anticipating Errors
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Error prevention is at least as important as error handling. This final section contains a short list of precautions your application can take to help make errors less likely to occur.</para>
    <para>Check the state of objects by checking the value in the <legacyBold>State</legacyBold> property before trying to perform an operation using those objects. For example, if your application uses a global <legacyBold>Connection</legacyBold>, check its <legacyBold>State</legacyBold> property to see if it is already open before calling the <legacyBold>Open</legacyBold> method.  </para>
    <list class="bullet">
      <listItem>
        <para>Any program that accepts data from a user must include code to validate that data before sending it to the data store. You cannot rely on the data store, the provider, ADO, or even your programming language to notify you of problems. You must check every byte entered by your users, making sure that data is the correct type for its field and that required fields are not empty.</para>
      </listItem>
    </list>
    <para>Check the data before you try to write any data to the data store. The easiest way to do so is to handle the <legacyBold>WillMove</legacyBold> event or the <legacyBold>WillUpdateRecordset</legacyBold> event. For a more complete discussion of handling ADO events, see <link xlink:href="e9003457-0762-48b3-942f-0820266b158f">Handling ADO Events</link>.</para>
    <para>Make sure that <legacyBold>Recordset</legacyBold> objects are not beyond the boundaries of the <legacyBold>Recordset</legacyBold> before attempting to move the record pointer. If you try to <legacyBold>MoveNext</legacyBold> when <legacyBold>EOF</legacyBold> is True or <legacyBold>MovePrev</legacyBold> when <legacyBold>BOF</legacyBold> is True, an error will occur. If you perform any of the <legacyBold>Move</legacyBold> methods when both <legacyBold>EOF</legacyBold> and <legacyBold>BOF</legacyBold> are True, an error will be generated.</para>
    <para>Errors also will occur if you try to perform operations such as <legacyBold>Seek</legacyBold> and <legacyBold>Find</legacyBold> on an empty <legacyBold>Recordset</legacyBold>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>