---
title: "ODBC Programmer&#39;s Reference"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b33c3c43-ae66-44a3-be17-9cd82624dd96
caps.latest.revision: 11
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC Programmer&#39;s Reference
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyItalic>ODBC Programmer's Reference</legacyItalic> contains the following sections.</para>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="854f0bb4-17e9-489b-9595-eefffb8ba99f">What's New in ODBC 3.8</link> lists the new ODBC features that were added in the Windows 8 SDK.</para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="38ae6b7f-f53b-48a7-8fe5-4bbd6e0e414b">Sample ODBC Program</link> presents a sample ODBC program.</para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="dbe0b5a3-d7fa-440d-80b4-6cc00de159dc">Introduction to ODBC</legacyLink> provides a brief history of Structured Query Language and ODBC, and conceptual information about the ODBC interface.</para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="0dd1a3b6-69dc-462f-9290-12ebee2b4a2a">Developing Applications</legacyLink> contains information about developing applications that use the ODBC interface and drivers that implement it.</para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="e2580f7d-d614-4e14-a9a3-804e8061b00e">Installing and Configuring ODBC Software</legacyLink> provides information about installation and a setup DLL function reference.</para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="3225a011-5605-46ba-bb74-1ca6106a5271">Developing an ODBC Driver</link> contains information on writing a driver.</para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="1ba0f6cc-dfa7-4fe8-8bc2-f862b386156d">API Reference</legacyLink> contains syntax and semantic information for all ODBC functions.</para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="3331aa89-24d0-4c0e-b377-c720c1107ad5">ODBC Appendixes</legacyLink> contain technical details and reference tables for ODBC error codes, data types, and SQL grammar.</para>
      </listItem>
    </list>
  </introduction>
  <section>
    <title>Working with the ODBC Documentation</title>
    <content>
      <para>The ODBC interface is designed for use with the C programming language. Use of the ODBC interface spans three areas: SQL statements, ODBC function calls, and C programming. This documentation assumes the following:  </para>
      <list class="bullet">
        <listItem>
          <para>A working knowledge of the C programming language.</para>
        </listItem>
        <listItem>
          <para>General DBMS knowledge and a familiarity with SQL.</para>
        </listItem>
      </list>
      <para>The following typographic conventions are used.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Format</para>
            </TD>
            <TD>
              <para>Used for</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>SELECT * FROM</para>
            </TD>
            <TD>
              <para>Uppercase letters indicate SQL statements, macro names, and terms used at the operating-system command level.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <codeInline>RETCODE SQLFetch(hdbc)</codeInline>
              </para>
            </TD>
            <TD>
              <para>The monospace font is used for sample command lines and program code.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>argument</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>Italicized words indicate programmatic arguments, information that the user or the application must provide, or word emphasis.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>SQLEndTran</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Bold type indicates that syntax must be typed exactly as shown, including function names.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>|</para>
            </TD>
            <TD>
              <para>A vertical bar separates two mutually exclusive choices in a syntax line.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>...</para>
            </TD>
            <TD>
              <para>An ellipsis indicates that arguments can be repeated several times.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>. . .</para>
            </TD>
            <TD>
              <para>A column of three dots indicates continuation of previous lines of code.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>About the Code Examples</title>
    <content>
      <para>The code examples in this guide are designed for illustration purposes only. Because they are written primarily to demonstrate ODBC principles, efficiency has sometimes been set aside in the interest of clarity. In addition, whole sections of code have sometimes been omitted for clarity. These include the definitions of non-ODBC functions (those functions whose names do not start with "SQL") and most error handling.</para>
      <para>All code examples use ANSI strings and the same database schema, which is shown at the start of <legacyLink xlink:href="81ba9453-c085-47c0-b411-90ca6a5ee428">Catalog Functions</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Recommended Reading</title>
    <content>
      <para>For more information about SQL, the following standards are available:  </para>
      <list class="bullet">
        <listItem>
          <para>Database Language — SQL with Integrity Enhancement, ANSI, 1989 ANSI X3.135-1989.</para>
        </listItem>
        <listItem>
          <para>Database Language — SQL: ANSI X3H2 and ISO/IEC JTC1/SC21/WG3 9075:1992 (SQL-92).</para>
        </listItem>
        <listItem>
          <para>Open Group, Data Management: Structured Query Language (SQL), Version 2 (The Open Group, 1996). </para>
        </listItem>
      </list>
      <para>In addition to standards and vendor-specific SQL guides, many books describe SQL, including:  </para>
      <list class="bullet">
        <listItem>
          <para>Date, C. J., with Darwen, Hugh: <legacyItalic>A Guide to the SQL Standard</legacyItalic> (Addison-Wesley, 1993).</para>
        </listItem>
        <listItem>
          <para>Emerson, Sandra L., Darnovsky, Marcy, and Bowman, Judith S.: <legacyItalic>The Practical SQL Handbook</legacyItalic> (Addison-Wesley, 1989).</para>
        </listItem>
        <listItem>
          <para>Groff, James R. and Weinberg, Paul N.: <legacyItalic>Using SQL</legacyItalic> (Osborne McGraw-Hill, 1990).</para>
        </listItem>
        <listItem>
          <para>Gruber, Martin: <legacyItalic>Understanding SQL</legacyItalic> (Sybex, 1990).</para>
        </listItem>
        <listItem>
          <para>Hursch, Jack L. and Carolyn J.: <legacyItalic>SQL, The Structured Query Language</legacyItalic> (TAB Books, 1988).</para>
        </listItem>
        <listItem>
          <para>Melton, Jim, and Simon, Alan R.: <legacyItalic>Understanding the New SQL: A Complete Guide</legacyItalic> (Morgan Kaufmann Publishers, 1993).</para>
        </listItem>
        <listItem>
          <para>Pascal, Fabian: <legacyItalic>SQL and Relational Basics</legacyItalic> (M &amp; T Books, 1990).</para>
        </listItem>
        <listItem>
          <para>Trimble, J. Harvey, Jr. and Chappell, David: <legacyItalic>A Visual Introduction to SQL</legacyItalic> (Wiley, 1989).</para>
        </listItem>
        <listItem>
          <para>Van der Lans, Rick F.: <legacyItalic>Introduction to SQL</legacyItalic> (Addison-Wesley, 1988).</para>
        </listItem>
        <listItem>
          <para>Vang, Soren: <legacyItalic>SQL and Relational Databases</legacyItalic> (Microtrend Books, 1990).</para>
        </listItem>
        <listItem>
          <para>Viescas, John: <legacyItalic>Quick Reference Guide to SQL</legacyItalic> (Microsoft Corp., 1989).</para>
        </listItem>
      </list>
      <para>For additional information about transaction processing, see:  </para>
      <list class="bullet">
        <listItem>
          <para>Gray, J. N. and Reuter, Andreas: <legacyItalic>Transaction Processing: Concepts and Techniques</legacyItalic> (Morgan Kaufmann Publishers, 1993).</para>
        </listItem>
        <listItem>
          <para>Hackathorn, Richard D.: <legacyItalic>Enterprise Database Connectivity</legacyItalic> (Wiley &amp; Sons, 1993).</para>
        </listItem>
      </list>
      <para>For more information about Call-Level Interfaces, the following standards are available:  </para>
      <list class="bullet">
        <listItem>
          <para>Open Group, <legacyItalic>Data Management: SQL Call Level Interface (CLI), C451</legacyItalic> (Open Group, 1995).</para>
        </listItem>
        <listItem>
          <para>ISO/IEC 9075-3:1995, Call-Level Interface (SQL/CLI).</para>
        </listItem>
      </list>
      <para>For additional information about ODBC, a number of books are available, including:  </para>
      <list class="bullet">
        <listItem>
          <para>Geiger, Kyle: <legacyItalic>Inside ODBC</legacyItalic> (Microsoft Press®, 1995).</para>
        </listItem>
        <listItem>
          <para>Gryphon, Robert, Charpentier, Luc, Oelschlager, Jon, Shoemaker, Andrew, Cross, Jim, and Lilley, Albert W.: <legacyItalic>Using ODBC 2</legacyItalic> (Que, 1994).</para>
        </listItem>
        <listItem>
          <para>Johnston, Tom and Osborne, Mark: <legacyItalic>ODBC Developers Guide</legacyItalic> (Howard W. Sams &amp; Company, 1994).</para>
        </listItem>
        <listItem>
          <para>North, Ken: <legacyItalic>Windows Multi-DBMS Programming: Using C++, Visual Basic, ODBC, OLE 2 and Tools for DBMS Projects</legacyItalic> (John Wiley &amp; Sons, Inc., 1995).</para>
        </listItem>
        <listItem>
          <para>Stegman, Michael O., Signore, Robert, and Creamer, John: <legacyItalic>The ODBC Solution, Open Database Connectivity in Distributed Environments</legacyItalic> (McGraw-Hill, 1995).</para>
        </listItem>
        <listItem>
          <para>Welch, Keith: <legacyItalic>Using ODBC 2</legacyItalic> (Que, 1994).</para>
        </listItem>
        <listItem>
          <para>Whiting, Bill: <legacyItalic>Teach Yourself ODBC in Twenty-One Days</legacyItalic> (Howard W. Sams &amp; Company, 1994).</para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>