---
title: "How to create certificate profiles in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-08-01
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 634d612c-92d7-4c03-873a-b2e730c9a72d
caps.latest.revision: 16
caps.handback.revision: 0
---
# How to create certificate profiles in System Center Configuration Manager
Certificate profiles in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] integrate with Active Directory Certificate Services and the Network Device Enrollment Service role to provision managed devices with authentication certificates so that users can access company resources by using certificates. The information in this topic can help you create certificate profiles in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].  
  
> [!IMPORTANT]  
>  You must perform configuration before you can create certificate profiles. For more information, see [Configuring certificate profiles in System Center Configuration Manager](../System Center Configuration Manager/Configuring-certificate-profiles-in-System-Center-Configuration-Manager.md).  
  
## Steps to Create a Certificate Profile  
 Use the following required steps to create a certificate profile by using the Create Certificate Profile Wizard.  
  
|Step|Details|More information|  
|----------|-------------|----------------------|  
|**Step 1:** Start the Create Certificate Profile Wizard|Start the wizard from the **Assets and Compliance** workspace, in the **Compliance Settings** node.|See the [Step 1: Start the Create Certificate Profile Wizard](#BKMK_Step1) section in this topic.|  
|**Step 2:** Provide general information about the certificate profile|Provide general information, such as the name and description of the certificate profile, and the type of certificate profile that you want to create.|See the [Step 2: Provide General Information About the Certificate Profile](#BKMK_Step2) section in this topic.|  
|**Step 3:** Provide information about the certificate profile|Provide configuration information for the certificate profile.|See the [Step 3: Provide Information About the Certificate Profile](#BKMK_Step3) section in this topic.|  
|**Step 4:** Configure supported platforms for the certificate profile|Specify the operating systems where you will install the certificate profile.|See the [Step 4: Configure Supported Platforms for the Certificate Profile](#BKMK_Step4) section in this topic.|  
|**Step 5:** Complete the wizard|Complete the wizard to create the new certificate profile.|See the [Step 5: Complete the Wizard](#BKMK_Step5) section in this topic.|  
  
> [!CAUTION]  
>  If you have already deployed a certificate by using a Simple Certificate Enrollment Protocol (SCEP) certificate profile, changing some configuration options will result in requesting a new certificate that has the new values. If the number of certificate request renewals is high because of these changes, those renewals can cause high CPU processing on the server that is running the Network Device Enrollment Service.  
>   
>  When the certificate request is for a client on the intranet (for example, Windows 8.1), the original certificate is deleted when a new certificate that has the new values is requested. However, when the certificate request is for a client that is managed by using the [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] connector, the original certificate is not deleted from the device and remains installed.  
>   
>  The following sections note the settings that will result in a certificate renewal request.  
  
## Supplemental Procedures to Create a New Certificate Profile  
 Use the following information when the steps in the preceding table require supplemental procedures.  
  
###  <a name="BKMK_Step1"></a> Step 1: Start the Create Certificate Profile Wizard  
 Use this procedure to start the Create Certificate Profile Wizard.  
  
##### To start the Create Certificate Profile Wizard  
  
1.  In the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] console, click **Assets and Compliance**.  
  
2.  In the **Assets and Compliance** workspace, expand **Compliance Settings**, expand **Company Resource Access**, and then click **Certificate Profiles**.  
  
3.  On the **Home** tab, in the **Create** group, click **Create Certificate Profile**.  
  
###  <a name="BKMK_Step2"></a> Step 2: Provide General Information About the Certificate Profile  
 Use this procedure to provide general information about the certificate profile.  
  
##### To provide general information about the certificate profile  
  
1.  On the **General** page of the Create Certificate Profile Wizard, specify the following information:  
  
    -   **Name**: Enter a unique name for the certificate profile. You can use a maximum of 256 characters.  
  
    -   **Description**: Provide a description that gives an overview of the certificate profile and other relevant information that helps to identify it in the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] console. You can use a maximum of 256 characters.  
  
    -   **Specify the type of certificate profile that you want to create**: Choose one of the following certificate profile types:  
  
        -   **Trusted CA certificate**: Select this certificate profile type if you want to deploy a trusted root certification authority (CA) or intermediate CA certificate to form a certificate chain of trust when the user or device must authenticate another device. For example, the device might be a Remote Authentication Dial-In User Service (RADIUS) server or a virtual private network (VPN) server. You must also configure a trusted CA certificate profile before you can create a SCEP certificate profile. In this case, the trusted CA certificate must be the trusted root certificate for the CA that will issue the certificate to the user or device.  
  
        -   **Simple Certificate Enrollment Protocol (SCEP) settings**: Select this certificate profile type if you want to request a certificate for a user or device, by using the Simple Certificate Enrollment Protocol and the Network Device Enrollment Service role service.  
  
###  <a name="BKMK_Step3"></a> Step 3: Provide Information About the Certificate Profile  
 Use one of the following procedures to configure certificate profile information for trusted CA certificates and SCEP certificates in the certificate profile.  
  
> [!IMPORTANT]  
>  You must configure at least one trusted CA certificate profile before you can create a SCEP certificate profile.  
  
##### To configure a trusted CA certificate  
  
1.  On the **Trusted CA Certificate** page of the Create Certificate Profile Wizard, specify the following information:  
  
    -   **Certificate file**: Click **Import** and then browse to the certificate file that you want to use.  
  
    -   **Destination store**: For devices that have more than one certificate store, select where to store the certificate. For devices that have only one store, this setting is ignored.  
  
2.  Use the **Certificate thumbprint** value to verify that you have imported the correct certificate.  
  
 Continue to [Step 4: Configure Supported Platforms for the Certificate Profile](#BKMK_Step4).  
  
##### To configure SCEP certificate information  
  
1.  On the **SCEP Servers** page of the Create Certificate Profile Wizard, specify the URLs for the NDES Servers that will issue certificates via SCEP. You can choose to automatically assign an NDES URL based on the configuration of the Certificate Registration Point site system server, or add URLs manually.  
  
2.  On the **SCEP Enrollment** page of the Create Certificate Profile Wizard, specify the following information:  
  
    -   **Retries**: Specify the number of times that the device automatically retries the certificate request to the server that is running the Network Device Enrollment Service. This setting supports the scenario where a CA manager must approve a certificate request before it is accepted. This setting is typically used for high-security environments or if you have a stand-alone issuing CA rather than an enterprise CA. You might also use this setting for testing purposes so that you can inspect the certificate request options before the issuing CA processes the certificate request. Use this setting with the **Retry delay (minutes)** setting.  
  
    -   **Retry delay (minutes)**: Specify the interval, in minutes, between each enrollment attempt when you use CA manager approval before the issuing CA processes the certificate request. If you use manager approval for testing purposes, you will probably want to specify a low value so that you are not waiting a long time for the device to retry the certificate request after you approve the request. However, if you use manager approval on a production network, you will probably want to specify a higher value to allow sufficient time for the CA administrator to check and approve or deny pending approvals.  
  
    -   **Renewal threshold (%)**: Specify the percentage of the certificate lifetime that remains before the device requests renewal of the certificate.  
  
    -   **Key Storage Provider (KSP)**: Specify where the key to the certificate will be stored. Choose from one of the following values:  
  
        -   **Install to Trusted Platform Module (TPM) if present**: Installs the key to the TPM. If the TPM is not present, the key will be installed to the storage provider for the software key.  
  
        -   **Install to Trusted Platform Module (TPM) otherwise fail**: Installs the key to the TPM. If the TPM module is not present, the installation will fail.  
  
        -   **Install to Windows Hello for Business otherwise fail**: This option is available for Windows 10 Desktop and Mobile devices. It  enrolls the key to **Windows Hello for Business**, described in [Windows Hello for Business settings in System Center Configuration Manager](../System Center Configuration Manager/Windows-Hello-for-Business-settings-in-System-Center-Configuration-Manager.md). This option also enables you to **Require multi-factor authentication** during enrollment of devices before issuing certificates to those devices. See [Protect Windows devices with multi-factor authentication](https://technet.microsoft.com/library/dn889751.aspx) for more information.
        > [!NOTE]  
        > When a user creates a Passport PIN, Windows sends a notification which Configuration Manager listens for. This allows Configuration Manager to quickly become aware of which users have created a Passport PIN. Configuration Manager can then also issue new certificates to those users if Passport is used as the Key Storage Provider in a certificate profile.  
  
        -   **Install to Software Key Storage Provider**: Installs the key to the storage provider for the software key.  
  
        > [!NOTE]  
        >  If you change this value after the certificate is deployed, the old certificate is deleted and a new certificate is requested.  
  
    -   **Devices for certificate enrollment**: If the certificate profile is deployed to a user collection, select whether to allow certificate enrollment on only the user's primary device or on all devices that the user logs on to. If the certificate profile is deployed to a device collection, select whether to allow certificate enrollment for only the primary user of the device or for all users that log on to the device.  
  
3.  On the **Certificate Properties** page of the Create Certificate Profile Wizard, specify the following information:  
  
    -   **Certificate template name**: Click **Browse** to select the name of a certificate template that the Network Device Enrollment Service is configured to use and that has been added to an issuing CA. To successfully browse to certificate templates, the user account that you are using to run the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] console must have Read permission to the certificate template. Alternatively, if you cannot use **Browse**, type the name of the certificate template.  
  
        > [!IMPORTANT]  
        >  If the certificate template name contains non-ASCII characters (for example, characters from the Chinese alphabet), the certificate will not be deployed. To ensure that the certificate is deployed, you must first create a copy of the certificate template on the CA and rename the copy by using ASCII characters.  
  
         Note the following, depending on whether you browse to the certificate template or type the certificate name:  
  
        -   If you browse to select the name of the certificate template, some fields on the page are automatically populated from the certificate template. In some cases, you cannot change these values unless you choose a different certificate template.  
  
        -   If you type the name of the certificate template, make sure that the name exactly matches one of the certificate templates that are listed in the registry of the server that is running the Network Device Enrollment Service. Make sure that you specify the name of the certificate template and not the display name of the certificate template.  
  
             To find the names of certificate templates, browse to the following key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP. You will see the certificate templates listed as the values for **EncryptionTemplate**, **GeneralPurposeTemplate**, and **SignatureTemplate**. By default, the value for all three certificate templates is **IPSECIntermediateOffline**, which maps to the template display name of **IPSec (Offline request)**.  
  
            > [!WARNING]  
            >  Because [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] cannot verify the contents of the certificate template when you type the name of the certificate template rather than browse, you might be able to select options that the certificate template does not support and that will result in a failed certificate request. When this happens, you will see an error message for w3wp.exe in the CPR.log file that the template name in the certificate signing request (CSR) and the challenge do not match.  
            >   
            >  When you type the name of the certificate template that is specified for the **GeneralPurposeTemplate** value, you must select the **Key encipherment** and the **Digital signature** options for this certificate profile. However, if you want to enable only the **Key encipherment** option in this certificate profile, specify the certificate template name for the **EncryptionTemplate** key. Similarly, if you want to enable only the **Digital signature** option in this certificate profile, specify the certificate template name for the **SignatureTemplate** key.  
  
        > [!NOTE]  
        >  If you change this value after the certificate is deployed, the old certificate is deleted and a new certificate is requested.  
  
    -   **Certificate type**: Select whether the certificate will be deployed to a device or a user.  
  
        > [!NOTE]  
        >  If you change this value after the certificate is deployed, the old certificate is deleted and a new certificate is requested.  
  
    -   **Subject name format**: From the list, select how [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] automatically creates the subject name in the certificate request. If the certificate is for a user, you can also include the user's email address in the subject name.  
  
        > [!NOTE]  
        >  If you change this value after the certificate is deployed, the old certificate is deleted and a new certificate is requested.  
  
    -   **Subject alternative name**: Specify how [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] automatically creates the values for the subject alternative name (SAN) in the certificate request. For example, if you selected a user certificate type, you can include the user principal name (UPN) in the subject alternative name.  
  
        > [!TIP]  
        >  If the client certificate will be used to authenticate to a Network Policy Server, you must set the subject alternative name to the UPN.  
  
        > [!NOTE]  
        >  If you change this value after the certificate is deployed, the old certificate is deleted and a new certificate is requested.  
  
        > [!IMPORTANT]  
        >  iOS devices support limited subject name formats and subject alternative names in SCEP certificates. If you specify a format that is not supported, certificates will not be enrolled on iOS devices. When you configure a SCEP certificate profile to be deployed to iOS devices, use the **Common name** for the **Subject name format**, and **DNS name**, **Email address** or **UPN** for the **Subject alternative name**.  
  
    -   **Certificate validity period**: If you have run the certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE command on the issuing CA, which allows a custom validity period, you can specify the amount of remaining time before the certificate expires. For more information about this command, see [Step 1: Install and Configure the Network Device Enrollment Service and Dependencies](../System Center Configuration Manager/Configuring-certificate-profiles-in-System-Center-Configuration-Manager.md#BKMK_Step1) in the [Configuring certificate profiles in System Center Configuration Manager](../System Center Configuration Manager/Configuring-certificate-profiles-in-System-Center-Configuration-Manager.md) topic.  
  
         You can specify a value that is lower than the validity period in the specified certificate template, but not higher. For example, if the certificate validity period in the certificate template is two years, you can specify a value of one year but not a value of five years. The value must also be lower than the remaining validity period of the issuing CA’s certificate.  
  
        > [!NOTE]  
        >  If you change this value after the certificate is deployed, the old certificate is deleted and a new certificate is requested.  
  
    -   **Key usage**: Specify key usage options for the certificate. You can choose from the following options:  
  
        -   **Key encipherment**: Allow key exchange only when the key is encrypted.  
  
        -   **Digital signature**: Allow key exchange only when a digital signature helps protect the key.  
  
             If you selected a certificate template by using **Browse**, you might not be able to change these settings unless you select a different certificate template.  
  
         The certificate template you selected must be configured with one or both of the two key usage options above. If it is not, you will see the message **Key usage in CSR and challenge do not match** in the certificate registration point log file, **Crp.log**.  
  
        > [!NOTE]  
        >  If you change this value after the certificate is deployed, the old certificate is deleted and a new certificate is requested.  
  
    -   **Key size (bits)**: Select the size of the key in bits.  
  
        > [!NOTE]  
        >  If you change this value after the certificate is deployed, the old certificate is deleted and a new certificate is requested.  
  
    -   **Extended key usage**: Click **Select** to add values for the certificate’s intended purpose. In most cases, the certificate will require **Client Authentication** so that the user or device can authenticate to a server. However, you can add any other key usages as required.  
  
        > [!NOTE]  
        >  If you change this value after the certificate is deployed, the old certificate is deleted and a new certificate is requested.  
  
    -   **Hash algorithm**: Select one of the available hash algorithm types to use with this certificate. Select the strongest level of security that the connecting devices support.  
  
        > [!NOTE]  
        >  **SHA-2** supports SHA-256, SHA-384, and SHA-512. **SHA-3** supports only SHA-3.  
  
    -   **Root CA certificate**: Click **Select** to choose a root CA certificate profile that you have previously configured and deployed to the user or device. This CA certificate must be the root certificate for the CA that will issue the certificate that you are configuring in this certificate profile.  
  
        > [!IMPORTANT]  
        >  If you specify a root CA certificate that is not deployed to the user or device, [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] will not initiate the certificate request that you are configuring in this certificate profile.  
  
        > [!NOTE]  
        >  If you change this value after the certificate is deployed, the old certificate is deleted and a new certificate is requested.  
  
###  <a name="BKMK_Step4"></a> Step 4: Configure Supported Platforms for the Certificate Profile  
 Use the following procedure to specify the operating systems where you will install the certificate profile.  
  
##### To specify supported platforms for the certificate profile  
  
-   On the **Supported Platforms** page of the Create Certificate Profile Wizard, select the operating systems where you want to install the certificate profile. Or, click **Select all** to install the certificate profile to all available operating systems.  
  
###  <a name="BKMK_Step5"></a> Step 5: Complete the Wizard  
 On the **Summary** page of the wizard, review the actions that will be taken, and then complete the wizard. The new certificate profile appears in the **Certificate Profiles** node in the **Assets and Compliance** workspace and is ready to be deployed to users or devices. For more information, see [How to deploy certificate profiles in System Center Configuration Manager](../System Center Configuration Manager/How-to-deploy-certificate-profiles-in-System-Center-Configuration-Manager.md).  
  
## See Also  
 [Operations and maintenance for certificate profiles in System Center Configuration Manager](../System Center Configuration Manager/Operations-and-maintenance-for-certificate-profiles-in-System-Center-Configuration-Manager.md)