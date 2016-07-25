---
title: "Boundaries of a Recordset"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c0dd4a0f-478d-4c5e-b5d5-7535f211d064
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
# Boundaries of a Recordset
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>       <legacyBold>Recordset</legacyBold> supports the <legacyBold>BOF</legacyBold> and <legacyBold>EOF</legacyBold> properties to delineate the beginning and end, respectively, of the dataset. You can think of <legacyBold>BOF</legacyBold> and <legacyBold>EOF</legacyBold> as "phantom" records that are positioned at the beginning and end of the <legacyBold>Recordset</legacyBold>. Counting <legacyBold>BOF</legacyBold> and <legacyBold>EOF</legacyBold>, our sample <legacyBold>Recordset</legacyBold> would now look like this:</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>ProductID</para>
          </TD>
          <TD>
            <para>ProductName</para>
          </TD>
          <TD>
            <para>UnitPrice</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>BOF</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>7</para>
          </TD>
          <TD>
            <para>Uncle Bob's Organic Dried Pears</para>
          </TD>
          <TD>
            <para>30.0000</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>14   </para>
          </TD>
          <TD>
            <para>Tofu</para>
          </TD>
          <TD>
            <para>23.2500</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>28   </para>
          </TD>
          <TD>
            <para>Rssle Sauerkraut</para>
          </TD>
          <TD>
            <para>45.6000</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>51   </para>
          </TD>
          <TD>
            <para>Manjimup Dried Apples</para>
          </TD>
          <TD>
            <para>53.0000</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>74</para>
          </TD>
          <TD>
            <para>Longlife Tofu</para>
          </TD>
          <TD>
            <para>10.0000</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>EOF</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>When a cursor moves past the last record, <legacyBold>EOF </legacyBold>is set to <legacyBold>True</legacyBold>; otherwise, its value is <legacyBold>False</legacyBold>. Similarly, when the cursor moves before the first record, <legacyBold>BOF</legacyBold> is set to <legacyBold>True</legacyBold>; otherwise, its value is <legacyBold>False</legacyBold>. These properties are commonly used to enumerate records in the dataset, as illustrated in the following JScript code fragment.</para>
    <code>while (objRecordset.EOF != true) 
{
   // Work on the current record.
   ...
   // Advance the cursor forward to the next record.
   objRecordset.MoveNext();
}
or
while (objRecordset.BOF != true) 
{
   // Work on the current record.
   ...
   // Move the cursor to the previous record.
   objRecordset.MovePrevious();
}</code>
    <para>If both <legacyBold>BOF</legacyBold> and <legacyBold>EOF</legacyBold> are <legacyBold>True</legacyBold>, the <legacyBold>Recordset</legacyBold> object is empty. Both properties will be <legacyBold>False</legacyBold> for a newly opened, non-empty <legacyBold>Recordset</legacyBold> object. You can use the <legacyBold>BOF</legacyBold> and <legacyBold>EOF</legacyBold> properties together to determine if a <legacyBold>Recordset</legacyBold> object is empty or not, as shown in the following JScript code fragment.</para>
    <code>if (objRecordset.EOF == true &amp;&amp; objRecordset.BOF == true)
{
   WScript.Echo("we got an empty dataset.");
}
else
{
   WScript.Echo("we got a full dataset.");
}</code>
    <para>This scheme works for all types of cursor and is independent of the underlying providers. If you attempt to determine the emptiness of a <legacyBold>Recordset</legacyBold> object by checking if its <legacyBold>RecordCount</legacyBold> property value is zero (0) or not, you must take precautions to use an appropriate cursor and provider that support returning of the number of records in the result. </para>
    <para>If you delete the last remaining record in the <legacyBold>Recordset</legacyBold> object, the cursor is left in an indeterminate state. The <legacyBold>BOF</legacyBold> and <legacyBold>EOF</legacyBold> properties may remain <legacyBold>False</legacyBold> until you attempt to reposition the current record, depending upon the provider. For more information, see <legacyLink xlink:href="bfed5cfa-7f57-463b-9da2-0c612a079d30">Deleting Records Using the Delete Method</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>