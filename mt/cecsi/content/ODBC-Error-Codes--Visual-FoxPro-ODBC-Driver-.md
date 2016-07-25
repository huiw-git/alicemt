---
title: "ODBC Error Codes (Visual FoxPro ODBC Driver)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b4251f2-6fa6-49df-8abf-7cc1cc35d1c8
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC Error Codes (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table lists Visual FoxPro error codes mapped to ODBC Error Code SQLSTATE values. The mapped SQLSTATE values come from <legacyLink xlink:href="5004060f-8510-4018-87a4-d41789e69d3e">SQLExecDirect</legacyLink> and <legacyLink xlink:href="0c4cb5a4-9729-4b2e-a0c6-52027b92e8fc">SQLPrepare</legacyLink>. No other SQLSTATE values from other ODBC API are mapped because <legacyBold>SQLExecDirect</legacyBold> and <legacyBold>SQLPrepare</legacyBold> are the only functions that access the Visual FoxPro engine.</para>
    <para>For more information on ODBC error codes, see <legacyLink xlink:href="c06902e4-721d-42e2-b818-05f0e18e4ce0">Appendix A: ODBC Error Codes</legacyLink>, in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>SQLSTATE</para>
          </TD>
          <TD>
            <para>Visual FoxPro error code</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>S1001</para>
          </TD>
          <TD>
            <para>149 </para>
            <para>150 </para>
            <para>182 </para>
            <para>202 </para>
            <para>308</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>1004</para>
          </TD>
          <TD>
            <para>159</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>37000</para>
          </TD>
          <TD>
            <para>132 </para>
            <para>200 </para>
            <para>219 </para>
            <para>221 </para>
            <para>222 </para>
            <para>227 </para>
            <para>229 </para>
            <para>230 </para>
            <para>498 </para>
            <para>499 </para>
            <para>713 </para>
            <para>901</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>22005</para>
          </TD>
          <TD>
            <para>301 </para>
            <para>302</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>22012</para>
          </TD>
          <TD>
            <para>307</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>23000</para>
          </TD>
          <TD>
            <para>581 </para>
            <para>583 </para>
            <para>884 </para>
            <para>886 </para>
            <para>988</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S0001</para>
          </TD>
          <TD>
            <para>121 </para>
            <para>571</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S0002</para>
          </TD>
          <TD>
            <para>173 </para>
            <para>120 </para>
            <para>123 </para>
            <para>295 </para>
            <para>562 </para>
            <para>563 </para>
            <para>802</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S0012</para>
          </TD>
          <TD>
            <para>683</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S0021</para>
          </TD>
          <TD>
            <para>156 </para>
            <para>712</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S0022</para>
          </TD>
          <TD>
            <para>158 </para>
            <para>806</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1000</para>
          </TD>
          <TD>
            <para>100 </para>
            <para>101 </para>
            <para>102 </para>
            <para>105 </para>
            <para>107 </para>
            <para>109 </para>
            <para>110 </para>
            <para>111 </para>
            <para>113 </para>
            <para>114 </para>
            <para>115 </para>
            <para>118 </para>
            <para>119 </para>
            <para>125 </para>
            <para>133 </para>
            <para>135 </para>
            <para>136 </para>
            <para>137 </para>
            <para>145 </para>
            <para>146 </para>
            <para>171 </para>
            <para>173 </para>
            <para>177 </para>
            <para>201 </para>
            <para>205 </para>
            <para>239 </para>
            <para>240 </para>
            <para>252 </para>
            <para>257 </para>
            <para>296 </para>
            <para>305 </para>
            <para>407 </para>
            <para>410 </para>
            <para>462 </para>
            <para>502 </para>
            <para>503 </para>
            <para>520 </para>
            <para>538 </para>
            <para>550 </para>
            <para>561 </para>
            <para>567 </para>
            <para>570 </para>
            <para>575 </para>
            <para>578 </para>
            <para>580 </para>
            <para>585 </para>
            <para>602 </para>
            <para>702 </para>
            <para>705 </para>
            <para>707 </para>
            <para>708 </para>
            <para>718 </para>
            <para>750 </para>
            <para>872 </para>
            <para>879 </para>
            <para>887 </para>
            <para>888 </para>
            <para>912 </para>
            <para>914 </para>
            <para>915 </para>
            <para>918 </para>
            <para>922 </para>
            <para>923 </para>
            <para>947 </para>
            <para>976 </para>
            <para>999</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>