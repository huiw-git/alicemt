---
title: "SchemaEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 21c97651-297f-469f-b5b5-c48af72b62a8
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
# SchemaEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the type of schema <legacyBold>Recordset</legacyBold> that the <legacyLink xlink:href="850cf3ce-f18f-4e7c-8597-96c1dc504866">OpenSchema</legacyLink> method retrieves.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>Additional information about the function and columns returned for each ADO constant can be found in topics in <legacyLink xlink:href="2b5fbf03-e50d-44ee-bc57-5a57666c55f1">Appendix B: Schema Rowsets</legacyLink> of the OLE DB Programmer's Reference. The name of each topic is listed in parentheses in the Description section of the following table.</para>
      <para>Additional information about the function and columns returned for each ADO MD constant can be found in topics in <legacyLink xlink:href="d20bb2a6-68bd-423f-9ec8-eb930cd0c144">OLE DB for OLAP Objects and Schema Rowsets</legacyLink> in the OLE DB for Online Analytical Processing (OLAP) documentation. The name of each topic is listed in parentheses in the Description column of the following table.</para>
      <para>You can translate the data types of columns in the OLE DB documentation to ADO data types by referring to the Description column of the ADO <legacyLink xlink:href="2c57eca6-9336-4b06-ba10-9fef5926b1d0">DataTypeEnum</legacyLink> topic. For example, an OLE DB data type of <legacyBold>DBTYPE_WSTR</legacyBold> is equivalent to an ADO data type of <legacyBold>adWChar</legacyBold>.</para>
      <para>ADO generates schema-like results for the constants, <legacyBold>adSchemaDBInfoKeywords</legacyBold> and <legacyBold>adSchemaDBInfoLiterals</legacyBold>. ADO creates a <legacyBold>Recordset</legacyBold>, and then fills each row with the values returned respectively by the <legacyBold>IDBInfo::GetKeywords</legacyBold> and <legacyBold>IDBInfo::GetLiteralInfo</legacyBold> methods. Additional information about these methods can be found in the <legacyLink xlink:href="3f5ad97f-3fc6-4f21-b691-f6911e4007f3">IDBInfo</legacyLink> section of the OLE DB Programmer's Reference.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Constant</para>
            </TD>
            <TD>
              <para>Value</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
            <TD>
              <para>Constraint Columns</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaAsserts</legacyBold>    </para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
            <TD>
              <para>Returns the assertions defined in the catalog that are owned by a given user.</para>
              <para>(ASSERTIONS Rowset)</para>
            </TD>
            <TD>
              <para>CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaCatalogs</legacyBold> </para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
            <TD>
              <para>Returns the physical attributes associated with catalogs accessible from the DBMS.</para>
              <para>(CATALOGS Rowset)</para>
            </TD>
            <TD>
              <para>CATALOG_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaCharacterSets</legacyBold>   </para>
            </TD>
            <TD>
              <para>2</para>
            </TD>
            <TD>
              <para>Returns the character sets defined in the catalog that are accessible to a given user.</para>
              <para>(CHARACTER_SETS Rowset)</para>
            </TD>
            <TD>
              <para>CHARACTER_SET_CATALOG CHARACTER_SET_SCHEMA CHARACTER_SET_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaCheckConstraints</legacyBold>  </para>
            </TD>
            <TD>
              <para>5</para>
            </TD>
            <TD>
              <para>Returns the check constraints defined in the catalog that are owned by a given user.</para>
              <para>(CHECK_CONSTRAINTS) Rowset)</para>
            </TD>
            <TD>
              <para>CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaCollations</legacyBold> </para>
            </TD>
            <TD>
              <para>3</para>
            </TD>
            <TD>
              <para>Returns the character collations defined in the catalog that are accessible to a given user.</para>
              <para>(COLLATIONS Rowset)</para>
            </TD>
            <TD>
              <para>COLLATION_CATALOG COLLATION_SCHEMA COLLATION_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaColumnPrivileges</legacyBold>  </para>
            </TD>
            <TD>
              <para>13</para>
            </TD>
            <TD>
              <para>Returns the privileges on columns of tables defined in the catalog that are available to, or granted by, a given user.</para>
              <para>(COLUMN_PRIVILEGES Rowset)</para>
            </TD>
            <TD>
              <para>TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME GRANTOR GRANTEE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaColumns</legacyBold>  </para>
            </TD>
            <TD>
              <para>4</para>
            </TD>
            <TD>
              <para>Returns the columns of tables (including views) defined in the catalog that are accessible to a given user.</para>
              <para>(COLUMNS Rowset)</para>
            </TD>
            <TD>
              <para>TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaColumnsDomainUsage</legacyBold>  </para>
            </TD>
            <TD>
              <para>11</para>
            </TD>
            <TD>
              <para>Returns the columns defined in the catalog that are dependent on a domain defined in the catalog and owned by a given user.</para>
              <para>(COLUMN_DOMAIN_USAGE Rowset)</para>
            </TD>
            <TD>
              <para>DOMAIN_CATALOG DOMAIN_SCHEMA DOMAIN_NAME COLUMN_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaConstraintColumnUsage</legacyBold>             </para>
            </TD>
            <TD>
              <para>6</para>
            </TD>
            <TD>
              <para>Returns the columns used by referential constraints, unique constraints, check constraints, and assertions, defined in the catalog and owned by a given user.</para>
              <para>(CONSTRAINT_COLUMN_USAGE Rowset)</para>
            </TD>
            <TD>
              <para>TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaConstraintTableUsage</legacyBold>
              </para>
            </TD>
            <TD>
              <para>7</para>
            </TD>
            <TD>
              <para>Returns the tables that are used by referential constraints, unique constraints, check constraints, and assertions defined in the catalog and owned by a given user.</para>
              <para>(CONSTRAINT_TABLE_USAGE Rowset)</para>
            </TD>
            <TD>
              <para>TABLE_CATALOG TABLE_SCHEMA TABLE_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaCubes</legacyBold> </para>
            </TD>
            <TD>
              <para>32</para>
            </TD>
            <TD>
              <para>Returns information about the available cubes in a schema (or the catalog, if the provider does not support schemas). </para>
              <para>(CUBES Rowset*)</para>
            </TD>
            <TD>
              <para>CATALOG_NAME SCHEMA_NAME CUBE_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaDBInfoKeywords</legacyBold>  </para>
            </TD>
            <TD>
              <para>30</para>
            </TD>
            <TD>
              <para>Returns a list of provider-specific keywords.</para>
              <para>(IDBInfo::GetKeywords)</para>
            </TD>
            <TD>
              <para>&lt;None&gt;</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaDBInfoLiterals</legacyBold>  </para>
            </TD>
            <TD>
              <para>31</para>
            </TD>
            <TD>
              <para>Returns a list of provider-specific literals used in text commands.</para>
              <para>(IDBInfo::GetLiteralInfo)</para>
            </TD>
            <TD>
              <para>&lt;None&gt;</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaDimensions</legacyBold> </para>
            </TD>
            <TD>
              <para>33</para>
            </TD>
            <TD>
              <para>Returns information about the dimensions in a given cube. It has one row for each dimension.</para>
              <para>(DIMENSIONS Rowset)</para>
            </TD>
            <TD>
              <para>CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_NAME DIMENSION_UNIQUE_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaForeignKeys</legacyBold> </para>
            </TD>
            <TD>
              <para>27</para>
            </TD>
            <TD>
              <para>Returns the foreign key columns defined in the catalog by a given user.</para>
              <para>(FOREIGN_KEYS Rowset)</para>
            </TD>
            <TD>
              <para>PK_TABLE_CATALOG PK_TABLE_SCHEMA PK_TABLE_NAME FK_TABLE_CATALOG FK_TABLE_SCHEMA FK_TABLE_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaHierarchies</legacyBold> </para>
            </TD>
            <TD>
              <para>34</para>
            </TD>
            <TD>
              <para>Returns information about the hierarchies available in a dimension.</para>
              <para>(HIERARCHIES Rowset)</para>
            </TD>
            <TD>
              <para>CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_NAME HIERARCHY_UNIQUE_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaIndexes</legacyBold> </para>
            </TD>
            <TD>
              <para>12</para>
            </TD>
            <TD>
              <para>Returns the indexes defined in the catalog that are owned by a given user.</para>
              <para>(INDEXES Rowset)</para>
            </TD>
            <TD>
              <para>TABLE_CATALOG TABLE_SCHEMA INDEX_NAME TYPE TABLE_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaKeyColumnUsage</legacyBold> </para>
            </TD>
            <TD>
              <para>8</para>
            </TD>
            <TD>
              <para>Returns the columns defined in the catalog that are constrained as keys by a given user.</para>
              <para>(KEY_COLUMN_USAGE Rowset)</para>
            </TD>
            <TD>
              <para>CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaLevels</legacyBold> </para>
            </TD>
            <TD>
              <para>35</para>
            </TD>
            <TD>
              <para>Returns information about the levels available in a dimension.</para>
              <para>(LEVELS Rowset)</para>
            </TD>
            <TD>
              <para>CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_NAME LEVEL_UNIQUE_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaMeasures</legacyBold> </para>
            </TD>
            <TD>
              <para>36</para>
            </TD>
            <TD>
              <para>Returns information about the available measures.</para>
              <para>(MEASURES Rowset)</para>
            </TD>
            <TD>
              <para>CATALOG_NAME SCHEMA_NAME CUBE_NAME MEASURE_NAME MEASURE_UNIQUE_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaMembers</legacyBold> </para>
            </TD>
            <TD>
              <para>38</para>
            </TD>
            <TD>
              <para>Returns information about the available members.</para>
              <para>(MEMBERS Rowset)</para>
            </TD>
            <TD>
              <para>CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_UNIQUE_NAME LEVEL_NUMBER MEMBER_NAME MEMBER_UNIQUE_NAME MEMBER_CAPTION MEMBER_TYPE Tree operator. For more information, see <?Comment JT: deleted bad link to this 2006-02-02T19:41:00Z  Id='0?>OLE DB for Online Analytical Processing (OLAP)<?CommentEnd Id='0'
    ?>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaPrimaryKeys</legacyBold>  </para>
            </TD>
            <TD>
              <para>28</para>
            </TD>
            <TD>
              <para>Returns the primary key columns defined in the catalog by a given user.</para>
              <para>(PRIMARY_KEYS Rowset)</para>
            </TD>
            <TD>
              <para>PK_TABLE_CATALOG PK_TABLE_SCHEMA PK_TABLE_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaProcedureColumns</legacyBold>   </para>
            </TD>
            <TD>
              <para>29</para>
            </TD>
            <TD>
              <para>Returns information about the columns of rowsets returned by procedures.</para>
              <para>(PROCEDURE_COLUMNS Rowset)</para>
            </TD>
            <TD>
              <para>PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME COLUMN_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaProcedureParameters</legacyBold>  </para>
            </TD>
            <TD>
              <para>26</para>
            </TD>
            <TD>
              <para>Returns information about the parameters and return codes of procedures.</para>
              <para>(PROCEDURE_PARAMETERS Rowset)</para>
            </TD>
            <TD>
              <para>PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME PARAMETER_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaProcedures</legacyBold> </para>
            </TD>
            <TD>
              <para>16</para>
            </TD>
            <TD>
              <para>Returns the procedures defined in the catalog that are owned by a given user.</para>
              <para>(PROCEDURES Rowset)</para>
            </TD>
            <TD>
              <para>PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME PROCEDURE_TYPE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaProperties</legacyBold>  </para>
            </TD>
            <TD>
              <para>37</para>
            </TD>
            <TD>
              <para>Returns information about the available properties for each level of the dimension.</para>
              <para>(PROPERTIES Rowset)</para>
            </TD>
            <TD>
              <para>CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_UNIQUE_NAME MEMBER_UNIQUE_NAME PROPERTY_TYPE PROPERTY_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaProviderSpecific</legacyBold> </para>
            </TD>
            <TD>
              <para>-1</para>
            </TD>
            <TD>
              <para>Used if the provider defines its own nonstandard schema queries.</para>
            </TD>
            <TD>
              <para>&lt;Provider specific&gt;</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaProviderTypes</legacyBold>
              </para>
            </TD>
            <TD>
              <para>22</para>
            </TD>
            <TD>
              <para>Returns the (base) data types supported by the data provider.</para>
              <para>(PROVIDER_TYPES Rowset)</para>
            </TD>
            <TD>
              <para>DATA_TYPE BEST_MATCH</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>AdSchemaReferentialConstraints</legacyBold> </para>
            </TD>
            <TD>
              <para>9</para>
            </TD>
            <TD>
              <para>Returns the referential constraints defined in the catalog that are owned by a given user.</para>
              <para>(REFERENTIAL_CONSTRAINTS Rowset)</para>
            </TD>
            <TD>
              <para>CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaSchemata</legacyBold>  </para>
            </TD>
            <TD>
              <para>17</para>
            </TD>
            <TD>
              <para>Returns the schemas (database objects) that are owned by a given user.</para>
              <para>(SCHEMATA Rowset)</para>
            </TD>
            <TD>
              <para>CATALOG_NAME SCHEMA_NAME SCHEMA_OWNER</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaSQLLanguages</legacyBold> </para>
            </TD>
            <TD>
              <para>18</para>
            </TD>
            <TD>
              <para>Returns the conformance levels, options, and dialects supported by the SQL-implementation processing data defined in the catalog.</para>
              <para>(SQL_LANGUAGES Rowset)</para>
            </TD>
            <TD>
              <para>&lt;None&gt;</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaStatistics</legacyBold>   </para>
            </TD>
            <TD>
              <para>19</para>
            </TD>
            <TD>
              <para>Returns the statistics defined in the catalog that are owned by a given user.</para>
              <para>(STATISTICS Rowset)</para>
            </TD>
            <TD>
              <para>TABLE_CATALOG TABLE_SCHEMA TABLE_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaTableConstraints</legacyBold>  </para>
            </TD>
            <TD>
              <para>10</para>
            </TD>
            <TD>
              <para>Returns the table constraints defined in the catalog that are owned by a given user.</para>
              <para>(TABLE_CONSTRAINTS Rowset)</para>
            </TD>
            <TD>
              <para>CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME TABLE_CATALOG TABLE_SCHEMA TABLE_NAME CONSTRAINT_TYPE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaTablePrivileges</legacyBold>  </para>
            </TD>
            <TD>
              <para>14</para>
            </TD>
            <TD>
              <para>Returns the privileges on tables defined in the catalog that are available to, or granted by, a given user.</para>
              <para>(TABLE_PRIVILEGES Rowset)</para>
            </TD>
            <TD>
              <para>TABLE_CATALOG TABLE_SCHEMA TABLE_NAME GRANTOR GRANTEE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaTables</legacyBold>  </para>
            </TD>
            <TD>
              <para>20</para>
            </TD>
            <TD>
              <para>Returns the tables (including views) defined in the catalog that are accessible to a given user.</para>
              <para>(TABLES Rowset)</para>
            </TD>
            <TD>
              <para>TABLE_CATALOG TABLE_SCHEMA TABLE_NAME TABLE_TYPE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaTranslations</legacyBold>   </para>
            </TD>
            <TD>
              <para>21</para>
            </TD>
            <TD>
              <para>Returns the character translations defined in the catalog that are accessible to a given user.</para>
              <para>(TRANSLATIONS Rowset)</para>
            </TD>
            <TD>
              <para>TRANSLATION_CATALOG TRANSLATION_SCHEMA TRANSLATION_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaTrustees</legacyBold>    </para>
            </TD>
            <TD>
              <para>39</para>
            </TD>
            <TD>
              <para>Reserved for future use.</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaUsagePrivileges</legacyBold>   </para>
            </TD>
            <TD>
              <para>15</para>
            </TD>
            <TD>
              <para>Returns the USAGE privileges on objects defined in the catalog that are available to, or granted by, a given user.</para>
              <para>(USAGE_PRIVILEGES Rowset)</para>
            </TD>
            <TD>
              <para>OBJECT_CATALOG OBJECT_SCHEMA OBJECT_NAME OBJECT_TYPE GRANTOR GRANTEE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaViewColumnUsage</legacyBold>  </para>
            </TD>
            <TD>
              <para>24</para>
            </TD>
            <TD>
              <para>Returns the columns on which viewed tables, defined in the catalog and owned by a given user, are dependent.</para>
              <para>(VIEW_COLUMN_USAGE Rowset)</para>
            </TD>
            <TD>
              <para>VIEW_CATALOG VIEW_SCHEMA VIEW_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaViews</legacyBold>  </para>
            </TD>
            <TD>
              <para>23</para>
            </TD>
            <TD>
              <para>Returns the views defined in the catalog that are accessible to a given user.</para>
              <para>(VIEWS Rowset)</para>
            </TD>
            <TD>
              <para>TABLE_CATALOG TABLE_SCHEMA TABLE_NAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adSchemaViewTableUsage</legacyBold>  </para>
            </TD>
            <TD>
              <para>25</para>
            </TD>
            <TD>
              <para>Returns the tables on which viewed tables, defined in the catalog and owned by a given user, are dependent.</para>
              <para>(VIEW_TABLE_USAGE Rowset)</para>
            </TD>
            <TD>
              <para>VIEW_CATALOG VIEW_SCHEMA VIEW_NAME</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>ADO/WFC Equivalent</title>
    <content>
      <para>Package: <legacyBold>com.ms.wfc.data</legacyBold></para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Constant</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>AdoEnums.Schema.ASSERTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.CATALOGS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.CHARACTERSETS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.CHECKCONSTRAINTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.COLLATIONS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.COLUMNPRIVILEGES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.COLUMNS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.COLUMNSDOMAINUSAGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.CONSTRAINTCOLUMNUSAGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.CONSTRAINTTABLEUSAGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.CUBES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.DBINFOKEYWORDS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.DBINFOLITERALS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.DIMENSIONS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.FOREIGNKEYS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.HIERARCHIES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.INDEXES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.KEYCOLUMNUSAGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.LEVELS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.MEASURES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.MEMBERS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.PRIMARYKEYS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.PROCEDURECOLUMNS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.PROCEDUREPARAMETERS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.PROCEDURES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.PROPERTIES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.PROVIDERSPECIFIC</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.PROVIDERTYPES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.REFERENTIALCONTRAINTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.SCHEMATA</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.SQLLANGUAGES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.STATISTICS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.TABLECONSTRAINTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.TABLEPRIVILEGES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.TABLES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.TRANSLATIONS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.TRUSTEES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.USAGEPRIVILEGES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.VIEWCOLUMNUSAGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.VIEWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Schema.VIEWTABLEUSAGE</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="850cf3ce-f18f-4e7c-8597-96c1dc504866">OpenSchema Method</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>