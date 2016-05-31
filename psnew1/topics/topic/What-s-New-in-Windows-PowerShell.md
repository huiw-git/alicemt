---
title: What&#39;s New in Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1476722e-947e-425d-a86c-50037488dc6e
---
# What&#39;s New in Windows PowerShell
[!INCLUDE[wps_1](../../tokencontainer/wps_1_md.md)] 5.0 includes significant new features that extend its use, improve its usability, and allow you to control and manage Windows\-based environments more easily and comprehensively.  
  
 [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] 5.0 is backward\-compatible. Cmdlets, providers, modules, snap\-ins, scripts, functions, and profiles that were designed for [!INCLUDE[psversion4](../../tokencontainer/psversion4_md.md)], [!INCLUDE[psversion3](../../tokencontainer/psversion3_md.md)], and [!INCLUDE[psversion2](../../tokencontainer/psversion2_md.md)] generally work in [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] 5.0 without changes.  
  
 [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] 5.0 is installed by default on [!INCLUDE[winthreshold_server_1](../../tokencontainer/winthreshold_server_1_md.md)] and [!INCLUDE[winthreshold_client_1](../../tokencontainer/winthreshold_client_1_md.md)]. To install [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] 5.0 on [!INCLUDE[winblue_server_2](../../tokencontainer/winblue_server_2_md.md)], [!INCLUDE[winblue_client_ent_2](../../tokencontainer/winblue_client_ent_2_md.md)], or [!INCLUDE[winblue_client_pro_2](../../tokencontainer/winblue_client_pro_2_md.md)], download and install [Windows Management Framework 5.0 Preview](http://go.microsoft.com/fwlink/?LinkID=395058). Be sure to read the download details, and meet all system requirements, before you install Windows Management Framework 5.0 Preview.  
  
## In this topic  
  
-   [Windows PowerShell 4.0 DSC updates in KB 3000850](#BKMK_3000850)  
  
-   [New features in Windows PowerShell 5.0](#BKMK_new50)  
  
-   [New features in Windows PowerShell 4.0](#BKMK_wps4)  
  
-   [New features in Windows PowerShell 3.0](#BKMK_wps3)  
  
##  <a name="BKMK_3000850"></a> Windows PowerShell 4.0 updates in November 2014 update rollup \(KB 3000850\)  
 Many updates and improvements to [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] Desired State Configuration \(DSC\) in [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] 4.0 are available in the [November 2014 update rollup for Windows RT 8.1, Windows 8.1, and Windows Server 2012 R2](https://support.microsoft.com/kb/3000850/) \(KB 3000850\). You can determine if KB 3000850 is installed on your system by running `Get-Hotfix -Id KB3000850` in [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)].  
  
-   Updates to existing cmdlets in the [PSDesiredStateConfiguration](https://technet.microsoft.com/library/dn391651\(v=wps.640\).aspx) module  
  
    -   [Get\-DscResource](http://technet.microsoft.com/library/dn521625.aspx) is faster \(especially in ISE\).  
  
    -   [Start\-DscConfiguration](http://technet.microsoft.com/library/dn521623.aspx) has a new parameter, –UseExisting, which reapplies the last\-applied configuration.  
  
    -   [Start\-DscConfiguration](http://technet.microsoft.com/library/dn521623.aspx) \-Force has been fixed.  
  
    -   [Get\-DscLocalConfigurationManager](http://technet.microsoft.com/library/dn407378.aspx) displays more useful information about the engine state.  
  
    -   [Test\-DscConfiguration](http://technet.microsoft.com/library/dn407382.aspx) now returns the computer name along with True or False.  
  
    -   [New\-DscChecksum](http://technet.microsoft.com/library/dn521622.aspx) now supports UNC paths.  
  
-   New cmdlets in the [PSDesiredStateConfiguration](http://technet.microsoft.com/library/dn391651\(v=wps.640\).aspx) module  
  
    -   [Update\-DscConfiguration](http://technet.microsoft.com/library/mt143541\(v=wps.630\).aspx):  Performs an on\-demand pull server check.  
  
    -   [Stop\-DscConfiguration](http://technet.microsoft.com/library/mt143542\(v=wps.630\).aspx):  Stops a configuration that is already running.  
  
    -   [Remove\-DscConfigurationDocument](http://technet.microsoft.com/library/mt143544\(v=wps.630\).aspx):  Lets you remove configuration documents in various stages \(pending, previous, or current\).  
  
-   Language enhancements  
  
    -   DependsOn now supports composite resources.  
  
    -   DependsOn now supports numbers in resource instance names.  
  
    -   Node expressions that evaluate to empty no longer throw errors.  
  
    -   An error that occurs if a node expression evaluates to empty has been fixed.  
  
    -   Configurations calling configurations now work in the [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] console.  
  
-   Pull mode enhancements  
  
    -   Pull mode now supports all ZIP files.  
  
    -   **AllowModuleOverwrite** now works correctly.  
  
-   Resiliency improvements  
  
    -   New **DebugMode** lets you reload resource modules.  
  
    -   If a configuration failure occurs, the pending.mof file is not deleted.  
  
    -   The Local Configuration Manager \(LCM\) is now more resilient when metaconfiguration settings have become corrupted.  
  
-   Diagnostic improvements  
  
    -   A warning is displayed when the LCM sets the timer to different settings than you have specified.  
  
    -   Error log files now contain the call stack for [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] resources.  
  
-   Flexibility improvements  
  
    -   The LocalConfigurationManager resource has a new property, **ActionAfterReboot**.  
  
        -   ContinueConfiguration \(default value\): Automatically resumes a configuration after a target node restarts.  
  
        -   StopConfiguration: Do not automatically resume a configuration after a node restarts.  
  
    -   A consistency run can now occur more often than a PULL operation, or vice\-versa.  
  
    -   Versioning support:  DSC can now recognize a document that was generated on a newer client \(included with [WMF 5.0 Preview](http://go.microsoft.com/fwlink/?LinkID=395058)\).  
  
-   Error prevention improvements  
  
    -   Module version is now enforced before a configuration is applied.  
  
    -   **DebugPreference** is now set correctly for Get\-, Set\-, or Test\-TargetResource calls.  
  
-   Credential handling improvements  
  
    -   A certificate is now used, if both **Certificate** and **PSDscAllowPlainTextPassword** are specified.  
  
    -   Credentials are decrypted, even for Get\-TargetResource.  
  
    -   Metaconfiguration credentials are encrypted and decrypted.  
  
    -   PSCredentials are now decrypted when they are in an embedded object.  
  
-   Built\-in resource improvements  
  
    -   The Package resource  
  
        -   No longer installs the wrong package \(either from local or web sources\).  
  
        -   Now supports HTTPS.  
  
    -   There is now support for HTTPS in the [Package resource](http://technet.microsoft.com/library/dn282132.aspx).  
  
    -   [Archive resource](http://technet.microsoft.com/library/dn249917.aspx) now supports credentials.  
  
##  <a name="BKMK_new50"></a> New features in Windows PowerShell 5.0  
  
-   [New features in Windows PowerShell](#BKMK_newcore)  
  
-   [New features in Windows PowerShell Desired State Configuration](#BKMK_newDSC)  
  
-   [New features in Windows PowerShell ISE](#BKMK_newISE)  
  
-   [New features in Windows PowerShell Web Services](#BKMK_newOData)  
  
-   [Notable bug fixes in Windows PowerShell 5.0](#BKMK_5bugfix)  
  
###  <a name="BKMK_newcore"></a> New features in Windows PowerShell  
  
-   Starting in [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] 5.0, you can develop by using classes, by using formal syntax and semantics that are similar to other object\-oriented programming languages. **Class**, **Enum**, and other keywords have been added to the [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] language to support the new feature. For more information about working with classes, see about\_Classes.  
  
-   [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] 5.0 introduces a new, structured information stream that you can use to transmit structured data between a script and its callers \(or hosting environment\). You can now use Write\-Host to emit output to the information stream. Information streams also work for PowerShell.Streams, jobs, scheduled jobs, and workflows. The following features support the information stream.  
  
    -   A new Write\-Information cmdlet that lets you specify how [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] handles information stream data for a command. Write\-Host is a wrapper for Write\-Information. Write\-Information is also a supported workflow activity.  
  
    -   Two new common parameters, InformationVariable and InformationAction, let you determine how information streams from a command are displayed. Valid values for InformationAction are SilentlyContinue, Stop, Continue, Inquire, Ignore, or Suspend, with Continue being the default. InformationVariable specifies a string as the name of a variable to which you want the Write\-Host data from a command saved.  
  
    -   A new preference variable, InformationPreference, specifies your default preference for information stream data in a [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] session. The default value is Continue.  
  
    -   Two new workflow common parameters, PSInformation and InformationAction, have been added.  
  
    -   When you use the Format\-Table command, table columns are now automatically formatted by evaluating the first 300ms of data that passes through the stream.  
  
-   In collaboration with [Microsoft Research](http://research.microsoft.com/), a new cmdlet, ConvertFrom\-String, has been added. ConvertFrom\-String lets you extract and parse structured objects from the content of text strings. For more information, see ConvertFrom\-String.  
  
-   A new Convert\-String cmdlet automatically formats text based on an example that you provide in an \-Example parameter.  
  
-   A new module, Microsoft.PowerShell.Archive, includes cmdlets that let you compress files and folders into archive \(also known as ZIP\) files, extract files from existing ZIP files, and update ZIP files with newer versions of files compressed within them.  
  
-   A new module, PackageManagement, lets you discover and install software packages on the Internet. The PackageManagement \(formerly known as OneGet\) module is a manager or multiplexer of existing package managers \(also called package providers\) to unify Windows package management with a single Windows PowerShell interface.  
  
-   A new module, PowerShellGet, lets you find, install, publish, and update modules and DSC resources on the [PowerShell Gallery](http://www.powershellgallery.com/), or on an internal module repository that you can set up by running the Register\-PSRepository cmdlet.  
  
-   A new language keyword, **Hidden**, has been added to specify that a member \(a property or a method\) is not shown by default in Get\-Member results \(unless you add the \-Force parameter\). Properties or methods that have been marked hidden also do not show up in IntelliSense results, unless you are in a context where the member should be visible; for example, the automatic variable $This should show hidden members when in the class method.  
  
-   New\-Item, Remove\-Item, and Get\-ChildItem have been enhanced to support creating and managing [symbolic links](http://en.wikipedia.org/wiki/Symbolic_link). The **ItemType** parameter for New\-Item accepts a new value, **SymbolicLink**. Now you can create symbolic links in a single line by running the New\-Item cmdlet.  
  
-   Get\-ChildItem also has a new –Depth parameter, which you use with the –Recurse parameter to limit the recursion. For example, Get\-ChildItem –Recurse –Depth 2 returns results from the current folder, all of the child folders within the current folder, and all of the folders within the child folders.  
  
-   Copy\-Item now lets you copy files or folders from one [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] session to another, meaning that you can copy files to sessions that are connected to remote computers, \(including computers that are running [Windows Nano Server](http://blogs.technet.com/b/windowsserver/archive/2015/04/08/microsoft-announces-nano-server-for-modern-apps-and-cloud.aspx), and thus have no other interface\). To copy files, specify PSSession IDs as the value of the new \-FromSession and \-ToSession parameters, and add –Path and –Destination to specify origin path and destination, respectively. For example, Copy\-Item \-Path c:\\myFile.txt \-ToSession $s \-Destination d:\\destinationFolder.  
  
-   [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] transcription has been improved to apply to all hosting applications \(such as [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] ISE\) in addition to the console host \(**powershell.exe**\). Transcription options \(including enabling a system\-wide transcript\) can be configured by enabling the **Turn on PowerShell Transcription** Group Policy setting, found in Administrative Templates\/Windows Components\/[!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)].  
  
-   A new detailed script tracing feature lets you enable detailed tracking and analysis of [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] scripting use on a system. After you enable detailed script tracing, [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] logs all script blocks to the Event Tracing for Windows \(ETW\) event log, **Microsoft\-Windows\-PowerShell\/Operational**.  
  
-   Starting in [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] 5.0, new Cryptographic Message Syntax cmdlets support encryption and decryption of content by using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](http://tools.ietf.org/html/rfc5652). The Get\-CmsMessage, Protect\-CmsMessage, and Unprotect\-CmsMessage cmdlets have been added to the [Microsoft.PowerShell.Security](http://technet.microsoft.com/library/hh849807.aspx) module.  
  
-   New cmdlets in the [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) module, Get\-Runspace, Debug\-Runspace, Get\-RunspaceDebug, Enable\-RunspaceDebug, and Disable\-RunspaceDebug, let you set debug options on a runspace, and start and stop debugging on a runspace. For debugging arbitrary runspaces—that is, runspaces that are not the default runspace for a [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] console or [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] ISE session—[!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] lets you set breakpoints in a script, and have added breakpoints stop the script from running until you can attach a debugger to debug the runspace script. Nested debugging support for arbitrary runspaces has been added to the [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] script debugger for runspaces.  
  
-   A new Format\-Hex cmdlet has been added to the [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) module. Format\-Hex lets you view text or binary data in hexadecimal format.  
  
-   Get\-Clipboard and Set\-Clipboard cmdlets have been added to the [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) module; they ease the transfer of content to and from a [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] session. The Clipboard cmdlets support images, audio files, file lists, and text.  
  
-   A new cmdlet, Clear\-RecycleBin, has been added to the [Microsoft.PowerShell.Management](http://technet.microsoft.com/library/hh849827\(v=wps.640\).aspx) module; this cmdlet empties the Recycle Bin for a fixed drive, which includes external drives. By default, you are prompted to confirm a Clear\-RecycleBin command, because the ConfirmImpact property of the cmdlet is set to ConfirmImpact.High.  
  
-   A new cmdlet, New\-TemporaryFile, lets you create a temporary file as part of scripting. By default, the new temporary file is created in C:\\Users\\\<user name\>\\AppData\\Local\\Temp.  
  
-   The Out\-File, Add\-Content, and Set\-Content cmdlets now have a new –NoNewline parameter, which omits a new line after the output.  
  
-   The New\-Guid cmdlet leverages the .NET Framework Guid class to generate a GUID, useful when you are writing scripts or DSC resources.  
  
-   Because file version information can be misleading, particularly after a file is patched, new FileVersionRaw and ProductVersionRaw script properties are available for FileInfo objects. For example, you can run the following command to display the values of these properties for PowerShell.exe, where $pid contains the process ID for a running session of Windows PowerShell:  Get\-Process \-Id $pid \-FileVersionInfo &#124; Format\-List \*version\* \-Force  
  
-   New cmdlets Enter\-PSHostProcess and Exit\-PSHostProcess let you debug [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] scripts in processes separate from the current process that is running in the [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] console. Run Enter\-PSHostProcess to enter, or attach to, a specific process ID, and then run Get\-Runspace to return the active runspaces within the process. Run Exit\-PSHostProcess to detach from the process when you are finished debugging the script within the process.  
  
-   A new Wait\-Debugger cmdlet has been added to the [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) module. You can run Wait\-Debugger to stop a script in the debugger before running the next statement in the script.  
  
-   The [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] Workflow debugger now supports command or tab completion, and you can debug nested workflow functions. You can now press **Ctrl\+Break** to enter the debugger in a running script, in both local and remote sessions, and in a workflow script.  
  
-   A Debug\-Job cmdlet has been added to the [Microsoft.PowerShell.Core](http://technet.microsoft.com/library/hh849695.aspx) module to debug running job scripts for [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] Workflow, background, and jobs running in remote sessions.  
  
-   A new state, AtBreakpoint, has been added for [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] jobs. The AtBreakpoint state applies when a job is running a script that includes set breakpoints, and the script has hit a breakpoint. When a job is stopped at a debug breakpoint, you must debug the job by running the Debug\-Job cmdlet.  
  
-   [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] 5.0 implements support for multiple versions of a single [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] module in the same folder in $PSModulePath. A RequiredVersion property has been added to the ModuleSpecification class to help you get the desired version of a module; this property is mutually\-exclusive with the ModuleVersion property. RequiredVersion is now supported as part of the value of the FullyQualifiedName parameter of the Get\-Module, Import\-Module, and Remove\-Module cmdlets.  
  
-   You can now perform module version validation by running the Test\-ModuleManifest cmdlet.  
  
-   Results of the Get\-Command cmdlet now display a Version column; a new Version property has been added to the CommandInfo class. Get\-Command shows commands from multiple versions of the same module. The Version property is also part of derived classes of CmdletInfo: CmdletInfo and ApplicationInfo.  
  
-   Get\-Command has a new parameter, \-ShowCommandInfo, that returns ShowCommand information as PSObjects. This is especially useful functionality for when Show\-Command is run in [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] ISE by using [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] remoting. The –ShowCommandInfo parameter replaces the existing Get\-SerializedCommand function in the Microsoft.PowerShell.Utility module, but the Get\-SerializedCommand script is still available to support downlevel scripting.  
  
-   A new Get\-ItemPropertyValue cmdlet lets you get the value of a property without using dot notation. For example, in older releases of [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)], you can run the following command to get the value of the Application Base property of the PowerShellEngine registry key: **\(Get\-ItemProperty \-Path HKLM:\\SOFTWARE\\Microsoft\\PowerShell\\3\\PowerShellEngine \-Name ApplicationBase\).ApplicationBase**. Starting in [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] 5.0, you can run **Get\-ItemPropertyValue \-Path HKLM:\\SOFTWARE\\Microsoft\\PowerShell\\3\\PowerShellEngine \-Name ApplicationBase**.  
  
-   The [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] console now uses syntax coloring, just as in [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] ISE.  
  
-   A new NetworkSwitch module contains cmdlets that enable you to apply switch, virtual LAN \(VLAN\), and basic Layer 2 network switch port configuration to [!INCLUDE[winblue_server_2](../../tokencontainer/winblue_server_2_md.md)] logo\-certified network switches.  
  
-   The FullyQualifiedName parameter has been added to Import\-Module and Remove\-Module cmdlets, to support storing multiple versions of a single module.  
  
-   Save\-Help, Update\-Help, Import\-PSSession, Export\-PSSession, and Get\-Command have a new parameter, FullyQualifiedModule, of type ModuleSpecification. Add this parameter to specify a module by its fully qualified name.  
  
-   The value of **$PSVersionTable.PSVersion** has been updated to 5.0.  
  
###  <a name="BKMK_newDSC"></a> New features in Windows PowerShell Desired State Configuration  
  
-   [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] language enhancements let you define [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] Desired State Configuration \(DSC\) resources by using classes. Import\-DscResource is now a true dynamic keyword; [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] parses the specified module’s root module, searching for classes that contain the DscResource attribute. You can now use classes to define DSC resources, in which neither a MOF file nor a DSCResource subfolder in the module folder is required. A [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] module file can contain multiple DSC resource classes.  
  
-   A new parameter, ThrottleLimit, has been added to the following cmdlets in the PSDesiredStateConfiguration module. Add the ThrottleLimit parameter to specify the number of target computers or devices on which you want the command to work at the same time.  
  
    -   Get\-DscConfiguration  
  
    -   Get\-DscConfigurationStatus  
  
    -   Get\-DscLocalConfigurationManager  
  
    -   Restore\-DscConfiguration  
  
    -   Test\-DscConfiguration  
  
    -   Compare\-DscConfiguration  
  
    -   Publish\-DscConfiguration  
  
    -   Set\-DscLocalConfigurationManager  
  
    -   Start\-DscConfiguration  
  
    -   Update\-DscConfiguration  
  
-   With centralized DSC error reporting, rich error information is not only logged in the event log, but it can be sent to a central location for later analysis. You can use this central location to store DSC configuration errors that have occurred for any server in their environment. After the report server is defined in the meta\-configuration, all errors are sent to the report server, and then stored in a database. You can set up this functionality regardless of whether or not a target node is configured to pull configurations from a pull server.  
  
-   Improvements to [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] ISE ease DSC resource authoring. You can now do the following.  
  
    -   List all DSC resources within a **configuration** or **node** block by entering **Ctrl\+Space** on a blank line within the block.  
  
    -   Automatic completion on resource properties of the **enumeration** type.  
  
    -   Automatic completion on the **DependsOn** property of DSC resources, based on other resource instances in the configuration.  
  
    -   Improved tab completion of resource property values.  
  
-   A user can now run a resource under a specified set of credentials by adding the **PSDscRunAsCredential** attribute to a Node block. For example, PSDscRunAsCredential \= Get\-Credential Contoso\\DscUser. This functionality is useful for creating configurations that run Windows Installer and executable installers, access the per\-user registry hive, or perform other tasks outside the current user context.  
  
-   32\-bit \(x86\-based\) support has been added for the **Configuration** keyword.  
  
-   [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] now includes support for custom help for DSC configurations, defined by adding \[CmdletBinding\(\)\] to the generated configuration function.  
  
-   A new **DscLocalConfigurationManager** attribute designates a configuration block as a meta\-configuration, which is used to configure the DSC Local Configuration Manager. This attribute restricts a configuration to containing only items which configure the DSC Local Configuration Manager. During processing, this configuration generates a \*.meta.mof file that is then sent to the appropriate target nodes by running the Set\-DscLocalConfigurationManager cmdlet.  
  
-   Partial configurations are now allowed in [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] 5.0. You can deliver configuration documents to a node in fragments. For a node to receive multiple fragments of a configuration document, the node’s Local Configuration Manager must be first set to specify the expected fragments  
  
-   Cross\-computer synchronization is new in DSC in [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] 5.0. By using the built\-in WaitFor\* resources \(**WaitForAll**, **WaitForAny**, and **WaitForSome**\), you can now specify dependencies across computers during configuration runs, without external orchestrations. These resources provide node\-to\-node synchronization by using CIM connections over the WS\-Man protocol. A configuration can wait for another computer’s specific resource state to change.  
  
-   Just Enough Administration \(JEA\), a new delegation security feature, leverages DSC and [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] constrained runspaces to help secure enterprises from data loss or compromise by employees, whether intentional or unintentional. For more information about JEA, including where you can download the xJEA DSC resource, see [Just Enough Administration, Step by Step](http://blogs.technet.com/b/privatecloud/archive/2014/05/14/just-enough-administration-step-by-step.aspx).  
  
-   The following new cmdlets have been added to the PSDesiredStateConfiguration module.  
  
    -   A new Get\-DscConfigurationStatus cmdlet gets high\-level information about configuration status from a target node. You can obtain the status of the last, or of all configurations.  
  
    -   A new Compare\-DscConfiguration cmdlet compares a specified configuration with the actual state of one or more target nodes.  
  
    -   A new Publish\-DscConfiguration cmdlet copies a configuration MOF file to a target node, but does not apply the configuration. The configuration is applied during the next consistency pass, or when you run the Update\-DscConfiguration cmdlet.  
  
    -   A new Test\-DscConfiguration cmdlet lets you verify that a resulting configuration matches the desired configuration, returning either True if the configuration matches the desired configuration, or False if the actual configuration does not match the desired configuration.  
  
    -   A new Update\-DscConfiguration cmdlet forces a configuration to be processed. If the Local Configuration Manager is in pull mode, the cmdlet gets the configuration from the pull server before applying it.  
  
###  <a name="BKMK_newISE"></a> New features in Windows PowerShell ISE  
  
-   You can now edit remote [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] scripts and files in a local copy of [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] ISE, by running Enter\-PSSession to start a remote session on the computer that’s storing the files you want to edit, and then running **PSEdit \<path and file name on the remote computer\>**. This feature eases editing [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] files that are stored on the Server Core installation option of Windows Server, where [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] ISE cannot run.  
  
-   The Start\-Transcript cmdlet is now supported in [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] ISE.  
  
-   You can now debug remote scripts in [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] ISE.  
  
-   A new menu command, **Break All** \(Ctrl\+B\), breaks into the debugger for both local and remotely\-running scripts.  
  
###  <a name="BKMK_newOData"></a> New features in Windows PowerShell Web Services \(Management OData IIS Extension\)  
  
-   Starting in [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] 5.0, you can generate a set of [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] cmdlets based on the functionality exposed by a given OData endpoint, by running the Export\-ODataEndpointProxy cmdlet, found in the new [Microsoft.PowerShell.OdataUtils](http://technet.microsoft.com/library/dn818507\(v=wps.640\).aspx) module.  
  
###  <a name="BKMK_5bugfix"></a> Notable bug fixes in Windows PowerShell 5.0  
  
-   [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] 5.0 includes a new COM implementation, which offers significant performance improvements when you are working with COM objects. For a video demonstration of the effect, see [Com\_Perf\_Improvements](http://1drv.ms/1qu3UPZ).  
  
-   Significant performance improvements have been made to the first tab completion in a [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] session, shortening tab completion time by nearly 500 ms.  
  
##  <a name="BKMK_wps4"></a> New features in Windows PowerShell 4.0  
 [!INCLUDE[psversion4](../../tokencontainer/psversion4_md.md)] is backward\-compatible. Cmdlets, providers, modules, snap\-ins, scripts, functions, and profiles that were designed for [!INCLUDE[psversion3](../../tokencontainer/psversion3_md.md)] and [!INCLUDE[psversion2](../../tokencontainer/psversion2_md.md)] work in [!INCLUDE[psversion4](../../tokencontainer/psversion4_md.md)] without changes.  
  
 [!INCLUDE[psversion4](../../tokencontainer/psversion4_md.md)] is installed by default on [!INCLUDE[winblue_client_1](../../tokencontainer/winblue_client_1_md.md)] and [!INCLUDE[winblue_server_2](../../tokencontainer/winblue_server_2_md.md)]. To install [!INCLUDE[psversion4](../../tokencontainer/psversion4_md.md)] on Windows 7 with SP1, or Windows Server 2008 R2, download and install [Windows Management Framework 4.0](http://www.microsoft.com/download/details.aspx?id=40855). Be sure to read the download details, and meet all system requirements, before you install Windows Management Framework 4.0.  
  
-   [New features in Windows PowerShell](#BKMK_core)  
  
-   [New features in Windows PowerShell Integrated Scripting Environment \(ISE\)](#BKMK_ise)  
  
-   [New features in Windows PowerShell Workflow](#BKMK_workflow)  
  
-   [New features in Windows PowerShell Web Services](#BKMK_psws)  
  
-   [New features in Windows PowerShell Web Access](#BKMK_powwa)  
  
-   [Notable bug fixes in Windows PowerShell 4.0](#BKMK_bugs)  
  
 [!INCLUDE[psversion4](../../tokencontainer/psversion4_md.md)] includes the following new features.  
  
###  <a name="BKMK_core"></a> New features in Windows PowerShell  
  
-   **[!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] Desired State Configuration** \(DSC\) is a new management system in [!INCLUDE[psversion4](../../tokencontainer/psversion4_md.md)] that enables the deployment and management of configuration data for software services and the environment in which these services run. For more information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](assetId:///c134aa32-b085-4656-9a89-955d8ff768d0).  
  
-   **Save\-Help** now lets you save help for modules that are installed on remote computers. You can use Save\-Help to download module Help from an Internet\-connected client \(on which not all of the modules for which you want help are necessarily installed\), and then copy the saved Help to a remote shared folder or a remote computer that does not have Internet access.  
  
-   The [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] debugger has been enhanced to allow debugging of [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] workflows, as well as scripts that are running on remote computers. [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] workflows can now be debugged at the script level from either the [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] command line or [!INCLUDE[ise_2](../../tokencontainer/ise_2_md.md)]. [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] scripts, including script workflows, can now be debugged over remote sessions. Remote debugging sessions are preserved over [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] remote sessions that are disconnected and then later reconnected.  
  
-   A **RunNow** parameter for **Register\-ScheduledJob** and **Set\-ScheduledJob** eliminates the need to set an immediate start date and time for jobs by using the **Trigger** parameter.  
  
-   **Invoke\-RestMethod** and **Invoke\-WebRequest** now let you set all headers by using the Headers parameter. Although this parameter has always existed, it was one of several parameters for the web cmdlets that resulted in exceptions or errors.  
  
-   **Get\-Module** has a new parameter, **FullyQualifiedName**, of the type **ModuleSpecification\[\]**. The **FullyQualifiedName** parameter of Get\-Module now lets you specify a module by using the module's name, version, and optionally, its GUID.  
  
-   The default execution policy setting on [!INCLUDE[winblue_server_2](../../tokencontainer/winblue_server_2_md.md)] is **RemoteSigned**. On [!INCLUDE[winblue_client_2](../../tokencontainer/winblue_client_2_md.md)], there is no change in default setting.  
  
-   Starting in [!INCLUDE[psversion4](../../tokencontainer/psversion4_md.md)], method invocation by using dynamic method names is supported. You can use a variable to store a method name, and then dynamically invoke the method by calling the variable.  
  
-   Asynchronous workflow jobs are no longer deleted when the time\-out period that is specified by the **PSElapsedTimeoutSec** workflow common parameter has elapsed.  
  
-   A new parameter, **RepeatIndefinitely**, has been added to the **New\-JobTrigger** and **Set\-JobTrigger** cmdlets. This eliminates the necessity of specifying a **TimeSpan.MaxValue** value for the **RepetitionDuration** parameter to run a scheduled job repeatedly for an indefinite period.  
  
-   A **Passthru** parameter has been added to the **Enable\-JobTrigger** and **Disable\-JobTrigger** cmdlets. The Passthru parameter displays any objects that are created or modified by your command.  
  
-   The parameter names for specifying a workgroup in the **Add\-Computer** and **Remove\-Computer** cmdlets are now consistent. Both cmdlets now use the parameter **WorkgroupName**.  
  
-   A new common parameter, **PipelineVariable**, has been added. PipelineVariable lets you save the results of a piped command \(or part of a piped command\) as a variable that can be passed through the remainder of the pipeline.  
  
-   Collection filtering by using a method syntax is now supported. This means that you can now filter a collection of objects by using simplified syntax, similar to that for Where\(\) or Where\-Object, formatted as a method call. The following is an example: \(Get\-Process\).where\({$\_.Name \-match 'powershell'}\)  
  
-   The **Get\-Process** cmdlet has a new switch parameter, **IncludeUserName**.  
  
-   A new cmdlet, **Get\-FileHash**, that returns a file hash in one of several formats for a specified file, has been added.  
  
-   In [!INCLUDE[psversion4](../../tokencontainer/psversion4_md.md)], if a module uses the **DefaultCommandPrefix** key in its manifest, or if the user imports a module with the **Prefix** parameter, the **ExportedCommands** property of the module shows the commands in the module with the prefix. When you run the commands by using the module\-qualified syntax, ModuleName\\CommandName, the command names must include the prefix.  
  
-   The value of **$PSVersionTable.PSVersion** has been updated to 4.0.  
  
-   **Where\(\)** operator behavior has changed. `Collection.Where('property –match name')` accepting a string expression in the format `"Property –CompareOperator Value"` is no longer supported. However, the **Where\(\)** operator accepts string expressions in the format of a scriptblock; this is still supported.  
  
###  <a name="BKMK_ise"></a> New features in Windows PowerShell Integrated Scripting Environment \(ISE\)  
  
-   [!INCLUDE[ise_2](../../tokencontainer/ise_2_md.md)] supports both [!INCLUDE[ps_workflow_2](../../tokencontainer/ps_workflow_2_md.md)] debugging and remote script debugging.  
  
-   IntelliSense support has been added for [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] Desired State Configuration providers and configurations.  
  
###  <a name="BKMK_workflow"></a> New features in Windows PowerShell Workflow  
  
-   Support has been added for a new **PipelineVariable** common parameter in the context of iterative pipelines, such as those used by System Center Orchestrator; that is, pipelines that run commands simply left\-to\-right, as opposed to interspersed running by using streaming.  
  
-   Parameter binding has been significantly enhanced to work outside of tab completion scenarios, such as with commands that do not exist in the current runspace.  
  
-   Support for custom container activities has been added to [!INCLUDE[ps_workflow_2](../../tokencontainer/ps_workflow_2_md.md)]. If an activity parameter is of the types **Activity**, **Activity\[\]**—or is a generic collection of activities—and the user has supplied a script block as an argument, then [!INCLUDE[ps_workflow_2](../../tokencontainer/ps_workflow_2_md.md)] converts the script block to XAML, as with normal [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] script\-to\-workflow compilation.  
  
-   After a crash, [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] Workflow automatically reconnects to managed nodes.  
  
-   You can now throttle **Foreach \-Parallel** activity statements by using the **ThrottleLimit** property.  
  
-   The **ErrorAction** common parameter has a new valid value, **Suspend**, that is exclusively for workflows.  
  
-   A workflow endpoint now automatically closes if there are no active sessions, no in\-progress jobs, and no pending jobs. This feature conserves resources on the computer that is acting as the workflow server, when the automatic closure conditions have been met.  
  
###  <a name="BKMK_psws"></a> New features in Windows PowerShell Web Services  
  
-   When an error occurs in [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] Web Services \(PSWS, also called Management OData IIS Extension\), while a cmdlet is running, more detailed error messages are returned to the caller. In addition, error codes follow [Windows Azure REST API error code guidelines](http://msdn.microsoft.com/library/windowsazure/dd179357.aspx).  
  
-   An endpoint can now define the API version, as well as enforce the usage of a specific API version. Whenever version mismatches occur between client and server, errors are displayed to both the client and the server.  
  
-   Management of the dispatch schema has been simplified by automatically generating values for any missing fields in the schema. Generation occurs, as a helpful starting point, even if the dispatch schema does not exist.  
  
-   Type handling in PSWS has been improved to support types that use a different constructor than the default constructor, by behaving similarly to the **PSTypeConverter** in [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)]. This lets you use complex types with PSWS.  
  
-   PSWS now allows expanding an associated instance while running a query. For larger binary contents \(such as images, audio, or video\), the transfer cost is significant, and it is better to transfer binary data without encoding. PSWS uses named resource streams for transferring without encoding. The named resource stream is a property of an entity of the **Edm.Stream** type. Each named resource stream has a separate URI for GET or UPDATE operations.  
  
-   OData actions now provide a mechanism for invoking non\-CRUD \(Create, Read, Update, and Delete\) methods on a resource. You can invoke an action by sending an HTTP POST request to the URI that is defined for the action. The parameters for the action are defined in the body of the POST request.  
  
-   To be consistent with Windows Azure guidelines, all URLs should be simplified. A change included in **Key As Segment** allows single keys to be represented as segments. Note that references that use multiple key values require comma\-separated values in parenthetical notation, as before.  
  
-   Before this release of PSWS, the only way to perform Create, Update, or Delete operations was to invoke Post, Put, or Delete on a top\-level resource. New in this release of PSWS, Contained Resource operations let users achieve the same results while reaching the same resource less directly, approaching as if these resources were contained.  
  
###  <a name="BKMK_powwa"></a> New features in Windows PowerShell Web Access  
  
-   You can disconnect from and reconnect to existing sessions in the web\-based [!INCLUDE[pswa_2](../../tokencontainer/pswa_2_md.md)] console. A **Save** button in the web\-based console lets you disconnect from a session without deleting it and reconnect to the session another time.  
  
-   Default parameters can be displayed on the sign\-in page. To display default parameters, configure values for all of the settings displayed in the **Optional Connection Settings** area of the sign\-in page in a file named **web.config**. You can use the **web.config** file to configure all optional connection settings except for a second or alternate set of credentials.  
  
-   In [!INCLUDE[winblue_server_2](../../tokencontainer/winblue_server_2_md.md)], you can remotely manage authorization rules for [!INCLUDE[pswa_2](../../tokencontainer/pswa_2_md.md)]. The **Add\-PswaAuthorizationRule** and **Test\-PswaAuthorizationRule** cmdlets now include a Credential parameter that enables administrators to manage authorization rules from a remote computer or in a [!INCLUDE[pswa_2](../../tokencontainer/pswa_2_md.md)] session.  
  
-   You can now have multiple [!INCLUDE[pswa_2](../../tokencontainer/pswa_2_md.md)] sessions in a single browser session by using a new browser tab for each session. You no longer need to open a new browser session to connect to a new session in the web\-based [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] console.  
  
###  <a name="BKMK_bugs"></a> Notable bug fixes in Windows PowerShell 4.0  
  
-   **Get\-Counter** can now return counters that contain an apostrophe character in French editions of Windows.  
  
-   You can now view the **GetType** method on deserialized objects.  
  
-   **\#Requires** statements now let users require Administrator access rights, if needed.  
  
-   The **Import\-Csv** cmdlet now ignores blank lines.  
  
-   A problem where [!INCLUDE[ise_2](../../tokencontainer/ise_2_md.md)] uses too much memory when you are running an **Invoke\-WebRequest** command has been fixed.  
  
-   **Get\-Module** now displays module versions in a **Version** column.  
  
-   Remove\-Item –Recurse now removes items from subfolders as expected.  
  
-   A **UserName** property has been added to **Get\-Process** output objects.  
  
-   The **Invoke\-RestMethod** cmdlet now returns all available results.  
  
-   **Add\-Member** now takes effect on hashtables, even if the hashtables have not yet been accessed.  
  
-   **Select\-Object –Expand** no longer fails or generates an exception if the value of the property is null or empty.  
  
-   **Get\-Process** can now be used in a pipeline with other commands that get the **ComputerName** property from objects.  
  
-   **ConvertTo\-Json** and **ConvertFrom\-Json** can now accept terms within double quotes, and its error messages are now localizable.  
  
-   **Get\-Job** now returns any completed scheduled jobs, even in new sessions.  
  
-   Issues with mounting and unmounting VHDs by using the **FileSystem** provider in [!INCLUDE[psversion4](../../tokencontainer/psversion4_md.md)] have been fixed. [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] is now able to detect new drives when they are mounted in the same session.  
  
-   You no longer need to explicitly load **ScheduledJob** or **Workflow** modules to work with their job types.  
  
-   Performance improvements have been made to the process of importing workflows that define nested workflows; this process is now faster.  
  
##  <a name="BKMK_wps3"></a> New features in Windows PowerShell 3.0  
 [!INCLUDE[psversion3](../../tokencontainer/psversion3_md.md)] includes the following new features.  
  
-   [Windows PowerShell Workflow](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Windows PowerShell Web Access](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [New Windows PowerShell ISE Features](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Support for Microsoft .NET Framework 4.0](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Support for Windows Preinstallation Environment](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Disconnected Sessions](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Robust Session Connectivity](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Updatable Help System](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Enhanced Online Help](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [CIM integration](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Session Configuration Files](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Scheduled Jobs and Task Scheduler Integration](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Windows PowerShell Language Enhancements](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [New Core Cmdlets](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Improvements to Existing Core Cmdlets and Providers](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Remote module import and discovery](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Enhanced Tab Completion](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Module Auto\-Loading](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Module Experience Improvements](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Simplified Command Discovery](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Improved Logging, Diagnostics, and Group Policy Support](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Formatting and Output Improvements](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Enhanced Console Host Experience](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [New Cmdlet and Hosting APIs](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Performance Improvements](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [RunAs and Shared Host Support](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
-   [Special Character Handling Improvements](../../topics/topic/What-s-New-in-Windows-PowerShell.md)  
  
###  <a name="BKMK_Workflow"></a> Windows PowerShell Workflow  
 [!INCLUDE[ps_workflow_1](../../tokencontainer/ps_workflow_1_md.md)] brings the power of Windows Workflow Foundation to [!INCLUDE[mshshort](../../tokencontainer/mshshort_md.md)]. You can write workflows in XAML or in the [!INCLUDE[mshshort](../../tokencontainer/mshshort_md.md)] language and run them just as you would run a cmdlet. The [Get\-Command](assetId:///59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet gets workflw commands and the [Get\-Help](assetId:///1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet gets help for workflows.  
  
 Workflows are sequences of multicomputer management activities that are long\-running, repeatable, frequent, parallelizable, interruptible, suspendable, and restartable. Workflows can be resumed from an intentional or accidental interruption, such as a network outage, a Windows restart, or a power failure.  
  
 Workflows are also portable; they can be exported as or imported from XAML files. You can write custom session configurations that allow workflow or activities in a workflow to be run by delegated or subordinate users.  
  
 The following are the benefits of [!INCLUDE[ps_workflow_2](../../tokencontainer/ps_workflow_2_md.md)]  
  
-   **Automation of sequenced, long\-running tasks.**  
  
-   **Remote monitoring of long\-running tasks**. Status and progress of activities are visible at any time.  
  
-   **Multicomputer management.** Simultaneously run tasks as workflows on hundreds of managed nodes. [!INCLUDE[ps_workflow_2](../../tokencontainer/ps_workflow_2_md.md)] includes a built\-in library of common management parameters, such as **PSComputerName**, which enable multi\-computer management scenarios.  
  
-   **Single task execution of complex processes.** You can combine related scripts that implement an entire end\-to\-end scenario into a single workflow.  
  
-   **Persistence.**: a workflow is saved \(or check\-pointed\) at specific points defined by its author so you can resume the workflow from the last persisted task \(or checkpoint\), instead of restarting the workflow from the beginning.  
  
-   **Robustness.** Automated failure recovery. Workflows survive planned and unplanned restarts. You can suspend workflow execution and then resume the workflow from the last persistence point. Workflow authors can designate specific activities to be re\-run in case of failure on one or more managed nodes.  
  
-   **Ability to disconnect, reconnect, and run in disconnected sessions.** Users can connect and disconnect from the workflow server, but the workflow runs continuously. You can log off of the client computer or restart the client computer and monitor the workflow execution from another computer without interrupting the workflow.  
  
-   **Scheduling.** Workflow tasks can be scheduled like any [!INCLUDE[mshshort](../../tokencontainer/mshshort_md.md)] cmdlet or script.  
  
-   **Workflow and Connection Throttling.** Workflow execution and connections to nodes can be throttled, thus enabling scalability and high\-availability scenarios.  
  
###  <a name="BKMK_WebAccess"></a> Windows PowerShell Web Access  
 [!INCLUDE[pswa_1](../../tokencontainer/pswa_1_md.md)] is a [!INCLUDE[win8_server_2](../../tokencontainer/win8_server_2_md.md)] feature that lets users run Windows PowerShell commands and scripts in a web\-based console. Devices that use the web\-based console do not require [!INCLUDE[mshshort](../../tokencontainer/mshshort_md.md)], remote management software, or browser plug\-in installations. All that is required is a properly\-configured [!INCLUDE[pswa_2](../../tokencontainer/pswa_2_md.md)] gateway and a client device browser that supports JavaScript® and accepts cookies.  
  
 For more information, see [Deploy Windows PowerShell Web Access](http://go.microsoft.com/fwlink/p/?LinkID=221050).  
  
###  <a name="BKMK_ISE"></a> New Windows PowerShell ISE Features  
 For [!INCLUDE[psversion3](../../tokencontainer/psversion3_md.md)], [!INCLUDE[ise_1](../../tokencontainer/ise_1_md.md)] has many new features, including IntelliSense, Show\-Command window, a unified Console Pane, snippets, brace\-matching, expand\-collapse sections, auto\-save, recent items list, rich copy, block copy, and full support for writing Windows PowerShell script workflows. For more information, see [about\_Windows\_PowerShell\_ISE &#91;v3&#93;](assetId:///dfa54d47-60c6-4fff-8197-c747e8d411bb).  
  
###  <a name="BKMK_NET4"></a> Support for Microsoft .NET Framework 4  
 Windows PowerShell is built against the Common Language Runtime 4.0. Cmdlet, script, and workflow authors can use the new Microsoft .NET Framework 4 classes in Windows PowerShell, with features that include Application Compatibility and Deployment, Managed Extensibility Framework, Parallel Computing, Networking, Windows Communication Foundation and Windows Workflow Foundation.  
  
###  <a name="BKMK_WinPE"></a> Support for Windows Preinstallation Environment  
 Windows PowerShell 3.0 is an optional component of Windows Preinstallation Environment \(Windows PE\) 4.0 for Windows 8. Windows PE is a minimal operating system that starts a computer that has no operating system and prepares it for Windows installation. Windows PE can be used to partition and format hard drives, copy disk images to a computer, and initiate Windows Setup from a network share. Windows PowerShell 3.0 can be used on Windows PE to manage deployment, diagnostics, and recovery scenarios.  
  
###  <a name="BKMK_Disconnected"></a> Disconnected Sessions  
 Beginning in Windows PowerShell 3.0, persistent user\-managed sessions \("PSSessions"\) that you create by using the New\-PSSession cmdlet are saved on the remote computer. They are no longer dependent on the session in which they were created.  
  
 You can now disconnect from a session without disrupting the commands that are running in the session. You can close the session and shut down your computer. Later, you can reconnect to the session from a different session on the same or on a different computer.  
  
 The **ComputerName** parameter of the [Get\-PSSession](assetId:///b2b10531-d0df-4746-b877-e75c09955cb6) cmdlet now gets all of the user's sessions that connect to the computer, even if they were started in a different session on a different computer. You can connect to the sessions, get the results of commands, start new commands, and then disconnect from the session.  
  
 New cmdlets have been added to support the Disconnected Sessions feature, including [Disconnect\-PSSession](assetId:///f8f95111-612f-4cba-9098-77904b0473d8), [Connect\-PSSession](assetId:///b803dd29-f208-4079-80d4-db04d778f060), and Receive\-PSSession, and new parameters have been added to cmdlets that manage PSSessions, such as the **InDisconnectedSession** parameter of the [Invoke\-Command](assetId:///906b4b41-7da8-4330-9363-e7164e5e6970) cmdlet.  
  
 The Disconnected Sessions feature is supported only when the computers at both the originating \("client"\) and terminating \("server"\) ends of the connection are running Windows PowerShell 3.0.  
  
###  <a name="BKMK_Robust"></a> Robust Session Connectivity  
 Windows PowerShell 3.0 detects unexpected losses of connectivity between the client and server and attempts to reestablish connectivity and resume execution automatically. If the client\-server connection cannot be reestablished in the allotted time, the user is notified and the session is disconnected. During the attempt to reconnect, Windows PowerShell provides continuous feedback to the user.  
  
 If the disconnected session was started by using the InvokeCommand, Windows PowerShell creates a job for the disconnected session to make it easier to reconnect and resume execution.  
  
 These features provide a more reliable and recoverable remoting experience and allow users to perform long\-running tasks that require robust sessions, such as workflows.  
  
###  <a name="BKMK_UpHelp"></a> Updatable Help System  
 You can now download updated help files for the cmdlets in your modules. The [Update\-Help](assetId:///93e1d870-ace6-432b-8778-8920291d7545) cmdlet identifies the newest help files, downloads them from the Internet, unpacks them, validates them, and installs them in the correct language\-specific directory for the module.  
  
 To use the updated help files, just type `Get-Help`. You do not need to restart Windows or [!INCLUDE[mshshort](../../tokencontainer/mshshort_md.md)]. To update help for modules in the $pshome directory, start [!INCLUDE[mshshort](../../tokencontainer/mshshort_md.md)] with the "Run as administrator" option.  
  
 To support users who don't have Internet access and users behind firewalls, the new [Save\-Help](assetId:///aed94f90-b73f-4e25-a25d-7c18d9f161fa) cmdlet downloads help files to a file system directory, such as a file share. Users can then use the [Update\-Help](assetId:///93e1d870-ace6-432b-8778-8920291d7545) cmdlet to get updated help files from the file share.  
  
 You can use the [Update\-Help](assetId:///93e1d870-ace6-432b-8778-8920291d7545) cmdlet to update help files for all or particular modules in all supported UI cultures. You can even put an [Update\-Help](assetId:///93e1d870-ace6-432b-8778-8920291d7545) command in your [!INCLUDE[mshshort](../../tokencontainer/mshshort_md.md)] profile. By default, [!INCLUDE[mshshort](../../tokencontainer/mshshort_md.md)] downloads the help files for a module no more than once each day.  
  
 [!INCLUDE[win8_client_2](../../tokencontainer/win8_client_2_md.md)] and [!INCLUDE[win8_server_2](../../tokencontainer/win8_server_2_md.md)] modules do not include help files. To download the latest help files, type `Update-Help`. For more information, type `Get-Help` \(without parameters\) or see [about\_Updatable\_Help](assetId:///10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe).  
  
 When the help files for a cmdlet are not installed on the computer, the [Get\-Help](assetId:///1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet now displays auto\-generated help. The auto\-generated help includes the command syntax and instructions for using the [Update\-Help](assetId:///93e1d870-ace6-432b-8778-8920291d7545) cmdlet to download help files.  
  
 Any module author can support Updatable Help for their module. You can include help files in the module and use Updatable Help to update them or omit the help files and use Updatable Help to install them. For more information about supporting Updatable Help, see [Supporting Updatable Help](http://go.microsoft.com/FWLink/?LinkID=242129) in MSDN.  
  
###  <a name="BKMK_Online"></a> Enhanced Online Help  
 [!INCLUDE[mshshort](../../tokencontainer/mshshort_md.md)] online help is a valuable resource for all users, but it is especially important to users who do not or cannot install updated help files.  
  
 To get online help for any [!INCLUDE[mshshort](../../tokencontainer/mshshort_md.md)] cmdlet, type:  
  
```  
Get-Help <cmdlet-name> -Online  
```  
  
 [!INCLUDE[mshshort](../../tokencontainer/mshshort_md.md)] opens the online version of the help topic in your default Internet browser.  
  
 The **Get\-Help \-Online** feature in [!INCLUDE[psversion3](../../tokencontainer/psversion3_md.md)] is now even more powerful because it works even when help files for the cmdlet are not installed on the computer. The **Get\-Help \-Online** feature gets the URI for online help topic from the HelpUri property of cmdlets and advanced functions.  
  
```  
PS C:\>(Get-Command Get-ScheduledJob).HelpUri  
http://go.microsoft.com/fwlink/?LinkID=223923  
```  
  
 Beginning in [!INCLUDE[psversion3](../../tokencontainer/psversion3_md.md)], authors of C\# cmdlets can populate the **HelpUri** property by creating a **HelpUri** attribute on the cmdlet class. Authors of advanced functions can define a **HelpUri** property on the **CmdletBinding** attribute. The value of the **HelpUri** property must begin with "http" or "https".  
  
 You can also include a **HelpUri** value in the first related link of an XML\-based cmdlet help file or the .Link directive of comment\-based help in a function.  
  
 For more information about supporting online help, see [Supporting Online Help](http://go.microsoft.com/fwlink/?LinkId=242132) in MSDN.  
  
###  <a name="BKMK_CIM"></a> CIM integration  
 [!INCLUDE[psversion3](../../tokencontainer/psversion3_md.md)] includes support for the Common Information Model \(CIM\), which provides common definitions of management information for systems, networks, applications, and services, allowing them the exchange of management information between heterogeneous systems. Support for CIM in [!INCLUDE[psversion3](../../tokencontainer/psversion3_md.md)], including the ability to author Windows PowerShell cmdlets based on new or existing CIM classes, commands based on cmdlet definition XML files, support for CIM .NET Framework. API, CIM management cmdlets and WMI 2.0 providers.  
  
###  <a name="BKMK_ConfigFile"></a> Session Configuration Files  
 Beginning in [!INCLUDE[psversion3](../../tokencontainer/psversion3_md.md)], you can design a custom session configuration by using a file. The new session configuration file lets you determine the environment of sessions that use the session configuration, including which modules, scripts, and format files are loaded into sessions, which cmdlets and language elements users can use, which modules and scripts they can run, and which variables they can see.  
  
 You can design a session in which users can only run the cmdlets from one particular module, or a session in which users have full language, access to all modules, and access to scripts that perform advanced tasks.  
  
 In previous versions of [!INCLUDE[mshshort](../../tokencontainer/mshshort_md.md)], control at this level was available only to those who could write a C\# program or a complex start\-up script. Now, any member of the Administrators group on the computer can customize a session configuration by using a configuration file.  
  
 To create a session configuration file, use the [New\-PSSessionConfigurationFile](assetId:///5f3e3633-6e90-479c-aea9-ba45a1954866) cmdlet. To apply the session configuration file to a session configuration, use the [Register\-PSSessionConfiguration](assetId:///e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) or [Set\-PSSessionConfiguration](assetId:///b21fbad3-1759-4260-b206-dcb8431cd6ea) cmdlets.  
  
 For more information, see [about\_Session\_Configuration\_Files](assetId:///c7217447-1ebf-477b-a8ef-4dbe9a1473b8) and [New\-PSSessionConfigurationFile](assetId:///5f3e3633-6e90-479c-aea9-ba45a1954866).  
  
###  <a name="BKMK_ScheduledJob"></a> Scheduled Jobs and Task Scheduler Integration  
 You can now schedule [!INCLUDE[mshshort](../../tokencontainer/mshshort_md.md)] background jobs and manage them in [!INCLUDE[mshshort](../../tokencontainer/mshshort_md.md)] and in Task Scheduler.  
  
 [!INCLUDE[mshshort](../../tokencontainer/mshshort_md.md)] scheduled jobs are a useful hybrid of [!INCLUDE[mshshort](../../tokencontainer/mshshort_md.md)] background jobs and Task Scheduler tasks.  
  
 Like [!INCLUDE[mshshort](../../tokencontainer/mshshort_md.md)] background jobs, scheduled jobs run asynchronously in the background. Instances of scheduled jobs that have completed can be managed by using the job cmdlets, such as [Start\-Job](assetId:///2bc04935-0deb-4ec0-b856-d7290cca6442) and [Get\-Job](assetId:///1352c534-7193-46ca-9ab1-0c5219a661ad).  
  
 Like Task Scheduler tasks, you can run scheduled jobs on a one\-time or recurrent schedule, or in response to an action or event. You can view and manage scheduled jobs in Task Scheduler, enable and disable them as needed, run them or use them as templates, and set conditions under which the jobs start.  
  
 In addition, scheduled jobs come with a customized set of cmdlets for managing them. The cmdlets let you create, edit, manage, disable, and re\-enable scheduled jobs, create scheduled job triggers and set scheduled job options.  
  
 For more information about scheduled jobs, see [about\_Scheduled\_Jobs](assetId:///3b546629-703c-4939-b44f-52dd567bce92).  
  
###  <a name="BKMK_Lang"></a> Windows PowerShell Language Enhancements  
 [!INCLUDE[psversion3](../../tokencontainer/psversion3_md.md)] includes many features that are designed to make its language simpler, easier to use, and to avoid common errors. The improvements include property enumeration, count and length properties on scalar objects, new redirection operators, the $Using scope modifier, PSItem automatic variable, flexible script formatting, attributes of variables, simplified attribute arguments, numeric command names, the Stop\-Parsing operator, improved array splatting, new bit operators, ordered dictionaries, PSCustomObject casting, and improved comment\-based help.  
  
###  <a name="BKMK_Core"></a> New Core Cmdlets  
 New cmdlets were added to the Windows PowerShell Core installation, including cmdlets to manage scheduled jobs, disconnected sessions, CIM integration and the Updatable Help System.  
  
|||  
|-|-|  
|Add\-JobTrigger|New\-JobTrigger|  
|Connect\-PSSession|New\-PSSessionConfigurationFile|  
|ConvertFrom\-Json|New\-PSTransportOption|  
|ConvertTo\-Json|New\-PSWorkflowExecutionOption|  
|Disable\-JobTrigger|New\-PSWorkflowSession|  
|Disable\-ScheduledJob|New\-ScheduledJobOption|  
|Disconnect\-PSSession|New\-WinEvent|  
|Enable\-JobTrigger|Receive\-PSSession|  
|Enable\-ScheduledJob|Register\-CimIndicationEvent|  
|Get\-CimAssociatedInstance|Register\-ScheduledJob|  
|Get\-CimClass|Remove\-CimInstance|  
|Get\-CimInstance|Remove\-CimSession|  
|Get\-CimSession|Remove\-TypeData|  
|Get\-ControlPanelItem|Rename\-Computer|  
|Get\-IseSnippet|Resume\-Job|  
|Get\-JobTrigger|Save\-Help|  
|Get\-ScheduledJob|Set\-CimInstance|  
|Get\-ScheduledJobOption|Set\-JobTrigger|  
|Get\-TypeData|Set\-ScheduledJob|  
|Import\-IseSnippet|Set\-ScheduledJobOption|  
|Invoke\-AsWorkflow|Show\-Command|  
|Invoke\-CimMethod|Show\-ControlPanelItem|  
|Invoke\-RestMethod|Suspend\-Job|  
|Invoke\-WebRequest|Test\-PSSessionConfigurationFile|  
|New\-CimInstance|Unblock\-File|  
|New\-CimSession|Unregister\-ScheduledJob|  
|New\-CimSessionOption|Update\-Help|  
|New\-IseSnippet||  
  
###  <a name="BKMK_Prov"></a> Improvements to Existing Core Cmdlets and Providers  
 [!INCLUDE[psversion3](../../tokencontainer/psversion3_md.md)] includes new features for existing cmdlets including the simplified syntax, and new parameters for the following cmdlets: Computer cmdlets, CSV cmdlets, Get\-ChildItem, Get\-Command, Get\-Content, Get\-History, Measure\-Object, Security cmdlets, Select\-Object, Select\-String, Split\-Path, Start\-Process, Tee\-Object, Test\-Connection, Add\-Member, and WMI cmdlets.  
  
 The Windows PowerShell providers were also improved significantly, including Certificate provider support for managing Secure Socket Layer \(SSL\) certificates for web hosting, support for credential, persistent network drives, and alternate data streams in file system drives.  
  
###  <a name="BKMK_REM"></a> Remote module import and discovery  
 [!INCLUDE[psversion3](../../tokencontainer/psversion3_md.md)] extends module discovery, importing, and implicit remoting capabilities on remote computers. The Module cmdlets get modules on remote computers and import the modules to the remote or local computer by using Windows PowerShell remoting. New CIM session support allows you to use CIM and WMI to manage non\-Windows computers by importing commands to the local computer that run implicitly on the remote computer.  
  
 For more information, see the help topics for the [Get\-Module](assetId:///2cccd4c4-9a21-4c77-b691-984ee57242e1) and [Import\-Module](assetId:///af616c24-e122-4098-930e-1e3ea2080ade) cmdlets.  
  
###  <a name="BKMK_TAB"></a> Enhanced Tab Completion  
 Tab completion in the [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] console now completes the names of cmdlets, parameters, parameter values, enumerations, .NET Frameworks types, COM objects, hidden directories, and more. The tab completion feature is completely rewritten based on a new parser and abstract syntax tree to support more scenarios, including in\-memory parsing trees and midline tab completion.  
  
###  <a name="BKMK_AutoLoad"></a> Module Auto\-Loading  
 The [Get\-Command](assetId:///59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet now gets all cmdlets and functions from all modules that are installed on the computer, even if the module is not imported into the current session.  
  
 When you get the cmdlet that you need, you can use it immediately without importing any modules. [!INCLUDE[mshshort](../../tokencontainer/mshshort_md.md)] modules are now imported automatically when you use any cmdlet in the module. You no longer need to search for the module and import it to use its cmdlets.  
  
 Automatic importing of modules is triggered by using the cmdlet in a command, running **Get\-Command** for a cmdlet without wildcards, or running [Get\-Help](assetId:///1f46eeb4-49d7-4bec-bb29-395d9b42f54a) for a cmdlet without wildcards.  
  
 You can enable, disable, and configure automatic importing of modules by using the **$PSModuleAutoLoadingPreference** preference variable.  
  
 For more information, see [about\_Modules &#91;v4&#93;](assetId:///94f57429-a539-4aee-bb0d-205cd7e801f9), [about\_Preference\_Variables &#91;v4&#93;](assetId:///31344314-be29-4286-b039-afa5460cbe8b), and the help topics for the [Get\-Command](assetId:///59c6d302-6e8c-48b7-a6f6-f0172df936ad) and [Import\-Module](assetId:///af616c24-e122-4098-930e-1e3ea2080ade) cmdlets.  
  
###  <a name="BKMK_MOD"></a> Module Experience Improvements  
 Windows PowerShell 3.0 brings advanced feature support to modules, including the following new features.  
  
1.  Module logging for individual modules \(LogPipelineExecutionDetails\) and the new "Turn on Module Logging" Group Policy setting  
  
2.  Extended module objects that expose the values from the module manifest  
  
3.  New **ExportedCommands** property of modules, including nested modules, that combines commands of all types  
  
4.  Improved discovery of available \(un\-imported\) modules, including allowing the **Path** and **ListAvailable** parameters in the same command  
  
5.  New **DefaultCommandPrefix** key in module manifests that avoids name conflicts without changing module code.  
  
6.  Improved module requirements, including fully\-qualified required modules with version and GUID and automatic importing of required modules  
  
7.  Quieter, streamlined operation of the [New\-ModuleManifest](assetId:///512adced-f42f-4e88-ba7c-834fc9e5d047) cmdlet.  
  
8.  New **Module** parameter for \#Requires  
  
9. Improved [Import\-Module](assetId:///af616c24-e122-4098-930e-1e3ea2080ade) cmdlet with both **MinimumVersion** and **RequiredVersion** parameters.  
  
###  <a name="BKMK_SIMPLE"></a> Simplified Command Discovery  
 You no longer need to import all modules to discover the commands available to your session. In [!INCLUDE[psversion3](../../tokencontainer/psversion3_md.md)], the [Get\-Command](assetId:///59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet gets all commands from all installed modules. And, if you use a command, the module that exports the command is automatically imported into your session.  
  
 The new [Show\-Command](assetId:///65bba50b-91a8-49d5-80a2-a30fc684ba41) cmdlet is designed especially for beginners. You can search for commands in a window. You can view all commands or filter by module, import a module by clicking a button, use text boxes and drop\-down lists to construct a valid command, and then copy or run the command without ever leaving the window.  
  
###  <a name="BKMK_LOG"></a> Improved Logging, Diagnostics, and Group Policy Support  
 [!INCLUDE[psversion3](../../tokencontainer/psversion3_md.md)] improves the logging and tracing support for commands and modules with support for Event Tracing in Windows \(ETW\) logs, an editable **LogPipelineExecutionDetails** property of modules, and the "Turn on Module Logging" Group Policy setting. You can now get parameter values from log details by displaying the log properties.  
  
###  <a name="BKMK_OUT"></a> Formatting and Output Improvements  
 New formatting and output improvements improve the efficiency of all [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] users. The improvements include output redirection for all streams, an enhanced Update\-Type cmdlet that adds types dynamically without Format.ps1xml files, word wrap in output, default formatting properties of custom objects, the **PSCustomObject** type, improved formatting for WMI objects and heterogeneous objects, and support for discovering method overloads.  
  
###  <a name="BKMK_HOST"></a> Enhanced Console Host Experience  
 The [!INCLUDE[wps_2](../../tokencontainer/wps_2_md.md)] console host program has new features in [!INCLUDE[psversion3](../../tokencontainer/psversion3_md.md)] including single threaded apartment by default. The new "Run with PowerShell" option in File Explorer lets you run scripts in a unrestricted session just by right\-clicking. New console host launch logic starts Windows PowerShell faster and new fonts allow you to personalize the familiar console window experience.  
  
 For more information, see [about\_Run\_With\_PowerShell](assetId:///c9d9ca5f-eff9-4409-be9d-e43b5b4087eb).  
  
###  <a name="BKMK_API"></a> New Cmdlet and Hosting APIs  
 The new Cmdlet API and Hosting API include public advanced syntax tree \(AST\) APIs, and APIs for pipeline paging, nested pipelines, runspace pools tab completion, Windows RT, the Obsolete cmdlet attribute, and Verb and Noun properties of the FunctionInfo object.  
  
###  <a name="BKMK_PERF"></a> Performance Improvements  
 Significant performance improvements in Windows PowerShell come from the new language parser, which is built on Dynamic Runtime Language \(DLR\) in .NET Framework 4., along with runtime script compilation, engine reliability improvements, and changes to the algorithm of the [Get\-ChildItem](assetId:///75cf79bb-4db6-4a67-8c36-3d20754e2190) that improve its performance, especially when searching network shares.  
  
###  <a name="BKMK_RUNAS"></a> RunAs and Shared Host Support  
 [!INCLUDE[psversion3](../../tokencontainer/psversion3_md.md)] includes support for RunAs and Shared Host features.  
  
 The *RunAs* feature, designed for Windows PowerShell Workflow, lets users of a session configuration create sessions that run with the permission of a shared user account. This enables less privileged users to run particular commands and scripts with administrator permissions, and reduces the need for adding less senior users to the Administrators group.  
  
 The **SharedHost** feature allows multiple users on multiple computers to connect to a workflow session concurrently and monitor the progress of a workflow. Users can start a workflow on one computer and then connect to the workflow session on another computer without disconnecting the session from the original computer. Users must have the same permissions and be using the same session configuration. For more information, see "Running a Windows PowerShell Workflow" in Getting Started with Windows PowerShell Workflow.  
  
###  <a name="BKMK_CHAR"></a> Special Character Handling Improvements  
 To improve the ability of [!INCLUDE[psversion3](../../tokencontainer/psversion3_md.md)] to interpret and correctly handle special characters, the **LiteralPath** parameter, which handles special characters in paths, is valid on almost all cmdlets that have a **Path** parameter, including the new [Update\-Help](assetId:///93e1d870-ace6-432b-8778-8920291d7545) and [Save\-Help](assetId:///aed94f90-b73f-4e25-a25d-7c18d9f161fa) cmdlets. The parser also includes special logic to improve handling of the backtick character \(\`\) and square brackets in file names and paths.  
  
## See Also  
 [about\_Windows\_PowerShell\_4.0](http://technet.microsoft.com/en-us/library/hh847833\(v=wps.630\).aspx)   
 [about\_Windows\_PowerShell\_5.0](assetId:///6d56fa88-371e-40c9-b2de-64a2a0cd49da)   
 [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116)