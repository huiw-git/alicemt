---
title: SQLServerResultSet Members
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a438d5d-2d6a-46a0-a2ae-f35fbae4a472
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
# SQLServerResultSet Members
  The following tables list the members that are exposed by the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) class.  
  
## Constructors  
 None.  
  
## Fields  
  
|Name|Description|  
|----------|-----------------|  
|[CONCUR\_SS\_OPTIMISTIC\_CC](../content/CONCUR_SS_OPTIMISTIC_CC-Field--SQLServerResultSet-.md)|Used to specify a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] read\/write optimistic concurrency type with no row locks.|  
|[CONCUR\_SS\_OPTIMISTIC\_CCVAL](../content/CONCUR_SS_OPTIMISTIC_CCVAL-Field--SQLServerResultSet-.md)|Used to specify a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] read\/write optimistic concurrency type with no row locks.|  
|[CONCUR\_SS\_SCROLL\_LOCKS](../content/CONCUR_SS_SCROLL_LOCKS-Field--SQLServerResultSet-.md)|Used to specify a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] read\/write optimistic concurrency type with row locks.|  
|[TYPE\_SS\_DIRECT\_FORWARD\_ONLY](../content/TYPE_SS_DIRECT_FORWARD_ONLY-Field--SQLServerResultSet-.md)|Used to specify a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] fast forward\-only, read\-only cursor type.|  
|[TYPE\_SS\_SCROLL\_DYNAMIC](../content/TYPE_SS_SCROLL_DYNAMIC-Field--SQLServerResultSet-.md)|Used to specify a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] dynamic cursor type.|  
|[TYPE\_SS\_SCROLL\_KEYSET](../content/TYPE_SS_SCROLL_KEYSET-Field--SQLServerResultSet-.md)|Used to specify a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] keyset cursor type.|  
|[TYPE\_SS\_SCROLL\_STATIC](../content/TYPE_SS_SCROLL_STATIC-Field--SQLServerResultSet-.md)|Used to specify a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] static cursor type.|  
|[TYPE\_SS\_SERVER\_CURSOR\_FORWARD\_ONLY](../content/TYPE_SS_SERVER_CURSOR_FORWARD_ONLY-Field--SQLServerResultSet-.md)|Used to specify a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] fast forward\-only, read\-only cursor type.|  
  
## Inherited Fields  
  
|Class inherited from:|Description|  
|---------------------------|-----------------|  
|java.sql.ResultSet|CLOSE\_CURSORS\_AT\_COMMIT, CONCUR\_READ\_ONLY, CONCUR\_UPDATABLE, FETCH\_FORWARD, FETCH\_REVERSE, FETCH\_UNKNOWN, HOLD\_CURSORS\_OVER\_COMMIT, TYPE\_FORWARD\_ONLY, TYPE\_SCROLL\_INSENSITIVE, TYPE\_SCROLL\_SENSITIVE|  
  
## Methods  
  
