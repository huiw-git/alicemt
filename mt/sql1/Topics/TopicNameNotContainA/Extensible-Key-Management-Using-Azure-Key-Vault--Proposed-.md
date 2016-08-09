---
title: "Extensible Key Management Using Azure Key Vault (Proposed)"
ms.custom: na
ms.date: 2016-05-02
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b5e186f-2e4f-4b0c-972d-ce1d6ba034ec
caps.latest.revision: 9
---
# Extensible Key Management Using Azure Key Vault (Proposed)
The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector for [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Azure Key Vault enables [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] encryption to use the Azure Key Vault service as an [Extensible Key Management (EKM)](../../Topics/TopicNameNotContainA/Extensible-Key-Management--EKM-.md) provider to protect [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] encryption keys.  
  
 This topic describes the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] connector. Additional information is available in [Setup Steps for Extensible Key Management Using the Azure Key Vault](../../Topics/TopicNameNotContainA/Setup-Steps-for-Extensible-Key-Management-Using-the-Azure-Key-Vault.md), [Use SQL Server Connector with SQL Encryption Features](../../Topics/TopicNameNotContainA/Use-SQL-Server-Connector-with-SQL-Encryption-Features.md), and [SQL Server Connector, Appendix](../../Topics/TopicNameNotContainA/SQL-Server-Connector--Appendix.md).  
  
##  <a name="Uses"></a> What is Extensible Key Management (EKM) & Why Use it?  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] provides several types of encryption that help protect sensitive data, including [Transparent Data Encryption (TDE)](../../Topics/TopicNameNotContainA/Transparent-Data-Encryption--TDE-.md), [Column Level Encryption](assetId:///0be5626b-5a25-4d8c-9f44-7abbfccf816c) (CLE), and [Backup Encryption](../../Topics/TopicNameNotContainA/Backup-Encryption.md). In all of these cases the data is encrypted using a symmetric data encryption key (DEK). The symmetric data encryption key is further protected by encrypting it with a hierarchy of keys stored in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. The following image represents how the traditional service-manage key hierarchy works.  
  
 ![ekm&#45;key&#45;hierarchy&#45;traditional](../../Topics/TopicNameNotContainA/images/ekm-key-hierarchy-traditional.png "ekm-key-hierarchy-traditional")  
  
 Instead of this model, the alternative is the EKM Provider Model. Using the EKM provider architecture enables [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to protect the data encryption keys by using an asymmetric key stored outside of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] in an external cryptographic provider. This model adds an additional layer of security and separates the management of keys and data.  
  
 The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector serves as a bridge between [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and Azure Key Vault, so [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] can leverage the scalability, high performance, and highly availability of the Azure Key Vault service. The following image represents how the key hierarchy works in the EKM provider architecture with Azure Key Vault and [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Connector.  
  
 ![ekm&#45;key&#45;hierarchy&#45;with&#45;akv](../../Topics/TopicNameNotContainA/images/ekm-key-hierarchy-with-akv.jpg "ekm-key-hierarchy-with-akv")  
  
 Azure Key Vault can be used with [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] installations on [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Azure Virtual Machines and for on-premises servers. The key vault service also provides the option to use tightly controlled and monitored Hardware Security Modules (HSMs) for a higher level of protection for asymmetric encryption keys. For more information about the key vault, see [Azure Key Vault](http://go.microsoft.com/fwlink/?LinkId=521401).  
  
 The following image summarizes the process flow of EKM using the key vault. (The process step numbers in the image are not meant to match the setup step numbers that follow the image.)  
  
 The following image summarizes the process flow of EKM using the key vault. The process step numbers in the image are not meant to match the setup step numbers that follow the image.  
  
 ![SQL Server EKM using the Azure Key Vault](../../Topics/TopicNameNotContainA/images/EKM_using_Azure_Key_Vault.png "EKM_using_Azure_Key_Vault")  
  
 For the next step, see [Setup Steps for Extensible Key Management Using the Azure Key Vault](../../Topics/TopicNameNotContainA/Setup-Steps-for-Extensible-Key-Management-Using-the-Azure-Key-Vault.md).  
  
 For use scenarios, see [Use SQL Server Connector with SQL Encryption Features](../../Topics/TopicNameNotContainA/Use-SQL-Server-Connector-with-SQL-Encryption-Features.md).  
  
## See Also  
 [SQL Server Connector, Appendix](../../Topics/TopicNameNotContainA/SQL-Server-Connector--Appendix.md)