---
title: "Types of Locks"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 12a978c0-b8a0-4ef0-87f0-a43c13659272
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
# Types of Locks
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <title>adLockBatchOptimistic</title>
    <content>
      <para>Indicates optimistic batch updates. Required for batch update mode.</para>
      <para>Many applications fetch a number of rows at once and then need to make coordinated updates that include the entire set of rows to be inserted, updated, or deleted. With batch cursors, only one round trip to the server is needed, thus improving update performance and decreasing network traffic. Using a batch cursor library, you can create a static cursor and then disconnect from the data source. At this point you can make changes to the rows and subsequently reconnect and post the changes to the data source in a batch.</para>
    </content>
  </section>
  <section>
    <title>adLockOptimistic</title>
    <content>
      <para>Indicates that the provider uses optimistic locking — locking records only when you call the <legacyBold>Update</legacyBold> method. This means that there is a chance that another user may change the data between the time you edit the record and when you call <legacyBold>Update</legacyBold>, which creates conflicts. Use this lock type in situations where the chances of a collision are low or where collisions can be readily resolved.</para>
    </content>
  </section>
  <section>
    <title>adLockPessimistic</title>
    <content>
      <para>Indicates pessimistic locking, record by record. The provider does what is necessary to ensure successful editing of the records, usually by locking records at the data source immediately before editing. Of course, this means that the records are unavailable to other users once you begin to edit, until you release the lock by calling <legacyBold>Update.</legacyBold> Use this type of lock in a system where you cannot afford to have concurrent changes to data, such as in a reservation system.</para>
    </content>
  </section>
  <section>
    <title>adLockReadOnly</title>
    <content>
      <para>Indicates read-only records. You cannot alter the data. A read-only lock is the "fastest" type of lock because it does not require the server to maintain a lock on the records.</para>
    </content>
  </section>
  <section>
    <title>adLockUnspecified</title>
    <content>
      <para>Does not specify a type of lock.</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>