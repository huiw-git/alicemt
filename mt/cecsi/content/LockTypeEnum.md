---
title: "LockTypeEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: d2894eaf-4450-4ace-aa51-c8b875fd3010
caps.latest.revision: 10
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
# LockTypeEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the type of lock placed on records during editing.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Constant</para>
          </TD>
          <TD>
            <para>Value</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>
              <legacyBold>adLockBatchOptimistic</legacyBold>
            </para>
          </TD>
          <TD>
            <para>4</para>
          </TD>
          <TD>
            <para>Indicates optimistic batch updates. Required for batch update mode.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adLockOptimistic</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3</para>
          </TD>
          <TD>
            <para>Indicates optimistic locking, record by record. The provider uses optimistic locking, locking records only when you call the <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adLockPessimistic</legacyBold>
            </para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>Indicates pessimistic locking, record by record. The provider does what is necessary to ensure successful editing of the records, usually by locking records at the data source immediately after editing.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adLockReadOnly</legacyBold>
            </para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>Indicates read-only records. You cannot alter the data.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adLockUnspecified</legacyBold>
            </para>
          </TD>
          <TD>
            <para>-1</para>
          </TD>
          <TD>
            <para>Does not specify a type of lock. For clones, the clone is created with the same lock type as the original.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <section>
    <title>ADO/WFC Equivalent</title>
    <content>
      <para>Package: <legacyBold>com.ms.wfc.data</legacyBold></para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Constant</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>AdoEnums.LockType.BATCHOPTIMISTIC</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.LockType.OPTIMISTIC</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.LockType.PESSIMISTIC</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.LockType.READONLY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.LockType.UNSPECIFIED</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="ad49265f-1c05-4271-9bbf-7c00010ac18c">Clone Method</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="9920c14e-033a-4de1-8149-0ce9737a3246">LockType Property</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="dd755e46-f589-48a3-93a9-51ff998d44b5">WillExecute Event</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>