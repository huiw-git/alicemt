---
title: Soft-NUMA (SQL Server)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1af22188-e08b-4c80-a27e-4ae6ed9ff969
---
# Soft-NUMA (SQL Server)
  Modern processors have multiple to many cores per socket. Each socket is represented, usually, as a single NUMA node. The SQL Server database engine partitions various internal structures and partitions service threads per NUMA node.  With processors containing 10 or more cores per socket, using software NUMA to split hardware NUMA nodes generally increases scalability and performance. Prior to SQL Server 2016, software\-based NUMA \(soft\-NUMA\) required you to edit the registry to add a node configuration affinity mask and was configured per computer rather than per instance.  With SQL Server 2016, soft\-NUMA is configured automatically at the database\-instance level when the SQL Server service starts.  
  
> [!NOTE]  
>  Hot\-add processors are not supported by soft\-NUMA.  
  
## Automatic Soft\-NUMA  
 With SQL Server 2016, whenever the database engine server detects more than 8 logical processors at startup, soft\-NUMA nodes are created automatically by default. Physical and hyper\-threaded processor cores are not differentiated when counting logical processors.  When the number of logical processors detected more than 8 per socket, the database engine service will create soft\-NUMA nodes that ideally contain 8 cores, but can go down to 5 or up to 9 logical processors per node. The size of the hardware node can be limited by a CPU affinity mask. See   
            [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../Topic/ALTER%20SERVER%20CONFIGURATION%20\(Transact-SQL\).md). The number of NUMA nodes will never exceed the maximum number of supported NUMA nodes.  
  
 You can disable or re\-enable soft\-NUMA using the [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../Topic/ALTER%20SERVER%20CONFIGURATION%20\(Transact-SQL\).md) statement with the SET SOFTNUMA argument. Changing the value of this setting requires a restart of the database engine to take effect.  
  
 The figure below shows the type of information regarding soft\-NUMA that you will see in the SQL Server error log when SQL Server detects hardware NUMA nodes with greater than 8 logical processors.  
  
 ![Soft-NUMA Error Log](../../Images\Image\ImageNotContaina/Soft-NUMA-Error-Log.PNG "Soft-NUMA Error Log")  
  
## Manual Soft\-NUMA  
 To can manually configure   
            [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to use soft\-NUMA by disabling automatic soft\_NUMA and editing the registry to add a node configuration affinity mask. When using this method, the soft\-NUMA mask can be stated as a binary, DWORD \(hexadecimal or decimal\), or QWORD \(hexadecimal or decimal\) registry entry. To configure more than the first 32 CPUs use QWORD or BINARY registry values. \(QWORD values cannot be used prior to   
            [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)].\) After modifying the registry, you must restart the   
            [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] for the soft\-NUMA configuration to take  effect.  
  