|Name|Description|  
|----------|-----------------|  
|[absolute](../content/absolute-Method--SQLServerResultSet-.md)|Moves the cursor to the specified row in this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[afterLast](../content/afterLast-Method--SQLServerResultSet-.md)|Moves the cursor to after the last row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[beforeFirst](../content/beforeFirst-Method--SQLServerResultSet-.md)|Moves the cursor to before the first row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[cancelRowUpdates](../content/cancelRowUpdates-Method--SQLServerResultSet-.md)|Cancels the updates made to the current row in this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[clearWarnings](../content/clearWarnings-Method--SQLServerResultSet-.md)|Clears all warnings reported on this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[close](../content/close-Method--SQLServerResultSet-.md)|Releases this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object's database and JDBC resources immediately instead of waiting for this to happen when it is automatically closed.|  
|[deleteRow](../content/deleteRow-Method--SQLServerResultSet-.md)|Deletes the current row from this[SQLServerResultSet](../content/SQLServerResultSet-Class.md) object and from the underlying database.|  
|[finalize](../content/finalize-Method--SQLServerResultSet-.md)|Explicitly closes this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[findColumn](../content/findColumn-Method--SQLServerResultSet-.md)|Retrieves the index of the first matching column for the specified column name in this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[first](../content/first-Method--SQLServerResultSet-.md)|Moves the cursor to the first row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[getArray](../content/getArray-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as an Array object.|  
|[getAsciiStream](../content/getAsciiStream-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a stream of ASCII characters.|  
|[getBigDecimal](../content/getBigDecimal-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column index in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a java.math.BigDecimal.|  
|[getBinaryStream](../content/getBinaryStream-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a binary stream of uninterpreted bytes.|  
|[getBlob](../content/getBlob-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a Blob object in the Java programming language.|  
|[getBoolean](../content/getBoolean-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a **boolean** in the Java programming language.|  
|[getByte](../content/getByte-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a **byte** in the Java programming language.|  
|[getBytes](../content/getBytes-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a **byte** array in the Java programming language.|  
|[getCharacterStream](../content/getCharacterStream-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a java.io.Reader object.|  
|[getClob](../content/getClob-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a Clob object in the Java programming language.|  
|[getConcurrency](../content/getConcurrency-Method--SQLServerResultSet-.md)|Retrieves the concurrency mode of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[getCursorName](../content/getCursorName-Method--SQLServerResultSet-.md)|Retrieves the name of the SQL cursor used by this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[getDate](../content/getDate-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a java.sql.Date object in the Java programming language.|  
|[getDateTimeOffset](../content/getDateTimeOffset--SQLServerResultSet-.md)|Retrieves the value of the specified column as a[DateTimeOffset Class](../content/DateTimeOffset-Class.md) object.|  
|[getDouble](../content/getDouble-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a **double** in the Java programming language.|  
|[getFetchDirection](../content/getFetchDirection-Method--SQLServerResultSet-.md)|Retrieves the fetch direction for this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[getFetchSize](../content/getFetchSize-Method--SQLServerResultSet-.md)|Retrieves the fetch size for this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[getFloat](../content/getFloat-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a **float** in the Java programming language.|  
|[getHoldability](../content/getHoldability-Method--SQLServerResultSet-.md)|Retrieves the holdability of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[getInt](../content/getInt-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as an **int** in the Java programming language.|  
|[getLong](../content/getLong-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a **long** in the Java programming language.|  
|[getMetaData](../content/getMetaData-Method--SQLServerResultSet-.md)|Retrieves the number, types, and properties of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object's columns.|  
|[getNCharacterStream](../content/getNCharacterStream-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a Reader object.|  
|[getNClob](../content/getNClob-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of the  [SQLServerResultSet](../content/SQLServerResultSet-Class.md)object as an **NClob** object in the Java programming language.|  
|[getNString](../content/getNString-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a String in the Java programming language.|  
|[getObject](../content/getObject-Method--SQLServerResultSet-.md)|Gets the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as an object in the Java programming language.|  
|[getRef](../content/getRef-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a Ref object in the Java programming language.|  
|[getRow](../content/getRow-Method--SQLServerResultSet-.md)|Retrieves the current row number.|  
|[getShort](../content/getShort-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a **short** in the Java programming language.|  
|[getStatement](../content/getStatement-Method--SQLServerResultSet-.md)|Retrieves the [SQLServerStatement](../content/SQLServerStatement-Class.md) object that produced this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[getString](../content/getString-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a **String** in the Java programming language.|  
|[getSQLXML](../content/getSQLXML-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a **SQLXML** object.|  
|[getTime](../content/getTime-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a java.sql.Time object in the Java programming language.|  
|[getTimestamp](../content/getTimestamp-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a java.sql.Timestamp object in the Java programming language.|  
|[getType](../content/getType-Method--SQLServerResultSet-.md)|Retrieves the cursor type of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[getUnicodeStream](../content/getUnicodeStream-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a stream of Unicode characters.|  
|[getURL](../content/getURL-Method--SQLServerResultSet-.md)|Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a URL object.|  
|[getWarnings](../content/getWarnings-Method--SQLServerResultSet-.md)|Retrieves the first warning reported by calls on this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[insertRow](../content/insertRow-Method--SQLServerResultSet-.md)|Inserts the contents of the insert row into this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object and into the database.|  
|[isAfterLast](../content/isAfterLast-Method--SQLServerResultSet-.md)|Retrieves whether the cursor is after the last row in this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[isBeforeFirst](../content/isBeforeFirst-Method--SQLServerResultSet-.md)|Retrieves whether the cursor is before the first row in this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[isClosed](../content/isClosed-Method--SQLServerResultSet-.md)|Indicates whether this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object has been closed.|  
|[isFirst](../content/isFirst-Method--SQLServerResultSet-.md)|Retrieves whether the cursor is on the first row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[isLast](../content/isLast-Method--SQLServerResultSet-.md)|Retrieves whether the cursor is on the last row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[last](../content/last-Method--SQLServerResultSet-.md)|Moves the cursor to the last row in this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[moveToCurrentRow](../content/moveToCurrentRow-Method--SQLServerResultSet-.md)|Moves the cursor to the remembered cursor position, usually the current row.|  
|[moveToInsertRow](../content/moveToInsertRow-Method--SQLServerResultSet-.md)|Moves the cursor to the insert row.|  
|[next](../content/next-Method--SQLServerResultSet-.md)|Moves the cursor down one row from its current position.|  
|[previous](../content/previous-Method--SQLServerResultSet-.md)|Moves the cursor to the previous row in this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[refreshRow](../content/refreshRow-Method--SQLServerResultSet-.md)|Refreshes the current row with its most recent value in the database.|  
|[relative](../content/relative-Method--SQLServerResultSet-.md)|Moves the cursor the given amount of rows, relative to the current row, in either a positive or a negative direction.|  
|[rowDeleted](../content/rowDeleted-Method--SQLServerResultSet-.md)|Retrieves whether a row has been deleted.|  
|[rowInserted](../content/rowInserted-Method--SQLServerResultSet-.md)|Retrieves whether the current row has had an insertion.|  
|[rowUpdated](../content/rowUpdated-Method--SQLServerResultSet-.md)|Retrieves whether the current row has been updated.|  
|[setFetchDirection](../content/setFetchDirection-Method--SQLServerResultSet-.md)|Gives a hint as to the direction in which the rows in this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object will be processed.|  
|[setFetchSize](../content/setFetchSize-Method--SQLServerResultSet-.md)|Gives the JDBC driver a hint as to the number of rows that should be fetched from the database when more rows are needed for this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[updateArray](../content/updateArray-Method--SQLServerResultSet-.md)|Updates the designated column with an Array object.|  
|[updateAsciiStream](../content/updateAsciiStream-Method--SQLServerResultSet-.md)|Updates the designated column with an ASCII stream value.|  
|[updateBigDecimal](../content/updateBigDecimal-Method--SQLServerResultSet-.md)|Updates the designated column with a BigDecimal object.|  
|[updateBinaryStream](../content/updateBinaryStream-Method--SQLServerResultSet-.md)|Updates the designated column with a binary stream value.|  
|[updateBlob](../content/updateBlob-Method--SQLServerResultSet-.md)|Updates the designated column with a java.sql.Blob value.|  
|[updateBoolean](../content/updateBoolean-Method--SQLServerResultSet-.md)|Updates the designated column with a **boolean** value.|  
|[updateByte](../content/updateByte-Method--SQLServerResultSet-.md)|Updates the designated column with a **byte** value.|  
|[updateBytes](../content/updateBytes-Method--SQLServerResultSet-.md)|Updates the designated column with an array of **byte** values.|  
|[updateCharacterStream](../content/updateCharacterStream-Method--SQLServerResultSet-.md)|Updates the designated column with a character stream value.|  
|[updateClob](../content/updateClob-Method--SQLServerResultSet-.md)|Updates the designated column with a java.sql.Clob value.|  
|[updateDate](../content/updateDate-Method--SQLServerResultSet-.md)|Updates the designated column with a date value.|  
|[updateDateTimeOffset](../content/updateDateTimeOffset--SQLServerResultSet-.md)|Updates a [DateTimeOffset Class](../content/DateTimeOffset-Class.md) column.|  
|[updateDouble](../content/updateDouble-Method--SQLServerResultSet-.md)|Updates the designated column with a **double** value.|  
|[updateFloat](../content/updateFloat-Method--SQLServerResultSet-.md)|Updates the designated column with a **float** value.|  
|[updateInt](../content/updateInt-Method--SQLServerResultSet-.md)|Updates the designated column with an **int** value.|  
|[updateLong](../content/updateLong-Method--SQLServerResultSet-.md)|Updates the designated column with a **long** value.|  
|[updateNCharacterStream](../content/updateNCharacterStream-Method--SQLServerResultSet-.md)|Updates the designated column with a character stream value.|  
|[updateNClob](../content/updateNClob-Method--SQLServerResultSet-.md)|Updates the designated column with the specified object value.|  
|[updateNString](../content/updateNString-Method--SQLServerResultSet-.md)|Updates the designated column with a **String** value.|  
|[updateNull](../content/updateNull-Method--SQLServerResultSet-.md)|Updates the designated column with a null value.|  
|[updateObject](../content/updateObject-Method--SQLServerResultSet-.md)|Updates the designated column with an **Object** value.|  
|[updateRef](../content/updateRef-Method--SQLServerResultSet-.md)|Updates the designated column with a java.sql.Ref value.|  
|[updateRow](../content/updateRow-Method--SQLServerResultSet-.md)|Updates the underlying database with the new contents of the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[updateShort](../content/updateShort-Method--SQLServerResultSet-.md)|Updates the designated column with a **short** value.|  
|[updateString](../content/updateString-Method--SQLServerResultSet-.md)|Updates the designated column with a **String** value.|  
|[updateSQLXML](../content/updateSQLXML-Method--SQLServerResultSet-.md)|Updates the designated column with a **SQLXML** value.|  
|[updateTime](../content/updateTime-Method--SQLServerResultSet-.md)|Updates the designated column with a time value.|  
|[updateTimestamp](../content/updateTimestamp-Method--SQLServerResultSet-.md)|Updates the designated column with a timestamp value.|  
|[wasNull](../content/wasNull-Method--SQLServerResultSet-.md)|Verifies whether the last value read was a null value.|  
  
## Inherited Methods  
  
|Class inherited from:|Methods|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## See Also  
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  