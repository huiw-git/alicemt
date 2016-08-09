---
title: "Set Up  a Data Science Client"
ms.custom: na
ms.date: 2016-04-01
ms.prod: r-server
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d15ee956-918f-40e0-b986-2bf929ef303a
caps.latest.revision: 9
manager: paulettm
---
# Set Up  a Data Science Client
After you have configured an instance of [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] to use as an R server by installing **R Services (In-Database)**, you'll want to set up an R development environment that is capable of connecting to the server for remote execution and deployment.  
  
 You can do this by running [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] setup and installing the shared components for **Microsoft R Server (Standalone)**. This includes a collection of enhanced R packages and connectivity tools that can be used to develop data science solutions using R.  
  
##  <a name="bkmk_installRServicesInDatabase"></a> Install Data Science Components  
  
1.  Run [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] setup.  
  
2.  On the **Installation** tab, click **New R Server (Standalone) installation** .  
  
     ![Setup option for R Server Standalone](../../Topics/TopicNameContainA/images/rsql_RStandaloneSetup.png "rsql_RStandaloneSetup")  
  
3.  On the **Feature Selection** page, the following option should be already selected:  
  
    -   **R Server (Standalone)**  
  
         This  option installs shared features, including open source R tools and base packages, and the enhanced R packages and connectivity tools provided by Microsoft R Services.  
  
     All other options should be ignored.  
  
4.  Accept the license terms for downloading and installing Microsoft R Open, which include a distribution of the open source R base packages and tools, together with enhanced R packages and connectivity providers from Revolution Analytics.  
  
     If the computer you are using does not have Internet access, you can download the installers separately as described here: [Installing R Components without Internet Access](../../Topics/TopicNameNotContainA/Installing-R-Components-without-Internet-Access.md)  
  
    > [!TIP]  
    >  Installation of these components (and any prerequisites they might require) might take a while.  
  
5.  On the **Ready to Install** page, verify your selections. Click **Install**  
  
6.  When setup is complete, optionally, install an R development environment, such as RStudio or [!INCLUDE[rsql_rtvs](../../Topics/TopicNameContainA/tokens/rsql_rtvs_md.md)].  
  
     Note that if you install [!INCLUDE[rsql_rtvs](../../Topics/TopicNameContainA/tokens/rsql_rtvs_md.md)], in some cases the add-in will not recognize that the R runtime is installed and will offer to download and install another version of R, such as the 64 bit editions of R 3.2.1, 3.2.2 and 3.2.3 (CRAN R distributions), or the Microsoft R distributions (Microsoft R Open, Revolution R Open).  
  
     It is important that you do NOT use the provided links to install a different version of R.  
    Instead, use one of the following options to register the currently installed version of the R runtime:  
  
    -   Run the R utility, RSetReg, and locate the locally installed R runtime version.  
  
    -   Manually create the following registry key:  
  
        ```  
        [HKEY_LOCAL_MACHINE\SOFTWARE\R-core\R\3.2.2.802 Microsoft R Server] "installPath"="<INSTALLATION_FOLDER>"  
        ```  
  
 For a complete walkthrough of how to connect to a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance for remote execution of R code, see this tutorial: [Data Science Deep Dive: Using the RevoScaleR Packages](assetId:///c2efb3f2-cad5-4188-b889-15d68b742ef5).  
  
## See Also  
 [Set up SQL Server R Services (In-Database)](../../Topics/TopicNameNotContainA/Set-up-SQL-Server-R-Services--In-Database-.md)