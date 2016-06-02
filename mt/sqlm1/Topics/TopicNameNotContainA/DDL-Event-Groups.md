---
title: DDL Event Groups
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-ddl
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 12b45cc3-2f91-4609-bb8a-3e82e28bf642
---
# DDL Event Groups
  The following tables list the DDL event groups that can be used to run a DDL trigger or an event notification, and also the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements they cover. Note the inclusive nature of the event groups. For example, a DDL trigger or event notification that specifies FOR DDL\_TABLE\_EVENTS \(10018\) covers the CREATE TABLE, ALTER TABLE and DROP TABLE [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements. A DDL trigger or event notification that specifies FOR DDL\_TABLE\_VIEW\_EVENTS \(10017\) covers all [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements under the types DDL\_TABLE\_EVENTS, DDL\_VIEW\_EVENTS, DDL\_INDEX\_EVENTS, and DDL\_STATISTICS\_EVENTS.  
  
> [!NOTE]  
>  Certain system stored procedures that perform DDL\-like operations can also fire DDL triggers or event notifications. Test your DDL triggers and event notifications to determine their responses to system stored procedures that are run. For example, the CREATE TYPE statement and **sp\_addtype** stored procedure will both fire a DDL trigger or event notification that is created on a CREATE\_TYPE event.  
  
## Events  
 The events listed under DDL\_DATABASE\_LEVEL\_EVENTS execute at the server \(instance\) or database level. Events listed under DDL\_SERVER\_LEVEL\_EVENTS execute only at the server level.  
  
||||  
|-|-|-|  
|parent\_type|type|name|  
|NULL|296|ALTER\_SERVER\_CONFIGURATION|  
|NULL|10001|DDL\_EVENTS|  
|10001|10016|&#124;    DDL\_DATABASE\_LEVEL\_EVENTS|  
|10016|10027|&#124;    &#124;    DDL\_ASSEMBLY\_EVENTS|  
|10027|102|&#124;    &#124;    &#124;    ALTER\_ASSEMBLY|  
|10027|101|&#124;    &#124;    &#124;    CREATE\_ASSEMBLY|  
|10027|103|&#124;    &#124;    &#124;    DROP\_ASSEMBLY|  
|10016|10029|&#124;    &#124;    DDL\_DATABASE\_SECURITY\_EVENTS|  
|10029|10033|&#124;    &#124;    &#124;    DDL\_APPLICATION\_ROLE\_EVENTS|  
|10033|138|&#124;    &#124;    &#124;    &#124;    ALTER\_APPLICATION\_ROLE|  
|10033|137|&#124;    &#124;    &#124;    &#124;    CREATE\_APPLICATION\_ROLE|  
|10033|139|&#124;    &#124;    &#124;    &#124;    DROP\_APPLICATION\_ROLE|  
|10029|10038|&#124;    &#124;    &#124;    DDL\_ASYMMETRIC\_KEY\_EVENTS|  
|10038|248|&#124;    &#124;    &#124;    &#124;    ALTER\_ASYMMETRIC\_KEY|  
|10038|247|&#124;    &#124;    &#124;    &#124;    CREATE\_ASYMMETRIC\_KEY|  
|10038|249|&#124;    &#124;    &#124;    &#124;    DROP\_ASYMMETRIC\_KEY|  
|10029|10036|&#124;    &#124;    &#124;    DDL\_AUTHORIZATION\_DATABASE\_EVENTS|  
|10036|205|&#124;    &#124;    &#124;    &#124;    ALTER\_AUTHORIZATION\_DATABASE|  
|10029|10030|&#124;    &#124;    &#124;    DDL\_CERTIFICATE\_EVENTS|  
|10030|198|&#124;    &#124;    &#124;    &#124;    ALTER\_CERTIFICATE|  
|10030|197|&#124;    &#124;    &#124;    &#124;    CREATE\_CERTIFICATE|  
|10030|199|&#124;    &#124;    &#124;    &#124;    DROP\_CERTIFICATE|  
|10029|10039|&#124;    &#124;    &#124;    DDL\_CRYPTO\_SIGNATURE\_EVENTS|  
|10039|257|&#124;    &#124;    &#124;    &#124;    ADD\_SIGNATURE|  
|10039|255|&#124;    &#124;    &#124;    &#124;    ADD\_SIGNATURE\_SCHEMA\_OBJECT|  
|10039|258|&#124;    &#124;    &#124;    &#124;    DROP\_SIGNATURE|  
|10039|256|&#124;    &#124;    &#124;    &#124;    DROP\_SIGNATURE\_SCHEMA\_OBJECT|  
|10029|10066|&#124;    &#124;    &#124;    DDL\_DATABASE\_AUDIT\_SPECIFICATION\_EVENTS|  
|10066|291|&#124;    &#124;    &#124;    &#124;    ALTER\_DATABASE\_AUDIT\_SPECIFICATION|  
|10066|290|&#124;    &#124;    &#124;    &#124;    CREATE\_DATABASE\_AUDIT\_SPECIFICATION|  
|10066|292|&#124;    &#124;    &#124;    &#124;    DROP\_DATABASE\_AUDIT\_SPECIFICATION|  
|10029|10062|&#124;    &#124;    &#124;    DDL\_DATABASE\_ENCRYPTION\_KEY\_EVENTS|  
|10062|279|&#124;    &#124;    &#124;    &#124;    ALTER\_DATABASE\_ENCRYPTION\_KEY|  
|10062|278|&#124;    &#124;    &#124;    &#124;    CREATE\_DATABASE\_ENCRYPTION\_KEY|  
|10062|280|&#124;    &#124;    &#124;    &#124;    DROP\_DATABASE\_ENCRYPTION\_KEY|  
|10029|10035|&#124;    &#124;    &#124;    DDL\_GDR\_DATABASE\_EVENTS|  
|10035|171|&#124;    &#124;    &#124;    &#124;    DENY\_DATABASE|  
|10035|170|&#124;    &#124;    &#124;    &#124;    GRANT\_DATABASE|  
|10035|172|&#124;    &#124;    &#124;    &#124;    REVOKE\_DATABASE|  
|10029|10040|&#124;    &#124;    &#124;    DDL\_MASTER\_KEY\_EVENTS|  
|10040|253|&#124;    &#124;    &#124;    &#124;    ALTER\_MASTER\_KEY|  
|10040|252|&#124;    &#124;    &#124;    &#124;    CREATE\_MASTER\_KEY|  
|10040|254|&#124;    &#124;    &#124;    &#124;    DROP\_MASTER\_KEY|  
|10029|10032|&#124;    &#124;    &#124;    DDL\_ROLE\_EVENTS|  
|10032|207|&#124;    &#124;    &#124;    &#124;    ADD\_ROLE\_MEMBER|  
|10032|135|&#124;    &#124;    &#124;    &#124;    ALTER\_ROLE|  
|10032|134|&#124;    &#124;    &#124;    &#124;    CREATE\_ROLE|  
|10032|136|&#124;    &#124;    &#124;    &#124;    DROP\_ROLE|  
|10032|208|&#124;    &#124;    &#124;    &#124;    DROP\_ROLE\_MEMBER|  
|10029|10034|&#124;    &#124;    &#124;    DDL\_SCHEMA\_EVENTS|  
|10034|142|&#124;    &#124;    &#124;    &#124;    ALTER\_SCHEMA|  
|10034|141|&#124;    &#124;    &#124;    &#124;    CREATE\_SCHEMA|  
|10034|143|&#124;    &#124;    &#124;    &#124;    DROP\_SCHEMA|  
|10029|10037|&#124;    &#124;    &#124;    DDL\_SYMMETRIC\_KEY\_EVENTS|  
|10037|245|&#124;    &#124;    &#124;    &#124;    ALTER\_SYMMETRIC\_KEY|  
|10037|244|&#124;    &#124;    &#124;    &#124;    CREATE\_SYMMETRIC\_KEY|  
|10037|246|&#124;    &#124;    &#124;    &#124;    DROP\_SYMMETRIC\_KEY|  
|10029|10031|&#124;    &#124;    &#124;    DDL\_USER\_EVENTS|  
|10031|132|&#124;    &#124;    &#124;    &#124;    ALTER\_USER|  
|10031|131|&#124;    &#124;    &#124;    &#124;    CREATE\_USER|  
|10031|133|&#124;    &#124;    &#124;    &#124;    DROP\_USER|  
|10016|10052|&#124;    &#124;    DDL\_DEFAULT\_EVENTS|  
|10052|218|&#124;    &#124;    &#124;    BIND\_DEFAULT|  
|10052|220|&#124;    &#124;    &#124;    CREATE\_DEFAULT|  
|10052|231|&#124;    &#124;    &#124;    DROP\_DEFAULT|  
|10052|242|&#124;    &#124;    &#124;    UNBIND\_DEFAULT|  
|10016|10026|&#124;    &#124;    DDL\_EVENT\_NOTIFICATION\_EVENTS|  
|10026|74|&#124;    &#124;    &#124;    CREATE\_EVENT\_NOTIFICATION|  
|10026|76|&#124;    &#124;    &#124;    DROP\_EVENT\_NOTIFICATION|  
|10016|10053|&#124;    &#124;    DDL\_EXTENDED\_PROPERTY\_EVENTS|  
|10053|211|&#124;    &#124;    &#124;    ALTER\_EXTENDED\_PROPERTY|  
|10053|222|&#124;    &#124;    &#124;    CREATE\_EXTENDED\_PROPERTY|  
|10053|233|&#124;    &#124;    &#124;    DROP\_EXTENDED\_PROPERTY|  
|10016|10054|&#124;    &#124;    DDL\_FULLTEXT\_CATALOG\_EVENTS|  
|10054|212|&#124;    &#124;    &#124;    ALTER\_FULLTEXT\_CATALOG|  
|10054|223|&#124;    &#124;    &#124;    CREATE\_FULLTEXT\_CATALOG|  
|10054|234|&#124;    &#124;    &#124;    DROP\_FULLTEXT\_CATALOG|  
|10016|10067|&#124;    &#124;    DDL\_FULLTEXT\_STOPLIST\_EVENTS|  
|10067|294|&#124;    &#124;    &#124;    ALTER\_FULLTEXT\_STOPLIST|  
|10067|293|&#124;    &#124;    &#124;    CREATE\_FULLTEXT\_STOPLIST|  
|10067|295|&#124;    &#124;    &#124;    DROP\_FULLTEXT\_STOPLIST|  
|10016|10023|&#124;    &#124;    DDL\_FUNCTION\_EVENTS|  
|10023|62|&#124;    &#124;    &#124;    ALTER\_FUNCTION|  
|10023|61|&#124;    &#124;    &#124;    CREATE\_FUNCTION|  
|10023|63|&#124;    &#124;    &#124;    DROP\_FUNCTION|  
|10016|10049|&#124;    &#124;    DDL\_PARTITION\_EVENTS|  
|10049|10050|&#124;    &#124;    &#124;    DDL\_PARTITION\_FUNCTION\_EVENTS|  
|10050|192|&#124;    &#124;    &#124;    &#124;    ALTER\_PARTITION\_FUNCTION|  
|10050|191|&#124;    &#124;    &#124;    &#124;    CREATE\_PARTITION\_FUNCTION|  
|10050|193|&#124;    &#124;    &#124;    &#124;    DROP\_PARTITION\_FUNCTION|  
|10049|10051|&#124;    &#124;    &#124;    DDL\_PARTITION\_SCHEME\_EVENTS|  
|10051|195|&#124;    &#124;    &#124;    &#124;    ALTER\_PARTITION\_SCHEME|  
|10051|194|&#124;    &#124;    &#124;    &#124;    CREATE\_PARTITION\_SCHEME|  
|10051|196|&#124;    &#124;    &#124;    &#124;    DROP\_PARTITION\_SCHEME|  
|10016|10055|&#124;    &#124;    DDL\_PLAN\_GUIDE\_EVENTS|  
|10055|216|&#124;    &#124;    &#124;    ALTER\_PLAN\_GUIDE|  
|10055|228|&#124;    &#124;    &#124;    CREATE\_PLAN\_GUIDE|  
|10055|238|&#124;    &#124;    &#124;    DROP\_PLAN\_GUIDE|  
|10016|10024|&#124;    &#124;    DDL\_PROCEDURE\_EVENTS|  
|10024|52|&#124;    &#124;    &#124;    ALTER\_PROCEDURE|  
|10024|51|&#124;    &#124;    &#124;    CREATE\_PROCEDURE|  
|10024|53|&#124;    &#124;    &#124;    DROP\_PROCEDURE|  
|10016|10056|&#124;    &#124;    DDL\_RULE\_EVENTS|  
|10056|219|&#124;    &#124;    &#124;    BIND\_RULE|  
|10056|229|&#124;    &#124;    &#124;    CREATE\_RULE|  
|10056|239|&#124;    &#124;    &#124;    DROP\_RULE|  
|10056|243|&#124;    &#124;    &#124;    UNBIND\_RULE|  
|10016|10069|&#124;    &#124;    DDL\_SEARCH\_PROPERTY\_LIST\_EVENTS|  
|10069|298|&#124;    &#124;    &#124;    ALTER\_SEARCH\_PROPERTY\_LIST|  
|10069|297|&#124;    &#124;    &#124;    CREATE\_SEARCH\_PROPERTY\_LIST|  
|10069|299|&#124;    &#124;    &#124;    DROP\_SEARCH\_PROPERTY\_LIST|  
|10016|10070|&#124;    &#124;    DDL\_SEQUENCE\_EVENTS|  
|10070|304|&#124;    &#124;    &#124;    ALTER\_SEQUENCE|  
|10070|303|&#124;    &#124;    &#124;    CREATE\_SEQUENCE|  
|10070|305|&#124;    &#124;    &#124;    DROP\_SEQUENCE|  
|10016|10041|&#124;    &#124;    DDL\_SSB\_EVENTS|  
|10041|10063|&#124;    &#124;    &#124;    DDL\_BROKER\_PRIORITY\_EVENTS|  
|10063|282|&#124;    &#124;    &#124;    &#124;    ALTER\_BROKER\_PRIORITY|  
|10063|281|&#124;    &#124;    &#124;    &#124;    CREATE\_BROKER\_PRIORITY|  
|10063|283|&#124;    &#124;    &#124;    &#124;    DROP\_BROKER\_PRIORITY|  
|10041|10043|&#124;    &#124;    &#124;    DDL\_CONTRACT\_EVENTS|  
|10043|154|&#124;    &#124;    &#124;    &#124;    CREATE\_CONTRACT|  
|10043|156|&#124;    &#124;    &#124;    &#124;    DROP\_CONTRACT|  
|10041|10042|&#124;    &#124;    &#124;    DDL\_MESSAGE\_TYPE\_EVENTS|  
|10042|152|&#124;    &#124;    &#124;    &#124;    ALTER\_MESSAGE\_TYPE|  
|10042|151|&#124;    &#124;    &#124;    &#124;    CREATE\_MESSAGE\_TYPE|  
|10042|153|&#124;    &#124;    &#124;    &#124;    DROP\_MESSAGE\_TYPE|  
|10041|10044|&#124;    &#124;    &#124;    DDL\_QUEUE\_EVENTS|  
|10044|158|&#124;    &#124;    &#124;    &#124;    ALTER\_QUEUE|  
|10044|157|&#124;    &#124;    &#124;    &#124;    CREATE\_QUEUE|  
|10044|159|&#124;    &#124;    &#124;    &#124;    DROP\_QUEUE|  
|10041|10047|&#124;    &#124;    &#124;    DDL\_REMOTE\_SERVICE\_BINDING\_EVENTS|  
|10047|175|&#124;    &#124;    &#124;    &#124;    ALTER\_REMOTE\_SERVICE\_BINDING|  
|10047|174|&#124;    &#124;    &#124;    &#124;    CREATE\_REMOTE\_SERVICE\_BINDING|  
|10047|176|&#124;    &#124;    &#124;    &#124;    DROP\_REMOTE\_SERVICE\_BINDING|  
|10041|10046|&#124;    &#124;    &#124;    DDL\_ROUTE\_EVENTS|  
|10046|165|&#124;    &#124;    &#124;    &#124;    ALTER\_ROUTE|  
|10046|164|&#124;    &#124;    &#124;    &#124;    CREATE\_ROUTE|  
|10046|166|&#124;    &#124;    &#124;    &#124;    DROP\_ROUTE|  
|10041|10045|&#124;    &#124;    &#124;    DDL\_SERVICE\_EVENTS|  
|10045|162|&#124;    &#124;    &#124;    &#124;    ALTER\_SERVICE|  
|10045|161|&#124;    &#124;    &#124;    &#124;    CREATE\_SERVICE|  
|10045|163|&#124;    &#124;    &#124;    &#124;    DROP\_SERVICE|  
|10016|10022|&#124;    &#124;    DDL\_SYNONYM\_EVENTS|  
|10022|34|&#124;    &#124;    &#124;    CREATE\_SYNONYM|  
|10022|36|&#124;    &#124;    &#124;    DROP\_SYNONYM|  
|10016|10017|&#124;    &#124;    DDL\_TABLE\_VIEW\_EVENTS|  
|10017|10020|&#124;    &#124;    &#124;    DDL\_INDEX\_EVENTS|  
|10020|213|&#124;    &#124;    &#124;    &#124;    ALTER\_FULLTEXT\_INDEX|  
|10020|25|&#124;    &#124;    &#124;    &#124;    ALTER\_INDEX|  
|10020|224|&#124;    &#124;    &#124;    &#124;    CREATE\_FULLTEXT\_INDEX|  
|10020|24|&#124;    &#124;    &#124;    &#124;    CREATE\_INDEX|  
|10020|274|&#124;    &#124;    &#124;    &#124;    CREATE\_SPATIAL\_INDEX|  
|10020|206|&#124;    &#124;    &#124;    &#124;    CREATE\_XML\_INDEX|  
|10020|235|&#124;    &#124;    &#124;    &#124;    DROP\_FULLTEXT\_INDEX|  
|10020|26|&#124;    &#124;    &#124;    &#124;    DROP\_INDEX|  
|10017|10021|&#124;    &#124;    &#124;    DDL\_STATISTICS\_EVENTS|  
|10021|27|&#124;    &#124;    &#124;    &#124;    CREATE\_STATISTICS|  
|10021|29|&#124;    &#124;    &#124;    &#124;    DROP\_STATISTICS|  
|10021|28|&#124;    &#124;    &#124;    &#124;    UPDATE\_STATISTICS|  
|10017|10018|&#124;    &#124;    &#124;    DDL\_TABLE\_EVENTS|  
|10018|22|&#124;    &#124;    &#124;    &#124;    ALTER\_TABLE|  
|10018|21|&#124;    &#124;    &#124;    &#124;    CREATE\_TABLE|  
|10018|23|&#124;    &#124;    &#124;    &#124;    DROP\_TABLE|  
|10017|10019|&#124;    &#124;    &#124;    DDL\_VIEW\_EVENTS|  
|10019|42|&#124;    &#124;    &#124;    &#124;    ALTER\_VIEW|  
|10019|41|&#124;    &#124;    &#124;    &#124;    CREATE\_VIEW|  
|10019|43|&#124;    &#124;    &#124;    &#124;    DROP\_VIEW|  
|10016|10025|&#124;    &#124;    DDL\_TRIGGER\_EVENTS|  
|10025|72|&#124;    &#124;    &#124;    ALTER\_TRIGGER|  
|10025|71|&#124;    &#124;    &#124;    CREATE\_TRIGGER|  
|10025|73|&#124;    &#124;    &#124;    DROP\_TRIGGER|  
|10016|10028|&#124;    &#124;    DDL\_TYPE\_EVENTS|  
|10028|91|&#124;    &#124;    &#124;    CREATE\_TYPE|  
|10028|93|&#124;    &#124;    &#124;    DROP\_TYPE|  
|10016|10048|&#124;    &#124;    DDL\_XML\_SCHEMA\_COLLECTION\_EVENTS|  
|10048|178|&#124;    &#124;    &#124;    ALTER\_XML\_SCHEMA\_COLLECTION|  
|10048|177|&#124;    &#124;    &#124;    CREATE\_XML\_SCHEMA\_COLLECTION|  
|10048|179|&#124;    &#124;    &#124;    DROP\_XML\_SCHEMA\_COLLECTION|  
|10016|241|&#124;    &#124;    RENAME|  
|10001|10002|&#124;    DDL\_SERVER\_LEVEL\_EVENTS|  
|10002|214|&#124;    &#124;    ALTER\_INSTANCE|  
|10002|10071|&#124;    &#124;    DDL\_AVAILABILITY\_GROUP\_EVENTS|  
|10071|307|&#124;    &#124;    &#124;    ALTER\_AVAILABILITY\_GROUP|  
|10071|306|&#124;    &#124;    &#124;    CREATE\_AVAILABILITY\_GROUP|  
|10071|308|&#124;    &#124;    &#124;    DROP\_AVAILABILITY\_GROUP|  
|10002|10004|&#124;    &#124;    DDL\_DATABASE\_EVENTS|  
|10004|202|&#124;    &#124;    &#124;    ALTER\_DATABASE|  
|10004|201|&#124;    &#124;    &#124;    CREATE\_DATABASE|  
|10004|203|&#124;    &#124;    &#124;    DROP\_DATABASE|  
|10002|10003|&#124;    &#124;    DDL\_ENDPOINT\_EVENTS|  
|10003|182|&#124;    &#124;    &#124;    ALTER\_ENDPOINT|  
|10003|181|&#124;    &#124;    &#124;    CREATE\_ENDPOINT|  
|10003|183|&#124;    &#124;    &#124;    DROP\_ENDPOINT|  
|10002|10057|&#124;    &#124;    DDL\_EVENT\_SESSION\_EVENTS|  
|10057|265|&#124;    &#124;    &#124;    ALTER\_EVENT\_SESSION|  
|10057|264|&#124;    &#124;    &#124;    CREATE\_EVENT\_SESSION|  
|10057|266|&#124;    &#124;    &#124;    DROP\_EVENT\_SESSION|  
|10002|10011|&#124;    &#124;    DDL\_EXTENDED\_PROCEDURE\_EVENTS|  
|10011|221|&#124;    &#124;    &#124;    CREATE\_EXTENDED\_PROCEDURE|  
|10011|232|&#124;    &#124;    &#124;    DROP\_EXTENDED\_PROCEDURE|  
|10002|10012|&#124;    &#124;    DDL\_LINKED\_SERVER\_EVENTS|  
|10012|263|&#124;    &#124;    &#124;    ALTER\_LINKED\_SERVER|  
|10012|225|&#124;    &#124;    &#124;    CREATE\_LINKED\_SERVER|  
|10012|10013|&#124;    &#124;    &#124;    DDL\_LINKED\_SERVER\_LOGIN\_EVENTS|  
|10013|226|&#124;    &#124;    &#124;    &#124;    CREATE\_LINKED\_SERVER\_LOGIN|  
|10013|236|&#124;    &#124;    &#124;    &#124;    DROP\_LINKED\_SERVER\_LOGIN|  
|10012|262|&#124;    &#124;    &#124;    DROP\_LINKED\_SERVER|  
|10002|10014|&#124;    &#124;    DDL\_MESSAGE\_EVENTS|  
|10014|215|&#124;    &#124;    &#124;    ALTER\_MESSAGE|  
|10014|227|&#124;    &#124;    &#124;    CREATE\_MESSAGE|  
|10014|237|&#124;    &#124;    &#124;    DROP\_MESSAGE|  
|10002|10015|&#124;    &#124;    DDL\_REMOTE\_SERVER\_EVENTS|  
|10015|217|&#124;    &#124;    &#124;    ALTER\_REMOTE\_SERVER|  
|10015|230|&#124;    &#124;    &#124;    CREATE\_REMOTE\_SERVER|  
|10015|240|&#124;    &#124;    &#124;    DROP\_REMOTE\_SERVER|  
|10002|10058|&#124;    &#124;    DDL\_RESOURCE\_GOVERNOR\_EVENTS|  
|10058|273|&#124;    &#124;    &#124;    ALTER\_RESOURCE\_GOVERNOR\_CONFIG|  
|10058|10059|&#124;    &#124;    &#124;    DDL\_RESOURCE\_POOL|  
|10059|268|&#124;    &#124;    &#124;    &#124;    ALTER\_RESOURCE\_POOL|  
|10059|267|&#124;    &#124;    &#124;    &#124;    CREATE\_RESOURCE\_POOL|  
|10059|269|&#124;    &#124;    &#124;    &#124;    DROP\_RESOURCE\_POOL|  
|10058|10060|&#124;    &#124;    &#124;    DDL\_WORKLOAD\_GROUP|  
|10060|271|&#124;    &#124;    &#124;    &#124;    ALTER\_WORKLOAD\_GROUP|  
|10060|270|&#124;    &#124;    &#124;    &#124;    CREATE\_WORKLOAD\_GROUP|  
|10060|272|&#124;    &#124;    &#124;    &#124;    DROP\_WORKLOAD\_GROUP|  
|10002|10005|&#124;    &#124;    DDL\_SERVER\_SECURITY\_EVENTS|  
|10005|209|&#124;    &#124;    &#124;    ADD\_SERVER\_ROLE\_MEMBER|  
|10005|301|&#124;    &#124;    &#124;    ALTER\_SERVER\_ROLE|  
|10005|300|&#124;    &#124;    &#124;    CREATE\_SERVER\_ROLE|  
|10005|10008|&#124;    &#124;    &#124;    DDL\_AUTHORIZATION\_SERVER\_EVENTS|  
|10008|204|&#124;    &#124;    &#124;    &#124;    ALTER\_AUTHORIZATION\_SERVER|  
|10005|10009|&#124;    &#124;    &#124;    DDL\_CREDENTIAL\_EVENTS|  
|10009|260|&#124;    &#124;    &#124;    &#124;    ALTER\_CREDENTIAL|  
|10009|259|&#124;    &#124;    &#124;    &#124;    CREATE\_CREDENTIAL|  
|10009|261|&#124;    &#124;    &#124;    &#124;    DROP\_CREDENTIAL|  
|10005|10061|&#124;    &#124;    &#124;    DDL\_CRYPTOGRAPHIC\_PROVIDER\_EVENTS|  
|10061|276|&#124;    &#124;    &#124;    &#124;    ALTER\_CRYPTOGRAPHIC\_PROVIDER|  
|10061|275|&#124;    &#124;    &#124;    &#124;    CREATE\_CRYPTOGRAPHIC\_PROVIDER|  
|10061|277|&#124;    &#124;    &#124;    &#124;    DROP\_CRYPTOGRAPHIC\_PROVIDER|  
|10005|10007|&#124;    &#124;    &#124;    DDL\_GDR\_SERVER\_EVENTS|  
|10007|168|&#124;    &#124;    &#124;    &#124;    DENY\_SERVER|  
|10007|167|&#124;    &#124;    &#124;    &#124;    GRANT\_SERVER|  
|10007|169|&#124;    &#124;    &#124;    &#124;    REVOKE\_SERVER|  
|10005|10006|&#124;    &#124;    &#124;    DDL\_LOGIN\_EVENTS|  
|10006|145|&#124;    &#124;    &#124;    &#124;    ALTER\_LOGIN|  
|10006|144|&#124;    &#124;    &#124;    &#124;    CREATE\_LOGIN|  
|10006|146|&#124;    &#124;    &#124;    &#124;    DROP\_LOGIN|  
|10005|10064|&#124;    &#124;    &#124;    DDL\_SERVER\_AUDIT\_EVENTS|  
|10064|285|&#124;    &#124;    &#124;    &#124;    ALTER\_SERVER\_AUDIT|  
|10064|284|&#124;    &#124;    &#124;    &#124;    CREATE\_SERVER\_AUDIT|  
|10064|286|&#124;    &#124;    &#124;    &#124;    DROP\_SERVER\_AUDIT|  
|10005|10065|&#124;    &#124;    &#124;    DDL\_SERVER\_AUDIT\_SPECIFICATION\_EVENTS|  
|10065|288|&#124;    &#124;    &#124;    &#124;    ALTER\_SERVER\_AUDIT\_SPECIFICATION|  
|10065|287|&#124;    &#124;    &#124;    &#124;    CREATE\_SERVER\_AUDIT\_SPECIFICATION|  
|10065|289|&#124;    &#124;    &#124;    &#124;    DROP\_SERVER\_AUDIT\_SPECIFICATION|  
|10005|10010|&#124;    &#124;    &#124;    DDL\_SERVICE\_MASTER\_KEY\_EVENTS|  
|10010|251|&#124;    &#124;    &#124;    &#124;    ALTER\_SERVICE\_MASTER\_KEY|  
|10005|302|&#124;    &#124;    &#124;    DROP\_SERVER\_ROLE|  
|10005|210|&#124;    &#124;    &#124;    DROP\_SERVER\_ROLE\_MEMBER|  
  
 The data above can be created by running the following code example.  
  
```  
WITH DirectReports(name, parent_type, type, level, sort) AS   
(  
    SELECT CONVERT(varchar(255),type_name), parent_type, type, 1, CONVERT(varchar(255),type_name)  
    FROM sys.trigger_event_types   
    WHERE parent_type IS NULL  
    UNION ALL  
    SELECT  CONVERT(varchar(255), REPLICATE ('|   ' , level) + e.type_name),  
        e.parent_type, e.type, level + 1,  
    CONVERT (varchar(255), RTRIM(sort) + '|   ' + e.type_name)  
    FROM sys.trigger_event_types AS e  
        INNER JOIN DirectReports AS d  
        ON e.parent_type = d.type   
)  
SELECT parent_type, type, name  
FROM DirectReports  
ORDER BY sort;  
```  
  
## See Also  
 [Event Notifications](../../Topics\TopicNameNotContainA/Event-Notifications.md)   
 [DDL Triggers](../../Topics\TopicNameNotContainA/DDL-Triggers.md)   
 [DDL Events](../../Topics\TopicNameNotContainA/DDL-Events.md)  
  
  