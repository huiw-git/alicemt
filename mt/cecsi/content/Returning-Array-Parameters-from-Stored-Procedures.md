---
title: Returning Array Parameters from Stored Procedures
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2018069b-da5d-4cee-a971-991897d4f7b5
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Returning Array Parameters from Stored Procedures
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>In Oracle 7.3, there is no way to access a PL/SQL Record Type except from a PL/SQL program. If a packaged procedure or function has a formal argument defined as a PL/SQL Record Type, it is not possible to bind that formal argument as a parameter. Use the PL/SQL TABLE type in the Microsoft ODBC Driver for Oracle to invoke array parameters from procedures containing the correct escape sequences.</para>
    <para>To invoke the procedure, use the following syntax:</para>
    <code>{call  &lt;package-name&gt;.&lt;proc-or-func&gt;;
(..., {resultset &lt;max-records-requested&gt; ,&lt;formal-array-param_1&gt;,;
 &lt;formal-array-param_2&gt;,...,&lt;formal-array-param_n&gt; }, ... ) }</code>
    <alert class="note">
      <para>The &lt;max-records-requested&gt; parameter must be greater than or equal to the number of rows present in the result set. Otherwise, Oracle returns an error that is passed to the user by the driver.</para>
      <para>PL/SQL records cannot be used as array parameters. Each array parameter can represent only one column of a database table.</para>
    </alert>
    <para>The following example defines a package containing two procedures that return different result sets, and then provides two ways to return result sets from the package.</para>
  </introduction>
  <section>
    <title>Package definition:</title>
    <content>
      <code>CREATE OR REPLACE PACKAGE SimplePackage AS

TYPE t_id is TABLE of  NUMBER(5)
    INDEX BY BINARY_INTEGER;

TYPE t_Course is TABLE of VARCHAR2(10)
    INDEX BY BINARY_INTEGER;

TYPE t_Dept is TABLE of VARCHAR2(5)
    INDEX BY BINARY_INTEGER;

PROCEDURE proc1
   (
   o_id             OUT    t_id,
   ao_course       OUT    t_Course,
   ao_dept         OUT    t_Dept
   );

TYPE t_pk1Type1 IS TABLE OF VARCHAR2(100) INDEX BY BINARY_INTEGER;
TYPE t_pk1Type2 IS TABLE OF NUMBER INDEX BY BINARY_INTEGER;
PROCEDURE proc2
   (
   i_Arg1         IN    NUMBER,
   ao_Arg2         OUT   t_pk1Type1,
   ao_Arg3         OUT   t_pk1Type2
   );

END SimplePackage;

CREATE OR REPLACE PACKAGE BODY SimplePackage AS
    PROCEDURE  proc1 ( o_id OUT t_id,
    ao_course OUT t_Course, ao_dept OUT t_Dept   ) AS
    BEGIN
          o_id(1):= 200;
          ao_course(1) :=  'M101';
          ao_dept(1) :=  'EEE' ;

          o_id(2) := 201;
          ao_course(2) :=  'PHY320';
          ao_dept(2) :=  'ECE' ;

     END proc1;
PROCEDURE proc2
   (
   i_Arg1         IN    NUMBER,
   ao_Arg2         OUT   t_pk1Type1,
   ao_Arg3         OUT   t_pk1Type2
   )
AS
   i   NUMBER;
BEGIN
   FOR i IN 1 .. i_Arg1 LOOP
      ao_Arg2(i) := 'Row Number ' || to_char(i);
   END LOOP;
   FOR i IN 1 .. i_Arg1 LOOP
      ao_Arg3(i) := i;
   END LOOP;
END proc2;
END SimplePackage;</code>
      <procedure>
        <title>To invoke procedure PROC1</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Return all the columns in a single result set: </para>
              <code>{call SimplePackage.Proc1( {resultset  3, o_id , ao_course, ao_dept  } ) }</code>
            </content>
          </step>
          <step>
            <content>
              <para>Return each column as a single result set: </para>
              <code>{call SimplePackage.Proc1( {resultset 3, o_id},  {resultset 3, ao_course}, {resultset 3, ao_dept} ) }</code>
              <para>This returns three result sets, one for each column. </para>
            </content>
          </step>
        </steps>
      </procedure>
      <procedure>
        <title>To invoke procedure PROC2</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Return all the columns in a single result set: </para>
              <code>{call SimplePackage.Proc2( 5 , {resultset  5, ao_Arg2, ao_Arg3} ) }</code>
            </content>
          </step>
          <step>
            <content>
              <para>Return each column as a single result set: </para>
              <code>{call SimplePackage.Proc2( 5 , {resultset 5, ao_Arg2}, {resultset 5, ao_Arg3} ) }</code>
            </content>
          </step>
        </steps>
      </procedure>
      <para>Ensure that your applications fetch all the result sets using the <legacyLink xlink:href="d9f49520-72d7-4234-8635-260d0ce4199c">SQLMoreResults</legacyLink> API. For more information, refer to the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
      <alert class="note">
        <para>In the ODBC Driver for Oracle version 2.0, Oracle functions that return PL/SQL arrays cannot be used to return result sets.</para>
      </alert>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>