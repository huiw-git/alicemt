---
title: "BOF, EOF Properties (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 36c31ab2-f3b6-4281-89b6-db7e04e38fd2
caps.latest.revision: 12
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
# BOF, EOF Properties (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>BOF</legacyBold>     Indicates that the current record position is before the first record in a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>EOF</legacyBold>     Indicates that the current record position is after the last record in a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object.</para>
      </listItem>
    </list>
  </introduction>
  <section>
    <title>Return Value</title>
    <content>
      <para>The <unmanagedCodeEntityReference>BOF</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>EOF</unmanagedCodeEntityReference> properties return <languageKeyword>Boolean</languageKeyword> values.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>BOF</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>EOF</unmanagedCodeEntityReference> properties to determine whether a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object contains records or whether you have gone beyond the limits of a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object when you move from record to record.</para>
      <para>The <unmanagedCodeEntityReference>BOF</unmanagedCodeEntityReference> property returns <languageKeyword>True</languageKeyword> (-1) if the current record position is before the first record and <languageKeyword>False</languageKeyword> (0) if the current record position is on or after the first record.</para>
      <para>The <unmanagedCodeEntityReference>EOF</unmanagedCodeEntityReference> property returns <languageKeyword>True</languageKeyword> if the current record position is after the last record and <languageKeyword>False</languageKeyword> if the current record position is on or before the last record.</para>
      <para>If either the <unmanagedCodeEntityReference>BOF</unmanagedCodeEntityReference> or <unmanagedCodeEntityReference>EOF</unmanagedCodeEntityReference> property is <languageKeyword>True</languageKeyword>, there is no current record.</para>
      <para>If you open a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object containing no records, the <unmanagedCodeEntityReference>BOF</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>EOF</unmanagedCodeEntityReference> properties are set to <languageKeyword>True</languageKeyword> (see the <legacyLink xlink:href="834f0121-394a-44d4-ad7d-999b43a6fe63">RecordCount</legacyLink> property for more information about this state of a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>). When you open a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object that contains at least one record, the first record is the current record and the <unmanagedCodeEntityReference>BOF</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>EOF</unmanagedCodeEntityReference> properties are <languageKeyword>False</languageKeyword>.</para>
      <para>If you delete the last remaining record in the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object, the <unmanagedCodeEntityReference>BOF</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>EOF</unmanagedCodeEntityReference> properties may remain <languageKeyword>False</languageKeyword> until you attempt to reposition the current record.</para>
      <para>This table shows which <legacyBold>Move</legacyBold> methods are allowed with different combinations of the <unmanagedCodeEntityReference>BOF</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>EOF</unmanagedCodeEntityReference> properties.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>
                <legacyBold> </legacyBold> </para>
            </TD>
            <TD>
              <para>MoveFirst,</para>
              <para>MoveLast</para>
            </TD>
            <TD>
              <para>MovePrevious,</para>
              <para>Move &lt; 0</para>
            </TD>
            <TD>
              <para>Move 0</para>
            </TD>
            <TD>
              <para>MoveNext,</para>
              <para>Move &gt; 0</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <unmanagedCodeEntityReference>BOF</unmanagedCodeEntityReference>=<languageKeyword>True</languageKeyword>, <unmanagedCodeEntityReference>EOF</unmanagedCodeEntityReference>=<languageKeyword>False</languageKeyword> </para>
            </TD>
            <TD>
              <para>Allowed</para>
            </TD>
            <TD>
              <para>Error</para>
            </TD>
            <TD>
              <para>Error</para>
            </TD>
            <TD>
              <para>Allowed</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <unmanagedCodeEntityReference>BOF</unmanagedCodeEntityReference>=<languageKeyword>False</languageKeyword>, <unmanagedCodeEntityReference>EOF</unmanagedCodeEntityReference>=<languageKeyword>True</languageKeyword> </para>
            </TD>
            <TD>
              <para>Allowed</para>
            </TD>
            <TD>
              <para>Allowed</para>
            </TD>
            <TD>
              <para>Error</para>
            </TD>
            <TD>
              <para>Error</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Both <languageKeyword>True</languageKeyword></para>
            </TD>
            <TD>
              <para>Error</para>
            </TD>
            <TD>
              <para>Error</para>
            </TD>
            <TD>
              <para>Error</para>
            </TD>
            <TD>
              <para>Error</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Both <languageKeyword>False</languageKeyword></para>
            </TD>
            <TD>
              <para>Allowed</para>
            </TD>
            <TD>
              <para>Allowed</para>
            </TD>
            <TD>
              <para>Allowed</para>
            </TD>
            <TD>
              <para>Allowed</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>Allowing a <legacyBold>Move</legacyBold> method does not guarantee that the method will successfully locate a record; it only means that calling the specified <legacyBold>Move</legacyBold> method will not generate an error.</para>
      <para>The following table shows what happens to the <unmanagedCodeEntityReference>BOF</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>EOF</unmanagedCodeEntityReference> property settings when you call various <legacyBold>Move</legacyBold> methods but are unable to successfully locate a record.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>
                <legacyBold> </legacyBold> </para>
            </TD>
            <TD>
              <para>BOF</para>
            </TD>
            <TD>
              <para>EOF</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyBold>MoveFirst</legacyBold>, <legacyBold>MoveLast</legacyBold></para>
            </TD>
            <TD>
              <para>Set to <languageKeyword>True</languageKeyword></para>
            </TD>
            <TD>
              <para>Set to <languageKeyword>True</languageKeyword></para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Move</legacyBold> 0</para>
            </TD>
            <TD>
              <para>No change</para>
            </TD>
            <TD>
              <para>No change</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>MovePrevious</legacyBold>, <legacyBold>Move</legacyBold> &lt; 0</para>
            </TD>
            <TD>
              <para>Set to <languageKeyword>True</languageKeyword></para>
            </TD>
            <TD>
              <para>No change</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>MoveNext</legacyBold>, <legacyBold>Move</legacyBold> &gt; 0</para>
            </TD>
            <TD>
              <para>No change</para>
            </TD>
            <TD>
              <para>Set to <languageKeyword>True</languageKeyword></para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b6573c6e-fee8-4267-a722-fadaec6eafe6">Visual Basic Example</link>
<link xlink:href="bd2b9d85-e75e-4fc8-a392-076582019caa">Visual C++ Example</link>
<link xlink:href="eecd75a8-3e4f-4a18-b1c1-4c053dd7833f">Visual J++ Example</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>