---
title: SQLServerDatabaseMetaData Members
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 327ba0bc-438a-494c-b119-1cd4a096bb58
manager:jhubbard
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - sv-se
  - zh-cn
  - zh-tw
---
# SQLServerDatabaseMetaData Members
  The following tables list the members that are exposed by the [SQLServerDatabaseMetaData](../content/SQLServerDatabaseMetaData-Class.md) class.  
  
## Constructors  
 None.  
  
## Fields  
 None.  
  
## Inherited Fields  
  
|Name|Description|  
|----------|-----------------|  
|java.sql.DatabaseMetaData|attributeNoNulls, attributeNullable, attributeNullableUnknown, bestRowNotPseudo, bestRowPseudo, bestRowSession, bestRowTemporary, bestRowTransaction, bestRowUnknown, columnNoNulls, columnNullable, columnNullableUnknown, importedKeyCascade, importedKeyInitiallyDeferred, importedKeyInitiallyImmediate, importedKeyNoAction, importedKeyNotDeferrable, importedKeyRestrict, importedKeySetDefault, importedKeySetNull, procedureColumnIn, procedureColumnInOut, procedureColumnOut, procedureColumnResult, procedureColumnReturn, procedureColumnUnknown, procedureNoNulls, procedureNoResult, procedureNullable, procedureNullableUnknown, procedureResultUnknown, procedureReturnsResult, sqlStateSQL, sqlStateSQL99, sqlStateXOpen, tableIndexClustered, tableIndexHashed, tableIndexOther, tableIndexStatistic, typeNoNulls, typeNullable, typeNullableUnknown, typePredBasic, typePredChar, typePredNone, typeSearchable, versionColumnNotPseudo, versionColumnPseudo, versionColumnUnknown|  
  
## Methods  
  
