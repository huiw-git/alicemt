---
title: SQLSTATEs
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f29fff2e-3d09-4a8c-a2f9-2059062cbebf
translation.priority.ht: 
  - en-gb
---
# SQLSTATEs
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>SQLSTATEs provide detailed information about the cause of a warning or error. The SQLSTATEs in this manual are based on those found in the ISO/IEF CLI specification, although those SQLSTATEs that start with IM are specific to ODBC.</para>
    <para>Unlike return codes, the SQLSTATEs in this manual are guidelines, and drivers are not required to return them. Therefore, while drivers should return the proper SQLSTATE for any error or warning they are capable of detecting, applications should not count on this always occurring. The reasons for this situation are twofold:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>Incompleteness</legacyBold> Although this manual lists a large number of errors and warnings and possible causes for those errors and warnings, it is not complete and probably never will be; driver implementations simply vary too much. Any given driver probably will not return all of the SQLSTATEs listed in this manual and might return SQLSTATEs not listed in this manual.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Complexity</legacyBold> Some database engines — particularly relational database engines — return literally thousands of errors and warnings. The drivers for such engines are unlikely to map all of these errors and warnings to SQLSTATEs because of the effort involved, the inexactness of the mappings, the large size of the resulting code, and the low value of the resulting code, which often returns programming errors that should never be encountered at run time. Therefore, drivers should map as many errors and warnings as seems reasonable and be sure to map those errors and warnings on which application logic might be based, such as SQLSTATE 01004 (Data truncated).</para>
      </listItem>
    </list>
    <para>Because SQLSTATEs are not returned reliably, most applications just display them to the user along with their associated diagnostic message, which is often tailored to the specific error or warning that occurred, and native error code. There is rarely any loss of functionality in doing this, because applications cannot base programming logic on most SQLSTATEs anyway. For example, suppose <legacyBold>SQLExecDirect</legacyBold> returns SQLSTATE 42000 (Syntax error or access violation). If the SQL statement that caused this error is hard-coded or built by the application, this is a programming error and the code needs to be fixed. If the SQL statement is entered by the user, this is a user error and the application has done all that is possible by informing the user of the problem.</para>
    <para>When applications do base programming logic on SQLSTATEs, they should be prepared for the SQLSTATE not to be returned or for a different SQLSTATE to be returned. Exactly which SQLSTATEs are returned reliably can be based only on experience with numerous drivers. However, a general guideline is that SQLSTATEs for errors that occur in the driver or Driver Manager, as opposed to the data source, are more likely to be returned reliably. For example, most drivers probably return SQLSTATE HYC00 (Optional feature not implemented), while fewer drivers probably return SQLSTATE 42021 (Column already exists).</para>
    <para>The following SQLSTATEs indicate run-time errors or warnings and are good candidates on which to base programming logic. However, there is no guarantee that all drivers return them.  </para>
    <list class="bullet">
      <listItem>
        <para>01004 (Data truncated)</para>
      </listItem>
      <listItem>
        <para>01S02 (Option value changed)</para>
      </listItem>
      <listItem>
        <para>HY008 (Operation canceled)</para>
      </listItem>
      <listItem>
        <para>HYC00 (Optional feature not implemented)</para>
      </listItem>
      <listItem>
        <para>HYT00 (Timeout expired)</para>
      </listItem>
    </list>
    <para>SQLSTATE HYC00 (Optional feature not implemented) is particularly significant because it is the only way in which an application can determine whether a driver supports a particular statement or connection attribute.</para>
    <para>For a complete list of SQLSTATEs and what functions return them, see <legacyLink xlink:href="c06902e4-721d-42e2-b818-05f0e18e4ce0">Appendix A: ODBC Error Codes</legacyLink>. For a detailed explanation of the conditions under which each function might return a particular SQLSTATE, see that function.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>