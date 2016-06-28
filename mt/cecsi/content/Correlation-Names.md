---
title: Correlation Names
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 76c36c6f-f8e1-4ece-a77b-611dde3bdd8a
translation.priority.ht: 
  - en-gb
---
# Correlation Names
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Correlation names are fully supported, including within the table list. For example, in the following string, E1 is the correlation name for the table named Emp:</para>
  </introduction>
  <section>
    <content>
      <code>SELECT * FROM Emp E1 
WHERE E1.LastName = 'Smith'</code>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>