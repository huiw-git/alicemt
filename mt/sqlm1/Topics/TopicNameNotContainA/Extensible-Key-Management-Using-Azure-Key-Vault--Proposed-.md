---
title: Extensible Key Management Using Azure Key Vault (Proposed)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b5e186f-2e4f-4b0c-972d-ce1d6ba034ec
---
# Extensible Key Management Using Azure Key Vault (Proposed)
  The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Connector for [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Azure Key Vault enables [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] encryption to use the Azure Key Vault service as an [Extensible Key Management &#40;EKM&#41;](../Topic/Extensible%20Key%20Management%20\(EKM\).md) provider to protect [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] encryption keys.  
  
 This topic describes the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] connector. Additional information is available in [Setup Steps for Extensible Key Management Using the Azure Key Vault](../../Topics\TopicNameNotContainA/Setup-Steps-for-Extensible-Key-Management-Using-the-Azure-Key-Vault.md), [Use SQL Server Connector with SQL Encryption Features](../../Topics\TopicNameNotContainA/Use-SQL-Server-Connector-with-SQL-Encryption-Features.md), and [SQL Server Connector, Appendix](../../Topics\TopicNameNotContainA/SQL-Server-Connector,-Appendix.md).  
  
##  <a name="Uses"></a> What is Extensible Key Management \(EKM\) & Why Use it?  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides several types of encryption that help protect sensitive data, including [Transparent Data Encryption &#40;TDE&#41;](../Topic/Transparent%20Data%20Encryption%20\(TDE\).md), [Column Level Encryption](../Topic/Cryptographic%20Functions%20\(Transact-SQL\).md) \(CLE\), and [Backup Encryption](../../Topics\TopicNameNotContainA/Backup-Encryption.md). In all of these cases the data is encrypted using a symmetric data encryption key \(DEK\). The symmetric data encryption key is further protected by encrypting it with a hierarchy of keys stored in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. The following image represents how the traditional service\-manage key hierarchy works.  
  
 ![ekm-key-hierarchy-traditional](../../Images\Image\ImageNotContaina/ekm-key-hierarchy-traditional.png "ekm-key-hierarchy-traditional")  
  
 Instead of this model, the alternative is the EKM Provider Model. Using the EKM provider architecture enables [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to protect the data encryption keys by using an asymmetric key stored outside of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in an external cryptographic provider. This model adds an additional layer of security and separates the management of keys and data.  
  
 The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Connector serves as a bridge between [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and Azure Key Vault, so [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] can leverage the scalability, high performance, and highly availability of the Azure Key Vault service. The following image represents how the key hierarchy works in the EKM provider architecture with Azure Key Vault and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Connector.  
  
 ![ekm-key-hierarchy-with-akv](../../Images\Image\ImageNotContaina/ekm-key-hierarchy-with-akv.jpg "ekm-key-hierarchy-with-akv")  
  
 Azure Key Vault can be used with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installations on [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Azure Virtual Machines and for on\-premises servers. The key vault service also provides the option to use tightly controlled and monitored Hardware Security Modules \(HSMs\) for a higher level of protection for asymmetric encryption keys. For more information about the key vault, see [Azure Key Vault](http://go.microsoft.com/fwlink/?LinkId=521401).  
  
 The following image summarizes the process flow of EKM using the key vault. \(The process step numbers in the image are not meant to match the setup step numbers that follow the image.\)  
  
 The following image summarizes the process flow of EKM using the key vault. The process step numbers in the image are not meant to match the setup step numbers that follow the image.  
  
 ![SQL Server EKM using the Azure Key Vault](../../Images\Image\ImageNotContaina/EKM_using_Azure_Key_Vault.png "EKM_using_Azure_Key_Vault")  
  
 For the next step, see [Setup Steps for Extensible Key Management Using the Azure Key Vault](../../Topics\TopicNameNotContainA/Setup-Steps-for-Extensible-Key-Management-Using-the-Azure-Key-Vault.md).  
  
 For use scenarios, see [Use SQL Server Connector with SQL Encryption Features](../../Topics\TopicNameNotContainA/Use-SQL-Server-Connector-with-SQL-Encryption-Features.md).  
  
## See Also  
 [SQL Server Connector, Appendix](../../Topics\TopicNameNotContainA/SQL-Server-Connector,-Appendix.md)  
  
  