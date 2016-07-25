---
title: "RDS Code Examples in VBScript"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 22f23c30-7c21-4fe3-8e76-36cea6448819
caps.latest.revision: 11
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
# RDS Code Examples in VBScript
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>Use the following code examples to learn how to use the RDS objects, methods, and properties when writing in Microsoft Visual Basic Scripting Edition (VBScript).</para>
    <alert class="note">
      <para>Paste the entire code example into your code editor. The example may not run correctly if partial examples are used or if paragraph formatting is lost.</para>
    </alert>
  </introduction>
  <section>
    <title>Objects</title>
    <content>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="4f306a51-d5a4-4785-b426-487639cda164">DataControl Object Example</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="12b0e160-5e5c-441f-bed7-ac0bd061e003">DataSpace Object Example</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="b4e2844a-120a-4513-860b-f1b6e4b5dda4">DataFactory Object Example</legacyLink>
          </para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Methods</title>
    <content>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="4ade106d-063d-486e-bc4d-a1a6b6e0bea9">Cancel Method Example</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="c23912f0-1288-4727-8fb4-f643b8811cf7">CancelUpdate Method Example</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="edd0a01c-1a1b-4b91-9966-2529e244abae">ConvertToString Method Example</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="12b0e160-5e5c-441f-bed7-ac0bd061e003">CreateObject Method</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="cce0d8b5-e87b-4f7b-a8a0-37d5025a1f5d">CreateRecordset Method Example</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="b4e2844a-120a-4513-860b-f1b6e4b5dda4">Query Method Example</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="f2926578-bc60-464b-916e-ddfdb8014253">Refresh Method Example</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="8a74802f-34d6-4676-bf94-07df5f8bff66">Reset Method Example</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="619bc7fd-ad0a-44ea-9678-ad40a662c258">SubmitChanges Method Example</legacyLink>
          </para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Properties</title>
    <content>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="06297993-fe72-4446-aa76-3b8bc25444f6">Connect Property Example</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="753a4a3d-0fba-40b8-86e7-50b34182ca69">ExecuteOptions and FetchOptions Properties Example</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="8a74802f-34d6-4676-bf94-07df5f8bff66">FilterColumn, FilterCriterion, FilterValue, SortColumn, and SortDirection Properties Example</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="e3e18da4-0511-4ece-a35d-699978bc28c6">ReadyState Property Example</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="95175316-cd10-4cf7-96ba-2a226fd97701">Recordset and SourceRecordset Properties Example</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="0fe57af9-a4d0-4986-a2e3-beaa4d26ed58">Server Property Example</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="32c33bcf-3320-4836-9e2e-99c8978ce581">SQL Property Example</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="6ae5ac50-c88c-4262-b7ab-f2b3de382a0b">URL Property Example</legacyLink>
          </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>