|Name|Description|  
|----------|-----------------|  
|[allProceduresAreCallable](../content/allProceduresAreCallable-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether the current user has permissions to call all the procedures returned by the [getProcedures](../content/getProcedures-Method--SQLServerDatabaseMetaData-.md) method.|  
|[allTablesAreSelectable](../content/allTablesAreSelectable-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether the current user has permissions to use all the tables returned by the [getTables](../content/getTables-Method--SQLServerDatabaseMetaData-.md) method in a SELECT statement.|  
|[autoCommitFailureClosesAllResultSets](../content/autoCommitFailureClosesAllResultSets-Method--SQLServerDatabaseMetaData-.md)|Indicates whether the JDBC driver closes all the open result sets, including the holdable ones, when an auto\-commit is enabled and an exception is raised.|  
|[dataDefinitionCausesTransactionCommit](../content/dataDefinitionCausesTransactionCommit-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether a data definition statement within a transaction forces the transaction to commit.|  
|[dataDefinitionIgnoredInTransactions](../content/dataDefinitionIgnoredInTransactions-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database ignores a data definition statement within a transaction.|  
|[deletesAreDetected](../content/deletesAreDetected-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether or not a visible row delete can be detected by calling the [rowDeleted](../content/rowDeleted-Method--SQLServerResultSet-.md) method of the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) class.|  
|[doesMaxRowSizeIncludeBlobs](../content/doesMaxRowSizeIncludeBlobs-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether the return value for the [getMaxRowSize](../content/getMaxRowSize-Method--SQLServerDatabaseMetaData-.md) method includes the SQL data types LONGVARCHAR and LONGVARBINARY.|  
|[getAttributes](../content/getAttributes-Method--SQLServerDatabaseMetaData-.md)|Retrieves a description of the given attribute of the given type for a user\-defined type that is available in the given schema and catalog.|  
|[getBestRowIdentifier](../content/getBestRowIdentifier-Method--SQLServerDatabaseMetaData-.md)|Retrieves a description of the optimal set of columns of a table that uniquely identifies a row.|  
|[getCatalogs](../content/getCatalogs-Method--SQLServerDatabaseMetaData-.md)|Retrieves the catalog names that are available in the connected server.|  
|[getCatalogSeparator](../content/getCatalogSeparator-Method--SQLServerDatabaseMetaData-.md)|Retrieves the **String** that this database uses as the separator between a catalog and table name.|  
|[getCatalogTerm](../content/getCatalogTerm-Method--SQLServerDatabaseMetaData-.md)|Retrieves the database vendor's preferred term for "catalog".|  
|[getClientInfoProperties](../content/getClientInfoProperties-Method--SQLServerDatabaseMetaData-.md)|Retrieves a list of the client information properties that the driver supports.|  
|[getColumnPrivileges](../content/getColumnPrivileges-Method--SQLServerDatabaseMetaData-.md)|Retrieves a description of the access rights for the columns in a table.|  
|[getColumns](../content/getColumns-Method--SQLServerDatabaseMetaData-.md)|Retrieves a description of the table columns that are available in the specified catalog.|  
|[getConnection](../content/getConnection-Method--SQLServerDatabaseMetaData-.md)|Retrieves the connection that produced this metadata object.|  
|[getCrossReference](../content/getCrossReference-Method--SQLServerDatabaseMetaData-.md)|Retrieves a description of the foreign key columns in the given foreign key table that references the primary key columns of the given primary key table.|  
|[getDatabaseMajorVersion](../content/getDatabaseMajorVersion-Method--SQLServerDatabaseMetaData-.md)|Retrieves the major version number of the underlying database.|  
|[getDatabaseMinorVersion](../content/getDatabaseMinorVersion-Method--SQLServerDatabaseMetaData-.md)|Retrieves the minor version number of the underlying database.|  
|[getDatabaseProductName](../content/getDatabaseProductName-Method--SQLServerDatabaseMetaData-.md)|Retrieves the name of this database product.|  
|[getDatabaseProductVersion](../content/getDatabaseProductVersion-Method--SQLServerDatabaseMetaData-.md)|Retrieves the version number of this database product.|  
|[getDefaultTransactionIsolation](../content/getDefaultTransactionIsolation-Method--SQLServerDatabaseMetaData-.md)|Retrieves the default transaction isolation level for this database.|  
|[getDriverMajorVersion](../content/getDriverMajorVersion-Method--SQLServerDatabaseMetaData-.md)|Retrieves the major version number of this JDBC driver.|  
|[getDriverMinorVersion](../content/getDriverMinorVersion-Method--SQLServerDatabaseMetaData-.md)|Retrieves the minor version number of this JDBC driver.|  
|[getDriverName](../content/getDriverName-Method--SQLServerDatabaseMetaData-.md)|Retrieves the name of this JDBC driver.|  
|[getDriverVersion](../content/getDriverVersion-Method--SQLServerDatabaseMetaData-.md)|Retrieves the version number of this JDBC driver.|  
|[getExportedKeys](../content/getExportedKeys-Method--SQLServerDatabaseMetaData-.md)|Retrieves a description of the foreign key columns that reference the given table's primary key columns.|  
|[getExtraNameCharacters](../content/getExtraNameCharacters-Method--SQLServerDatabaseMetaData-.md)|Retrieves all the extra characters that can be used in unquoted identifier names, for example, those beyond a\-z, A\-Z, 0\-9, and \_.|  
|[getFunctions](../content/getFunctions-Method--SQLServerDatabaseMetaData-.md)|Retrieves a description of the system and user functions.|  
|[getFunctionColumns](../content/getFunctionColumns-Method--SQLServerDatabaseMetaData-.md)|Retrieves a description of the specified catalog's system\- or user\-function parameters and return type.|  
|[getIdentifierQuoteString](../content/getIdentifierQuoteString-Method--SQLServerDatabaseMetaData-.md)|Retrieves the **String** that is used to quote SQL identifiers.|  
|[getImportedKeys](../content/getImportedKeys-Method--SQLServerDatabaseMetaData-.md)|Retrieves a description of the primary key columns that are referenced by a table's foreign key columns.|  
|[getIndexInfo](../content/getIndexInfo-Method--SQLServerDatabaseMetaData-.md)|Retrieves a description of the indexes and statistics of the given table.|  
|[getJDBCMajorVersion](../content/getJDBCMajorVersion-Method--SQLServerDatabaseMetaData-.md)|Retrieves the major JDBC version number for this driver.|  
|[getJDBCMinorVersion](../content/getJDBCMinorVersion-Method--SQLServerDatabaseMetaData-.md)|Retrieves the minor JDBC version number for this driver.|  
|[getMaxBinaryLiteralLength](../content/getMaxBinaryLiteralLength-Method--SQLServerDatabaseMetaData-.md)|Retrieves the maximum number of hex characters that this database allows in an inline binary literal.|  
|[getMaxCatalogNameLength](../content/getMaxCatalogNameLength-Method--SQLServerDatabaseMetaData-.md)|Retrieves the maximum number of characters that this database allows in a catalog name.|  
|[getMaxCharLiteralLength](../content/getMaxCharLiteralLength-Method--SQLServerDatabaseMetaData-.md)|Retrieves the maximum number of characters that this database allows for a character literal.|  
|[getMaxColumnNameLength](../content/getMaxColumnNameLength-Method--SQLServerDatabaseMetaData-.md)|Retrieves the maximum number of characters that this database allows for a column name.|  
|[getMaxColumnsInGroupBy](../content/getMaxColumnsInGroupBy-Method--SQLServerDatabaseMetaData-.md)|Retrieves the maximum number of columns that this database allows in a GROUP BY clause.|  
|[getMaxColumnsInIndex](../content/getMaxColumnsInIndex-Method--SQLServerDatabaseMetaData-.md)|Retrieves the maximum number of columns that this database allows in an index.|  
|[getMaxColumnsInOrderBy](../content/getMaxColumnsInOrderBy-Method--SQLServerDatabaseMetaData-.md)|Retrieves the maximum number of columns that this database allows in an ORDER BY clause.|  
|[getMaxColumnsInSelect](../content/getMaxColumnsInSelect-Method--SQLServerDatabaseMetaData-.md)|Retrieves the maximum number of columns that this database allows in a SELECT list.|  
|[getMaxColumnsInTable](../content/getMaxColumnsInTable-Method--SQLServerDatabaseMetaData-.md)|Retrieves the maximum number of columns that this database allows in a table.|  
|[getMaxConnections](../content/getMaxConnections-Method--SQLServerDatabaseMetaData-.md)|Retrieves the maximum number of concurrent connections to this database that are possible.|  
|[getMaxCursorNameLength](../content/getMaxCursorNameLength-Method--SQLServerDatabaseMetaData-.md)|Retrieves the maximum number of characters that this database allows in a cursor name.|  
|[getMaxIndexLength](../content/getMaxIndexLength-Method--SQLServerDatabaseMetaData-.md)|Retrieves the maximum number of bytes that this database allows for an index, including all of the parts of the index.|  
|[getMaxProcedureNameLength](../content/getMaxProcedureNameLength-Method--SQLServerDatabaseMetaData-.md)|Retrieves the maximum number of characters that this database allows in a procedure name.|  
|[getMaxRowSize](../content/getMaxRowSize-Method--SQLServerDatabaseMetaData-.md)|Retrieves the maximum number of bytes that this database allows in a single row.|  
|[getMaxSchemaNameLength](../content/getMaxSchemaNameLength-Method--SQLServerDatabaseMetaData-.md)|Retrieves the maximum number of characters that this database allows in a schema name.|  
|[getMaxStatementLength](../content/getMaxStatementLength-Method--SQLServerDatabaseMetaData-.md)|Retrieves the maximum number of characters that this database allows in an SQL statement.|  
|[getMaxStatements](../content/getMaxStatements-Method--SQLServerDatabaseMetaData-.md)|Retrieves the maximum number of active statements to this database that can be open at the same time.|  
|[getMaxTableNameLength](../content/getMaxTableNameLength-Method--SQLServerDatabaseMetaData-.md)|Retrieves the maximum number of characters that this database allows in a table name.|  
|[getMaxTablesInSelect](../content/getMaxTablesInSelect-Method--SQLServerDatabaseMetaData-.md)|Retrieves the maximum number of tables that this database allows in a SELECT statement.|  
|[getMaxUserNameLength](../content/getMaxUserNameLength-Method--SQLServerDatabaseMetaData-.md)|Retrieves the maximum number of characters that this database allows in a user name.|  
|[getNumericFunctions](../content/getNumericFunctions-Method--SQLServerDatabaseMetaData-.md)|Retrieves a comma\-separated list of math functions that are available with this database.|  
|[getPrimaryKeys](../content/getPrimaryKeys-Method--SQLServerDatabaseMetaData-.md)|Retrieves a description of the primary key columns of the given table.|  
|[getProcedureColumns](../content/getProcedureColumns-Method--SQLServerDatabaseMetaData-.md)|Retrieves a description of the stored procedure parameters and result columns.|  
|[getProcedures](../content/getProcedures-Method--SQLServerDatabaseMetaData-.md)|Retrieves a description of the stored procedures that are available in the given catalog, schema, or stored procedure name pattern.|  
|[getProcedureTerm](../content/getProcedureTerm-Method--SQLServerDatabaseMetaData-.md)|Retrieves the preferred term for "procedure" in this database.|  
|[getResultSetHoldability](../content/getResultSetHoldability-Method--SQLServerDatabaseMetaData-.md)|Retrieves the default holdability of result sets for this database.|  
|[getRowIdLifetime](../content/getRowIdLifetime-Method--SQLServerDatabaseMetaData-.md)|Returns a status indicating whether or not SQL RowId data type is supported. If supported, it returns the lifetime for which a RowId object remains valid.|  
|[getSchemas](../content/getSchemas-Method---.md)|Retrieves the schema names that are available in the current database.|  
|[getSchemaTerm](../content/getSchemaTerm-Method--SQLServerDatabaseMetaData-.md)|Retrieves the preferred term for "schema" in this database.|  
|[getSearchStringEscape](../content/getSearchStringEscape-Method--SQLServerDatabaseMetaData-.md)|Retrieves the **String** that can be used to escape wildcard characters.|  
|[getSQLKeywords](../content/getSQLKeywords-Method--SQLServerDatabaseMetaData-.md)|Retrieves a comma\-separated list of all of this database's SQL keywords that are not also SQL92 keywords.|  
|[getSQLStateType](../content/getSQLStateType-Method--SQLServerDatabaseMetaData-.md)|Indicates whether the SQLSTATE returned by the SQLException.getSQLState method is X\/Open \(now known as Open Group\), SQL CLI, SQL99 \(JDBC 3.0\), or SQL:2003 \(JDBC 4.0\).|  
|[getStringFunctions](../content/getStringFunctions-Method--SQLServerDatabaseMetaData-.md)|Retrieves a comma\-separated list of **String** functions that are available with this database.|  
|[getSuperTables](../content/getSuperTables-Method--SQLServerDatabaseMetaData-.md)|Retrieves a description of the table hierarchies that are defined in a particular schema in this database.|  
|[getSuperTypes](../content/getSuperTypes-Method--SQLServerDatabaseMetaData-.md)|Retrieves a description of the user\-defined type hierarchies that are defined in a particular schema in this database.|  
|[getSystemFunctions](../content/getSystemFunctions-Method--SQLServerDatabaseMetaData-.md)|Retrieves a comma\-separated list of system functions that are available with this database.|  
|[getTablePrivileges](../content/getTablePrivileges-Method--SQLServerDatabaseMetaData-.md)|Retrieves a description of the access rights for each table that is available in the given catalog, schema, or table name pattern.|  
|[getTables](../content/getTables-Method--SQLServerDatabaseMetaData-.md)|Retrieves a description of the tables that are available in the given catalog, schema, or table name pattern.|  
|[getTableTypes](../content/getTableTypes-Method--SQLServerDatabaseMetaData-.md)|Retrieves the table types that are available in the current database.|  
|[getTimeDateFunctions](../content/getTimeDateFunctions-Method--SQLServerDatabaseMetaData-.md)|Retrieves a comma\-separated list of the time and date functions that are available with this database.|  
|[getTypeInfo](../content/getTypeInfo-Method--SQLServerDatabaseMetaData-.md)|Retrieves a description of all the standard SQL types that are supported by the current database.|  
|[getUDTs](../content/getUDTs-Method--SQLServerDatabaseMetaData-.md)|Retrieves a description of the user\-defined types that are defined in a particular schema.|  
|[getURL](../content/getURL-Method--SQLServerDatabaseMetaData-.md)|Retrieves the URL for this database.|  
|[getUserName](../content/getUserName-Method--SQLServerDatabaseMetaData-.md)|Retrieves the user name as known to this database.|  
|[getVersionColumns](../content/getVersionColumns-Method--SQLServerDatabaseMetaData-.md)|Retrieves a description of the columns of a table that is automatically updated when any value in a row is updated.|  
|[insertsAreDetected](../content/insertsAreDetected-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether or not a visible row insert can be detected by calling the method [rowInserted](../content/rowInserted-Method--SQLServerResultSet-.md) method of the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) class.|  
|[isCatalogAtStart](../content/isCatalogAtStart-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether a catalog appears at the start of a fully qualified table name.|  
|[isReadOnly](../content/isReadOnly-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database is in read\-only mode.|  
|[locatorsUpdateCopy](../content/locatorsUpdateCopy-Method--SQLServerDatabaseMetaData-.md)|Indicates whether updates made to a LOB are made on a copy or directly to the LOB.|  
|[nullPlusNonNullIsNull](../content/nullPlusNonNullIsNull-Method--SQLServerDatabaseMetaData-.md)|Indicates whether this database supports concatenations between NULL and non\-NULL values being NULL.|  
|[nullsAreSortedAtEnd](../content/nullsAreSortedAtEnd-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether NULL values are sorted at the end regardless of sort order.|  
|[nullsAreSortedAtStart](../content/nullsAreSortedAtStart-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether NULL values are sorted at the start regardless of sort order.|  
|[nullsAreSortedHigh](../content/nullsAreSortedHigh-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether NULL values are sorted high.|  
|[nullsAreSortedLow](../content/nullsAreSortedLow-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether NULL values are sorted low.|  
|[othersDeletesAreVisible](../content/othersDeletesAreVisible-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether deletes that are made by others are visible.|  
|[othersInsertsAreVisible](../content/othersInsertsAreVisible-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether inserts that are made by others are visible.|  
|[othersUpdatesAreVisible](../content/othersUpdatesAreVisible-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether updates that are made by others are visible.|  
|[ownDeletesAreVisible](../content/ownDeletesAreVisible-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether a result set's own deletes are visible.|  
|[ownInsertsAreVisible](../content/ownInsertsAreVisible-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether a result set's own inserts are visible.|  
|[ownUpdatesAreVisible](../content/ownUpdatesAreVisible-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether the result set's own updates are visible.|  
|[storesLowerCaseIdentifiers](../content/storesLowerCaseIdentifiers-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database treats mixed\-case SQL identifiers that are not enclosed in quotation marks as case\-insensitive and stores them in lowercase.|  
|[storesLowerCaseQuotedIdentifiers](../content/storesLowerCaseQuotedIdentifiers-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database treats mixed\-case SQL identifiers that are enclosed in quotation marks as case\-insensitive and stores them in lowercase.|  
|[storesMixedCaseIdentifiers](../content/storesMixedCaseIdentifiers-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database treats mixed\-case SQL identifiers that are not enclosed in quotation marks as case\-insensitive and stores them in mixed case.|  
|[storesMixedCaseQuotedIdentifiers](../content/storesMixedCaseQuotedIdentifiers-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database treats mixed\-case SQL identifiers that are enclosed in quotation marks as case\-insensitive and stores them in mixed case.|  
|[storesUpperCaseIdentifiers](../content/storesUpperCaseIdentifiers-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database treats mixed\-case SQL identifiers that are not enclosed in quotation marks as case\-insensitive and stores them in uppercase.|  
|[storesUpperCaseQuotedIdentifiers](../content/storesUpperCaseQuotedIdentifiers-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database treats mixed\-case SQL identifiers that are enclosed in quotation marks as case\-insensitive and stores them in uppercase.|  
|[supportsAlterTableWithAddColumn](../content/supportsAlterTableWithAddColumn-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports ALTER TABLE with add column.|  
|[supportsAlterTableWithDropColumn](../content/supportsAlterTableWithDropColumn-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports ALTER TABLE with drop column.|  
|[supportsANSI92EntryLevelSQL](../content/supportsANSI92EntryLevelSQL-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports the ANSI92 entry level SQL grammar.|  
|[supportsANSI92FullSQL](../content/supportsANSI92FullSQL-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports the ANSI92 full SQL grammar.|  
|[supportsANSI92IntermediateSQL](../content/supportsANSI92IntermediateSQL-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports the ANSI92 intermediate SQL grammar.|  
|[supportsBatchUpdates](../content/supportsBatchUpdates-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports batch updates.|  
|[supportsCatalogsInDataManipulation](../content/supportsCatalogsInDataManipulation-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether a catalog name can be used in a data manipulation statement.|  
|[supportsCatalogsInIndexDefinitions](../content/supportsCatalogsInIndexDefinitions-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether a catalog name can be used in an index definition statement.|  
|[supportsCatalogsInPrivilegeDefinitions](../content/supportsCatalogsInPrivilegeDefinitions-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether a catalog name can be used in a privilege definition statement.|  
|[supportsCatalogsInProcedureCalls](../content/supportsCatalogsInProcedureCalls-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether a catalog name can be used in a procedure call statement.|  
|[supportsCatalogsInTableDefinitions](../content/supportsCatalogsInTableDefinitions-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether a catalog name can be used in a table definition statement.|  
|[supportsColumnAliasing](../content/supportsColumnAliasing-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports column aliasing.|  
|[supportsConvert](../content/supportsConvert-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports the CONVERT function between SQL types.|  
|[supportsCoreSQLGrammar](../content/supportsCoreSQLGrammar-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports the ODBC Core SQL grammar.|  
|[supportsCorrelatedSubqueries](../content/supportsCorrelatedSubqueries-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports correlated subqueries.|  
|[supportsDataDefinitionAndDataManipulationTransactions](../content/supportsDataDefinitionAndDataManipulationTransactions-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports both data definition and data manipulation statements within a transaction.|  
|[supportsDataManipulationTransactionsOnly](../content/supportsDataManipulationTransactionsOnly-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports only data manipulation statements within a transaction.|  
|[supportsDifferentTableCorrelationNames](../content/supportsDifferentTableCorrelationNames-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether, when table correlation names are supported, they are restricted to being different from the names of the tables.|  
|[supportsExpressionsInOrderBy](../content/supportsExpressionsInOrderBy-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports expressions in ORDER BY lists.|  
|[supportsExtendedSQLGrammar](../content/supportsExtendedSQLGrammar-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports the ODBC Extended SQL grammar.|  
|[supportsFullOuterJoins](../content/supportsFullOuterJoins-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports full nested outer joins.|  
|[supportsGetGeneratedKeys](../content/supportsGetGeneratedKeys-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether auto\-generated keys can be retrieved after a statement has been executed.|  
|[supportsGroupBy](../content/supportsGroupBy-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports some form of the GROUP BY clause.|  
|[supportsGroupByBeyondSelect](../content/supportsGroupByBeyondSelect-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports using columns not included in the SELECT statement in a GROUP BY clause provided that all of the columns in the SELECT statement are included in the GROUP BY clause.|  
|[supportsGroupByUnrelated](../content/supportsGroupByUnrelated-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports using a column that is not in the SELECT statement in a GROUP BY clause.|  
|[supportsIntegrityEnhancementFacility](../content/supportsIntegrityEnhancementFacility-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports the SQL Integrity Enhancement Facility.|  
|[supportsLikeEscapeClause](../content/supportsLikeEscapeClause-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports specifying a LIKE escape clause.|  
|[supportsLimitedOuterJoins](../content/supportsLimitedOuterJoins-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database provides limited support for outer joins.|  
|[supportsMinimumSQLGrammar](../content/supportsMinimumSQLGrammar-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports the ODBC Minimum SQL grammar.|  
|[supportsMixedCaseIdentifiers](../content/supportsMixedCaseIdentifiers-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database treats mixed\-case SQL identifiers that are not enclosed in quotation marks as case\-insensitive and stores them in mixed case.|  
|[supportsMixedCaseQuotedIdentifiers](../content/supportsMixedCaseQuotedIdentifiers-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database treats mixed\-case SQL identifiers that are enclosed in quotation marks as case\-insensitive and stores them in mixed case.|  
|[supportsMultipleOpenResults](../content/supportsMultipleOpenResults-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether it is possible to have multiple [SQLServerResultSet](../content/SQLServerResultSet-Class.md) objects returned from a [SQLServerCallableStatement](../content/SQLServerCallableStatement-Class.md) object simultaneously.|  
|[supportsMultipleResultSets](../content/supportsMultipleResultSets-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports getting multiple [SQLServerResultSet](../content/SQLServerResultSet-Class.md) objects from a single call to the [execute](../content/execute-Method---.md) method of the [SQLServerCallableStatement](../content/SQLServerCallableStatement-Class.md) class.|  
|[supportsMultipleTransactions](../content/supportsMultipleTransactions-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database allows having multiple transactions open at once on different connections.|  
|[supportsNamedParameters](../content/supportsNamedParameters-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports named parameters in callable statements.|  
|[supportsNonNullableColumns](../content/supportsNonNullableColumns-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether columns in this database can be defined as non\-nullable.|  
|[supportsOpenCursorsAcrossCommit](../content/supportsOpenCursorsAcrossCommit-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports keeping cursors open across commits.|  
|[supportsOpenCursorsAcrossRollback](../content/supportsOpenCursorsAcrossRollback-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports keeping cursors open across rollbacks.|  
|[supportsOpenStatementsAcrossCommit](../content/supportsOpenStatementsAcrossCommit-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports keeping statements open across commits.|  
|[supportsOpenStatementsAcrossRollback](../content/supportsOpenStatementsAcrossRollback-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports keeping statements open across rollbacks.|  
|[supportsOrderByUnrelated](../content/supportsOrderByUnrelated-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports using a column that is not in the SELECT statement in an ORDER BY clause.|  
|[supportsOuterJoins](../content/supportsOuterJoins-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports some form of outer join.|  
|[supportsPositionedDelete](../content/supportsPositionedDelete-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports positioned DELETE statements.|  
|[supportsPositionedUpdate](../content/supportsPositionedUpdate-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports positioned UPDATE statements.|  
|[supportsResultSetConcurrency](../content/supportsResultSetConcurrency-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports the given concurrency type in combination with the given result set type.|  
|[supportsResultSetHoldability](../content/supportsResultSetHoldability-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports the given result set holdability.|  
|[supportsResultSetType](../content/supportsResultSetType-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports the given result set type.|  
|[supportsSavepoints](../content/supportsSavepoints-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports savepoints.|  
|[supportsSchemasInDataManipulation](../content/supportsSchemasInDataManipulation-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether a schema name can be used in a data manipulation statement.|  
|[supportsSchemasInIndexDefinitions](../content/supportsSchemasInIndexDefinitions-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether a schema name can be used in an index definition statement.|  
|[supportsSchemasInPrivilegeDefinitions](../content/supportsSchemasInPrivilegeDefinitions-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether a schema name can be used in a privilege definition statement.|  
|[supportsSchemasInProcedureCalls](../content/supportsSchemasInProcedureCalls-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether a schema name can be used in a procedure call statement.|  
|[supportsSchemasInTableDefinitions](../content/supportsSchemasInTableDefinitions-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether a schema name can be used in a table definition statement.|  
|[supportsSelectForUpdate](../content/supportsSelectForUpdate-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports SELECT FOR UPDATE statements.|  
|[supportsStatementPooling](../content/supportsStatementPooling-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports statement pooling.|  
|[supportsStoredFunctionsUsingCallSyntax](../content/supportsStoredFunctionsUsingCallSyntax-Method--SQLServerDatabaseMetaData-.md)|Indicates whether the current database supports invoking user\- or vendor\-defined functions by using the stored procedure escape syntax.|  
|[supportsStoredProcedures](../content/supportsStoredProcedures-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports stored procedure calls that use the stored procedure escape syntax.|  
|[supportsSubqueriesInComparisons](../content/supportsSubqueriesInComparisons-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports subqueries in comparison expressions.|  
|[supportsSubqueriesInExists](../content/supportsSubqueriesInExists-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports subqueries in EXISTS expressions.|  
|[supportsSubqueriesInIns](../content/supportsSubqueriesInIns-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports subqueries in IN statements.|  
|[supportsSubqueriesInQuantifieds](../content/supportsSubqueriesInQuantifieds-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports subqueries in quantified expressions.|  
|[supportsTableCorrelationNames](../content/supportsTableCorrelationNames-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports table correlation names.|  
|[supportsTransactionIsolationLevel](../content/supportsTransactionIsolationLevel-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports the given transaction isolation level.|  
|[supportsTransactions](../content/supportsTransactions-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports transactions.|  
|[supportsUnion](../content/supportsUnion-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports SQL UNION.|  
|[supportsUnionAll](../content/supportsUnionAll-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database supports SQL UNION ALL.|  
|[updatesAreDetected](../content/updatesAreDetected-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether or not a visible row update can be detected by calling the [rowUpdated](../content/rowUpdated-Method--SQLServerResultSet-.md) method of the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) class.|  
|[usesLocalFilePerTable](../content/usesLocalFilePerTable-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database uses a file for each table.|  
|[usesLocalFiles](../content/usesLocalFiles-Method--SQLServerDatabaseMetaData-.md)|Retrieves whether this database stores tables in a local file.|  
  
## Inherited Methods  
  
|Class inherited from:|Methods|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## See Also  
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  