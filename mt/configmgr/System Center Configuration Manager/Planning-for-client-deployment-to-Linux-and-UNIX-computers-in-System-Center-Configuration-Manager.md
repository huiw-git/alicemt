---
title: "Planning for client deployment to Linux and UNIX computers in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 44153689-70e8-42ad-9ae8-17ae35f6a2e3
caps.latest.revision: 9
caps.handback.revision: 0
---
# Planning for client deployment to Linux and UNIX computers in System Center Configuration Manager
You can install the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] client on computers that run Linux or UNIX. This client is designed for servers that operate as a workgroup computer, and the client does not support interaction with logged-on users. After you install the client software and the client establishes communication with the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site, you manage the client by using the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console and reports.  
  
> [!NOTE]  
>  The [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client for Linux and UNIX computers does not support the following management capabilities:  
>   
>  -   Client push installation  
> -   Operating system deployment  
> -   Application deployment; instead, deploy software by using packages and programs.  
> -   Software inventory  
> -   Software updates  
> -   Compliance settings  
> -   Remote control  
> -   Power management  
> -   Client status client check and remediation  
> -   Internet-based client management  
  
 For information about the supported Linux and UNIX distributions and the hardware required to support the client for Linux and UNIX, see [Recommended hardware for System Center Configuration Manager](../System Center Configuration Manager/Recommended-hardware-for-System-Center-Configuration-Manager.md).  
  
 Use the information in the following sections to help you plan to deploy the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client for Linux and UNIX.  
  
-   [Prerequisites for Client Deployment to Linux and UNIX Servers](#BKMK_ClientDeployPrereqforLnU)  
  
-   [Dependencies External to Configuration Manager:](#BKMK_ClientDeployExternalforLnU)  
  
-   [Planning for Communication across Forest Trusts for Linux and UNIX Servers](#BKMK_PlanningforCommunicationsforLnU)  
  
-   [Service Location by the client for Linux and UNIX](#BKMK_ServiceLocationforLnU)  
  
-   [Planning for Security and Certificates for Linux and UNIX Servers](#BKMK_SecurityforLnU)  
  
-   [About Certificates for use by Linux and UNIX Servers](#BKMK_AboutCertsforLnU)  
  
-   [Configuring Certificates for Linux and UNIX Servers](#BKMK_ConfigCertsforLnU)  
  
-   [About Linux and UNIX Operating Systems That do not Support SHA-256](#BKMK_NoSHA-256)  
  
##  <a name="BKMK_ClientDeployPrereqforLnU"></a> Prerequisites for Client Deployment to Linux and UNIX Servers  
 Use the following information to determine the prerequisites you must have in place to successfully install the client for Linux and UNIX.  
  
###  <a name="BKMK_ClientDeployExternalforLnU"></a> Dependencies External to Configuration Manager:  
 The following tables describe the required UNIX and Linux operating systems and package dependencies.  
  
 **Red Hat Enterprise Linux ES Release 4**  
  
|Required package|Description|Minimum version|  
|----------------------|-----------------|---------------------|  
|glibc|C Standard Libraries|2.3.4-2|  
|Openssl|OpenSSL Libraries; Secure Network Communications Protocol|0.9.7a-43.1|  
|PAM|Pluggable Authentication Modules|0.77-65.1|  
  
 **Red Hat Enterprise Linux Server release 5.1 (Tikanga)**  
  
|Required package|Description|Minimum version|  
|----------------------|-----------------|---------------------|  
|glibc|C Standard Libraries|2.5-12|  
|Openssl|OpenSSL Libraries; Secure Network Communications Protocol|0.9.8b-8.3.el5|  
|PAM|Pluggable Authentication Modules|0.99.6.2-3.14.el5|  
  
 **Red Hat Enterprise Linux Server release 6**  
  
|Required package|Description|Minimum version|  
|----------------------|-----------------|---------------------|  
|glibc|C Standard Libraries|2.12-1.7|  
|Openssl|OpenSSL Libraries; Secure Network Communications Protocol|1.0.0-4|  
|PAM|Pluggable Authentication Modules|1.1.1-4|  
  
 **Solaris 9 SPARC**  
  
|Required package|Description|Minimum version|  
|----------------------|-----------------|---------------------|  
|Required operating system patch|PAM memory leak|112960-48|  
|SUNWlibC|Sun Workshop Compilers Bundled libC (sparc)|5.9,REV=2002.03.18|  
|SUNWlibms|Forte Developer Bundled Shared libm (sparc)|5.9,REV=2001.12.10|  
|OpenSSL|SMCosslg (sparc)<br /><br /> Sun does not provide a version of OpenSSL for Solaris 9 SPARC. There is a version available from Sunfreeware.|0.9.7g|  
|PAM|Pluggable Authentication Modules<br /><br /> SUNWcsl, Core Solaris, (Shared Libs) (sparc)|11.9.0,REV=2002.04.06.15.27|  
  
 **Solaris 10 SPARC**  
  
|Required package|Description|Minimum version|  
|----------------------|-----------------|---------------------|  
|Required operating system patch|PAM memory leak|117463-05|  
|SUNWlibC|Sun Workshop Compilers Bundled libC (sparc)|5.10, REV=2004.12.22|  
|SUNWlibms|Math & Microtasking Libraries (Usr) (sparc)|5.10, REV=2004.11.23|  
|SUNWlibmsr|Math & Microtasking Libraries (Root) (sparc)|5.10, REV=2004.11.23|  
|SUNWcslr|Core Solaris Libraries (Root) (sparc)|11.10.0, REV=2005.01.21.15.53|  
|SUNWcsl|Core Solaris Libraries (Root) (sparc)|11.10.0, REV=2005.01.21.15.53|  
|OpenSSL|SUNopenssl-librararies (Usr)<br /><br /> Sun provides the OpenSSL libraries for Solaris 10 SPARC. They are bundled with the operating system.|11.10.0,REV=2005.01.21.15.53|  
|PAM|Pluggable Authentication Modules<br /><br /> SUNWcsr, Core Solaris, (Root) (sparc)|11.10.0, REV=2005.01.21.15.53|  
  
 **Solaris 10 x86**  
  
|Required package|Description|Minimum version|  
|----------------------|-----------------|---------------------|  
|Required operating system patch|PAM memory leak|117464-04|  
|SUNWlibC|Sun Workshop Compilers Bundled libC (i386)|5.10,REV=2004.12.20|  
|SUNWlibmsr|Math & Microtasking Libraries (Root) (i386)|5.10, REV=2004.12.18|  
|SUNWcsl|Core Solaris, (Shared Libs) (i386)|11.10.0,REV=2005.01.21.16.34|  
|SUNWcslr|Core Solaris Libraries (Root) (i386)|11.10.0, REV=2005.01.21.16.34|  
|OpenSSL|SUNWopenssl-libraries; OpenSSL Libraries (Usr) (i386)|11.10.0, REV=2005.01.21.16.34|  
|PAM|Pluggable Authentication Modules<br /><br /> SUNWcsr Core Solaris, (Root)(i386)|11.10.0,REV=2005.01.21.16.34|  
  
 **Solaris 11 SPARC**  
  
|Required package|Description|Minimum version|  
|----------------------|-----------------|---------------------|  
|SUNWlibC|Sun Workshop Compilers Bundled libC|5.11, REV=2011.04.11|  
|SUNWlibmsr|Math & Microtasking Libraries (Root)|5.11, REV=2011.04.11|  
|SUNWcslr|Core Solaris Libraries (Root)|11.11, REV=2009.11.11|  
|SUNWcsl|Core Solaris, (Shared Libs)|11.11, REV=2009.11.11|  
|SUNWcsr|Core Solaris, (Root)|11.11, REV=2009.11.11|  
|SUNWopenssl-libraries|OpenSSL Libraries (Usr)|11.11.0,REV=2010.05.25.01.00|  
  
 **Solaris 11 x86**  
  
||||  
|-|-|-|  
|Required package|Description|Minimum version|  
|SUNWlibC|Sun Workshop Compilers Bundled libC|5.11, REV=2011.04.11|  
|SUNWlibmsr|Math & Microtasking Libraries (Root)|5.11, REV=2011.04.11|  
|SUNWcslr|Core Solaris Libraries (Root)|11.11, REV=2009.11.11|  
|SUNWcsl|Core Solaris, (Shared Libs)|11.11, REV=2009.11.11|  
|SUNWcsr|Core Solaris, (Root)|11.11, REV=2009.11.11|  
|SUNWopenssl-libraries|OpenSSL Libraries (Usr)|11.11.0,REV=2010.05.25.01.00|  
  
 **SUSE Linux Enterprise Server 9 (i586)**  
  
|Required package|Description|Minimum version|  
|----------------------|-----------------|---------------------|  
|Service Pack 4|SUSE Linux Enterprise Server 9||  
|OS Patch lib gcc-41.rpm|Standard shared library|41-4.1.2_20070115-0.6|  
|OS Patch lib stdc++-41.rpm|Standard shared library|41-4.1.2_20070115-0.6|  
|Openssl|OpenSSL Libraries; Secure Network Communications Protocol|0.9.7d-15.35|  
|PAM|Pluggable Authentication Modules|0.77-221-11|  
  
 **SUSE Linux Enterprise Server 10 SP1 (i586)**  
  
|Required package|Description|Minimum version|  
|----------------------|-----------------|---------------------|  
|glibc-2.4-31.30|C Standard shared library|2.4-31.30|  
|OpenSSL|OpenSSL Libraries; Secure Network Communications Protocol|0.9.8a-18.15|  
|PAM|Pluggable Authentication Modules|0.99.6.3-28.8|  
  
 **SUSE Linux Enterprise Server 11 (i586)**  
  
|Required package|Description|Minimum version|  
|----------------------|-----------------|---------------------|  
|glibc-2.9-13.2|C Standard shared library|2.9-13.2|  
|PAM|Pluggable Authentication Modules|pam-1.0.2-20.1|  
  
 **Universal Linux (Debian package) Debian, Ubuntu Server**  
  
|Required package|Description|Minimum version|  
|----------------------|-----------------|---------------------|  
|libc6|C Standard shared library|2.3.6|  
|OpenSSL|OpenSSL Libraries; Secure Network Communications Protocol|0.9.8 or 1.0|  
|PAM|Pluggable Authentication Modules|0.79-3|  
  
 **Universal Linux (RPM package) CentOS, Oracle Linux**  
  
|Required package|Description|Minimum version|  
|----------------------|-----------------|---------------------|  
|glibc|C Standard shared library|2.5-12|  
|OpenSSL|OpenSSL Libraries; Secure Network Communications Protocol|0.9.8 or 1.0|  
|PAM|Pluggable Authentication Modules|0.99.6.2-3.14|  
  
 **IBM AIX 5L 5.3**  
  
|Required package|Description|Minimum version|  
|----------------------|-----------------|---------------------|  
|OS version|Version of the operating system|AIX 5.3, Technology Level 6, Service Pack 5|  
|xlC.rte|XL C/C++ Runtime|9.0.0.2|  
|openssl.base|OpenSSL Libraries; Secure Network Communications Protocol|0.9.8.4|  
  
 **IBM AIX 6.1**  
  
|Required package|Description|Minimum version|  
|----------------------|-----------------|---------------------|  
|OS version|Version of operating system|AIX 6.1, any Technology Level and Service Pack|  
|xlC.rte|XL C/C++ Runtime|9.0.0.5|  
|OpenSSL/openssl.base|OpenSSL Libraries; Secure Network Communications Protocol|0.9.8.4|  
  
 **IBM AIX 7.1 (Power)**  
  
|Required package|Description|Minimum version|  
|----------------------|-----------------|---------------------|  
|OS version|Version of operating system|AIX 7.1, any Technology Level and Service Pack|  
|xlC.rte|XL C/C++ Runtime||  
|OpenSSL/openssl.base|OpenSSL Libraries; Secure Network Communications Protocol||  
  
 **HP-UX 11i v2 IA 64**  
  
|Required package|Description|Minimum version|  
|----------------------|-----------------|---------------------|  
|HPUXBaseOS|Base OS|B.11.23|  
|HPUXBaseAux|HP-UX Base OS Auxiliary|B.11.23.0706|  
|HPUXBaseAux.openssl|OpenSSL Libraries; Secure Network Communications Protocol|A.00.09.07l.003|  
|PAM|Pluggable Authentication Modules|On HP-UX, PAM is part of the core operating system components. There are no other dependencies.|  
  
 **HP-UX 11i v2 PA-RISC**  
  
|Required package|Description|Minimum version|  
|----------------------|-----------------|---------------------|  
|HPUX11i-OE|HP-UX Foundation Operating Environment|B.11.23.0706|  
|OS-Core.MinimumRuntime.CORE-SHLIBS|Compatible development tools libraries|B.11.23|  
|HPUXBaseAux|HP-UX Base OS Auxiliary|B.11.23.0706|  
|HPUXBaseAux.openssl|OpenSSL Libraries; Secure Network Communications Protocol|A.00.09.071.003|  
|PAM|Pluggable Authentication Modules|On HP-UX, PAM is part of the core operating system components. There are no other dependencies.|  
  
 **HP-UX 11i v3 PA-RISC**  
  
|Required package|Description|Minimum version|  
|----------------------|-----------------|---------------------|  
|HPUX11i-OE|HP-UX Foundation Operating Environment|B.11.31.0709|  
|OS-Core.MinimumRuntime.CORE2-SHLIBS|Specific IA emulator libraries|B.11.31|  
|openssl/Openssl.openssl|OpenSSL Libraries; Secure Network Communications Protocol|A.00.09.08d.002|  
|PAM|Pluggable Authentication Modules|On HP-UX, PAM is part of the core operating system components. There are no other dependencies.|  
  
 **HP-UX 11i v3 IA64**  
  
|Required package|Description|Minimum version|  
|----------------------|-----------------|---------------------|  
|HPUX11i-OE|HP-UX Foundation Operating Environment|B.11.31.0709|  
|OS-Core.MinimumRuntime.CORE-SHLIBS|Specific IA development libraries|B.11.31|  
|SysMgmtMin|Minimum Software Deployment Tools|B.11.31.0709|  
|SysMgmtMin.openssl|OpenSSL Libraries; Secure Network Communications Protocol|A.00.09.08d.002|  
|PAM|Pluggable Authentication Modules|On HP-UX, PAM is part of the core operating system components. There are no other dependencies.|  
  
 **[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Dependencies:** The following table lists site system roles that support Linux and UNIX clients. For more information about these site system roles, see [Determine the site system roles for System Center Configuration Manager clients](../System Center Configuration Manager/Determine-the-site-system-roles-for-System-Center-Configuration-Manager-clients.md).  
  
|[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site system|More information|  
|---------------------------------------|----------------------|  
|Management point|Although a management point is not required to install a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client for Linux and UNIX, you must have a management point to transfer information between client computers and [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] servers. Without a management point, you cannot manage client computers.|  
|Distribution point|The distribution point is not required to install a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client for Linux and UNIX. However, the site system role is required if you deploy software to Linux and UNIX servers.<br /><br /> Because the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client for Linux and UNIX does not support communications that use SMB, the distribution points you use with the client must support HTTP or HTTPS communication.|  
|Fallback status point|The fallback status point is not required to install a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client for Linux and UNIX. However, The fallback status point enables computers in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site to send state messages when they cannot communicate with a management point. Client can also send their installation status to the fallback status point.|  
  
 **Firewall Requirements**: Ensure that firewalls do not block communications across the ports you specify as client request ports. The client for Linux and UNIX communicates directly with management points, distribution points, and fallback status points.  
  
 For information about client communication and request ports, see  [Configure the Client for Linux and UNIX to Locate Management Points](../System Center Configuration Manager/How-to-deploy-clients-to-UNIX-and-Linux-servers-in-System-Center-Configuration-Manager.md#BKMK_ConfigClientMP).  
  
##  <a name="BKMK_PlanningforCommunicationsforLnU"></a> Planning for Communication across Forest Trusts for Linux and UNIX Servers  
 Linux and UNIX servers you manage with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] operate as workgroup clients and require similar configurations as Windows-based clients that are in a workgroup. For information about communications from computers that are in workgroups, see the [Communications across Active Directory forests](../System Center Configuration Manager/Communications-between-endpoints-in-System-Center-Configuration-Manager.md#Plan_Com_X-Forest) section in the [Communications between endpoints in System Center Configuration Manager](../System Center Configuration Manager/Communications-between-endpoints-in-System-Center-Configuration-Manager.md) topic.  
  
###  <a name="BKMK_ServiceLocationforLnU"></a> Service Location by the client for Linux and UNIX  
 The task of locating a site system server that provides service to clients is referred to as service location. Unlike a Windows-based client, the client for Linux and UNIX does not use Active Directory for service location. Additionally, the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client for Linux and UNIX does not support a client property that specifies the domain suffix of a management point. Instead, the client learns about additional site system servers that provide services to clients from a known management point you assign when you install the client software.  
  
 For more information about service location, see the [Service Location and how clients determine their assigned management point](../System Center Configuration Manager/Understand-how-clients-find-site-resources-and-services-for-System-Center-Configuration-Manager.md#BKMK_Plan_Service_Location) section in the [Understand how clients find site resources and services for System Center Configuration Manager](../System Center Configuration Manager/Understand-how-clients-find-site-resources-and-services-for-System-Center-Configuration-Manager.md) topic.  
  
##  <a name="BKMK_SecurityforLnU"></a> Planning for Security and Certificates for Linux and UNIX Servers  
 For secure and authenticated communications with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] sites, the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client for Linux and UNIX uses the same model for communication as the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client for Windows.  
  
 When you install the Linux and UNIX client, you can assign the client a PKI certificate that enables it to use HTTPS to communicate with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] sites. If you do not assign a PKI certificate, the client creates a self-signed certificate and communicates only by HTTP.  
  
 Clients that are provided a PKI certificate when they install use HTTPS to communicate with management points. When a client is unable to locate a management point that supports HTTPS, it will fall back to use HTTP with the provided PKI certificate.  
  
 When a Linux or UNIX client uses a PKI certificate you do not have to approve them. When a client uses a self-signed certificate, review the hierarchy settings for client approval in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. If the client approval method is not **Automatically approve all computers (not recommended)**, you must manually approve the client.  
  
 For more information about how to manually approve the client, see the [Manage Clients from the Devices Node](../System Center Configuration Manager/How-to-manage-clients-in-System-Center-Configuration-Manager.md#BKMK_ManagingClients_DevicesNode) section in the [How to manage clients in System Center Configuration Manager](../System Center Configuration Manager/How-to-manage-clients-in-System-Center-Configuration-Manager.md) topic.  
  
 For information about how to use certificates in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [PKI certificate requirements for System Center Configuration Manager](../System Center Configuration Manager/PKI-certificate-requirements-for-System-Center-Configuration-Manager.md).  
  
###  <a name="BKMK_AboutCertsforLnU"></a> About Certificates for use by Linux and UNIX Servers  
 The [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client for Linux and UNIX uses a self-signed certificate or an X.509 PKI certificate just like Windows-based clients. There are no changes to the PKI requirements for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site systems when you manage Linux and UNIX clients.  
  
 The certificates you use for Linux and UNIX clients that communicate to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site systems must be in a Public Key Certificate Standard (PKCS#12) format, and the password must be known so you can specify it to the client when you specify the PKI certificate.  
  
 The [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client for Linux and UNIX supports a single PKI certificate, and does not support multiple certificates. Therefore, the certificate selection criteria you configure for a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site does not apply.  
  
###  <a name="BKMK_ConfigCertsforLnU"></a> Configuring Certificates for Linux and UNIX Servers  
 To configure a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client for Linux and UNIX servers to use HTTPS communications, you must configure the client to use a PKI certificate at the time you install the client. You cannot provision a certificate prior to installation of the client software.  
  
 When you install a client that uses a PKI certificate, you use the command-line parameter **-UsePKICert** to specify the location and name of a PKCS#12 file that contains the PKI certificate. Additionally you must use the command line parameter **-certpw** to specify the password for the certificate.  
  
 If you do not specify **-UsePKICert**, the client generates a self-signed certificate and attempts to communicate to site system servers by using HTTP only.  
  
##  <a name="BKMK_NoSHA-256"></a> About Linux and UNIX Operating Systems That do not Support SHA-256  
 The following Linux and UNIX operating systems that are supported as clients for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] were released with versions of OpenSSL that do not support SHA-256:  
  
-   Red Hat Enterprise Linux Version 4 (x86/x64)  
  
-   Solaris Version 9 (SPARC) and Solaris Version 10 (SPARC/x86)  
  
-   SUSE Linux Enterprise Server Version 9 (x86)  
  
-   HP-UX Version 11iv2 (PA-RISH/IA64)  
  
 To manage these operating systems with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], you must install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client for Linux and UNIX with a command line switch that directs the client to skip validation of SHA-256. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients that run on these operating system versions operate in a less secure mode than clients that support SHA-256. This less secure mode of operation has the following behavior:  
  
-   Clients do not validate the site server signature associated with policy they request from a management point.  
  
-   Clients do not validate the hash for packages that they download from a distribution point.  
  
> [!IMPORTANT]  
>  The **ignoreSHA256validation** option allows you to run the client for Linux and UNIX computers in a less secure mode. This is intended for use on older platforms that did not include support for SHA-256. This is a security override and is not recommended by Microsoft, but is supported for use in a secure and trusted datacenter environment.  
  
 When the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client for Linux and UNIX installs, the install script checks the operating system version. By default, if the operating system version is identified as having released without a version of OpenSSL that supports SHA-256, the installation of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client fails.  
  
 To install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client on Linux and UNIX operating systems that did not release with a version of OpenSSL that supports SHA-256, you must use the install command line switch **ignoreSHA256validation**. When you use this command line option on an applicable Linux or UNIX operating system, the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client will skip SHA-256 validation and after installation, the client will not use SHA-256 to sign data it submits to site systems by using HTTP. For information about configuring Linux and UNIX clients to use certificates, see [Planning for Security and Certificates for Linux and UNIX Servers](#BKMK_SecurityforLnU) in this topic. For information about requiring SHA-256, see the [Configure Signing and Encryption](../System Center Configuration Manager/Configure-security-in-System-Center-Configuration-Manager.md#BKMK_ConfigureSigningEncryption) section in the [Configure security in System Center Configuration Manager](../System Center Configuration Manager/Configure-security-in-System-Center-Configuration-Manager.md) topic.  
  
> [!NOTE]  
>  The command line option **ignoreSHA256validation** is ignored on computers that run a version of Linux and UNIX that released with versions of OpenSSL that support SHA-256.  
  
## See Also  
 [Planning considerations for deploying clients in System Center Configuration Manager](../System Center Configuration Manager/Planning-considerations-for-deploying-clients-in-System-Center-Configuration-Manager.md)