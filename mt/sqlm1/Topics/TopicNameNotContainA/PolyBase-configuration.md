---
title: PolyBase configuration
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 80ff73c1-2861-438b-a13f-309155f3d6e1
---
# PolyBase configuration
  Use the procedures below to configure PolyBase.  
  
## External data source configuration  
 You must ensure connectivity to the external data source from SQL Server. The type of connectivity strongly influences the expected query performance. For example, a 10Gbit Ethernet link will result in a faster query response time for PolyBase queries than a 1Gbit Ethernet link.  
  
 You must configure SQL Server to connect to  either your Hadoop version or Azure Blob storage using **sp\_configure**. PolyBase supports two Hadoop distributions: Hortonworks Data Platform \(HDP\) and Cloudera Distributed Hadoop \(CDH\).  For a complete list of supported external data sources, see [PolyBase Connectivity Configuration &#40;Transact-SQL&#41;](../Topic/PolyBase%20Connectivity%20Configuration%20\(Transact-SQL\).md).  
  
### Run sp\_configure  
  
1.  Run sp\_configure ‘hadoop connectivity’ and set an appropriate value.  To find the value, see [PolyBase Connectivity Configuration &#40;Transact-SQL&#41;](../Topic/PolyBase%20Connectivity%20Configuration%20\(Transact-SQL\).md).  
  
    ```tsql  
    -- Values map to various external data sources.  
    -- Example: value 7 stands for Azure blob storage and Hortonworks HDP 2.3 on Linux.  
    sp_configure @configname = 'hadoop connectivity', @configvalue = 7;   
    GO   
  
    RECONFIGURE   
    GO   
    ```  
  
2.  You must restart  SQL Server using **services.msc**. Restarting SQL Server restarts these services:  
  
    -   SQL Server PolyBase Data Movement Service  
  
    -   SQL Server PolyBase Engine  
  
## Pushdown configuration  
 To improve query performance,  enable pushdown computation to a Hadoop cluster:  
  
1.  Find the file **yarn\-site.xml** in the installation path of SQL Server. Typically, the path is:  
  
    ```  
  
    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Polybase\Hadoop\conf\  
  
    ```  
  
2.  On the Hadoop machine, find the analogous file in the Hadoop configuration directory. In the file, find and copy the value of the configuration key yarn.application.classpath.  
  
3.  On the SQL Server machine, in the **yarn.site.xml file,** find the **yarn.application.classpath** property. Paste the value from the Hadoop machine into the value element.  
  
## Kerberos configuration  
 To connect to a Kerberos\-secured Hadoop cluster:  
  
1.  Find the Hadoop configuration directory in the installation path of SQL Server. Typically, the path is:  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Polybase\Hadoop\conf\  
  
    ```  
  
2.  Find the Hadoop side configuration value of the configuration keys listed in the table. \(On the Hadoop machine, find the files in the Hadoop configuration directory.\)  
  
3.  Copy the configuration values into the value property in the corresponding files on the SQL Server machine.  
  
    |**No**|  
    |------------|  
    |**Configuration file**|**Configuration key**|**Action**|  
    |1|core\-site.xml|polybase.kerberos.kdchost|Specify the Kerberos realm. For example: YOUR\-REALM.COM|  
    |2|core\-site.xml|polybase.kerberos.realm|Specify the KDC hostname. For example: kerberos.your\-realm.com.|  
    |3|core\-site.xml|hadoop.security.authentication|Find the Hadoop side configuration and copy to SQL Server machine. For example: kerberos|  
    |4|hdfs\-site.xml|dfs.namenode.kerberos.principal|Find the Hadoop side configuration and copy to SQL Server machine. For example: hdfs\/\_HOST@YOUR\-REALM.COM|  
    |5|mapred\-site.xml|mapreduce.jobhistory.address|Find the Hadoop side configuration and copy to SQL Server machine. For example: mapred\/\_HOST@YOUR\-REALM.COM|  
    |6|mapred\-site.xml|mapreduce.jobhistory.principal|Find the Hadoop side configuration and copy to SQL Server machine. For example: 10.193.26.174:10020|  
    |7|yarn\-site.xml yarn.|yarn.resourcemanager.principal|Find the Hadoop side configuration and copy to SQL Server machine. For example: yarn\/\_HOST@YOUR\-REALM.COM|  
  
4.  Create a database\-scoped credential object to specify the authentication information for each Hadoop user. See [PolyBase T-SQL objects](../../Topics\TopicNameNotContainA/PolyBase-T-SQL-objects.md).  
  
## Next steps  
 [PolyBase T-SQL objects](../../Topics\TopicNameNotContainA/PolyBase-T-SQL-objects.md)  
  
 [Get started with PolyBase](../../Topics\TopicNameNotContainA/Get-started-with-PolyBase.md)  
  
## See Also  
 [PolyBase Connectivity Configuration &#40;Transact-SQL&#41;](../Topic/PolyBase%20Connectivity%20Configuration%20\(Transact-SQL\).md)   
 [PolyBase Guide](../../Topics\TopicNameNotContainA/PolyBase-Guide.md)  
  
  