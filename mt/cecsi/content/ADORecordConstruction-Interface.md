---
title: "ADORecordConstruction Interface"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 52a5429e-5829-455e-be3b-31f05cbecf2d
caps.latest.revision: 8
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
# ADORecordConstruction Interface
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>ADORecordConstruction</legacyBold>interface is used to construct an ADO <legacyBold>Record</legacyBold> object from an OLE DB <legacyBold>Row</legacyBold> object in a C/C++ application.</para>
    <para>This interface supports the following properties:</para>
  </introduction>
  <section>
    <title>Properties</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
              <legacyLink xlink:href="5ea8029b-eda4-490b-ae84-2ad036fb582f">ParentRow</legacyLink>
            </para>
            </TD>
            <TD>
              <para>Write-only.
Sets the container of an OLE DB <legacyBold>Row</legacyBold> object on this ADO <legacyBold>Record</legacyBold> object.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyLink xlink:href="21019d89-2dd1-4a26-ac6f-384b81d66949">Row</legacyLink>
            </para>
            </TD>
            <TD>
              <para>Read/Write.
Gets/sets an OLE DB <legacyBold>Row</legacyBold> object from/on this ADO <legacyBold>Record</legacyBold> object.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Methods</title>
    <content>
      <para>None.</para>
    </content>
  </section>
  <section>
    <title>Events</title>
    <content>
      <para>None.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Given an OLE DB <legacyBold>Row</legacyBold> object (<codeInline>pRow</codeInline>), the construction of an ADO <legacyBold>Record</legacyBold> object (<codeInline>adoR</codeInline>), amounts to the following three basic operations:

</para>
      <list class="ordered">
        <listItem>
          <para>Create an ADO <legacyBold>Record</legacyBold> object:
</para>
          <code>_RecordPtr adoR;
adoRs.CreateInstance(__uuidof(_Record));</code>
        </listItem>
        <listItem>
          <para>Query the <legacyBold>IADORecordConstruction</legacyBold> interface on the <legacyBold>Record</legacyBold> object:
</para>
          <code>adoRecordConstructionPtr adoRConstruct=NULL;
adoR-&gt;QueryInterface(__uuidof(ADORecordConstruction),
                    (void**)&amp;adoRConstruct);</code>
        </listItem>
        <listItem>
          <para>Call the <legacyBold>IADORecordConstruction::put_Row</legacyBold> property method to set the OLE DB <legacyBold>Row</legacyBold> object on the ADO <legacyBold>Record</legacyBold> object:
</para>
          <code>IUnknown *pUnk=NULL;
pRow-&gt;QueryInterface(IID_IUnknown, (void**)&amp;pUnk);
adoRConstruct-&gt;put_Row(pUnk);</code>
        </listItem>
      </list>
      <para>The resultant <legacyBold>adoR</legacyBold> object now represents the ADO <legacyBold>Record</legacyBold> object constructed from the OLE DB <legacyBold>Row</legacyBold> object.</para>
      <para>An ADO <legacyBold>Record</legacyBold> object can also be constructed from the container of an OLE DB <legacyBold>Row</legacyBold> object.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Requirements</title>
    <content>
      <para>
        <legacyBold>Version:</legacyBold> ADO 2.0 and later</para>
      <para>
        <legacyBold>Library:</legacyBold> msado15.dll</para>
      <para>
        <legacyBold>UUID:</legacyBold> 00000567-0000-0010-8000-00AA006D2EA4</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>