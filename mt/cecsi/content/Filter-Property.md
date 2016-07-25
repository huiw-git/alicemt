---
title: "Filter Property"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 80263a7a-5d21-45d1-84fc-34b7a9be4c22
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
# Filter Property
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates a filter for data in a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <legacyBold>Variant</legacyBold> value, which can contain one of the following: </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyBold>Criteria string</legacyBold> — a string made up of one or more individual clauses concatenated with <legacyBold>AND</legacyBold> or <legacyBold>OR</legacyBold> operators. </para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Array of bookmarks</legacyBold> — an array of unique bookmark values that point to records in the <legacyBold>Recordset</legacyBold> object. </para>
        </listItem>
        <listItem>
          <para>A <link xlink:href="b22e725e-84bd-4286-a070-290c278c3783">FilterGroupEnum</link> value.</para>
        </listItem>
      </list>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>Filter</legacyBold> property to selectively screen out records in a <legacyBold>Recordset</legacyBold> object. The filtered <legacyBold>Recordset</legacyBold> becomes the current cursor. Other properties that return values based on the current <legacyBold>cursor</legacyBold> are affected, such as <link xlink:href="79f8ee5e-fc70-46d8-8c29-ebf943c66592">AbsolutePosition Property (ADO)</link>, <link xlink:href="ddb58a35-ec3a-423c-a504-3c65e62c23d4">AbsolutePage Property (ADO)</link>, <link xlink:href="834f0121-394a-44d4-ad7d-999b43a6fe63">RecordCount Property (ADO)</link>, and <link xlink:href="b601b56c-0ac4-44ee-bc91-c3d2d104f00a">PageCount Property (ADO)</link>. This is because setting the <legacyBold>Filter</legacyBold> property to a specific value will move the current record to the first record that satisfies the new value.</para>
      <para>The criteria string is made up of clauses in the form <legacyItalic>FieldName-Operator-Value</legacyItalic> (for example, <codeInline>"LastName = 'Smith'"</codeInline>). You can create compound clauses by concatenating individual clauses with <legacyBold>AND</legacyBold> (for example, <codeInline>"LastName = 'Smith' AND FirstName = 'John'"</codeInline>) or <legacyBold>OR</legacyBold> (for example, <codeInline>"LastName = 'Smith' OR LastName = 'Jones'"</codeInline>). Use the following guidelines for criteria strings:</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyItalic>FieldName</legacyItalic> must be a valid field name from the <legacyBold>Recordset</legacyBold>. If the field name contains spaces, you must enclose the name in square brackets. </para>
        </listItem>
        <listItem>
          <para>Operator must be one of the following: &lt;, &gt;, &lt;=, &gt;=, &lt;&gt;, =, or <legacyBold>LIKE</legacyBold>. </para>
        </listItem>
        <listItem>
          <para>Value is the value with which you will compare the field values (for example, 'Smith', #8/24/95#, 12.345, or $50.00). Use single quotes with strings and pound signs (#) with dates. For numbers, you can use decimal points, dollar signs, and scientific notation. If Operator is <legacyBold>LIKE</legacyBold>, Value can use wildcards. Only the asterisk (*) and percent sign (%) wild cards are allowed, and they must be the last character in the string. Value cannot be null.</para>
        </listItem>
      </list>
      <alert class="note">
        <para>To include single quotation marks (') in the filter Value, use two single quotation marks to represent one. For example, to filter on O'Malley, the criteria string should be "col1 = 'O''Malley'". To include single quotation marks at both the beginning and the end of the filter value, enclose the string with pound signs (#). For example, to filter on '1', the criteria string should be "col1 = #'1'#".</para>
      </alert>
      <list class="bullet">
        <listItem>
          <para>There is no precedence between AND and OR. Clauses can be grouped within parentheses. However, you cannot group clauses joined by an OR and then join the group to another clause with an AND, like this: <codeInline>(LastName = 'Smith' OR LastName = 'Jones') AND FirstName = 'John'</codeInline></para>
        </listItem>
        <listItem>
          <para>Instead, you would construct this filter as <codeInline>(LastName = 'Smith' AND FirstName = 'John') OR (LastName = 'Jones' AND FirstName = 'John')</codeInline></para>
        </listItem>
        <listItem>
          <para>In a <legacyBold>LIKE</legacyBold> clause, you can use a wildcard at the beginning and end of the pattern (for example, LastName Like '*mit*'), or only at the end of the pattern (for example, LastName Like 'Smit*').</para>
        </listItem>
      </list>
      <para>The filter constants make it easier to resolve individual record conflicts during batch update mode by allowing you to view, for example, only those records that were affected during the last <link xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch Method</link> method call.</para>
      <para>Setting the Filter property itself may fail because of a conflict with the underlying data (for example, a record has already been deleted by another user). In such a case, the provider returns warnings to the <link xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors Collection (ADO)</link> collection but does not halt program execution. A run-time error occurs only if there are conflicts on all the requested records. Use the <link xlink:href="41d70d89-880f-4850-9d17-19d9790cc8eb">Status Property (ADO Recordset)</link> property to locate records with conflicts.</para>
      <para>Setting the <legacyBold>Filter</legacyBold> property to a zero-length string ("") has the same effect as using the <legacyBold>adFilterNone</legacyBold> constant.</para>
      <para>Whenever the <legacyBold>Filter</legacyBold> property is set, the current record position moves to the first record in the filtered subset of records in the <legacyBold>Recordset</legacyBold>. Similarly, when the <legacyBold>Filter</legacyBold> property is cleared, the current record position moves to the first record in the <legacyBold>Recordset</legacyBold>.</para>
      <para>When a <legacyBold>Recordset</legacyBold> is filtered based on a field of some variant type (e.g., sql_variant), an error (DISP_E_TYPEMISMATCH or 80020005) will result if the subtypes of the field and filter values used in the criteria string do not match. For example, if a <legacyBold>Recordset</legacyBold> object (rs) contains a column (C) of the sql_variant type and a field of this column has been assigned a value of 1 of the I4 type, setting the criteria string of rs.Filter = "C='A'" on the field will produce the error at run time. However, rs.Filter = "C=2" applied on the same field will not produce any error although the field will be filtered out of the current record set.</para>
      <para>See the <link xlink:href="481dcc93-487b-490e-ac58-a1e9b2ebfd43">Bookmark Property (ADO)</link> property for an explanation of bookmark values from which you can build an array to use with the Filter property.</para>
      <para>Only Filters in the form of Criteria Strings (e.g. OrderDate &gt; '12/31/1999') affect the contents of a persisted <legacyBold>Recordset</legacyBold>. Filters created with an Array of Bookmarks or using a value from the FilterGroupEnum will not affect the contents of the persisted <legacyBold>Recordset</legacyBold>. These rules apply to Recordsets created with either client-side or server-side cursors.</para>
      <alert class="note">
        <para>When you apply the adFilterPendingRecords flag to a filtered and modified <legacyBold>Recordset</legacyBold> in the batch update mode, the resultant <legacyBold>Recordset</legacyBold> is empty if the filtering was based on the key field of a single-keyed table and the modification was made on the key field values. The resultant <legacyBold>Recordset</legacyBold> will be non-empty if one of the following is true:</para>
      </alert>
      <list class="bullet">
        <listItem>
          <para>The filtering was based on non-key fields in a single-keyed table. </para>
        </listItem>
        <listItem>
          <para>The filtering was based on any fields in a multiple-keyed table. </para>
        </listItem>
        <listItem>
          <para>Modifications were made on non-key fields in a single-keyed table. </para>
        </listItem>
        <listItem>
          <para>Modifications were made on any fields in a multiple-keyed table. </para>
        </listItem>
      </list>
      <para>The following table summarizes the effects of <legacyBold>adFilterPendingRecords</legacyBold> in different combinations of filtering and modifications. The left column shows the possible modifications; modifications can be made on any of the non-keyed fields, on the key field in a single-keyed table, or on any of the key fields in a multiple-keyed table. The top row shows the filtering criterion; filtering can be based on any of the non-keyed fields, the key field in a single-keyed table, or any of the key fields in a multiple-keyed table. The intersecting cells show the results: + means that applying <legacyBold>adFilterPendingRecords</legacyBold> results in a non-empty <legacyBold>Recordset</legacyBold>; - means an empty <legacyBold>Recordset</legacyBold>.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para>Non keys</para>
            </TD>
            <TD>
              <para>Single Key</para>
            </TD>
            <TD>
              <para>Multiple Keys</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyBold>Non keys</legacyBold>
              </para>
            </TD>
            <TD>
              <para>+</para>
            </TD>
            <TD>
              <para>+</para>
            </TD>
            <TD>
              <para>+</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Single Key</legacyBold>
              </para>
            </TD>
            <TD>
              <para>+</para>
            </TD>
            <TD>
              <para>-</para>
            </TD>
            <TD>
              <para>N/A</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Multiple Keys</legacyBold>
              </para>
            </TD>
            <TD>
              <para>+</para>
            </TD>
            <TD>
              <para>N/A</para>
            </TD>
            <TD>
              <para>+</para>
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
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object_ADO</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="e8bc63c7-8967-438a-9a49-512478a87a15">Filter and RecordCount Properties Example (VB)</link>
<link xlink:href="b71346cb-3b09-4b8c-a600-976171a1c336">Filter and RecordCount Properties Example (VC++)</link>
<link xlink:href="16d5d896-9905-4f75-973b-e1e696cd169f">Filter and RecordCount Properties Example (VJ++)</link>
<link xlink:href="0a61ba7a-20b8-426a-91a0-9040e7c5a98a">Clear Method (ADO)</link>
<link xlink:href="a491c4ce-2b04-4c84-be83-3846bde8d16b">Optimize Property-Dynamic (ADO)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>