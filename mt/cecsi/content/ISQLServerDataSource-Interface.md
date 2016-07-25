---
title: "ISQLServerDataSource Interface"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ba1d3242-19ca-4321-83fe-867a4f69f1d4
caps.latest.revision: 15
manager: jhubbard
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - sv-se
  - zh-cn
  - zh-tw
---
# ISQLServerDataSource Interface
  A factory to create connections to the data source represented by this object. This interface was added in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0.  
  
 **Package:** com.microsoft.sqlserver.jdbc  
  
 **Extends:** java.sql.CommonDataSource  
  
## Syntax  
  
```  
  
public interface ISQLServerDataSource  
```  
  
## Remarks  
 This interface is implemented by [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md).  
  
 This interface exposes the following [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]-specific methods:  
  
|Method|For more information, see|  
|------------|-------------------------------|  
|public String getApplicationName()|[getApplicationName](../content/getApplicationName-Method--SQLServerDataSource-.md)|  
|public String getDatabaseName()|[getDatabaseName](../content/getDatabaseName-Method--SQLServerDataSource-.md)|  
|public String getDescription()|[getDescription](../content/getDescription-Method--SQLServerDataSource-.md)|  
|public boolean getEncrypt()|[getEncrypt](../content/getEncrypt-Method--SQLServerDataSource-.md)|  
|public String getFailoverPartner()|[getFailoverPartner](../content/getFailoverPartner-Method--SQLServerDataSource-.md)|  
|public String getHostNameInCertificate()|[getHostNameInCertificate](../content/getHostNameInCertificate-Method--SQLServerDataSource-.md)|  
|public String getInstanceName()|[getInstanceName](../content/getInstanceName-Method--SQLServerDataSource-.md)|  
|public boolean getLastUpdateCount()|[getLastUpdateCount](../content/getLastUpdateCount-Method--SQLServerDataSource-.md)|  
|public int getLockTimeout()|[getLockTimeout](../content/getLockTimeout-Method--SQLServerDataSource-.md)|  
|public boolean getMultiSubnetFailover()|[getMultiSubnetFailover](../content/getMultiSubnetFailover-Method--SQLServerDataSource-.md)|  
|public int getPacketSize()|[getPacketSize](../content/getPacketSize-Method--SQLServerDataSource-.md)|  
|public int getPortNumber()|[getPortNumber](../content/getPortNumber-Method--SQLServerDataSource-.md)|  
|public String getResponseBuffering()|[getResponseBuffering](../content/getResponseBuffering-Method--SQLServerDataSource-.md)|  
|public String getSelectMethod()|[getSelectMethod](../content/getSelectMethod-Method--SQLServerDataSource-.md)|  
|public boolean getSendStringParametersAsUnicode()|[getSendStringParametersAsUnicode](../content/getSendStringParametersAsUnicode-Method--SQLServerDataSource-.md)|  
|public boolean getSendTimeAsDatetime()|[getSendTimeAsDatetime](../content/getSendTimeAsDatetime-Method--SQLServerDataSource-.md)|  
|public String getServerName()|[getServerName](../content/getServerName-Method--SQLServerDataSource-.md)|  
|public boolean getTrustServerCertificate()|[getTrustServerCertificate](../content/getTrustServerCertificate-Method--SQLServerDataSource-.md)|  
|public String getTrustStore()|[getTrustStore](../content/getTrustStore-Method--SQLServerDataSource-.md)|  
|public String getURL()|[getURL](../content/getURL-Method--SQLServerDataSource-.md)|  
|public String getUser()|[getUser](../content/getUser-Method--SQLServerDataSource-.md)|  
|public String getWorkstationID()|[getWorkstationID](../content/getWorkstationID-Method--SQLServerDataSource-.md)|  
|public boolean getXopenStates()|[getXopenStates](../content/getXopenStates-Method--SQLServerDataSource-.md)|  
|public void setApplicationName(String)|[setApplicationName](../content/setApplicationName-Method--SQLServerDataSource-.md)|  
|public void setAuthenticationSceme(String)|[setAuthenticationSceme](../content/setAuthenticationScheme--SQLServerDataSource-.md)|  
|public void setDatabaseName(String)|[setDatabaseName](../content/setDatabaseName-Method--SQLServerDataSource-.md)|  
|public void setDescription(String)|[setDescription](../content/setDescription-Method--SQLServerDataSource-.md)|  
|public void setEncrypt(boolean)|[setEncrypt](../content/setEncrypt-Method--SQLServerDataSource-.md)|  
|public void setFailoverPartner(String)|[setFailoverPartner](../content/setFailoverPartner-Method--SQLServerDataSource-.md)|  
|public void setHostNameInCertificate(String)|[setHostNameInCertificate](../content/setHostNameInCertificate-Method--SQLServerDataSource-.md)|  
|public void setInstanceName(String)|[setInstanceName](../content/setInstanceName-Method--SQLServerDataSource-.md)|  
|public void setIntegratedSecurity(boolean)|[setIntegratedSecurity](../content/setIntegratedSecurity-Method--SQLServerDataSource-.md)|  
|public void setLastUpdateCount(boolean)|[setLastUpdateCount](../content/setLastUpdateCount-Method--SQLServerDataSource-.md)|  
|public void setLockTimeout(int)|[setLockTimeout](../content/setLockTimeout-Method--SQLServerDataSource-.md)|  
|public void setMultiSubnetFailover(boolean multiSubnetFailover)|[setMultiSubnetFailover](../content/setMultiSubnetFailover-Method--SQLServerDataSource-.md)|  
|public void setPacketSize(int)|[setPacketSize](../content/setPacketSize-Method--SQLServerDataSource-.md)|  
|public void setPassword(String)|[setPassword](../content/setPassword-Method--SQLServerDataSource-.md)|  
|public void setPortNumber(int)|[setPortNumber](../content/setPortNumber-Method--SQLServerDataSource-.md)|  
|public void setResponseBuffering(String)|[setResponseBuffering](../content/setResponseBuffering-Method--SQLServerDataSource-.md)|  
|public void setSelectMethod(String)|[setSelectMethod](../content/setSelectMethod-Method--SQLServerDataSource-.md)|  
|public void setSendStringParametersAsUnicode(boolean)|[setSendStringParametersAsUnicode](../content/setSendStringParametersAsUnicode-Method--SQLServerDataSource-.md)|  
|public void setSendTimeAsDatetime(boolean)|[setSendTimeAsDatetime](../content/setSendTimeAsDatetime-Method--SQLServerDataSource-.md)|  
|public void setServerName(String)|[setServerName](../content/setServerName-Method--SQLServerDataSource-.md)|  
|public void setTrustServerCertificate(boolean)|[setTrustServerCertificate](../content/setTrustServerCertificate-Method--SQLServerDataSource-.md)|  
|public void setTrustStore(String)|[setTrustStore](../content/setTrustStore-Method--SQLServerDataSource-.md)|  
|public void setTrustStorePassword(String)|[setTrustStorePassword](../content/setTrustStorePassword-Method--SQLServerDataSource-.md)|  
|public void setURL(String url)|[setURL](../content/setURL-Method--SQLServerDataSource-.md)|  
|public void setUser(String)|[setUser](../content/setUser-Method--SQLServerDataSource-.md)|  
|public void setWorkstationID(String)|[setWorkstationID](../content/setWorkstationID-Method--SQLServerDataSource-.md)|  
|public void setXopenStates(boolean)|[setXopenStates](../content/setXopenStates-Method--SQLServerDataSource-.md)|  
  
## See Also  
 [JDBC Driver API Reference](../content/JDBC-Driver-API-Reference.md)  
  
  