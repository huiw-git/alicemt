---
title: "Working with Recordsets"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bdf9a56a-de4a-44de-9111-2f11ab7b16ea
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
# Working with Recordsets
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>Recordset</legacyBold> object has built-in features that let you rearrange the order of the data in the result set, to search for a specific record based on criteria that you supply, and even to optimize those search operations using indexes. Whether these features are available for use depends on the provider and in some cases — such as that of the <legacyLink xlink:href="1c79e271-21ec-41a8-8163-c5e89f0001a7">Index</legacyLink> property — the structure of the data source itself.</para>
  </introduction>
  <section>
    <title>Arranging Data</title>
    <content>
      <para>Frequently, the most efficient way to order the data in your <legacyBold>Recordset</legacyBold> is by specifying an ORDER BY clause in the SQL command used to return results to it. However, you might have to change the order of the data in a <legacyBold>Recordset</legacyBold> that has already been created. You can use the <legacyBold>Sort</legacyBold> property to establish the order in which rows of a <legacyBold>Recordset</legacyBold> are traversed. Additionally, the <legacyBold>Filter</legacyBold> property determines which rows are can be accessed when traversing rows.</para>
      <para>The <legacyBold>Sort</legacyBold> property sets or returns a <legacyBold>String</legacyBold> value that indicates the field names in the <legacyBold>Recordset</legacyBold> on which to sort. Each name is separated by a comma and is optionally followed by a space and the keyword <legacyBold>ASC</legacyBold> (which sorts the field in ascending order) or <legacyBold>DESC</legacyBold> (which sorts the field in descending order). By default, if no keyword is specified, the field is sorted in ascending order.</para>
      <para>The sort operation is efficient because data is not physically rearranged but is accessed in the order specified by an index.</para>
      <para>The <legacyBold>Sort</legacyBold> property requires the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property to be set to <legacyBold>adUseClient</legacyBold>. A temporary index will be created for each field specified in the <legacyBold>Sort</legacyBold> property if an index does not already exist.</para>
      <para>Setting the <legacyBold>Sort</legacyBold> property to an empty string will reset the rows to their original order and delete temporary indexes. Existing indexes will not be deleted.</para>
      <para>Suppose a <legacyBold>Recordset</legacyBold> contains three fields named <legacyItalic>firstName</legacyItalic>, <legacyItalic>middleInitial</legacyItalic>, and <legacyItalic>lastName</legacyItalic>. Set the <legacyBold>Sort</legacyBold> property to the string "<codeInline>lastName DESC, firstName ASC</codeInline>", which will order the <legacyBold>Recordset</legacyBold> by last name in descending order and then by first name in ascending order. The middle initial is ignored.</para>
      <para>No field referenced in a sort criteria string can be named "ASC" or "DESC" because those names conflict with the keywords <legacyBold>ASC</legacyBold> and <legacyBold>DESC</legacyBold>. Give a field that has a conflicting name an alias by using the <legacyBold>AS</legacyBold> keyword in the query that returns the <legacyBold>Recordset</legacyBold>.</para>
      <para>For more information about <legacyBold>Recordset</legacyBold> filtering, see "Filtering the Results" later in this topic.</para>
    </content>
  </section>
  <section>
    <title>Finding a Specific Record</title>
    <content>
      <para>ADO provides the <legacyLink xlink:href="55c9810a-d8ca-46c2-a9dc-80e7ee7aa188">Find</legacyLink> and <legacyLink xlink:href="129293d2-19d3-4940-bf64-483ee72fb4a1">Seek</legacyLink> methods for locating a particular record in a <legacyBold>Recordset</legacyBold>. The <legacyBold>Find</legacyBold> method is supported by a variety of providers but is limited to a single search criterion. The <legacyBold>Seek</legacyBold> method supports searching on multiple criteria, but is not supported by many providers.</para>
      <para>Indexes on fields can greatly enhance the performance of the <legacyBold>Find</legacyBold> method and <legacyBold>Sort</legacyBold> and <legacyBold>Filter</legacyBold> properties of the <legacyBold>Recordset</legacyBold> object. You can create an internal index for a <legacyBold>Field</legacyBold> object by setting its dynamic <legacyLink xlink:href="a491c4ce-2b04-4c84-be83-3846bde8d16b">Optimize</legacyLink> property. This dynamic property is added to the <legacyBold>Properties</legacyBold> collection of the <legacyBold>Field</legacyBold> object when you set the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property to <legacyBold>adUseClient</legacyBold>. Remember that this index is internal to ADO — you cannot gain access to it or use it for any other purpose. Also, this index is distinct from the <legacyLink xlink:href="1c79e271-21ec-41a8-8163-c5e89f0001a7">Index</legacyLink> property of the <legacyBold>Recordset</legacyBold> object.</para>
      <para>The <legacyBold>Find</legacyBold> method quickly locates a value within a column (field) of a <legacyBold>Recordset</legacyBold>. You can frequently improve the speed of the <legacyBold>Find</legacyBold> method on a column by using the <legacyBold>Optimize</legacyBold> property to create an index on it.</para>
      <para>The <legacyBold>Find</legacyBold> method limits your search to the contents of one field. The <legacyBold>Seek</legacyBold> method requires that you have an index and has other limitations as well. If you must search on multiple fields that are not the basis of an index, or if your provider does not support indexes, you can limit your results by using the <legacyBold>Filter</legacyBold> property of the <legacyBold>Recordset</legacyBold> object.</para>
    </content>
    <sections>
      <section>
        <title>Find</title>
        <content>
          <para>The <legacyBold>Find</legacyBold> method searches a <legacyBold>Recordset</legacyBold> for the row that satisfies a specified criterion. Optionally, the direction of the search, starting row, and offset from the starting row may be specified. If the criterion is met, the current row position is set on the found record; otherwise, the position is set to the end (or start) of the <legacyBold>Recordset</legacyBold>, depending on search direction.</para>
          <para>Only a single-column name can be specified for the criterion. In other words, this method does not support multicolumn searches.</para>
          <para>The comparison operator for the criterion can be "<legacyBold>&gt;</legacyBold>" (greater than), "<legacyBold>&lt;</legacyBold>" (less than), "=" (equal), "&gt;=" (greater than or equal), "&lt;=" (less than or equal), "&lt;&gt;" (not equal), or "LIKE" (pattern matching).</para>
          <para>The criterion value can be a string, floating-point number, or date. String values are delimited with single quotation marks or "#" (number sign) marks (for example, "state = 'WA'" or "state = #WA#"). Date values are delimited with "#" (number sign) marks (for example, "start_date &gt; #7/22/97#").</para>
          <para>If the comparison operator is "like", the string value can contain an asterisk (*) to find one or more occurrences of any character or substring. For example, "state like 'M*'" matches Maine and Massachusetts. You can also use leading and trailing asterisks to find a substring that is contained within the values. For example, "state like '*as*'" matches Alaska, Arkansas, and Massachusetts.</para>
          <para>Asterisks can be used only at the end of a criteria string or together at both the beginning and end of a criteria string, as shown earlier. You cannot use the asterisk as a leading wildcard ('*str') or embedded wildcard ('s*r'). This will cause an error.</para>
        </content>
      </section>
      <section>
        <title>Seek and Index</title>
        <content>
          <para>Use the <legacyBold>Seek</legacyBold> method together with the <legacyBold>Index</legacyBold> property if the underlying provider supports indexes on the <legacyBold>Recordset</legacyBold> object. Use the <legacyLink xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports</legacyLink><legacyBold>(adSeek)</legacyBold> method to determine whether the underlying provider supports <legacyBold>Seek</legacyBold>, and the <legacyBold>Supports(adIndex)</legacyBold> method to determine whether the provider supports indexes. (For example, the <legacyLink xlink:href="fd956da1-5203-40af-aa7e-fc13a6c6581f">OLE DB Provider for Microsoft Jet</legacyLink> supports <legacyBold>Seek</legacyBold> and <legacyBold>Index</legacyBold>.)</para>
          <para>If <legacyBold>Seek</legacyBold> does not find the desired row, no error occurs, and the row is positioned at the end of the <legacyBold>Recordset</legacyBold>. Set the <legacyBold>Index</legacyBold> property to the desired index before executing this method.</para>
          <para>This method is supported only with server-side cursors. Seek is not supported when the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property value of the <legacyBold>Recordset</legacyBold> object is <legacyBold>adUseClient</legacyBold>.</para>
          <para>This method can be used only when the <legacyBold>Recordset</legacyBold> object has been opened with a <legacyLink xlink:href="4b1feb9c-a855-40fe-a906-efe688687e9f">CommandTypeEnum</legacyLink> value of <legacyBold>adCmdTableDirect</legacyBold>.</para>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Filtering the Results</title>
    <content>
      <para>The <legacyBold>Find</legacyBold> method limits your search to the contents of one field. The <legacyBold>Seek</legacyBold> method requires that you have an index and has other limitations as well. If you must search on multiple fields that are not the basis of an index or if your provider does not support indexes, you can limit your results by using the <legacyBold>Filter</legacyBold> property of the <legacyBold>Recordset</legacyBold> object.</para>
      <para>Use the <legacyBold>Filter</legacyBold> property to selectively screen out records in a <legacyBold>Recordset</legacyBold> object. The filtered <legacyBold>Recordset</legacyBold> becomes the current cursor, which means that records that do not satisfy the <legacyBold>Filter</legacyBold> criteria are not available in the <legacyBold>Recordset</legacyBold> until the <legacyBold>Filter</legacyBold> is removed. Other properties that return values based on the current cursor are affected, such as <legacyBold>AbsolutePosition</legacyBold>, <legacyBold>AbsolutePage</legacyBold>, <legacyBold>RecordCount</legacyBold>, and <legacyBold>PageCount</legacyBold>. This is because setting the <legacyBold>Filter</legacyBold> property to a specific value will move the current record to the first record that satisfies the new value.</para>
      <para>The <legacyBold>Filter</legacyBold> property takes a variant argument. This value represents one of three methods for using the <legacyBold>Filter</legacyBold> property: a criteria string, a <legacyBold>FilterGroupEnum</legacyBold> constant, or an array of bookmarks. For more information, see Filtering with a Criteria String, Filtering with a Constant, and Filtering with Bookmarks later in this topic.</para>
      <alert class="note">
        <para>When you know the data that you want to select, it is usually more efficient to open a <legacyBold>Recordset</legacyBold> with an SQL statement that effectively filters the result set, instead of relying on the <legacyBold>Filter</legacyBold> property.</para>
      </alert>
      <para>To remove a filter from a <legacyBold>Recordset</legacyBold>, use the <legacyBold>adFilterNone</legacyBold> constant. Setting the <legacyBold>Filter</legacyBold> property to a zero-length string ("") has the same effect as using the <legacyBold>adFilterNone</legacyBold> constant.</para>
    </content>
    <sections>
      <section>
        <title>Filtering with a Criteria String</title>
        <content>
          <para>The criteria string consists of clauses in the form <legacyItalic>FieldName Operator Value</legacyItalic> (for example, <codeInline>"LastName = 'Smith'"</codeInline>). You can create compound clauses by concatenating individual clauses with <languageKeyword>AND</languageKeyword> (for example, <codeInline>"LastName = 'Smith' AND FirstName = 'John'"</codeInline>) and<languageKeyword> OR </languageKeyword>(for example, <codeInline>"LastName = 'Smith' OR LastName = 'Jones'"</codeInline>). Use the following guidelines for criteria strings:   </para>
          <list class="bullet">
            <listItem>
              <para>
                <legacyItalic>FieldName</legacyItalic> must be a valid field name from the <legacyBold>Recordset</legacyBold>. If the field name contains spaces, you must enclose the name in square brackets.</para>
            </listItem>
            <listItem>
              <para>
                <legacyItalic>Operator</legacyItalic> must be one of the following: <languageKeyword>&lt;</languageKeyword>, <languageKeyword>&gt;</languageKeyword>, <languageKeyword>&lt;=</languageKeyword>, <languageKeyword>&gt;=</languageKeyword>, <languageKeyword>&lt;&gt;</languageKeyword>, <languageKeyword>=</languageKeyword>, or <languageKeyword>LIKE</languageKeyword>.</para>
            </listItem>
            <listItem>
              <para>
                <legacyItalic>Value</legacyItalic> is the value with which you will compare the field values (for example, <codeInline>'Smith'</codeInline>, <codeInline>#8/24/95#</codeInline>, <codeInline>12.345</codeInline>, or <codeInline>$50.00</codeInline>). Use single quotation marks (') with strings and pound signs (<codeInline>#</codeInline>) with dates. For numbers, you can use decimal points, dollar signs, and scientific notation. If <legacyItalic>Operator</legacyItalic> is <languageKeyword>LIKE</languageKeyword>, <legacyItalic>Value</legacyItalic> can use wildcard characters. Only the asterisk (*) and percent sign (%) wildcard characters are allowed, and they must be the last character in the string. <legacyItalic>Value</legacyItalic> cannot be null.  </para>
              <alert class="note">
                <para>To include single quotation marks (') in the filter <legacyItalic>Value</legacyItalic>, use two single quotation marks to represent one. For example, to filter on <legacyItalic>O'Malley</legacyItalic>, the criteria string should be <codeInline>"col1 = 'O''Malley'"</codeInline>. To include single quotation marks at both the beginning and the end of the filter value, enclose the string in pound signs (#). For example, to filter on <legacyItalic>'1'</legacyItalic>, the criteria string should be <codeInline>"col1 = #'1'#"</codeInline>. </para>
              </alert>
            </listItem>
          </list>
          <para>There is no precedence between <languageKeyword>AND</languageKeyword> and <languageKeyword>OR</languageKeyword>. Clauses can be grouped within parentheses. However, you cannot group clauses joined by an <languageKeyword>OR</languageKeyword> and then join the group to another clause with an AND, as follows. </para>
          <code>(LastName = 'Smith' OR LastName = 'Jones') AND FirstName = 'John'</code>
          <para>Instead, you would construct this filter as follows. </para>
          <code>(LastName = 'Smith' AND FirstName = 'John') OR (LastName = 'Jones' AND FirstName = 'John')</code>
          <para>In a <languageKeyword>LIKE</languageKeyword> clause, you can use a wildcard at the beginning and end of the pattern (for example,<codeInline> LastName Like '*mit*'</codeInline>) or only at the end of the pattern (for example, <codeInline>LastName Like 'Smit*'</codeInline>). </para>
        </content>
      </section>
      <section>
        <title>Filtering with a Constant</title>
        <content>
          <para>The following constants are available for filtering <legacyBold>Recordsets</legacyBold>.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Constant</para>
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
                    <legacyBold>adFilterAffectedRecords</legacyBold>                 </para>
                </TD>
                <TD>
                  <para>Filters for viewing only records affected by the last <legacyBold>Delete</legacyBold>, <legacyBold>Resync</legacyBold>, <legacyBold>UpdateBatch</legacyBold>, or <legacyBold>CancelBatch</legacyBold> call.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <legacyBold>adFilterConflictingRecords</legacyBold>                 </para>
                </TD>
                <TD>
                  <para>Filters for viewing the records that failed the last batch update.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <legacyBold>adFilterFetchedRecords</legacyBold>                 </para>
                </TD>
                <TD>
                  <para>Filters for viewing the records in the current cache — that is, the results of the last call to retrieve records from the database.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <legacyBold>adFilterNone</legacyBold>                 </para>
                </TD>
                <TD>
                  <para>Removes the current filter and restores all records for viewing.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <legacyBold>adFilterPendingRecords</legacyBold>                 </para>
                </TD>
                <TD>
                  <para>Filters for viewing only records that have changed but have not yet been sent to the server. Applicable only for batch update mode.</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>The filter constants make it easier to resolve individual record conflicts during batch update mode by allowing you to view, for example, only those records that were affected during the last <legacyBold>UpdateBatch</legacyBold> method call, as shown in the following example.</para>
          <para>
            <codeInline>Attribute VB_Name = "modExaminingData"</codeInline>
          </para>
        </content>
      </section>
      <section>
        <title>Filtering with Bookmarks</title>
        <content>
          <para>Finally, you can pass a variant array of bookmarks to the <legacyBold>Filter</legacyBold> property. The resulting cursor will contain only those records whose bookmark was passed in to the property. The following code example creates an array of bookmarks from the records in a <legacyBold>Recordset</legacyBold> which have a "B" in the <legacyItalic>ProductName</legacyItalic> field. It then passes the array to the <legacyBold>Filter</legacyBold> property and displays information about the resulting filtered <legacyBold>Recordset</legacyBold>.</para>
          <code>    'BeginFilterBkmk
    Dim vBkmkArray() As Variant
    Dim i As Integer

    'Recordset created using "SELECT * FROM Products" as command.
    'So, we will check to see if ProductName has a capital B, and
    'if so, add to the array.
    i = 0
    Do While Not objRs.EOF
        If InStr(1, objRs("ProductName"), "B") Then
            ReDim Preserve vBkmkArray(i)
            vBkmkArray(i) = objRs.Bookmark
            i = i + 1
            Debug.Print objRs("ProductName")
        End If
        objRs.MoveNext
    Loop
    
    'Filter using the array of bookmarks.
    objRs.Filter = vBkmkArray
    
    objRs.MoveFirst
    Do While Not objRs.EOF
        Debug.Print objRs("ProductName")
        objRs.MoveNext
    Loop
    'EndFilterBkmk</code>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Creating a Clone of a Recordset</title>
    <content>
      <para>Use the <legacyBold>Clone</legacyBold> method to create multiple, duplicate <legacyBold>Recordset</legacyBold> objects, especially if you want to maintain more than one current record in a given set of records. Using the <legacyBold>Clone</legacyBold> method is more efficient than creating and opening a new <legacyBold>Recordset</legacyBold> object with the same definition as the original.</para>
      <para>The current record of a newly created clone is originally set to the first record. The current record pointer in a cloned <legacyBold>Recordset</legacyBold> is not synchronized with the original or vice versa. You can navigate independently in each <legacyBold>Recordset</legacyBold>.</para>
      <para>Changes you make to one <legacyBold>Recordset</legacyBold> object are visible in all of its clones regardless of cursor type. However, after you execute <legacyLink xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery</legacyLink> on the original <legacyBold>Recordset</legacyBold>, the clones will no longer be synchronized to the original.</para>
      <para>Closing the original <legacyBold>Recordset</legacyBold> does not close its copies, nor does closing a copy close the original or any of the other copies.</para>
      <para>You can clone a <legacyBold>Recordset</legacyBold> object only if it supports bookmarks. Bookmark values are interchangeable; that is, a bookmark reference from one <legacyBold>Recordset</legacyBold> object refers to the same record in any of its clones.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>