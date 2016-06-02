---
title: Prepare the Input Trace Data
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c14fd3d2-5770-47c2-a851-cc13ddbc9bf5
---
# Prepare the Input Trace Data
  Before you can start a distributed replay with the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Distributed Replay feature, you must prepare the input trace data by initiating the preprocess stage from the distributed replay administration tool. In the preprocess stage, the distributed replay controller processes the trace data and generates an intermediate file:  
  
 ![Distributed replay preprocess stage](../../Images\Image\ImageNotContaina/Preprocess.gif "Preprocess")  
  
 For more information about the preprocess stage, see [SQL Server Distributed Replay](../../Topics\TopicNameNotContainA/SQL-Server-Distributed-Replay.md).  
  
> [!NOTE]  
>  The input trace data must be captured in a version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that is compatible with Distributed Replay. The input trace data must also be compatible with the target server that you want to replay the trace data against. For more information about version requirements, see [Distributed Replay Requirements](../../Topics\TopicNameNotContainA/Distributed-Replay-Requirements.md).  
  
### To prepare the input trace data  
  
1.  **\(Optional\) Modify preprocess configuration settings**: If you want to modify the preprocess configuration settings, such as whether to filter system sessions or to configure the maximum idle time, you must modify the `<PreprocessModifiers>` element of the XML\-based preprocess configuration file, `DReplay.exe.preprocess.config`. If you modify the preprocess configuration file, we recommend that you modify a copy rather than the original. To modify settings, follow these steps:  
  
    1.  Make a copy of the default preprocess configuration file, `DReplay.exe.preprocess.config`, and rename the new file. The default preprocess configuration file is located in the administration tool installation folder.  
  
    2.  Modify the preprocess configuration settings in the new configuration file.  
  
    3.  When initiating the preprocess stage \(the next step\), use the *config\_file* parameter of the **preprocess** option to specify the location of the modified configuration file.  
  
     For more information about the preprocess configuration file, see [Configure Distributed Replay](../../Topics\TopicNameNotContainA/Configure-Distributed-Replay.md).  
  
2.  **Initiate the preprocess stage**: To prepare the input trace data, you must run the administration tool with the **preprocess** option. For more information, see [Preprocess Option &#40;Distributed Replay Administration Tool&#41;](../Topic/Preprocess%20Option%20\(Distributed%20Replay%20Administration%20Tool\).md).  
  
    1.  Open the Windows Command Prompt utility \(**CMD.exe**\), and navigate to the installation location of the Distributed Replay administration tool \(**DReplay.exe**\).  
  
    2.  \(Optional\) Use the *controller* parameter, **\-m**, to specify the controller, if the controller service is running on a computer different from the administration tool.  
  
    3.  Use the *input\_trace\_file* parameter, **\-i**, to specify the location and name of the input trace files.  
  
    4.  Use the *controller\_working\_directory* parameter, **\-d**, to specify where the intermediate file should be saved on the controller.  
  
    5.  \(Optional\) Use the *config\_file* parameter, **\-c**, to specify location of the preprocess configuration file. Use this parameter to point to the new configuration file if you have modified a copy of the default preprocess configuration file.  
  
    6.  \(Optional\) Use the *status\_interval* parameter, **\-f**, to specify if you want the administration tool to display status messages at a frequency different than 30 seconds.  
  
     For example, initiating the preprocess stage on the same computer as the controller service, for a trace file located at `c:\trace1.trc`, a controller working directory located at `c:\WorkingDir` , and a status message displayed at the default value of 30 seconds, requires the syntax: `dreplay preprocess -i c:\trace1.trc -d c:\WorkingDir`  
  
3.  After the preprocess stage is complete, the intermediate file is stored in the controller working directory. To initiate the event replay stage, you must run the administration tool with the **replay** option. For more information, see [Replay Trace Data](../../Topics\TopicNameNotContainA/Replay-Trace-Data.md).  
  
## See Also  
 [SQL Server Distributed Replay](../../Topics\TopicNameNotContainA/SQL-Server-Distributed-Replay.md)   
 [Distributed Replay Requirements](../../Topics\TopicNameNotContainA/Distributed-Replay-Requirements.md)   
 [Administration Tool Command-line Options &#40;Distributed Replay Utility&#41;](../Topic/Administration%20Tool%20Command-line%20Options%20\(Distributed%20Replay%20Utility\).md)   
 [Configure Distributed Replay](../../Topics\TopicNameNotContainA/Configure-Distributed-Replay.md)  
  
  