> [!TIP]  
>  CPUs are numbered starting with 0.  
  
 [!INCLUDE[ssNoteRegistry](../../Token\Other/ssNoteRegistry_md.md)]  
  
 Consider the following example. A computer with eight CPUs does not have hardware NUMA. Three soft\-NUMA nodes are configured.   
            [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] instance A is configured to use CPUs 0 through 3. A second instance of the   
            [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] is installed and configured to use CPUs 4 through 7. The example can be visually represented as:  
  
 `CPUs          0  1  2  3  4  5  6  7`  
  
 `Soft-NUMA   <-N0--><-N1-><----N2---->`  
  
 `SQL Server  <instance A ><instance B>`  
  
 Instance A, which experiences significant I\/O, now has two I\/O threads and   
            one l  
            azy writer thread, while instance B, which performs processor\-intensive operations, has only one I\/O thread and one lazy writer thread. Differing amounts of memory can be assigned to the instances, but unlike hardware NUMA, they both receive memory from the same operating system memory block and there is no memory\-to\-processor affinity.  
  
 The lazy   
            writer thread is tied to the SQL OS view of the physical NUMA memory nodes. Therefore, whatever the hardware presents as physical NUMA nodes will equate to the number of lazy writer threads that are created. For more information, see   
            [How It Works: Soft NUMA, I\/O Completion Thread, Lazy Writer Workers and Memory Nodes](http://blogs.msdn.com/b/psssql/archive/2010/04/02/how-it-works-soft-numa-i-o-completion-thread-lazy-writer-workers-and-memory-nodes.aspx).  
  
> [!NOTE]  
>  The   
>                 **Soft\-NUMA** registry keys are not copied when you upgrade an instance of   
>                 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
### Set the CPU affinity mask  
 Run the following statement on instance A to configure it to use CPUs 0, 1, 2, and 3 by setting the CPU affinity mask:  
  
```  
ALTER SERVER CONFIGURATION   
SET PROCESS AFFINITY CPU=0 TO 3;  
```  
  
 Run the following statement on instance B to configure it to use CPUs 4, 5, 6, and 7 by setting the CPU affinity mask:  
  
```  
ALTER SERVER CONFIGURATION   
SET PROCESS AFFINITY CPU=4 TO 7;  
```  
  
### Map soft\-NUMA nodes to CPUs  
 Using the Registry Editor program \(regedit.exe\), add the following registry keys to map soft\-NUMA node 0 to CPUs 0 and 1, soft\-NUMA node 1 to CPUs 2 and 3, and soft\-NUMA node 2 to CPUs 4. 5, 6, and 7.  
  
> [!TIP]  
>  To specify CPUs 60 through 63, use a QWORD value of   
>                             F000000000000000 or a BINARY value of 1111000000000000000000000000000000000000000000000000000000000000.  
  
 In the following example, assume you have a DL580 G9 server, with 18 cores per socket \(in 4 sockets\), and each socket is in its own K\-group. A soft\-numa configuration that you might create would look something like following. \(6 cores per Node, 3 nodes per group, 4 groups\).  
  
|Example for a <br />                                        [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] server with multiple K\-Groups|Type|Value name|Value data|  
|-----------------------------------------------------------------------------------------------------------------|----------|----------------|----------------|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node0|DWORD|CPUMask|0x3F|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node0|DWORD|Group|0|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node1|DWORD|CPUMask|0x0fc0|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node1|DWORD|Group|0|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node2|DWORD|CPUMask|0x3f000|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node2|DWORD|Group|0|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node3|DWORD|CPUMask|0x3F|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node3|DWORD|Group|1|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node4|DWORD|CPUMask|0x0fc0|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node4|DWORD|Group|1|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node5|DWORD|CPUMask|0x3f000|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node5|DWORD|Group|1|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node6|DWORD|CPUMask|0x3F|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node6|DWORD|Group|2|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node7|DWORD|CPUMask|0x0fc0|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node7|DWORD|Group|2|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node8|DWORD|CPUMask|0x3f000|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node8|DWORD|Group|2|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node9|DWORD|CPUMask|0x3F|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node9|DWORD|Group|3|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node10|DWORD|CPUMask|0x0fc0|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node10|DWORD|Group|3|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node11|DWORD|CPUMask|0x3f000|  
|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\130\\NodeConfiguration\\Node11|DWORD|Group|3|  
  
## Metadata  
 You can use the following DMVs to view the current state and configuration of soft\_NUMA.  
  
-   [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md): Displays the current value \(0 or 1\) for SOFTNUMA  
  
-   [sys.dm_os_nodes &#40;Transact-SQL&#41;](../Topic/sys.dm_os_nodes%20\(Transact-SQL\).md): The node\_state\_desc column for each NUMA node will show whether the node was created by soft\-NUMA or not.  
  
-   [sys.dm_os_sys_info &#40;Transact-SQL&#41;](../Topic/sys.dm_os_sys_info%20\(Transact-SQL\).md): The softnuma and softnuma\_desc columns will show the configuration values.  
  
> [!NOTE]  
>  While you can view   the running value for automatic soft\-NUMA using [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md), you cannot change its value using **sp\_configure**. You must use the [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../Topic/ALTER%20SERVER%20CONFIGURATION%20\(Transact-SQL\).md) statement with the SET SOFTNUMA argument.  
  
## See Also  
 [Map TCP IP Ports to NUMA Nodes &#40;SQL Server&#41;](../Topic/Map%20TCP%20IP%20Ports%20to%20NUMA%20Nodes%20\(SQL%20Server\).md)   
 [affinity mask Server Configuration Option](../../Topics\TopicNameNotContainA/affinity-mask-Server-Configuration-Option.md)   
 [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../Topic/ALTER%20SERVER%20CONFIGURATION%20\(Transact-SQL\).md)  
  
  