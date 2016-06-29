---
title: INDEX Command
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 694e8cf5-2f69-4001-9c1e-b735a4da3aff
translation.priority.ht: 
  - en-gb
---
# INDEX Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Creates an index file to display and access table records in a logical order.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
INDEX ON <parameterReference>eExpression</parameterReference> TO <parameterReference>IDXFileName</parameterReference> | TAG <parameterReference>TagName</parameterReference> [OF <parameterReference>CDXFileName</parameterReference>]
   [FOR <parameterReference>lExpression</parameterReference>]
   [COMPACT]
   [ASCENDING | DESCENDING]
   [UNIQUE | CANDIDATE]
   [ADDITIVE]</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>eExpression</legacyItalic> </definedTerm>
        <definition>
          <para>Specifies an index expression that can include the name of a field or fields from the current table. An index key based on the index expression is created in the index file for each record in the table. Visual FoxPro uses these keys to display and access records in the table.</para>
          <alert class="note">
            <para>Although not recommended, <legacyItalic>eExpression</legacyItalic> can also be a memory variable, an array element, or a field or field expression from a table in another work area. Memo fields cannot be used alone in index file expressions; they must be combined with other character expressions. If you access an index that contains a variable or field that no longer exists or cannot be located, Visual FoxPro generates an error message.</para>
          </alert>
          <para>If you attempt to build an index with a key that varies in length, the key will be padded with spaces. Variable-length index keys aren't supported in Visual FoxPro.


</para>
          <para>It is possible to create an index key with zero length. For example, a zero length index key is created when the index expression is a substring of an empty memo field. A zero length index key generates an error message. When Visual FoxPro creates an index, it evaluates fields in the first record in the table. If a field is empty, it might be necessary to enter some temporary data in the field in the first record to prevent a 0-length index key.
</para>
        </definition>
        <definedTerm>TO <legacyItalic>IDXFileName</legacyItalic></definedTerm>
        <definition>
          <para>Creates an .idx index file. The index file is given the default extension .idx.</para>
        </definition>
        <definedTerm>TAG <legacyItalic>TagName</legacyItalic>[OF <legacyItalic>CDXFileName</legacyItalic>] </definedTerm>
        <definition>
          <para>Creates a compound index file. A compound index file is a single index file that consists of any number of separate tags (index entries). Each tag is identified by its unique tag name. Tag names must begin with a letter or an underscore and can consist of any combination of up to 10 letters, digits, or underscores. The number of tags in a compound index file is limited only by available memory and disk space.</para>
          <para>Multiple-entry compound index files are always compact. It isn't necessary to include COMPACT when creating a compound index file. Names of compound index files are given a .cdx extension.


</para>
          <para>Two types of compound index files can be created: structural and nonstructural.


</para>
          <para>
            <legacyBold>Structural Compound Index Files   </legacyBold>You can create a structural compound index file with TAG <legacyItalic>TagName</legacyItalic> by excluding the optional OF <legacyItalic>CDXFileName</legacyItalic> clause. A structural compound index file always has the same base name as the table and is automatically opened when the table is opened.


</para>
          <para>
            <legacyBold>Nonstructural Compound Index Files   </legacyBold>You can create a nonstructural compound index file by including OF <legacyItalic>CDXFileName</legacyItalic> after TAG <legacyItalic>TagName</legacyItalic>. Unlike a structural compound index file, a nonstructural compound index file must be explicitly opened with the INDEX clause in USE.


</para>
          <para>If a compound index file has already been created and opened, issuing INDEX with TAG <legacyItalic>TagName</legacyItalic> adds a tag to the compound index file.
</para>
        </definition>
        <definedTerm>FOR <legacyItalic>lExpression</legacyItalic></definedTerm>
        <definition>
          <para>Specifies a condition whereby only records that satisfy the filter expression <legacyItalic>lExpression</legacyItalic> are available for display and access; index keys are created in the index file for just those records matching the filter expression.</para>
          <para>Visual FoxPro Rushmore technology optimizes an INDEX ... FOR <legacyItalic>lExpression</legacyItalic> command if <legacyItalic>lExpression</legacyItalic> is an optimizable expression. For best performance, use an optimizable expression in the FOR clause.
