---
title: "ADO Glossary"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b0478836-4123-4357-969a-c5784fc28be5
caps.latest.revision: 14
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
# ADO Glossary
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This topic defines terms relevant to ADO.</para>
  </introduction>
  <section>
    <title>A</title>
    <content>
      <definitionTable>
        <definedTerm>absolute URL</definedTerm>
        <definition>
          <para>A fully-qualified URL that specifies the location of a resource that resides on the Internet or an intranet. See also <newTerm>URL</newTerm> and <newTerm>relative URL</newTerm>.</para>
        </definition>
        <definedTerm>ActiveX control</definedTerm>
        <definition>
          <para>Self-registering, in-process COM component that often has a visual element either at design time or run time. ActiveX controls also have the ability to communicate with an Active Document container, such as Microsoft Internet Explorer. </para>
        </definition>
        <definedTerm>ADISAPI (Advanced Data Internet Server Application Programming Interface)</definedTerm>
        <definition>
          <para>An ISAPI DLL that provides parsing, Automation control, Recordset marshaling, and MIME packaging. The ADISAPI component works through the API provided by Internet Information Services (IIS). See also <newTerm>ISAPI</newTerm>.</para>
        </definition>
        <definedTerm>aggregate function</definedTerm>
        <definition>
          <para>In a query, a function such as COUNT, AVG, or STDEV that calculates a value using all the rows in a column of a table. In writing expressions and in programming, you can use SQL aggregate functions (including the three listed above) and domain aggregate functions to determine various statistics.</para>
        </definition>
        <definedTerm>alias</definedTerm>
        <definition>
          <para>An alternate name you give to a column or expression in an SQL SELECT statement, often shorter or more meaningful. For example, BobSales is the alias in the following SELECT statement: "Select wr-Sales as BobSales from SalesDB". An alias can be used to dynamically assign columns to control bindings on the DataControl object.</para>
        </definition>
        <definedTerm>apartment threading</definedTerm>
        <definition>
          <para>A COM threading model where all calls to an object occur on one thread. In apartment threading, COM synchronizes and marshals calls. See also <newTerm>COMmddefcom</newTerm>.</para>
        </definition>
        <definedTerm>asynchronous operation </definedTerm>
        <definition>
          <para>An operation that returns control to the calling program without waiting for the operation to complete. Before the operation is complete, code execution continues. See also <newTerm>synchronous operation</newTerm>.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>B</title>
    <content>
      <definitionTable>
        <definedTerm>binding entry</definedTerm>
        <definition>
          <para>A mapping between a field in a table and a variable. In the ADO Visual C++ extensions, <legacyBold>Recordset</legacyBold> fields are mapped to C/C++ variables.</para>
        </definition>
        <definedTerm>bitmask</definedTerm>
        <definition>
          <para>A numeric value intended for a bit-by-bit value comparison with other numeric values, typically to flag options in parameter or return values. Usually this comparison is done with bitwise logical operators, such as <legacyBold>And</legacyBold> and <legacyBold>Or</legacyBold> in Visual Basic, <legacyBold>&amp;</legacyBold> and <legacyBold>|</legacyBold> in C++.</para>
          <para>For example, the ADO <legacyBold>FieldAttributeEnum</legacyBold> values can be used as bitmasks to determine the attributes of a field. Suppose you wanted to determine if a field was updateable. You could test for this with the following expression in Visual Basic:<codeInline>Field.Attributes AND adFldUpdatable</codeInline></para>
          <para>If the result is TRUE, then the field is updateable.</para>
        </definition>
        <definedTerm>bookmark</definedTerm>
        <definition>
          <para>A marker that uniquely identifies a row within a set of rows so that a user can quickly navigate to it.</para>
        </definition>
        <definedTerm>business object</definedTerm>
        <definition>
          <para>An object that performs a defined set of operations, such as data validation or business rule logic. Business objects usually reside on the middle tier. </para>
        </definition>
        <definedTerm>business rule</definedTerm>
        <definition>
          <para>The combination of validation edits, logon verifications, database lookups, policies, and algorithmic transformations that constitute an enterprise's way of doing business. Also known as <legacyItalic>business logic</legacyItalic>.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>C</title>
    <content>
      <definitionTable>
        <definedTerm>calculated expression</definedTerm>
        <definition>
          <para>An expression that is not constant, but whose value depends upon other values. To be evaluated, a calculated expression must obtain and compute values from other sources, typically in other fields or rows. </para>
        </definition>
        <definedTerm>chapter</definedTerm>
        <definition>
          <para>A reference to a range of rows from a data source. In ADO, a chapter is typically a reference to another <legacyBold>Recordset</legacyBold>.</para>
          <para>Chapter columns make it possible to define a <legacyItalic>parent-child</legacyItalic> relationship where the <legacyItalic>parent</legacyItalic> is the <legacyBold>Recordset</legacyBold> containing the chapter column and the <legacyItalic>child</legacyItalic> is the <legacyBold>Recordset</legacyBold> represented by the chapter.</para>
        </definition>
        <definedTerm>chapter-alias</definedTerm>
        <definition>
          <para>An alias that refers to the column appended to the parent.</para>
        </definition>
        <definedTerm>character set</definedTerm>
        <definition>
          <para>A mapping of a set of characters to their numeric values. For example, Unicode is a 16-bit character set capable of encoding all known characters and used as a worldwide character-encoding standard.</para>
        </definition>
        <definedTerm>child</definedTerm>
        <definition>
          <para>The dependant side of a hierarchical relationship. A child is a node in a hierarchical structure that has another node above it (closer to the root). See also <newTerm>child-alias</newTerm>, <newTerm>parent-child relationship</newTerm>, <newTerm>parent</newTerm>.</para>
        </definition>
        <definedTerm>child-alias</definedTerm>
        <definition>
          <para>An alias that refers to the child. See also <newTerm>alias</newTerm>, <newTerm>child</newTerm>.</para>
        </definition>
        <definedTerm>CLSID (class identifier)</definedTerm>
        <definition>
          <para>A universally unique identifier (UUID) that identifies a COM component. Each COM component has its CLSID in the Windows Registry so that it can be loaded by other applications. See also <newTerm>ProgID</newTerm>, <newTerm>COM</newTerm>.</para>
        </definition>
        <definedTerm>client tier</definedTerm>
        <definition>
          <para>A logical layer of a distributed system that typically presents data to and processes input from the user, sometimes referred to as the <legacyItalic>front end</legacyItalic>. Usually, the client tier requests data from a server based on input, and then formats and displays the result. See also <newTerm>middle tier</newTerm>, <newTerm>data source tier</newTerm>, <newTerm>distributed application</newTerm>.</para>
        </definition>
        <definedTerm>COM (Component Object Model)</definedTerm>
        <definition>
          <para>A binary standard that enables objects to interoperate in a networked environment regardless of the language in which they were developed or on which computers they reside. COM-based technologies include ActiveX Controls, Automation, and object linking and embedding (OLE). COM allows an object to expose its functionality to other components and to host applications. It defines both how the object exposes itself and how this exposure works across processes and across networks. COM also defines the object's life cycle. </para>
        </definition>
        <definedTerm>COM component</definedTerm>
        <definition>
          <para>Binary file — such as .dll, .ocx, and some .exe files — that supports the COM standard for providing objects. Such a file contains code for one or more class factories, COM classes, registry-entry mechanisms, loading code, and so on.</para>
        </definition>
        <definedTerm>comparison operator</definedTerm>
        <definition>
          <para>An operator that compares two expressions and returns a Boolean value.</para>
          <para>A criteria parameter that may be expressed as "&gt;" (greater than), "&lt;" (less than), "=" (equal), "&gt;=" (greater than or equal), "&lt;=" (less than or equal), "&lt;&gt;" (not equal), or "like" (pattern matching).</para>
        </definition>
        <definedTerm>component</definedTerm>
        <definition>
          <para>An object that encapsulates both data and code, and provides a well-specified set of publicly available services.</para>
        </definition>
        <definedTerm>compound file</definedTerm>
        <definition>
          <para>An implementation of COM structured storage for files. A compound file stores separate objects in a single, structured file consisting of two main elements: storage objects and stream objects. Together, they function like a file system within a file.</para>
          <para>A number of individual files bound together in one physical file. Each individual file in a compound file can be accessed as if it were a single physical file.</para>
        </definition>
        <definedTerm>constant</definedTerm>
        <definition>
          <para>A numeric or string value that does not change. Named ADO enumerations (enumerated constants) can be used in your code instead of actual values, for example, <legacyBold>adUseClient</legacyBold> is a constant whose value is 3. (Const adUseClient = 3). See also <newTerm>enumeration</newTerm>.</para>
        </definition>
        <definedTerm>cursor</definedTerm>
        <definition>
          <para>A database element that controls record navigation, updateability of data, and the visibility of changes made to the database by other users.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>D</title>
    <content>
      <definitionTable>
        <definedTerm>data binding</definedTerm>
        <definition>
          <para>The process of associating the objects or controls of an application to a data source. A control associated with a data source is called a <legacyItalic>data-bound control</legacyItalic>.</para>
          <para>The contents of a data-bound control are associated with values from a database. For example, a grid control that is bound to a <legacyBold>Recordset</legacyBold> object can be updated when the rows in the <legacyBold>Recordset</legacyBold> are updated. When new values are retrieved by the <legacyBold>Recordset</legacyBold>, new values are displayed in the grid. </para>
        </definition>
        <definedTerm>data provider</definedTerm>
        <definition>
          <para>Software that exposes data to an ADO application either directly or via a service provider. See also service provider.</para>
        </definition>
        <definedTerm>data shaping</definedTerm>
        <definition>
          <para>A technique which makes use of a formalized syntax (called <legacyBold>Shape language</legacyBold>) to define a specialized <legacyBold>Recordset</legacyBold> object (called a <newTerm>shaped Recordset</newTerm>) that contains not just data, but also references to other <legacyBold>Recordset</legacyBold> objects and/or computed values based on those other <legacyBold>Recordset</legacyBold> objects.</para>
        </definition>
        <definedTerm>data source tier</definedTerm>
        <definition>
          <para>A logical layer of a distributed system that represents a computer running a DBMS, such as an SQL Server database. See also <newTerm>client tier</newTerm>, <newTerm>middle tier</newTerm>, <newTerm>distributed application</newTerm>.</para>
        </definition>
        <definedTerm>DCOM</definedTerm>
        <definition>
          <para>A wire protocol that enables COM components to communicate directly with each other across a network. See also <newTerm>COM</newTerm>, <newTerm>component</newTerm>.</para>
        </definition>
        <definedTerm>DDL (Data Definition Language)</definedTerm>
        <definition>
          <para>Those statements in SQL that define, as opposed to manipulate, data. The schema of a database is created or modified with DDL. For example, <legacyBold>CREATE TABLE</legacyBold>, <legacyBold>CREATE INDEX</legacyBold>, <legacyBold>GRANT</legacyBold>, and <legacyBold>REVOKE</legacyBold> are SQL DDL statements.</para>
        </definition>
        <definedTerm>default stream</definedTerm>
        <definition>
          <para>A text or binary stream (represented by a <legacyBold>Stream</legacyBold> object) that is associated with <legacyBold>Record</legacyBold> or <legacyBold>Recordset</legacyBold> objects when using certain OLE DB providers, such as the Microsoft OLE DB Provider for Internet Publishing. The default stream typically contains the contents of a file such as the HTML code for the root of a Web site.</para>
        </definition>
        <definedTerm>distributed application</definedTerm>
        <definition>
          <para>A program written so that the processing can be divided across multiple computers over a network. Typically, a distributed application is divided into presentation, business logic, and data store layers, or <legacyItalic>tiers</legacyItalic>. See also client tier, middle tier, data source tier.</para>
        </definition>
        <definedTerm>disconnected Recordset</definedTerm>
        <definition>
          <para>A <legacyBold>Recordset</legacyBold> object in a client cache that no longer has a live connection to the server. If the original data source needs to be accessed again for some reason, such as updating data, the connection must be re-established. However, the collections, properties, and methods of a disconnected <legacyBold>Recordset</legacyBold> can still be accessed.</para>
        </definition>
        <definedTerm>DML (Data Manipulation Language)</definedTerm>
        <definition>
          <para>Those statements in SQL that manipulate, as opposed to define, data. The values in a database are selected and modified with DML. For example, <legacyBold>INSERT</legacyBold>, <legacyBold>UPDATE</legacyBold>, <legacyBold>DELETE</legacyBold>, and <legacyBold>SELECT</legacyBold> are SQL DML statements.</para>
        </definition>
        <definedTerm>document source provider</definedTerm>
        <definition>
          <para>A special class of providers that manage folders and documents. When a document is represented by a <legacyBold>Record</legacyBold> object, or a folder of documents is represented by a <legacyBold>Recordset</legacyBold> object, the document source provider populates those objects with a unique set of fields that describe characteristics of the document, instead of the actual document itself. See also resource record.</para>
        </definition>
        <definedTerm>DSN (data source name)</definedTerm>
        <definition>
          <para>The collection of information used to connect your application to a particular ODBC database. The ODBC Driver Manager uses this information to create a connection to the database. A DSN can be stored in a file (a file DSN) or in the Windows Registry (a machine DSN).</para>
        </definition>
        <definedTerm>dynamic property</definedTerm>
        <definition>
          <para>A property specific to a data provider or the cursor service. The <legacyBold>Properties</legacyBold> collection of an object is populated with these automatically ("dynamically"). An object has no dynamic properties until it is connected to a data source through a particular data provider. See also data provider, cursor.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>E</title>
    <content>
      <definitionTable>
        <definedTerm>Enumeration</definedTerm>
        <definition>
          <para>A list of named constants. Enumerated values need not be unique. However the name of each value must be unique within the scope where the enumeration is defined. In ADO, enumerations are used for numeric parameter and return values, to add meaning to ADO code and to shield the developer from the numeric values (which may change from version to version). For example, to open a static <legacyBold>Recordset</legacyBold>, use the <legacyBold>adOpenStatic</legacyBold> enumerated value: <codeInline>Recordset.Open ,,adOpenStatic</codeInline></para>
          <para> Also referred to as <legacyItalic>enumerated constant</legacyItalic>. See also <newTerm>constant</newTerm>.</para>
        </definition>
        <definedTerm>event</definedTerm>
        <definition>
          <para>An action recognized by an object, for which you can write code to respond. Events can be generated by command execution, transaction completion, recordset navigation, and data updates, among other actions. See also <newTerm>event handler</newTerm>.</para>
        </definition>
        <definedTerm>event handler</definedTerm>
        <definition>
          <para>An event handler is the code that is executed when an event occurs. See also event.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>H</title>
    <content>
      <definitionTable>
        <definedTerm>handler</definedTerm>
        <definition>
          <para>A routine that manages a common and relatively simple condition or operation, such as error recovery or data management.</para>
        </definition>
        <definedTerm>hierarchical Recordset</definedTerm>
        <definition>
          <para>A <legacyBold>Recordset</legacyBold> that contains another <legacyBold>Recordset</legacyBold>. See also data shaping, chapter.</para>
          <para>For more information, see <legacyLink xlink:href="25f1d2a1-6d5e-4457-aa07-5db5c75dee18">Accessing Rows in a Hierarchical Recordset</legacyLink>.</para>
        </definition>
        <definedTerm>hierarchy</definedTerm>
        <definition>
          <para>In general, a hierarchy is a ranked structure with a top level and subordinate levels. In ADO, hierarchical <legacyBold>Recordsets</legacyBold> are used to represent the parent-child relationship between a record and a chapter. Also in ADO, <legacyBold>Record</legacyBold> and <legacyBold>Stream</legacyBold> objects can be used to access hierarchical tree structures such as a folder and documents. ADO MD also includes <legacyBold>Hierarchy</legacyBold> objects to represent a relationship between the levels of a dimension in an OLAP cube. See also hierarchical Recordsets, parent-child relationship, chapter, tree.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>I-L</title>
    <content>
      <definitionTable>
        <definedTerm>ISAPI (Internet Server Application Programming Interface)</definedTerm>
        <definition>
          <para>A set of functions for Internet servers, such as a Windows NT® Server/Windows 2000 Server running Microsoft® Internet Information Services (IIS).</para>
        </definition>
        <definedTerm>Key</definedTerm>
        <definition>
          <para>A column or columns in a table that uniquely identify a row; often used to index a table.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>M</title>
    <content>
      <definitionTable>
        <definedTerm>marshaling</definedTerm>
        <definition>
          <para>The process of packaging, sending, and unpackaging interface method parameters across thread or process boundaries.</para>
        </definition>
        <definedTerm>middle tier</definedTerm>
        <definition>
          <para>The logical layer in a distributed system between a user interface or Web client and the database. This is typically where business objects are instantiated. The middle tier is a collection of business rules and functions that generate and operate upon receiving information. They accomplish this through business rules, which can change frequently, and are thus encapsulated into components that are physically separate from the application logic itself. Also known as <legacyItalic>application server tier</legacyItalic>. See also distributed application, client tier, data source tier.</para>
        </definition>
        <definedTerm>MIME (Multi-purpose Internet Mail Extension)</definedTerm>
        <definition>
          <para>An Internet protocol originally developed to allow exchange of electronic mail messages with rich content across heterogeneous network, machine, and e-mail environments. In practice, MIME has also been adopted and extended by non-mail applications.</para>
          <para>MIME is a standard that allows binary data to be published and read on the Internet. The header of a file with binary data contains the MIME type of the data; this informs client programs (Web browsers and mail packages, for instance) that they will need to handle the data in a different way than they handle straight text. For example, the header of a Web document containing a JPEG graphic contains the MIME type specific to the JPEG file format. This allows a browser to display the file with its JPEG viewer, if one is present.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>N-O</title>
    <content>
      <definitionTable>
        <definedTerm>node</definedTerm>
        <definition>
          <para>An element in a hierarchical tree structure. A node may be the root, or the child of another node. A node can also be the parent of multiple children. See also hierarchy, tree, root, child, parent.</para>
        </definition>
        <definedTerm>object variable</definedTerm>
        <definition>
          <para>A variable that contains a reference to an object. For example, <codeInline>objCustomObject</codeInline> is a variable that points to an object of type CustomObject:<codeInline>Set objCustomObject = CreateObject(adodb.Recordset)</codeInline></para>
        </definition>
        <definedTerm>ODBC (Open Database Connectivity)</definedTerm>
        <definition>
          <para>A standard programming language interface used to connect to a variety of data sources. This is usually accessed through Control Panel, where data source names (DSNs) can be assigned to use specific ODBC drivers.</para>
        </definition>
        <definedTerm>OLE DB</definedTerm>
        <definition>
          <para>A set of interfaces that expose data from a variety of sources using COM. OLE DB interfaces provide applications with uniform access to data stored in diverse information sources. These interfaces support the amount of DBMS functionality appropriate to the data source, enabling it to share its data. See also COM.</para>
        </definition>
        <definedTerm>optimistic locking</definedTerm>
        <definition>
          <para>A type of locking in which the data page containing one or more records, including the record being edited, is unavailable to other users only while the record is being updated by the <legacyBold>Update</legacyBold> method, but is available before and after the call to <legacyBold>Update</legacyBold>.</para>
          <para> Optimistic locking is used when the <legacyBold>Recordset</legacyBold> object is opened with the <legacyBold>LockType</legacyBold> parameter or property set to <legacyBold>adLockOptimistic</legacyBold> or <legacyBold>adLockBatchOptimistic</legacyBold>. See also pessimistic locking.</para>
        </definition>
        <definedTerm>ordinal value</definedTerm>
        <definition>
          <para>The numeric location of an item within an order. In an ADO collection, the ordinal value of the first item is zero (0). The next item is one (1), and so on.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>P</title>
    <content>
      <definitionTable>
        <definedTerm>parameterized command</definedTerm>
        <definition>
          <para>A query or command that allows you to set parameter values before the command is executed. For example, a SQL string can be parameterized by embedding parameter markers in the SQL string (designated by the '?' character). The application then specifies values for each parameter and executes the command.</para>
        </definition>
        <definedTerm>parent</definedTerm>
        <definition>
          <para>The controlling side of a hierarchical relationship. In a hierarchical structure, a parent has one or more child nodes directly beneath it in the hierarchy. See also parent-alias, parent-child relationship, child.</para>
        </definition>
        <definedTerm>parent-alias</definedTerm>
        <definition>
          <para>An alias that refers to the parent. See also alias, parent.</para>
        </definition>
        <definedTerm>parent-child relationship</definedTerm>
        <definition>
          <para>A relationship in a hierarchical structure in which the parent is one level higher and directly associated with one or more children. A child is one level lower and must have one parent. See also parent, child.</para>
        </definition>
        <definedTerm>pessimistic locking</definedTerm>
        <definition>
          <para>A type of locking in which the page containing one or more records, including the record being edited, is unavailable to other users to ensure that an update will be made. Pessimistic locking behavior is defined by the OLE DB provider. Typically, records are locked upon editing and remain unavailable until the <legacyBold>Update</legacyBold> method has completed.</para>
          <para> Pessimistic locking is enabled when the <legacyBold>Recordset</legacyBold> object is opened with the <legacyBold>LockType</legacyBold> parameter or property set to <legacyBold>adLockPessimistic</legacyBold>. See also optimistic locking.</para>
        </definition>
        <definedTerm>pooling</definedTerm>
        <definition>
          <para>A performance optimization based on using collections of pre-allocated resources, such as objects or database connections. It is more efficient to draw an existing resource from the pool than to create a new resource.</para>
        </definition>
        <definedTerm>ProgID (programmatic identifier)</definedTerm>
        <definition>
          <para>A unique name mapped to the Windows registry by a COM application. The ProgID for an ADO Connection is "ADODB.Connection". See also CLSID, COM.</para>
        </definition>
        <definedTerm>proxy</definedTerm>
        <definition>
          <para>An interface-specific object that provides the parameter marshaling and communication required for a client to call an application object that is running in a different execution environment, such as on a different thread or in another process. The proxy is located with the client and communicates with a corresponding stub that is located with the application object that is being called. See also stub.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>R</title>
    <content>
      <definitionTable>
        <definedTerm>relative URL</definedTerm>
        <definition>
          <para>A partially qualified URL that specifies a resource on the Internet or an intranet whose location is relative to a starting point specified by an absolute URL or equivalent ADO Connection object. In effect, the concatenated absolute and relative URLs consitute a complete URL. See also URL and absolute URL.</para>
        </definition>
        <definedTerm>remote data source</definedTerm>
        <definition>
          <para>A data source that exists on a another computer, rather than on the local system (where the client application runs).</para>
        </definition>
        <definedTerm>resource record</definedTerm>
        <definition>
          <para>A record from a document source provider that contains fields for the definition and description of a folder or document. The document itself is not contained in the resource record but typically can be accessed by the default stream or a field in the resource record containing a URL. See also document source provider, default stream, URL.</para>
        </definition>
        <definedTerm>rowset</definedTerm>
        <definition>
          <para>A set of rows from a data source, all having the same field schema. A rowset can represent all or some fields from a table. A rowset can also represent a virtual table, created by a query or a join of two or more tables. In ADO, rowsets are represented by <legacyBold>Recordset</legacyBold> objects.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>S</title>
    <content>
      <definitionTable>
        <definedTerm>Scope</definedTerm>
        <definition>
          <para>The range of reference for an object or variable or a range of records in a view or table. For example, local variables can be referenced only within the procedure in which they were defined. Public variables are accessible from anywhere in the application. Objects, such as the current database, are in scope if they are in the defined search path. Record ranges can be specified with a Scope clause in many commands.</para>
        </definition>
        <definedTerm>service provider</definedTerm>
        <definition>
          <para>Software that encapsulates a service by producing and consuming data, augmenting features in your ADO applications. It is a provider that does not directly expose data, rather it provides a service, such as query processing. The service provider may process data provided by a data provider. See also data provider.</para>
        </definition>
        <definedTerm>shaped Recordset</definedTerm>
        <definition>
          <para>A <legacyBold>Recordset</legacyBold> whose columns have been specifically defined to contain not just data, but also references (called chapters) to other <legacyBold>Recordset</legacyBold> objects and/or computed values based on other <legacyBold>Recordset</legacyBold> objects.</para>
        </definition>
        <definedTerm>sibling</definedTerm>
        <definition>
          <para>Any two or more nodes in a hierarchical structure that are on the same level in the hierarchy. The root node in a hierarchy has no siblings.</para>
        </definition>
        <definedTerm>stored procedure</definedTerm>
        <definition>
          <para>A precompiled collection of code such as SQL statements and optional control-of-flow statements stored under a name and processed as a unit. Stored procedures are stored within a database; they can be executed with one call from an application and allow user-declared variables, conditional execution, and other powerful programming features.</para>
        </definition>
        <definedTerm>stub</definedTerm>
        <definition>
          <para>An interface-specific object that provides the parameter marshaling and communication required for an application object to receive calls from a client that is running in a different execution environment, such as on a different thread or in another process. The stub is located with the application object and communicates with a corresponding proxy that is located with the client that calls it. See also proxy.</para>
        </definition>
        <definedTerm>sub-node</definedTerm>
        <definition>
          <para>See child.</para>
        </definition>
        <definedTerm>synchronous operation</definedTerm>
        <definition>
          <para>An operation initiated by code that completes before the next operation may start. See also asynchronous operation.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>T-Z</title>
    <content>
      <definitionTable>
        <definedTerm>Tree</definedTerm>
        <definition>
          <para>A structure representing a hierarchical relationship between elements (nodes). There is one node at the top level of a tree (the root). Underneath the root, there can be multiple children. Each child may in turn be the parent of other children, thus branching like a tree. A folder containing documents and other folders is a typical example of a tree structure. See also hierarchy, node, root, child, parent.</para>
        </definition>
        <definedTerm>Web server</definedTerm>
        <definition>
          <para>A computer that provides Web services and pages to intranet and Internet users.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>