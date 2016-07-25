---
title: "EventStatusEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: ebfd4cda-4017-4873-9d28-38b1c7db12a8
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
# EventStatusEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the current status of the execution of an event.</para>
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
              <legacyBold>adStatusCancel</legacyBold>
            </para>
          </TD>
          <TD>
            <para>4</para>
          </TD>
          <TD>
            <para>Requests cancellation of the operation that caused the event to occur.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adStatusCantDeny</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3</para>
          </TD>
          <TD>
            <para>Indicates that the operation cannot request cancellation of the pending operation.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adStatusErrorsOccurred</legacyBold>
            </para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>Indicates that the operation that caused the event failed due to an error or errors.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adStatusOK</legacyBold>
            </para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>Indicates that the operation that caused the event was successful.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adStatusUnwantedEvent</legacyBold>
            </para>
          </TD>
          <TD>
            <para>5</para>
          </TD>
          <TD>
            <para>Prevents subsequent notifications before the event method has finished executing.</para>
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
              <para>AdoEnums.EventStatus.CANCEL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.EventStatus.CANTDENY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.EventStatus.ERRORSOCCURRED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.EventStatus.OK</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.EventStatus.UNWANTEDEVENT</para>
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
                <link xlink:href="ec4e4b38-e9c6-4757-b2ef-4e468ae5f1d8">BeginTransComplete, CommitTransComplete, and RollbackTransComplete Events</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="568f5252-d069-4d99-a01b-2ada87ad1304">ConnectComplete and Disconnect Events</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="475de5e2-f634-4954-9edf-0027a6ba38d6">EndOfRecordset Event</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="62470d42-e511-494c-bec4-ad4591734b7b">ExecuteComplete Event</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="a28d3858-566c-468d-b070-d1de4339fbea">FetchComplete Event</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="468c87dd-e3bc-4084-9941-94d10743d4e9">InfoMessage Event</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="3e49fb89-c45b-4d39-823e-3cc887c59b37">WillChangeField and FieldChangeComplete Events</link>
              </para>
            </TD>
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
                <link xlink:href="da561d58-eb58-446c-a4fd-1838c76073c0">WillConnect Event</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="dd755e46-f589-48a3-93a9-51ff998d44b5">WillExecute Event</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="1a3d1042-4f30-4526-a0c7-853c242496db">WillMove and MoveComplete Events</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>