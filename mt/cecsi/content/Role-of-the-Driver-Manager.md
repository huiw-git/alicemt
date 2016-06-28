---
title: Role of the Driver Manager
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b861c82-357e-4590-8074-45136e9ed15e
translation.priority.ht: 
  - en-gb
---
# Role of the Driver Manager
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Driver Manager determines the final order in which to return status records that it generates. In particular, it determines which record has the highest rank and is to be returned first. The driver is responsible for ordering status records that it generates. If status records are posted by both the Driver Manager and the driver, the Driver Manager is responsible for ordering them. For more information, see <legacyLink xlink:href="0e0436cc-230f-44b0-b373-04a57e83ee76">Sequence of Status Records</legacyLink>.</para>
    <para>The Driver Manager does as much error checking as it can. This saves every driver from checking for the same errors. For example, if a function argument accepts a discrete number of values, such as <legacyItalic>Operation</legacyItalic> in <legacyBold>SQLSetPos</legacyBold>, the Driver Manager checks that the specified value is legal.</para>
    <para>The following sections describe the types of conditions checked by the Driver Manager. They are not intended to be exhaustive; for a complete list of the SQLSTATEs the Driver Manager returns, see the "Diagnostics" section of each function; the description of each check made by the Driver Manager starts with the letters "(DM)." Also see the state transition tables in <legacyLink xlink:href="15088dbe-896f-4296-b397-02bb3d0ac0fb">Appendix B: ODBC State Transition Tables</legacyLink>; errors shown in parentheses are detected by the Driver Manager.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="37a65f8b-83aa-456c-b7cf-500404abb38a">Argument Value Checks</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="0706db7d-e125-4845-a13a-7fe4308f7360">State Transition Checks</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="0c9a3425-0a7c-48de-9ff6-73601c26283e">General Error Checks</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="eeb5ab3f-987d-4f30-87d2-7425a81ad1d7">Driver Manager Error and Warning Checks</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>