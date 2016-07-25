---
title: "EventReasonEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 7d4a5496-ec2d-4936-b36a-7049a82be4b4
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
# EventReasonEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the reason that caused an event to occur.</para>
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
              <legacyBold>adRsnAddNew</legacyBold>
            </para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>An operation added a new record.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRsnClose</legacyBold>
            </para>
          </TD>
          <TD>
            <para>9</para>
          </TD>
          <TD>
            <para>An operation closed the <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRsnDelete</legacyBold>
            </para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>An operation deleted a record.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRsnFirstChange</legacyBold>
            </para>
          </TD>
          <TD>
            <para>11</para>
          </TD>
          <TD>
            <para>An operation made the first change to a record.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRsnMove</legacyBold>
            </para>
          </TD>
          <TD>
            <para>10</para>
          </TD>
          <TD>
            <para>An operation moved the record pointer within the <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRsnMoveFirst</legacyBold>
            </para>
          </TD>
          <TD>
            <para>12</para>
          </TD>
          <TD>
            <para>An operation moved the record pointer to the first record in the <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRsnMoveLast</legacyBold>
            </para>
          </TD>
          <TD>
            <para>15</para>
          </TD>
          <TD>
            <para>An operation moved the record pointer to the last record in the <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRsnMoveNext</legacyBold>
            </para>
          </TD>
          <TD>
            <para>13</para>
          </TD>
          <TD>
            <para>An operation moved the record pointer to the next record in the <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRsnMovePrevious</legacyBold>
            </para>
          </TD>
          <TD>
            <para>14</para>
          </TD>
          <TD>
            <para>An operation moved the record pointer to the previous record in the <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRsnRequery</legacyBold>
            </para>
          </TD>
          <TD>
            <para>7</para>
          </TD>
          <TD>
            <para>An operation requeried the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRsnResynch</legacyBold>
            </para>
          </TD>
          <TD>
            <para>8</para>
          </TD>
          <TD>
            <para>An operation resynchronized the <legacyBold>Recordset</legacyBold> with the database.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRsnUndoAddNew</legacyBold>
            </para>
          </TD>
          <TD>
            <para>5</para>
          </TD>
          <TD>
            <para>An operation reversed the addition of a new record.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRsnUndoDelete</legacyBold>
            </para>
          </TD>
          <TD>
            <para>6</para>
          </TD>
          <TD>
            <para>An operation reversed the deletion of a record.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRsnUndoUpdate</legacyBold>
            </para>
          </TD>
          <TD>
            <para>4</para>
          </TD>
          <TD>
            <para>An operation reversed the update of a record.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRsnUpdate</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3</para>
          </TD>
          <TD>
            <para>An operation updated an existing record.</para>
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
              <para>AdoEnums.EventReason.ADDNEW</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.EventReason.CLOSE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.EventReason.DELETE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.EventReason.FIRSTCHANGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.EventReason.MOVE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.EventReason.MOVEFIRST</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.EventReason.MOVELAST</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.EventReason.MOVENEXT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.EventReason.MOVEPREVIOUS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.EventReason.REQUERY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.EventReason.RESYNCH</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.EventReason.UNDOADDNEW</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.EventReason.UNDODELETE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.EventReason.UNDOUPDATE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.EventReason.UPDATE</para>
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
                <link xlink:href="cbc369fd-63af-4a7d-96ae-efa91b78ca69">WillChangeRecord and RecordChangeComplete Events</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="d5d44659-e0d9-46d9-a297-99c43555082f">WillChangeRecordset and RecordsetChangeComplete Events</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="1a3d1042-4f30-4526-a0c7-853c242496db">WillMove and MoveComplete Events</link>
              </para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>