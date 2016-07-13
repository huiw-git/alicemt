---
title: ISQLServerResultSet Interface
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 002496f7-8ec0-4267-b4e6-ba095e2ef306
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
# ISQLServerResultSet Interface
  Represents a JDBC result set. This interface was added in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0.  
  
 **Package:** com.microsoft.sqlserver.jdbc  
  
 **Extends:** java.sql.ResultSet  
  
## Syntax  
  
```  
  
public interface ISQLServerResultSet  
```  
  
## Remarks  
 This interface is implemented by [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md).  
  
 This interface exposes the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]\-specific methods:  
  
|Method|For more information, see|  
|------------|-------------------------------|  
|public microsoft.sql.DateTimeOffset getDateTimeOffset\(int\)|[getDateTimeOffset](../content/getDateTimeOffset-int---SQLServerResultSet-.md)|  
|public microsoft.sql.DateTimeOffset getDateTimeOffset\(String\)|[getDateTimeOffset](../content/getDateTimeOffset-java.lang.string---SQLServerResultSet-.md)|  
|public void updateDateTimeOffset\(int, microsoft.sql.DateTimeOffset\)|[updateDateTimeOffset](../content/updateDateTimeOffset-int--microsoft.sql.DateTimeOffset---SQLServerResultSet-.md)|  
|public void updateDateTimeOffset\(String, microsoft.sql.DateTimeOffset\)|[updateDateTimeOffset](../content/updateDateTimeOffset-string--microsoft.sql.DateTimeOffset---SQLServerResultSet-.md)|  
  
 This interface exposes the following [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]\-specific fields:  
  
|Field|For more information, see|  
|-----------|-------------------------------|  
|public static final int CONCUR\_SS\_OPTIMISTIC\_CC|[CONCUR\_SS\_OPTIMISTIC\_CC](../content/CONCUR_SS_OPTIMISTIC_CC-Field--SQLServerResultSet-.md)|  
|public static final int CONCUR\_SS\_OPTIMISTIC\_CCVAL|[CONCUR\_SS\_OPTIMISTIC\_CCVAL](../content/CONCUR_SS_OPTIMISTIC_CCVAL-Field--SQLServerResultSet-.md)|  
|public static final int CONCUR\_SS\_SCROLL\_LOCKS|[CONCUR\_SS\_SCROLL\_LOCKS](../content/CONCUR_SS_SCROLL_LOCKS-Field--SQLServerResultSet-.md)|  
|public static final int TYPE\_SS\_DIRECT\_FORWARD\_ONLY|[TYPE\_SS\_DIRECT\_FORWARD\_ONLY](../content/TYPE_SS_DIRECT_FORWARD_ONLY-Field--SQLServerResultSet-.md)|  
|public static final int TYPE\_SS\_SCROLL\_DYNAMIC|[TYPE\_SS\_SCROLL\_DYNAMIC](../content/TYPE_SS_SCROLL_DYNAMIC-Field--SQLServerResultSet-.md)|  
|public static final int TYPE\_SS\_SCROLL\_KEYSET|[TYPE\_SS\_SCROLL\_KEYSET](../content/TYPE_SS_SCROLL_KEYSET-Field--SQLServerResultSet-.md)|  
|public static final int TYPE\_SS\_SCROLL\_STATIC|[TYPE\_SS\_SCROLL\_STATIC](../content/TYPE_SS_SCROLL_STATIC-Field--SQLServerResultSet-.md)|  
|public static final int TYPE\_SS\_SERVER\_CURSOR\_FORWARD\_ONLY|[TYPE\_SS\_SERVER\_CURSOR\_FORWARD\_ONLY](../content/TYPE_SS_SERVER_CURSOR_FORWARD_ONLY-Field--SQLServerResultSet-.md)|  
  
## See Also  
 [JDBC Driver API Reference](../content/JDBC-Driver-API-Reference.md)  
  
  