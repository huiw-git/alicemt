---
title: "Visual C++ ADO Programming"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 11233b96-e05c-4221-9aed-5f20944b0f1c
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
# Visual C++ ADO Programming
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The ADO API Reference describes the functionality of the ADO application programming interface (API) using a syntax similar to Microsoft Visual Basic. Though the intended audience is all users, ADO programmers employ diverse languages such as Visual Basic, Visual C++ (with and without the <legacyBold>#import</legacyBold> directive), and Visual J++ (with the ADO/WFC class package).</para>
    <para>To accommodate this diversity, the <legacyLink xlink:href="07d25fc0-4958-4e12-b616-36257ead812b">ADO for Visual C++ Syntax Indexes</legacyLink> provide Visual C++ language-specific syntax with links to common descriptions of functionality, parameters, exceptional behaviors, and so on, in the API Reference.</para>
    <para>ADO is implemented with COM (Component Object Model) interfaces. However, it is easier for programmers to work with COM in certain programming languages than others. For example, nearly all the details of using COM are handled implicitly for Visual Basic programmers, whereas Visual C++ programmers must attend to those details themselves.</para>
    <para>The following sections summarize details for C and C++ programmers using ADO and the <legacyBold>#import</legacyBold> directive. It focuses on data types specific to COM (<legacyBold>Variant</legacyBold>, <legacyBold>BSTR</legacyBold>, and <legacyBold>SafeArray</legacyBold>), and error handling (_com_error).</para>
  </introduction>
  <section>
    <title>Using the #import Compiler Directive</title>
    <content>
      <para>The <legacyBold>#import</legacyBold> Visual C++ compiler directive simplifies working with the ADO methods and properties. The directive takes the name of a file containing a type library, such as the ADO .dll (Msado15.dll), and generates header files containing typedef declarations, smart pointers for interfaces, and enumerated constants. Each interface is encapsulated, or wrapped, in a class. </para>
      <para>For each operation within a class (that is, a method or property call), there is a declaration to call the operation directly (that is, the "raw" form of the operation), and a declaration to call the raw operation and throw a COM error if the operation fails to execute successfully. If the operation is a property, there is usually a compiler directive that creates an alternative syntax for the operation that has syntax like Visual Basic.</para>
      <para>Operations that retrieve the value of a property have names of the form, <legacyBold>Get</legacyBold><legacyItalic>Property</legacyItalic>. Operations that set the value of a property have names of the form, <legacyBold>Put</legacyBold><legacyItalic>Property</legacyItalic>. Operations that set the value of a property with a pointer to an ADO object have names of the form, <legacyBold>PutRef</legacyBold><legacyItalic>Property</legacyItalic>. </para>
      <para>You can get or set a property with calls of these forms:</para>
      <code>variable = objectPtr-&gt;Get<legacyItalic>Property</legacyItalic>(); // get property value 
objectPtr-&gt;Put<legacyItalic>Property</legacyItalic>(<legacyItalic>value</legacyItalic>);       // set property value
objectPtr-&gt;PutRef<legacyItalic>Property</legacyItalic>(&amp;<legacyItalic>value</legacyItalic>);   // set property with object pointer</code>
    </content>
  </section>
  <section>
    <title>Using Property Directives</title>
    <content>
      <para>The <legacyBold>__declspec(property...)</legacyBold> compiler directive is a Microsoft-specific C language extension that declares a function used as a property to have an alternative syntax. As a result, you can set or get values of a property in a way similar to Visual Basic. For example, you can set and get a property this way:</para>
      <code>objectPtr-&gt;<legacyItalic>property</legacyItalic> = <legacyItalic>value</legacyItalic>;        // set property value
variable = objectPtr-&gt;<legacyItalic>property</legacyItalic>;     // get property value</code>
      <para>Notice you do not have to code:</para>
      <code>objectPtr-&gt;Put<legacyItalic>Property</legacyItalic>(<legacyItalic>value</legacyItalic>);      // set property value
variable = objectPtr-&gt;Get<legacyItalic>Property</legacyItalic>;  // get property value</code>
      <para>The compiler will generate the appropriate <legacyBold>Get</legacyBold><legacyItalic>-</legacyItalic>, <legacyBold>Put</legacyBold>-, or <legacyBold>PutRef</legacyBold><legacyItalic>Property</legacyItalic> call based on what alternative syntax is declared and whether the property is being read or written. </para>
      <para>The <legacyBold>__declspec(property...)</legacyBold> compiler directive can only declare <legacyBold>get</legacyBold>, <legacyBold>put</legacyBold>, or <legacyBold>get</legacyBold> and <legacyBold>put</legacyBold> alternative syntax for a function. Read-only operations only have a <legacyBold>get</legacyBold> declaration; write-only operations only have a <legacyBold>put</legacyBold> declaration; operations that are both read and write have both <legacyBold>get</legacyBold> and <legacyBold>put</legacyBold> declarations.</para>
      <para>Only two declarations are possible with this directive; however, each property may have three property functions: <legacyBold>Get</legacyBold><legacyItalic>Property</legacyItalic>, <legacyBold>Put</legacyBold><legacyItalic>Property</legacyItalic>, and <legacyBold>PutRef</legacyBold><legacyItalic>Property</legacyItalic>. In that case, only two forms of the property have the alternative syntax.</para>
      <para>For example, the <legacyBold>Command</legacyBold> object <legacyBold>ActiveConnection</legacyBold> property is declared with an alternative syntax for <legacyBold>Get</legacyBold><legacyItalic>ActiveConnection</legacyItalic> and <legacyBold>PutRef</legacyBold><legacyItalic>ActiveConnection</legacyItalic>. The <legacyBold>PutRef</legacyBold>- syntax is a good choice because in practice, you will typically want to put an open <legacyBold>Connection</legacyBold> object (that is, a <legacyBold>Connection</legacyBold> object pointer) in this property. On the other hand, the <legacyBold>Recordset</legacyBold> object has <legacyBold>Get</legacyBold>-, <legacyBold>Put</legacyBold>-, and <legacyBold>PutRef</legacyBold><legacyItalic>ActiveConnection</legacyItalic> operations, but no alternative syntax.</para>
    </content>
  </section>
  <section>
    <title>Collections, the GetItem Method, and the Item Property</title>
    <content>
      <para>ADO defines several collections, including <legacyBold>Fields</legacyBold>, <legacyBold>Parameters</legacyBold>, <legacyBold>Properties</legacyBold>, and <legacyBold>Errors</legacyBold>. In Visual C++, the <legacyBold>GetItem(</legacyBold><legacyItalic>index</legacyItalic><legacyBold>)</legacyBold> method returns a member of the collection. <legacyItalic>Index</legacyItalic> is a <legacyBold>Variant</legacyBold>, the value of which is either a numeric index of the member in the collection, or a string containing the name of the member.</para>
      <para>The <legacyBold>__declspec(property...)</legacyBold> compiler directive declares the <legacyBold>Item</legacyBold> property as an alternative syntax to each collection's fundamental <legacyBold>GetItem() </legacyBold>method. The alternative syntax uses square brackets and looks similar to an array reference. In general, the two forms look like the following:</para>
      <code>
        <legacyItalic>collectionPtr-&gt;</legacyItalic>GetItem(index);
<legacyItalic>collectionPtr</legacyItalic>-&gt;Item[index];</code>
      <para>For example, assign a value to a field of a <legacyBold>Recordset</legacyBold> object, named <legacyBold><legacyItalic>rs</legacyItalic></legacyBold>, derived from the <legacyBold>authors</legacyBold> table of the <legacyBold>pubs</legacyBold> database. Use the <legacyBold>Item()</legacyBold> property to access the third <legacyBold>Field</legacyBold> of the <legacyBold>Recordset</legacyBold> object <legacyBold>Fields</legacyBold> collection (collections are indexed from zero; assume the third field is named <legacyBold><legacyItalic>au_fname</legacyItalic></legacyBold>). Then call the <legacyBold>Value()</legacyBold> method on the <legacyBold>Field</legacyBold> object to assign a string value.</para>
      <para>This can be expressed in Visual Basic in the following four ways (the last two forms are unique to Visual Basic; other languages do not have equivalents):</para>
      <code>rs.Fields.Item(2).Value = "<legacyItalic>value</legacyItalic>"
rs.Fields.Item("au_fname").Value = "<legacyItalic>value</legacyItalic>"
rs(2) = "<legacyItalic>value</legacyItalic>"
rs!au_fname = "<legacyItalic>value</legacyItalic>"</code>
      <para>The equivalent in Visual C++ to the first two forms above is:</para>
      <code>rs-&gt;Fields-&gt;GetItem(long(2))-&gt;PutValue("<legacyItalic>value</legacyItalic>"); 
rs-&gt;Fields-&gt;GetItem("au_fname")-&gt;PutValue("<legacyItalic>value</legacyItalic>");</code>
      <para>-or- (the alternative syntax for the <legacyBold>Value</legacyBold> property is also shown)</para>
      <code>rs-&gt;Fields-&gt;Item[long(2)]-&gt;Value = "<legacyItalic>value</legacyItalic>";
rs-&gt;Fields-&gt;Item["au_fname"]-&gt;Value = "<legacyItalic>value</legacyItalic>";</code>
      <para>For examples of iterating through a collection, see the "ADO Collections" section of "ADO Reference".</para>
    </content>
  </section>
  <section>
    <title>COM-Specific Data Types</title>
    <content>
      <para>In general, any Visual Basic data type you find in the ADO API Reference has a Visual C++ equivalent. These include standard data types such as <legacyBold>unsigned char</legacyBold> for a Visual Basic <legacyBold>Byte</legacyBold>, <legacyBold>short</legacyBold> for <legacyBold>Integer</legacyBold>, and <legacyBold>long </legacyBold>for <legacyBold>Long</legacyBold>. Look in the Syntax Indexesto see exactly what is required for the operands of a given method or property.</para>
      <para>The exceptions to this rule are the data types specific to COM: <legacyBold>Variant</legacyBold>, <legacyBold>BSTR</legacyBold>, and <legacyBold>SafeArray</legacyBold>.</para>
    </content>
    <sections>
      <section>
        <title>Variant</title>
        <content>
          <para>A <legacyBold>Variant</legacyBold> is a structured data type that contains a value member and a data type member. A <legacyBold>Variant</legacyBold> may contain a wide range of other data types including another Variant, BSTR, Boolean, IDispatch or IUnknown pointer, currency, date, and so on. COM also provides methods that make it easy to convert one data type to another. </para>
          <para>The <legacyBold>_variant_t</legacyBold> class encapsulates and manages the <legacyBold>Variant</legacyBold> data type.</para>
          <para>When the ADO API Reference says a method or property operand takes a value, it usually means the value is passed in a <legacyBold>_variant_t</legacyBold>.</para>
          <para>This rule is explicitly true when the <legacyBold>Parameters</legacyBold> section in the topics of the ADO API Reference says an operand is a <legacyBold>Variant</legacyBold>. One exception is when the documentation explicitly says the operand takes a standard data type, such as <legacyBold>Long</legacyBold> or <legacyBold>Byte</legacyBold>, or an enumeration. Another exception is when the operand takes a <legacyBold>String</legacyBold>.</para>
        </content>
      </section>
      <section>
        <title>BSTR</title>
        <content>
          <para>A <legacyBold>BSTR</legacyBold> (<legacyBold>B</legacyBold>asic <legacyBold>STR</legacyBold>ing) is a structured data type that contains a character string and the string's length. COM provides methods to allocate, manipulate, and free a <legacyBold>BSTR</legacyBold>.</para>
          <para>The <legacyBold>_bstr_t</legacyBold> class encapsulates and manages the <legacyBold>BSTR</legacyBold> data type.</para>
          <para>When the ADO API Reference says a method or property takes a <legacyBold>String</legacyBold> value, it means the value is in the form of a <legacyBold>_bstr_t</legacyBold>.</para>
        </content>
      </section>
      <section>
        <title>Casting _variant_t and _bstr_t Classes</title>
        <content>
          <para>Often it is not necessary to explicitly code a <legacyBold>_variant_t</legacyBold> or <legacyBold>_bstr_t</legacyBold> in an argument to an operation. If the <legacyBold>_variant_t</legacyBold> or <legacyBold>_bstr_t</legacyBold> class has a constructor that matches the data type of the argument, the compiler will generate the appropriate <legacyBold>_variant_t</legacyBold> or <legacyBold>_bstr_t</legacyBold>.</para>
          <para>However, if the argument is ambiguous, that is, the argument's data type matches more than one constructor, you must cast the argument with the appropriate data type to invoke the correct constructor.</para>
          <para>For example, the declaration for the <legacyBold>Recordset::Open</legacyBold> method is:</para>
          <code>    HRESULT Open (
        const _variant_t &amp; Source,
        const _variant_t &amp; ActiveConnection,
        enum CursorTypeEnum CursorType,
        enum LockTypeEnum LockType,
        long Options );</code>
          <para>The <codeInline>ActiveConnection </codeInline>argument takes a reference to a <legacyBold>_variant_t</legacyBold>, which you may code as a connection string or a pointer to an open <legacyBold>Connection</legacyBold> object.</para>
          <para>The correct <legacyBold>_variant_t</legacyBold> will be constructed implicitly if you pass a string such as "<codeInline>DSN=pubs;uid=MyUserName;pwd=MyPassword;</codeInline>", or a pointer such as "<codeInline>(IDispatch *) pConn</codeInline>".</para>
          <alert class="note">
            <para>If you are connecting to a data source provider that supports Windows authentication, you should specify <system>Trusted_Connection=yes</system> or <system>Integrated Security = SSPI</system> instead of user ID and password information in the connection string.</para>
          </alert>
          <para>Or you may explicitly code a <legacyBold>_variant_t</legacyBold> containing a pointer such as "<codeInline>_variant_t((IDispatch *) pConn, true)</codeInline>". The cast, <codeInline>(IDispatch *)</codeInline>, resolves the ambiguity with another constructor that takes a pointer to an IUnknown interface.</para>
          <para>It is a crucial, though seldom mentioned fact, that ADO is an IDispatch interface. Whenever a pointer to an ADO object must be passed as a <legacyBold>Variant</legacyBold>, that pointer must be cast as a pointer to an IDispatch interface.</para>
          <para>The last case explicitly codes the second boolean argument of the constructor with its optional, default value of <codeInline>true</codeInline>. This argument causes the <legacyBold>Variant</legacyBold> constructor to call its <legacyBold>AddRef</legacyBold>() method, which compensates for ADO automatically calling the <legacyBold>_variant_t::Release</legacyBold>() method when the ADO method or property call completes.</para>
        </content>
      </section>
      <section>
        <title>SafeArray</title>
        <content>
          <para>A <legacyBold>SafeArray</legacyBold> is a structured data type that contains an array of other data types. A <legacyBold>SafeArray</legacyBold> is called <legacyItalic>safe</legacyItalic> because it contains information about the bounds of each array dimension, and limits access to array elements within those bounds.</para>
          <para>When the ADO API Reference says a method or property takes or returns an array, it means the method or property takes or returns a <legacyBold>SafeArray</legacyBold>, not a native C/C++ array.</para>
          <para>For example, the second parameter of the <legacyBold>Connection</legacyBold> object <legacyBold>OpenSchema</legacyBold> method requires an array of <legacyBold>Variant</legacyBold> values. Those <legacyBold>Variant</legacyBold> values must be passed as elements of a <legacyBold>SafeArray</legacyBold>, and that <legacyBold>SafeArray</legacyBold> must be set as the value of another <legacyBold>Variant</legacyBold>. It is that other <legacyBold>Variant</legacyBold> that is passed as the second argument of <legacyBold>OpenSchema</legacyBold>.</para>
          <para>As further examples, the first argument of the <legacyBold>Find</legacyBold> method is a <legacyBold>Variant</legacyBold> whose value is a one-dimensional <legacyBold>SafeArray</legacyBold>; each of the optional first and second arguments of <legacyBold>AddNew</legacyBold> is a one-dimensional <legacyBold>SafeArray</legacyBold>; and the return value of the <legacyBold>GetRows</legacyBold> method is a <legacyBold>Variant</legacyBold> whose value is a two-dimensional <legacyBold>SafeArray</legacyBold>.</para>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Missing and Default Parameters</title>
    <content>
      <para>Visual Basic allows missing parameters in methods. For example, the <legacyBold>Recordset</legacyBold> object <legacyBold>Open</legacyBold> method has five parameters, but you can skip intermediate parameters and leave off trailing parameters. A default <legacyBold>BSTR</legacyBold> or <legacyBold>Variant</legacyBold> will be substituted depending on the data type of the missing operand.</para>
      <para>In C/C++, all operands must be specified. If you want to specify a missing parameter whose data type is a string, specify a <legacyBold>_bstr_t</legacyBold> containing a null string. If you want to specify a missing parameter whose data type is a <legacyBold>Variant</legacyBold>, specify a <legacyBold>_variant_t</legacyBold> with a value of DISP_E_PARAMNOTFOUND and a type of VT_ERROR. Alternatively, specify the equivalent <legacyBold>_variant_t</legacyBold> constant, <legacyBold>vtMissing</legacyBold>, which is supplied by the <legacyBold>#import</legacyBold> directive.</para>
      <para>Three methods are exceptions to the typical use of <legacyBold>vtMissing</legacyBold>. These are the <legacyBold>Execute</legacyBold> methods of the <legacyBold>Connection</legacyBold> and <legacyBold>Command</legacyBold> objects, and the <legacyBold>NextRecordset</legacyBold> method of the <legacyBold>Recordset</legacyBold> object. The following are their signatures:</para>
      <code>_RecordsetPtr &lt;A HREF="mdmthcnnexecute.htm"&gt;Execute&lt;/A&gt;( _bstr_t <legacyItalic>CommandText</legacyItalic>, VARIANT * <legacyItalic>RecordsAffected</legacyItalic>, 
        long<legacyItalic> Options </legacyItalic>);  // Connection
_RecordsetPtr &lt;A HREF="mdmthcmdexecute.htm"&gt;Execute&lt;/A&gt;( VARIANT * <legacyItalic>RecordsAffected</legacyItalic>, VARIANT * <legacyItalic>Parameters</legacyItalic>, 
        long<legacyItalic> Options </legacyItalic>);  // Command
_RecordsetPtr &lt;A HREF="mdmthnextrec.htm"&gt;NextRecordset&lt;/A&gt;( VARIANT *<legacyItalic> RecordsAffected </legacyItalic>);  // Recordset</code>
      <para>The parameters, <legacyItalic>RecordsAffected</legacyItalic> and <legacyItalic>Parameters</legacyItalic>, are pointers to a <legacyBold>Variant</legacyBold>. <legacyItalic>Parameters</legacyItalic> is an input parameter which specifies the address of a <legacyBold>Variant</legacyBold> containing a single parameter, or array of parameters, that will modify the command being executed. <legacyItalic>RecordsAffected </legacyItalic>is an output parameter that specifies the address of a <legacyBold>Variant</legacyBold>, where the number of rows affected by the method is returned. </para>
      <para>In the <legacyBold>Command</legacyBold> object <legacyBold>Execute</legacyBold> method, indicate that no parameters are specified by setting <legacyItalic>Parameters</legacyItalic> to either <codeInline>&amp;vtMissing</codeInline> (which is recommended) or to the null pointer (that is, <legacyBold>NULL</legacyBold> or zero (0)). If <legacyItalic>Parameters</legacyItalic> is set to the null pointer, the method internally substitutes the equivalent of <legacyBold>vtMissing</legacyBold>, and then completes the operation. </para>
      <para>In all the methods, indicate that the number of records affected should not be returned by setting <legacyItalic>RecordsAffected </legacyItalic>to the null pointer. In this case, the null pointer is not so much a missing parameter as an indication that the method should discard the number of records affected.</para>
      <para>Thus, for these three methods, it is valid to code something such as:</para>
      <code>pConnection-&gt;Execute("<legacyItalic>commandText</legacyItalic>", NULL, adCmdText); 
pCommand-&gt;Execute(NULL, NULL, adCmdText);
pRecordset-&gt;NextRecordset(NULL);</code>
    </content>
  </section>
  <section>
    <title>Error Handling</title>
    <content>
      <para>In COM, most operations return an HRESULT return code that indicates whether a function completed successfully. The <legacyBold>#import</legacyBold> directive generates wrapper code around each "raw" method or property and checks the returned HRESULT. If the HRESULT indicates failure, the wrapper code throws a COM error by calling _com_issue_errorex() with the HRESULT return code as an argument. COM error objects can be caught in a <legacyBold>try</legacyBold>-<legacyBold>catch</legacyBold> block. (For efficiency's sake, catch a reference to a <legacyBold>_com_error</legacyBold> object.)</para>
      <para>Remember, these are ADO errors: they result from the ADO operation failing. Errors returned by the underlying provider appear as <legacyBold>Error</legacyBold> objects in the <legacyBold>Connection</legacyBold> object <legacyBold>Errors</legacyBold> collection.</para>
      <para>The <legacyBold>#import</legacyBold> directive creates only error handling routines for methods and properties declared in the ADO .dll. However, you can take advantage of this same error handling mechanism by writing your own error checking macro or inline function. See the topic, <legacyLink xlink:href="2952ece0-7217-4448-bb09-f6b64f43b7e2">Visual C++ Extensions</legacyLink>, or the code in the following sections for examples.</para>
    </content>
  </section>
  <section>
    <title>Visual C++ Equivalents of Visual Basic Conventions</title>
    <content>
      <para>The following is a summary of several conventions in the ADO documentation, coded in Visual Basic, as well as their equivalents in Visual C++.</para>
    </content>
    <sections>
      <section>
        <title>Declaring an ADO Object</title>
        <content>
          <para>In Visual Basic, an ADO object variable (in this case for a <legacyBold>Recordset</legacyBold> object) is declared as follows:</para>
          <code>Dim rst As ADODB.Recordset</code>
          <para>The clause, "<codeInline>ADODB.Recordset</codeInline>", is the ProgID of the <legacyBold>Recordset</legacyBold> object as defined in the registry. A new instance of a <legacyBold>Record</legacyBold> object is declared as follows:</para>
          <code>Dim rst As New ADODB.Recordset</code>
          <para>-or-</para>
          <code>Dim rst As ADODB.Recordset
Set rst = New ADODB.Recordset</code>
          <para>In Visual C++, the <legacyBold>#import </legacyBold>directive generates smart pointer-type declarations for all the ADO objects. For example, a variable that points to a <legacyBold>_Recordset</legacyBold> object is of type <legacyBold>_RecordsetPtr</legacyBold>, and is declared as follows:</para>
          <code>_RecordsetPtr  rs;</code>
          <para>A variable that points to a new instance of a <legacyBold>_Recordset</legacyBold> object is declared as follows:</para>
          <code>_RecordsetPtr  rs("ADODB.Recordset");</code>
          <para>-or-</para>
          <code>_RecordsetPtr  rs;
rs.CreateInstance("ADODB.Recordset");</code>
          <para>-or-</para>
          <code>_RecordsetPtr  rs;
rs.CreateInstance(__uuidof(_Recordset));</code>
          <para>After the <legacyBold>CreateInstance</legacyBold> method is called, the variable can be used as follows:</para>
          <code>rs-&gt;Open(...);</code>
          <para>Notice that in one case, the "<codeInline>.</codeInline>" operator is used as if the variable were an instance of a class (<codeInline>rs.CreateInstance</codeInline>), and in another case, the "<codeInline>-&gt;</codeInline>" operator is used as if the variable were a pointer to an interface (<codeInline>rs-&gt;Open</codeInline>).</para>
          <para>One variable can be used in two ways because the "<codeInline>-&gt;</codeInline>" operator is overloaded to allow an instance of a class to behave like a pointer to an interface. A private class member of the instance variable contains a pointer to the <legacyBold>_Recordset</legacyBold> interface; the "<codeInline>-&gt;</codeInline>" operator returns that pointer; and the returned pointer accesses the members of the <legacyBold>_Recordset</legacyBold> object.</para>
        </content>
      </section>
      <section>
        <title>Coding a Missing Parameter — String</title>
        <content>
          <para>When you need to code a missing <legacyBold>String</legacyBold> operand in Visual Basic, you merely omit the operand. You must specify the operand in Visual C++. Code a <legacyBold>_bstr_t</legacyBold> that has an empty string as a value.</para>
          <code>_bstr_t strMissing(L"");</code>
        </content>
      </section>
      <section>
        <title>Coding a Missing Parameter — Variant</title>
        <content>
          <para>When you need to code a missing <legacyBold>Variant</legacyBold> operand in Visual Basic, you merely omit the operand. You must specify all operands in Visual C++. Code a missing <legacyBold>Variant</legacyBold> parameter with a <legacyBold>_variant_t</legacyBold> set to the special value, DISP_E_PARAMNOTFOUND, and type, VT_ERROR. Alternatively, specify <legacyBold>vtMissing</legacyBold>, which is an equivalent predefined constant supplied by the <legacyBold>#import</legacyBold> directive.</para>
          <code>_variant_t  vtMissingYours(DISP_E_PARAMNOTFOUND, VT_ERROR); </code>
          <para>-or use -</para>
          <code>...vtMissing...;</code>
        </content>
      </section>
      <section>
        <title>Declaring a Variant</title>
        <content>
          <para>In Visual Basic, a <legacyBold>Variant</legacyBold> is declared with the <legacyBold>Dim</legacyBold> statement as follows:</para>
          <code>Dim <legacyItalic>VariableName</legacyItalic> As Variant</code>
          <para>In Visual C++, declare a variable as type <legacyBold>_variant_t</legacyBold>. A few schematic <legacyBold>_variant_t </legacyBold>declarations are shown below.</para>
          <alert class="note">
            <para>These declarations merely give a rough idea of what you would code in your own program. For more information, see the examples below, and the Visual C++documentation.</para>
          </alert>
          <code>_variant_t  VariableName(<legacyItalic>value</legacyItalic>);
_variant_t  VariableName((<legacyItalic>data type cast</legacyItalic>) <legacyItalic>value</legacyItalic>);
_variant_t  VariableName(<legacyItalic>value, </legacyItalic>VT<legacyItalic>_DATATYPE</legacyItalic>);
_variant_t  VariableName(interface * <legacyItalic>value, </legacyItalic>bool fAddRef = true);</code>
        </content>
      </section>
      <section>
        <title>Using Arrays of Variants</title>
        <content>
          <para>In Visual Basic, arrays of <legacyBold>Variants</legacyBold> can be coded with the <legacyBold>Dim</legacyBold> statement, or you may use the <legacyBold>Array</legacyBold> function, as demonstrated in the following example code:</para>
          <code>Public Sub ArrayOfVariants
Dim cn As ADODB.Connection
Dim rs As ADODB.Recordset
Dim fld As ADODB.Field

    cn.Open "DSN=pubs"
    rs = cn.OpenSchema(adSchemaColumns, _
        Array(Empty, Empty, "authors", Empty))
    For Each fld in rs.Fields
        Debug.Print "Name = "; fld.Name
    Next fld
    rs.Close
    cn.Close
End Sub</code>
          <para>The following Visual C++ example demonstrates using a <legacyBold>SafeArray</legacyBold> used with a <legacyBold>_variant_t</legacyBold>.</para>
        </content>
        <sections>
          <section>
            <title>Notes</title>
            <content>
              <para>The following notes correspond to commented sections in the code example.  </para>
              <list class="ordered">
                <listItem>
                  <para>Once again, the TESTHR() inline function is defined to take advantage of the existing error-handling mechanism.</para>
                </listItem>
                <listItem>
                  <para>You only need a one-dimensional array, so you can use <legacyBold>SafeArrayCreateVector</legacyBold>, instead of the general purpose <legacyBold>SAFEARRAYBOUND</legacyBold> declaration and <legacyBold>SafeArrayCreate</legacyBold> function. The following is what that code would look like using <legacyBold>SafeArrayCreate</legacyBold>: </para>
                  <code>   SAFEARRAYBOUND   sabound[1];
   sabound[0].lLbound = 0;
   sabound[0].cElements = 4;
   pSa = SafeArrayCreate(VT_VARIANT, 1, sabound);</code>
                </listItem>
                <listItem>
                  <para>The schema identified by the enumerated constant, <legacyBold>adSchemaColumns</legacyBold>, is associated with four constraint columns: TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME, and COLUMN_NAME. Therefore, an array of <legacyBold>Variant</legacyBold> values with four elements is created. Then a constraint value that corresponds to the third column, TABLE_NAME, is specified. </para>
                  <para>The <legacyBold>Recordset</legacyBold> that is returned consists of several columns, a subset of which is the constraint columns. The values of the constraint columns for each returned row must be the same as the corresponding constraint values. </para>
                </listItem>
                <listItem>
                  <para>Those familiar with <legacyBold>SafeArrays </legacyBold>may be surprised that <legacyBold>SafeArrayDestroy</legacyBold>() is not called before the exit. In fact, calling <legacyBold>SafeArrayDestroy</legacyBold>() in this case will cause a run-time exception. The reason is that the destructor for <codeInline>vtCriteria</codeInline> will call <legacyBold>VariantClear</legacyBold>() when the <legacyBold>_variant_t </legacyBold>goes out of scope, which will free the <legacyBold>SafeArray</legacyBold>. Calling <legacyBold>SafeArrayDestroy</legacyBold>, without manually clearing the <legacyBold>_variant_t</legacyBold>, would cause the destructor to try to clear an invalid <legacyBold>SafeArray</legacyBold> pointer. </para>
                  <para>If <legacyBold>SafeArrayDestroy</legacyBold> were called, the code would look like this:</para>
                  <code>      TESTHR(SafeArrayDestroy(pSa));
   vtCriteria.vt = VT_EMPTY;
      vtCriteria.parray = NULL;</code>
                  <para>However, it is much simpler to let the <legacyBold>_variant_t</legacyBold> manage the <legacyBold>SafeArray</legacyBold>. </para>
                </listItem>
              </list>
              <code>// Visual_CPP_ADO_Prog_1.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

// Note 1
inline void TESTHR( HRESULT _hr ) { 
   if FAILED(_hr) 
      _com_issue_error(_hr); 
}

int main() {
   CoInitialize(NULL);
   try {
      _RecordsetPtr pRs("ADODB.Recordset");
      _ConnectionPtr pCn("ADODB.Connection");
      _variant_t vtTableName("authors"), vtCriteria;
      long ix[1];
      SAFEARRAY *pSa = NULL;

      pCn-&gt;Provider = "sqloledb";
      pCn-&gt;Open("Data Source='(local)';Initial Catalog='pubs';Integrated Security=SSPI", "", "", adConnectUnspecified);
      // Note 2, Note 3
      pSa = SafeArrayCreateVector(VT_VARIANT, 1, 4);
      if (!pSa) 
         _com_issue_error(E_OUTOFMEMORY);

      // Specify TABLE_NAME in the third array element (index of 2). 
      ix[0] = 2;      
      TESTHR(SafeArrayPutElement(pSa, ix, &amp;vtTableName));

      // There is no Variant constructor for a SafeArray, so manually set the 
      // type (SafeArray of Variant) and value (pointer to a SafeArray).

      vtCriteria.vt = VT_ARRAY | VT_VARIANT;
      vtCriteria.parray = pSa;

      pRs = pCn-&gt;OpenSchema(adSchemaColumns, vtCriteria, vtMissing);

      long limit = pRs-&gt;GetFields()-&gt;Count;
      for ( long x = 0 ; x &lt; limit ; x++ )
         printf( "%d: %s\n", x + 1, ((char*) pRs-&gt;GetFields()-&gt;Item[x]-&gt;Name) );
      // Note 4
      pRs-&gt;Close();
      pCn-&gt;Close();
   }
   catch (_com_error &amp;e) {
      printf("Error:\n");
      printf("Code = %08lx\n", e.Error());
      printf("Code meaning = %s\n", (char*) e.ErrorMessage());
      printf("Source = %s\n", (char*) e.Source());
      printf("Description = %s\n", (char*) e.Description());
   }
   CoUninitialize();
}</code>
            </content>
          </section>
        </sections>
      </section>
      <section>
        <title>Using Property Get/Put/PutRef</title>
        <content>
          <para>In Visual Basic, the name of a property is not qualified by whether it is retrieved, assigned, or assigned a reference.</para>
          <code>Public Sub GetPutPutRef
Dim rs As New ADODB.Recordset
Dim cn As New ADODB.Connection
Dim sz as Integer
cn.Open "Provider=sqloledb;Data Source=yourserver;" &amp; _
         "Initial Catalog=pubs;Integrated Security=SSPI;"
rs.PageSize = 10
sz = rs.PageSize
rs.ActiveConnection = cn
rs.Open "authors",,adOpenStatic
' ...
rs.Close
cn.Close
End Sub</code>
          <para>This Visual C++ example demonstrates the <legacyBold>Get</legacyBold>/<legacyBold>Put</legacyBold>/<legacyBold>PutRef</legacyBold><legacyItalic>Property</legacyItalic>.</para>
        </content>
        <sections>
          <section>
            <title>Notes</title>
            <content>
              <para>The following notes correspond to commented sections in the code example.  </para>
              <list class="ordered">
                <listItem>
                  <para>This example uses two forms of a missing string argument: an explicit constant, <legacyBold>strMissing</legacyBold>, and a string that the compiler will use to create a temporary <legacyBold>_bstr_t</legacyBold> that will exist for the scope of the <legacyBold>Open</legacyBold> method.</para>
                </listItem>
                <listItem>
                  <para>It is not necessary to cast the operand of <codeInline>rs-&gt;PutRefActiveConnection(cn)</codeInline> to <codeInline>(IDispatch *)</codeInline> because the type of the operand is already <codeInline>(IDispatch *)</codeInline>.</para>
                </listItem>
              </list>
              <code>// Visual_CPP_ado_prog_2.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

int main() {
   CoInitialize(NULL);
   try {
      _ConnectionPtr cn("ADODB.Connection");
      _RecordsetPtr rs("ADODB.Recordset");
      _bstr_t strMissing(L"");
      long oldPgSz = 0, newPgSz = 5;

      // Note 1
      cn-&gt;Provider = "sqloledb";
      cn-&gt;Open("Data Source='(local)';Initial Catalog=pubs;Integrated Security=SSPI;", strMissing, "", adConnectUnspecified);

      oldPgSz = rs-&gt;GetPageSize();
      // -or-
      // oldPgSz = rs-&gt;PageSize;

      rs-&gt;PutPageSize(newPgSz);
      // -or-
      // rs-&gt;PageSize = newPgSz;

      // Note 2
      rs-&gt;PutRefActiveConnection( cn );
      rs-&gt;Open("authors", vtMissing, adOpenStatic, adLockReadOnly, adCmdTable);
      printf("Original pagesize = %d, new pagesize = %d\n", oldPgSz, rs-&gt;GetPageSize());
      rs-&gt;Close();
      cn-&gt;Close();
      
   }
   catch (_com_error &amp;e) {
      printf("Description = %s\n", (char*) e.Description());
   }
   ::CoUninitialize();
}</code>
            </content>
          </section>
        </sections>
      </section>
      <section>
        <title>Using GetItem(x) and Item[x]</title>
        <content>
          <para>This Visual Basic example demonstrates the standard and alternative syntax for <legacyBold>Item</legacyBold>().</para>
          <code>Public Sub GetItemItem
Dim rs As New ADODB.Recordset
Dim name as String
rs = rs.Open "authors", "DSN=pubs;", adOpenDynamic, _
         adLockBatchOptimistic, adTable
name = rs(0)
' -or-
name = rs.Fields.Item(0)
rs(0) = "Test"
rs.UpdateBatch
' Restore name
rs(0) = name
rs.UpdateBatch
rs.Close
End Sub</code>
          <para>This Visual C++ example demonstrates <legacyBold>Item</legacyBold>.</para>
          <alert class="note">
            <para>The following note corresponds to commented sections in the code example:  When the collection is accessed with <legacyBold>Item</legacyBold>, the index, <legacyBold>2</legacyBold>, must be cast to <legacyBold>long</legacyBold> so an appropriate constructor will be invoked.</para>
          </alert>
          <code>// Visual_CPP_ado_prog_3.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

void main() {
   CoInitialize(NULL);
   try {
      _ConnectionPtr cn("ADODB.Connection");
      _RecordsetPtr rs("ADODB.Recordset");
      _variant_t vtFirstName;

      cn-&gt;Provider = "sqloledb";
      cn-&gt;Open("Data Source='(local)';Initial Catalog=pubs;Integrated Security=SSPI;", "", "", adConnectUnspecified);

      rs-&gt;PutRefActiveConnection( cn );
      rs-&gt;Open("authors", vtMissing, adOpenStatic, adLockOptimistic, adCmdTable);
      rs-&gt;MoveFirst();

      // Note 1. Get a field.
      vtFirstName = rs-&gt;Fields-&gt;GetItem((long)2)-&gt;GetValue();
      // -or-
      vtFirstName = rs-&gt;Fields-&gt;Item[(long)2]-&gt;Value;

      printf( "First name = '%s'\n", (char*)( (_bstr_t)vtFirstName) );

      rs-&gt;Fields-&gt;GetItem((long)2)-&gt;Value = L"TEST";
      rs-&gt;Update(vtMissing, vtMissing);

      // Restore name
      rs-&gt;Fields-&gt;GetItem((long)2)-&gt;PutValue(vtFirstName);
      // -or-
      rs-&gt;Fields-&gt;GetItem((long)2)-&gt;Value = vtFirstName;
      rs-&gt;Update(vtMissing, vtMissing);
      rs-&gt;Close();
   }
   catch (_com_error &amp;e) {
      printf("Description = '%s'\n", (char*) e.Description());
   }
   ::CoUninitialize();
}</code>
        </content>
      </section>
      <section>
        <title>Casting ADO object pointers with (IDispatch *)</title>
        <content>
          <para>The following Visual C++ example demonstrates using (IDispatch *) to cast ADO object pointers.</para>
        </content>
        <sections>
          <section>
            <title>Notes</title>
            <content>
              <para>The following notes correspond to commented sections in the code example.  </para>
              <list class="ordered">
                <listItem>
                  <para>Specify an open <legacyBold>Connection</legacyBold> object in an explicitly coded <legacyBold>Variant</legacyBold>. Cast it with (IDispatch *) so the correct constructor will be invoked. Also, explicitly set the second <legacyBold>_variant_t</legacyBold> parameter to the default value of <legacyBold>true</legacyBold>, so the object reference count will be correct when the <legacyBold>Recordset::Open</legacyBold> operation ends.</para>
                </listItem>
                <listItem>
                  <para>The expression, <codeInline>(_bstr_t)</codeInline>, is not a cast, but a <legacyBold>_variant_t</legacyBold> operator that extracts a <legacyBold>_bstr_t </legacyBold>string from the <legacyBold>Variant</legacyBold> returned by <legacyBold>Value</legacyBold>.</para>
                </listItem>
              </list>
              <para>The expression, <codeInline>(char*)</codeInline>, is not a cast, but a <legacyBold>_bstr_t</legacyBold> operator that extracts a pointer to the encapsulated string in a <legacyBold>_bstr_t</legacyBold> object.</para>
              <para>This section of code demonstrates some of the useful behaviors of <legacyBold>_variant_t</legacyBold> and <legacyBold>_bstr_t</legacyBold> operators.</para>
              <code>// Visual_CPP_ado_prog_4.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

int main() {
   CoInitialize(NULL);
   try {
      _ConnectionPtr pConn("ADODB.Connection");
      _RecordsetPtr pRst("ADODB.Recordset");

      pConn-&gt;Provider = "sqloledb";
      pConn-&gt;Open("Data Source='(local)';Initial Catalog='pubs';Integrated Security=SSPI", "", "", adConnectUnspecified);

      // Note 1.
      pRst-&gt;Open("authors", _variant_t((IDispatch *) pConn, true), adOpenStatic, adLockReadOnly, adCmdTable);
      pRst-&gt;MoveLast();

      // Note 2.
      printf("Last name is '%s %s'\n", 
         (char*) ((_bstr_t) pRst-&gt;GetFields()-&gt;GetItem("au_fname")-&gt;GetValue()),
         (char*) ((_bstr_t) pRst-&gt;Fields-&gt;Item["au_lname"]-&gt;Value));

      pRst-&gt;Close();
      pConn-&gt;Close();
   }
   catch (_com_error &amp;e) {
      printf("Description = '%s'\n", (char*) e.Description());
   }   
   ::CoUninitialize();
}</code>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>