---
title: "Rules for Conversions"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 89f846a3-001d-496a-9843-ac9c38dc1762
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Rules for Conversions
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The rules in this section apply for conversions involving numeric literals. For the purposes of these rules, the following terms are defined:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyItalic>Store assignment:</legacyItalic> When sending data into a table column in a database. This occurs during calls to <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, and <legacyBold>SQLSetPos</legacyBold>. During store assignment, "target" refers to a database column and "source" refers to data in application buffers.</para>
      </listItem>
      <listItem>
        <para>
          <legacyItalic>Retrieval assignment:</legacyItalic> When retrieving data from the database into application buffers. This occurs during calls to <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLGetData</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, and <legacyBold>SQLSetPos</legacyBold>. During retrieval assignment, "target" refers to the application buffers and "source" refers to the database column.</para>
      </listItem>
      <listItem>
        <para>
          <legacyItalic>CS:</legacyItalic> The value in the character source.</para>
      </listItem>
      <listItem>
        <para>
          <legacyItalic>NT:</legacyItalic> The value in the numeric target.</para>
      </listItem>
      <listItem>
        <para>
          <legacyItalic>NS:</legacyItalic> The value in the numeric source.</para>
      </listItem>
      <listItem>
        <para>
          <legacyItalic>CT:</legacyItalic> The value in the character target.</para>
      </listItem>
      <listItem>
        <para>Precision of an exact numeric literal: the number of digits it contains.</para>
      </listItem>
      <listItem>
        <para>The scale of an exact numeric literal: the number of digits to the right of the expressed or implied period.</para>
      </listItem>
      <listItem>
        <para>The precision of an approximate numeric literal: the precision of its mantissa.</para>
      </listItem>
    </list>
  </introduction>
  <section>
    <title>Character Source to Numeric Target</title>
    <content>
      <para>Following are the rules for converting from a character source (CS) to a numeric target (NT):  </para>
      <list class="ordered">
        <listItem>
          <para>Replace CS with the value obtained by removing any leading or trailing spaces in CS. If CS is not a valid <legacyItalic>numeric-literal</legacyItalic>, SQLSTATE 22018 (Invalid character value for cast specification) is returned.</para>
        </listItem>
        <listItem>
          <para>Replace CS with the value obtained by removing leading zeroes before the decimal point, trailing zeroes after the decimal point, or both.</para>
        </listItem>
        <listItem>
          <para>Convert CS to NT. If the conversion results in a loss of significant digits, SQLSTATE 22003 (Numeric value out of range) is returned. If the conversion results in the loss of nonsignificant digits, SQLSTATE 01S07 (Fractional truncation) is returned.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Numeric Source to Character Target</title>
    <content>
      <para>Following are the rules for converting from a numeric source (NS) to a character target (CT):  </para>
      <list class="ordered">
        <listItem>
          <para>Let LT be the length in characters of CT. For retrieval assignment, LT is equal to the length of the buffer in characters minus the number of bytes in the null-termination character for this character set.</para>
        </listItem>
        <listItem>
          <para>Cases: </para>
          <list class="bullet">
            <listItem>
              <para>If NS is an exact numeric type, then let YP equal the shortest character string that conforms to the definition of <legacyItalic>exact-numeric-literal</legacyItalic> such that the scale of YP is the same as the scale of NS, and the interpreted value of YP is the absolute value of NS.</para>
            </listItem>
            <listItem>
              <para>If NS is an approximate numeric type, then let YP be a character string as follows: </para>
              <para>Case:  </para>
              <para>If NS is equal to 0, then YP is 0.  </para>
              <para>Let YSN be the shortest character string that conforms to the definition of exact-<legacyItalic>numeric-literal</legacyItalic> and whose interpreted value is the absolute value of NS. If the length of YSN is less than the (<legacyItalic>precision</legacyItalic> + 1) of the data type of NS, then let YP equal YSN.  </para>
              <para>Otherwise, YP is the shortest character string that conforms to the definition of <legacyItalic>approximate-numeric-literal </legacyItalic>whose interpreted value is the absolute value of NS and whose <legacyItalic>mantissa</legacyItalic> consists of a single <legacyItalic>digit</legacyItalic> that is not '0', followed by a <legacyItalic>period</legacyItalic> and an <legacyItalic>unsigned-integer</legacyItalic>. </para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>Case: </para>
          <list class="bullet">
            <listItem>
              <para>If NS is less than 0, then let Y be the result of: </para>
              <para>'-' || YP  </para>
              <para>where '||' is the string concatenation operator.  </para>
              <para>Otherwise, let Y equal YP. </para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>Let LY be the length in characters of Y.</para>
        </listItem>
        <listItem>
          <para>Case: </para>
          <list class="bullet">
            <listItem>
              <para>If LY equals LT, then CT is set to Y.</para>
            </listItem>
            <listItem>
              <para>If LY is less than LT, then CT is set to Y extended on the right by appropriate number of spaces. </para>
              <para>Otherwise (LY &gt; LT), copy the first LT characters of Y into CT.  </para>
              <para>Case:  </para>
              <para>If this is a store assignment, return the error SQLSTATE 22001 (String data, right-truncated).  </para>
              <para>If this is retrieval assignment, return the warning SQLSTATE 01004 (String data, right-truncated). When the copy results in the loss of fractional digits (other than trailing zeros), it is driver-defined whether one of the following occurs:  </para>
              <para>(1)   The driver truncates the string in Y to an appropriate scale        (which can be zero also) and writes the result into CT. </para>
              <para>(2)   The driver rounds the string in Y to an appropriate scale        (which can be zero also) and writes the result into CT. </para>
              <para>(3)   The driver neither truncates nor rounds, but just copies        the first LT characters of Y into CT. </para>
            </listItem>
          </list>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>