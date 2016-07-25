---
title: "Dealing with Failed Updates"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 299c37bd-19ff-4261-8571-b9665687e075
caps.latest.revision: 2
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
# Dealing with Failed Updates
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an update concludes with errors, how you resolve the errors depends on the nature and severity of the errors and the logic of your application. However, if the database is shared with other users, a typical error is that someone else modifies the field before you do. This type of error is called a conflict. ADO detects this situation and reports an error.</para>
  </introduction>
  <section>
    <title>Remarks</title>
    <content>
      <para>If there are update errors, they will be trapped in an error-handling routine. Filter the Recordset with the adFilterConflictingRecords constant so that only the conflicting rows are visible. In this example, the error-resolution strategy is merely to print the author's first and last names (au_fname and au_lname).</para>
      <para>The code to alert the user to the update conflict looks like this:</para>
      <code>objRs.Filter = adFilterConflictingRecords
objRs.MoveFirst
Do While Not objRst.EOF
   Debug.Print "Conflict: Name =  "; objRs!au_fname; " "; objRs!au_lname
   objRs.MoveNext
Loop</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="0cb548e0-fcb4-4c49-98c8-be287911f826">Batch Mode</link>
</relatedTopics>
</developerConceptualDocument>