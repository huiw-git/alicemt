---
title: "MoveRecordOptionsEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: f53c2ce4-1021-4a45-92b8-775e8bebad99
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
# MoveRecordOptionsEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the behavior of the <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> object <legacyLink xlink:href="6d2807b0-b861-4583-bcaf-fb0b82e0f2d0">MoveRecord</legacyLink> method.</para>
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
              <legacyBold>adMoveUnspecified</legacyBold>
            </para>
          </TD>
          <TD>
            <para>-1</para>
          </TD>
          <TD>
            <para>Default. Performs the default move operation: The operation fails if the destination file or directory already exists, and the operation updates hypertext links.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adMoveOverWrite</legacyBold>
            </para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>Overwrites the destination file or directory, even if it already exists.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adMoveDontUpdateLinks</legacyBold>
            </para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>Modifies the default behavior of <legacyBold>MoveRecord</legacyBold> method by not updating the hypertext links of the source <legacyBold>Record</legacyBold>. The default behavior depends on the capabilities of the provider. Move operation updates links if the provider is capable. If the provider cannot fix links or if this value is not specified, then the move succeeds even when links have not been fixed.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adMoveAllowEmulation</legacyBold>
            </para>
          </TD>
          <TD>
            <para>4</para>
          </TD>
          <TD>
            <para>Requests that the provider attempt to simulate the move (using download, upload, and delete operations). If the attempt to move the <legacyBold>Record</legacyBold> fails because the destination URL is on a different server or serviced by a different provider than the source, this may cause increased latency or data loss, due to different provider capabilities when moving resources between providers.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <section>
    <title>ADO/WFC Equivalent</title>
    <content>
      <para>These constants do not have ADO/WFC equivalents.</para>
    </content>
  </section>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="6d2807b0-b861-4583-bcaf-fb0b82e0f2d0">MoveRecord Method</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>