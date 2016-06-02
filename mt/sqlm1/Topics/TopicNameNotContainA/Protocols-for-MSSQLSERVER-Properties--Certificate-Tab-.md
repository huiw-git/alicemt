---
title: Protocols for MSSQLSERVER Properties (Certificate Tab)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 776addd6-25f3-4875-9a71-064035787090
---
# Protocols for MSSQLSERVER Properties (Certificate Tab)
  Use the **Certificate** tab on the **Protocols for MSSQLSERVER Properties** dialog box to select a certificate for [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], or to view the properties of a certificate. All fields are blank until a certificate is selected.  
  
 Certificates are stored locally for the users on the computer. To load a certificate for use by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], you must be running [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager under the same user account as the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service.  
  
## Page Header  
 **View**  
 Provides access to additional details on the certificate. Not available until a certificate is selected in the **Certificate** box. For additional information on certificate details, see your [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows documentation.  
  
 **Clear**  
 Removes the selection from the **Certificate** box.  
  
 **Certificate**  
 Name of certificate as determined by security provider. Select a certificate to see the details in the properties grid.  
  
## Options  
 Expiration Date  
 The final date for the period in which the certificate is valid.  
  
 Friendly Name  
 A friendly or common name for the individual or certification authority to whom the certificate is issued.  
  
 Issued By  
 Information regarding the certification authority that issued the certificate.  
  
 Issued To  
 Information regarding the recipient of the certificate.  
  
  