---
title: "Unattended Installs of SQL Server R Services"
ms.custom: na
ms.date: 2016-05-31
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 77e92b2d-5777-4c31-bf02-f931ed54a247
caps.latest.revision: 13
manager: paulettm
---
# Unattended Installs of SQL Server R Services
-   You **must** install the database engine to use R Services (In-Database) in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)].  
  
-   If you are performing an offline install, you need to download the required R components first to a local folder. (Note: *nnnn* is a number representing the language identifier and will be different depending on your system language.)  
  
     [SRO_3.2.2.0_nnnn.cab](http://go.microsoft.com/fwlink/?linkid=733805)  
  
     [SRS_8.0.3.0_nnnn.cab](http://go.microsoft.com/fwlink/?linkid=735050)  
  
> [!NOTE]  
>  There is a new parameter, */IACCEPTROPENLICENSETERMS*, for accepting the license terms for using the open source R components. You must include this parameter in your command line or setup will fail.  
  
## Perform an Unattended Install of R Services (In-Database)  
 The following example shows the minimum required features to specify in the command line when performing a silent, unattended install of R Services in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)].  
  
###  <a name="bkmk_Unattended"></a>  
  
1.  For RC2 and RC3, run the following command from an elevated command prompt:  
  
    ```  
    Setup.exe /q /ACTION=Install /FEATURES=SQL,AdvancedAnalytics /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS  
    ```  
  
2.  After installation is complete, in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], run the following command to enable the feature.  
  
    ```  
    Exec sp_configure  'external scripts enabled', 1  
    Reconfigure  with  override  
  
    ```  
  
    > [!NOTE]  
    >  You must explicitly enable the engine feature; otherwise, it will not be possible to invoke R scripts even if the feature has been installed configured by setup.  
  
3.  Restart the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance. This will automatically restart the related [!INCLUDE[rsql_launchpad](../../Topics/TopicNameNotContainA/tokens/rsql_launchpad_md.md)] service as well.  
  
## See Also  
 [Troubleshooting R Services Setup](../../Topics/TopicNameNotContainA/Troubleshooting-R-Services-Setup.md)