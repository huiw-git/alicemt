---
title: Structured Query Language (SQL)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bebfd93e-0dc0-46b3-a531-518beb7ea976
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Structured Query Language (SQL)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A typical DBMS allows users to store, access, and modify data in an organized, efficient way. Originally, the users of DBMSs were programmers. Accessing the stored data required writing a program in a programming language such as COBOL. While these programs were often written to present a friendly interface to a nontechnical user, access to the data itself required the services of a knowledgeable programmer. Casual access to the data was not practical.</para>
    <para>Users were not entirely happy with this situation. While they could access data, it often required convincing a DBMS programmer to write special software. For example, if a sales department wanted to see the total sales in the previous month by each of its salespeople and wanted this information ranked in order by each salesperson's length of service in the company, it had two choices: Either a program already existed that allowed the information to be accessed in exactly this way, or the department had to ask a programmer to write such a program. In many cases, this was more work than it was worth, and it was always an expensive solution for one-time, or ad hoc, inquiries. As more and more users wanted easy access, this problem grew larger and larger.</para>
    <para>Allowing users to access data on an ad hoc basis required giving them a language in which to express their requests. A single request to a database is defined as a query; such a language is called a query language. Many query languages were developed for this purpose, but one of these became the most popular: Structured Query Language, invented at IBM in the 1970s. It is more commonly known by its acronym, SQL, and is pronounced both as "ess-cue-ell" and as "sequel"; this manual uses the former pronunciation. SQL became an ANSI standard in 1986 and an ISO standard in 1987; it is used today in a great many database management systems.</para>
    <para>Although SQL solved the ad hoc needs of users, the need for data access by computer programs did not go away. In fact, most database access still was (and is) programmatic, in the form of regularly scheduled reports and statistical analyses, data entry programs such as those used for order entry, and data manipulation programs, such as those used to reconcile accounts and generate work orders.</para>
    <para>These programs also use SQL, using one of the following three techniques:  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyBold>Embedded SQL</legacyBold>, in which SQL statements are embedded in a host language such as C or COBOL.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQL modules</legacyBold>, in which SQL statements are compiled on the DBMS and called from a host language.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Call-level interface</legacyBold>, or CLI, which consists of functions called to pass SQL statements to the DBMS and to retrieve results from the DBMS.</para>
      </listItem>
    </list>
    <alert class="note">
      <para>It is a historical accident that the term call-level interface is used instead of application programming interface (API), another term for the same thing. In the database world, API is used to describe SQL itself: SQL is the API to a DBMS.</para>
    </alert>
    <para>Of these choices, embedded SQL is the most commonly used, although most major DBMSs support proprietary CLIs.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="96270c4f-2efd-4dc1-a985-ed7fd5658db2">Processing an SQL Statement</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="8eee3527-f225-4aa2-bd18-a16bd3ab0fb7">Embedded SQL</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="07551472-87ee-4765-951f-1364ed32f0c0">SQL Modules</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="42257bb6-0bf1-4533-a4ef-4a6dd2aecb18">Call-Level Interfaces</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>