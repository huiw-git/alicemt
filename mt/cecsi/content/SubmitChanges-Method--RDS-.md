---
title: "SubmitChanges Method (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 250062a4-13c4-4bed-807d-8b9ad81536d4
caps.latest.revision: 14
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
# SubmitChanges Method (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Submits pending changes of the locally cached and updatable <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> to the data source specified in the <legacyLink xlink:href="dbad5e77-b213-4eb8-aecf-d60f203fdb59">Connect</legacyLink> property or the <legacyLink xlink:href="8c56b233-1be8-442c-8d0e-a4c96465bc99">URL</legacyLink> property.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>DataControl.</parameterReference><legacyBold>SubmitChanges </legacyBold><parameterReference>DataFactory</parameterReference>.<legacyBold>SubmitChanges </legacyBold><parameterReference>Connection, Recordset</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>DataControl</legacyItalic> </definedTerm>
        <definition>
          <para>An object variable that represents an <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object.</para>
        </definition>
        <definedTerm> <legacyItalic>DataFactory</legacyItalic> </definedTerm>
        <definition>
          <para>An object variable that represents an <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">RDSServer.DataFactory</legacyLink> object.</para>
        </definition>
        <definedTerm> <legacyItalic>Connection</legacyItalic> </definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> value that represents the connection created with the <unmanagedCodeEntityReference>RDS.DataControl</unmanagedCodeEntityReference> object's <legacyLink xlink:href="dbad5e77-b213-4eb8-aecf-d60f203fdb59">Connect</legacyLink> property.</para>
        </definition>
        <definedTerm> <legacyItalic>Recordset</legacyItalic> </definedTerm>
        <definition>
          <para>An object variable that represents a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyLink xlink:href="dbad5e77-b213-4eb8-aecf-d60f203fdb59">Connect</legacyLink>, <legacyLink xlink:href="d2727ce7-da9f-4271-ae3c-9334ef477c14">Server</legacyLink>, and <legacyLink xlink:href="e0dabf23-a159-4fe5-a962-3df544a21f5c">SQL</legacyLink> properties must be set before you can use the <unmanagedCodeEntityReference>SubmitChanges</unmanagedCodeEntityReference> method with the <unmanagedCodeEntityReference>RDS.DataControl</unmanagedCodeEntityReference> object.</para>
      <para>If you call the <legacyLink xlink:href="76d8a6e9-bc6c-4ea0-8e7a-2bae5ed06650">CancelUpdate</legacyLink> method after you have called <unmanagedCodeEntityReference>SubmitChanges</unmanagedCodeEntityReference> for the same <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object, the <unmanagedCodeEntityReference>CancelUpdate</unmanagedCodeEntityReference> call fails because the changes have already been committed.</para>
      <para>Only the changed records are sent for modification, and either all of the changes succeed or all the changes fail together.</para>
      <para>You can use <unmanagedCodeEntityReference>SubmitChanges</unmanagedCodeEntityReference> only with the default <unmanagedCodeEntityReference>RDSServer.DataFactory</unmanagedCodeEntityReference> object. Custom business objects cannot use this method.</para>
      <para>If the <unmanagedCodeEntityReference>URL</unmanagedCodeEntityReference> property has been set, <unmanagedCodeEntityReference>SubmitChanges</unmanagedCodeEntityReference> will submit changes to the location specified by the URL.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">DataFactory Object (RDSServer)</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="619bc7fd-ad0a-44ea-9678-ad40a662c258">VBScript Example</link>
<link xlink:href="80676831-6488-4dad-a558-c47c52256a22">Address Book Command Buttons</link>
<link xlink:href="76d8a6e9-bc6c-4ea0-8e7a-2bae5ed06650">CancelUpdate Method (RDS)</link>
<link xlink:href="c90a8050-0ff4-4c83-9925-261f2f2ccfe9">Refresh Method (RDS)</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>