---
title: "SQL Server Drivers"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a5a9e591-4236-4105-9464-70cd36eeeb51
caps.latest.revision: 11
manager: jhubbard
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
# SQL Server Drivers
<?xml version="1.0" encoding="UTF-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xlink="http://www.w3.org/1999/xlink" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
    <introduction>
        <para>SQL Server supports a wide variety of drivers, which are used by client applications or services to connect and query for data.  Please see below for a summary of the different drivers, both current and legacy.</para>
    </introduction>
    <section>
		<title>Current SQL Drivers</title>
		<content>
		<para>The following SQL Drivers are actively developed. Each driver has a support statement that can be found by following the links.</para> 
		</content>
		<sections>
			<section>
		        <title>ADO.NET</title>
		        <content>
		            <para>       
							ADO.NET is a library that is a standard part of the .Net framework.  It is a C# implementation of the TDS protocol, which is supported by all modern versions of SQL Server.  
						  This driver is developed, tested, and supported by Microsoft.</para>
						<para><link xlink:href="5e467fce-7237-4678-bafa-a16f32323d0c">Microsoft ADO.NET for SQL Server</link></para>
		        </content>
		    </section>
		    <section>
		        <title>JDBC</title>
		        <content>
		            <para>The JDBC SQL driver is a Java implementation of the TDS protocol, which is supported by all modern versions of SQL Server.  This driver is developed, tested, and supported by Microsoft.</para><para>       
							<link xlink:href="baf420ab-c058-4cec-a673-d7cb6397210e">Microsoft JDBC Driver for SQL Server</link>
						</para>
		        </content>
		    </section>
		    <section>
		        <title>ODBC</title>
		        <content>
		            <para>The ODBC SQL driver is a C++ implementation of the TDS protocol, which is supported by all modern versions of SQL Server.  This driver is developed, tested, and supported by Microsoft.</para>
		        		<para><link xlink:href="9f2ae91b-06af-4c9a-9d24-062df7bc4662">Microsoft ODBC Driver for SQL Server</link></para>
				  </content>
		    </section>
		    <section>
		        <title>PHP</title>
		        <content>
		                   
							
						<para>The PHP SQL driver relies on the Microsoft SQL Server ODBC Driver to handle the low-level communication with SQL Server.  This driver is developed, tested, and supported by Microsoft.</para><para><link xlink:href="9e78bbf3-9e9a-426d-99d3-6fa2cb33ff6b">Microsoft Drivers for PHP for SQL Server</link></para>
		        </content>
		    </section>
			 
			<section>
	        <title>Node.js</title>
	        <content>
	            <para>The tedious module is a javascript implementation of the TDS protocol, which is supported by all modern versions of SQL Server.  The driver is an open source project, available on Github.</para><para>       
						<link xlink:href="c4cdbfa6-9b73-4b72-a1a6-e1b45d8a773d">Node.js Driver for SQL Server</link>
					</para>
	        </content>
			</section>
			<section>
	        <title>Python</title>
	        <content>
	            <para>The pymssql module is a Python implementation of the TDS protocol, which is supported by all modern versions of SQL Server.  </para><para><link xlink:href="3a1568d1-917b-46d3-b5cb-facdc740408f">Python Driver for SQL Server</link>
					</para>
	        </content>
			</section>
			<section>
	        <title>Ruby</title>
	        <content>
	            <para>The TinyTDS gem is a Ruby implementation of the TDS protocol, which is supported by all modern versions of SQL Server. </para><para>       
						<link xlink:href="45d1b1b6-363d-4924-bcb1-b2582b60f76b">Ruby Driver for SQL Server</link></para>
	        </content>
			</section>
		</sections>
	</section>
	
	
	<section>
		<title> Legacy SQL Drivers</title>
		<content>
		<para>The following SQL Drivers were developed and tested by Microsoft, but are not recommended to be used for new development. Each driver has a support statement that can be found by following the links.</para> 
		</content>
		<sections>
		   <section>
	        <title>OLEDB</title>
	        <content>
	            <para>       
						The OLE DB provider will not be included after SQL Server 2012.
					</para>
	        <para><externalLink><linkText>Microsoft OLE DB</linkText><linkUri>https://msdn.microsoft.com/library/ms722784.aspx</linkUri></externalLink></para></content>
		   </section>
	    	<section>
	        <title>ADO</title>
	        <content>
	            <para>       
						The ADO SQL driver has a direct dependency on the OLE DB provider.  As such, it will not be supported after SQL Server 2012.
					</para>
	        <para><link xlink:href="8e9d52da-342d-46b5-8535-c57f07711db0">ActiveX Data Objects (ADO)</link></para></content>
	     	</section>	 
		</sections>
	</section>
	 
	<relatedTopics/>
</developerConceptualDocument>