</para>
        </definition>
        <definedTerm>COMPACT </definedTerm>
        <definition>
          <para>Creates a compact .idx file.</para>
        </definition>
        <definedTerm>ASCENDING </definedTerm>
        <definition>
          <para>Specifies an ascending order for the .cdx file. By default, .cdx tags are created in ascending order. (You can include ASCENDING as a reminder of the index file's order.) A table can be indexed in reverse order by including DESCENDING.</para>
        </definition>
        <definedTerm>DESCENDING </definedTerm>
        <definition>
          <para>Specifies a descending order for the .cdx file. You can't include DESCENDING when creating .idx index files.</para>
        </definition>
        <definedTerm>UNIQUE </definedTerm>
        <definition>
          <para>Specifies that only the first record encountered with a particular index key value is included in an .idx file or a .cdx tag. UNIQUE can be used to prevent the display of or access to duplicate records. All records added with duplicate index keys are excluded from the index file. Using the UNIQUE option of INDEX is identical to executing SET UNIQUE ON before issuing INDEX or REINDEX.</para>
          <para>When a UNIQUE index or index tag is active and a duplicate record is changed in a manner that changes its index key, the index or index tag is updated. However, the next duplicate record with the original index key cannot be accessed or displayed until you reindex the file using REINDEX.
</para>
        </definition>
        <definedTerm>CANDIDATE </definedTerm>
        <definition>
          <para>Creates a candidate structural index tag. The CANDIDATE keyword can be included only when creating a structural index tag; otherwise, Visual FoxPro generates an error message.</para>
          <para>A candidate index tag prevents duplicate values in the field or combination of fields specified in the index expression <legacyItalic>eExpression</legacyItalic>. The term <legacyItalic>candidate</legacyItalic> refers to the type of index; because candidate indexes prevent duplicate values, they qualify as a "candidate" to be a primary index.


</para>
          <para>Visual FoxPro generates an error if you create a candidate index tag for a field or combination of fields that already contains duplicate values.
</para>
        </definition>
        <definedTerm>ADDITIVE </definedTerm>
        <definition>
          <para>Keeps open any previously opened index files. If you omit the ADDITIVE clause when you create an index file or files for a table with INDEX, any previously opened index files (except the structural compound index) are closed.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Records in a table that has an index file are displayed and accessed in the order specified by the index expression. The physical order of the records in the table isn't changed by an index file.</para>
    </content>
    <sections>
      <section>
        <title>Index Types</title>
        <content>
          <para>Visual FoxPro lets you create two types of index files:

</para>
          <list class="bullet">
            <listItem>
              <para>Compound .cdx index files containing multiple index entries called tags</para>
            </listItem>
            <listItem>
              <para>.idx index files containing one index entry</para>
            </listItem>
          </list>
          <para>You can also create a structural compound index file, which is automatically opened with the table.</para>
          <alert class="note">
            <para>Because structural compound index files are automatically opened when the table is opened, they are the preferred index type.</para>
          </alert>
          <para>Include COMPACT to create compact .idx index files. Compound index files are always compact.</para>
        </content>
      </section>
      <section>
        <title>Index Order and Updating</title>
        <content>
          <para>Only one index file (the master index file) or tag (the master tag) controls the order in which the table is displayed or accessed. Certain commands (SEEK, for example) use the master index file or tag to search for records. However, all open .idx and .cdx index files are updated as changes are made to the table.</para>
        </content>
      </section>
      <section>
        <title>User-Defined Functions</title>
        <content>
          <para>Although an index expression can contain a user-defined function, you should not use user-defined functions in an index expression. User-defined functions in an index expression increase the time it takes to create or update the index. Also, index updates might not occur when a user-defined function is used for an index expression.</para>
          <para>If you use a user-defined function in an index expression, Visual FoxPro must be able to locate the user-defined function. When Visual FoxPro creates an index, the index expression is saved in the index file but only a reference to the user-defined function is included in the index expression.</para>
        </content>
      </section>
    </sections>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="3a01a291-f4d9-43bc-a725-5a95546ff364">ALTER TABLE</link>
<link xlink:href="4f4e1362-a5f3-4b15-8a3c-d4e96605f221">DELETE TAG</link>
<link xlink:href="00efbcd4-fea8-4061-86a5-82de413cb753">SET COLLATE</link>
<link xlink:href="1f69e31e-4599-47cc-ac89-b86fba8703c5">SET UNIQUE</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>