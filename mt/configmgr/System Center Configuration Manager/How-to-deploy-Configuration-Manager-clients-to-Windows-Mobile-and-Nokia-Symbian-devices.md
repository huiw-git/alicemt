---
title: "How to deploy Configuration Manager clients to Windows Mobile and Nokia Symbian devices"
ms.custom: na
ms.date: 08/22/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 354e2d41-d718-4268-9537-c1043f38fcbb
caps.latest.revision: 4
---
# How to deploy Configuration Manager clients to Windows Mobile and Nokia Symbian devices
> [!IMPORTANT]  
>  The information in this topic does not apply to mobile devices that are managed by [!INCLUDE[wit_firstref](../System Center Configuration Manager/itokens/wit_firstref_md.md)]. For information about how to get your mobile devices managed by [!INCLUDE[wit_firstref](../System Center Configuration Manager/itokens/wit_firstref_md.md)], see [Manage mobile devices with Microsoft Intune](https://technet.microsoft.com/en-US/library/dn646962.aspx).  
  
 When you enroll mobile devices by using [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)], this action installs the [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] client to provide management capabilities that include hardware inventory, software deployment for required applications, settings, and remote wipe.  
  
 Mobile device clients are automatically assigned to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site that enrolls them. These mobile device clients install as Internet-only clients, which means that they will communicate with the site system roles (management points and distribution points) in their assigned site when you configure these site system roles to allow client connections from the Internet. They do not communicate with site system roles outside their assigned site.  
  
 To enroll these mobile devices, you must use Microsoft Certificate Services with an enterprise certification authority (CA) and the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] enrollment point and enrollment proxy point site system roles. During and after enrollment, public key infrastructure (PKI) certificates secure the communication between the mobile device and the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site. When the certificate on the mobile device is due for renewal, users are automatically prompted to renew their certificate. When they confirm the prompt, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] automatically re-enrolls their mobile device.  
  
> [!NOTE]  
>  If you no longer want a mobile device to be enrolled for [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)], you must wipe the mobile device. You can also block the client from communicating with the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy. If you remove the enrollment site system roles, any mobile devices that were enrolled continue to be managed by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], unless they are wiped.  
  
 Use the following steps and the supplemental procedures to install the client and enroll mobile devices in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. After you complete these steps, you can monitor the mobile devices that are enrolled by viewing the collections that display mobile devices, and by using the reports for mobile devices.  
  
 To manage the settings for these mobile devices, create mobile device configuration items and deploy them in a configuration baseline. For more information, see [How to Create Mobile Device Configuration Items for Compliance Settings in Configuration Manager 2012](assetId:///ac8f5bc8-d9e1-487a-9b30-b0b1ad96ee4a).  
  
## Steps to Install the Client and Enroll Mobile Devices  
 Use the following table for the steps, details, and more information about how to install the client and enroll mobile devices.  
  
> [!IMPORTANT]  
>  Before you perform these steps, make sure that you have all the prerequisites to install and enroll clients on mobile devices. For more information, see [Prerequisites for Client Deployment in Configuration Manager](assetId:///3337610a-a720-4276-a090-4667e9765701).  
  
|Steps|Details|More information|  
|-----------|-------------|----------------------|  
|**Step 1:** Deploy a web server certificate to site system servers.|Deploy a web server certificate to the computers that host the following site system roles:<br /><br /> -   Management point<br />-   Distribution point<br />-   Enrollment point<br />-   Enrollment proxy point<br /><br /> Additionally, if you want to allow users to wipe their own mobile devices, configure Internet Information Services (IIS) with a web server certificate on the computers that host the Application Catalog website point and the Application Catalog web service point. **Important:**  The web server certificate must contain the Internet FQDN that is specified in the site system properties.|For information about the certificate requirements, see [PKI Certificate Requirements for Configuration Manager 2012](assetId:///19dedcfb-fb97-4c43-b777-e2701e935be7).<br /><br /> For an example deployment that creates and installs this web server certificate, see the [Deploying the Web Server Certificate for Site Systems that Run IIS](assetId:///230dfec0-bddb-4429-a5db-30020e881f1e#BKMK_webserver2008_cm2012) section in the [Step-by-Step Example Deployment of the PKI Certificates for Configuration Manager: Windows Server 2008 Certification Authority](assetId:///230dfec0-bddb-4429-a5db-30020e881f1e) topic. **Important:**  Make sure that you specify the Internet FQDN in the web server certificate for the management point, the distribution point, and the enrollment proxy point.|  
|**Step 2:** Deploy a client authentication certificate to site system servers.|Deploy a client authentication certificate to the following computers that host the following site system roles:<br /><br /> -   Management point<br />-   Distribution point|For information about the certificate requirements, see [PKI Certificate Requirements for Configuration Manager 2012](assetId:///19dedcfb-fb97-4c43-b777-e2701e935be7).<br /><br /> For an example deployment that creates and installs the client certificate for management points, see the [Deploying the Client Certificate for Computers](assetId:///230dfec0-bddb-4429-a5db-30020e881f1e#BKMK_client2008_cm2012) section in the [Step-by-Step Example Deployment of the PKI Certificates for Configuration Manager: Windows Server 2008 Certification Authority](assetId:///230dfec0-bddb-4429-a5db-30020e881f1e) topic.<br /><br /> For an example deployment that creates and installs the client certificate for distribution points, see the [Deploying the Client Certificate for Distribution Points](assetId:///230dfec0-bddb-4429-a5db-30020e881f1e#BKMK_clientdistributionpoint2008_cm2012) section in the [Step-by-Step Example Deployment of the PKI Certificates for Configuration Manager: Windows Server 2008 Certification Authority](assetId:///230dfec0-bddb-4429-a5db-30020e881f1e) topic.|  
|**Step 3:** Create and issue a certificate template for mobile device enrollment.|The certificate template must have Read and Enroll permissions for the users that have mobile devices to enroll.|See the [Deploying the Enrollment Certificate for Mobile Devices](assetId:///230dfec0-bddb-4429-a5db-30020e881f1e#BKMK_mobiledevices2008_cm2012) section in the [Step-by-Step Example Deployment of the PKI Certificates for Configuration Manager: Windows Server 2008 Certification Authority](assetId:///230dfec0-bddb-4429-a5db-30020e881f1e) topic.|  
|**Step 4:** Optional but recommended: Configure automatic discovery for the enrollment service.|Create a DNS alias (CNAME record) named **configmgrenroll** that references the site system server on which you will install the enrollment proxy point.|For more information about how to create a DNS alias, consult your DNS documentation.|  
|**Step 5:** Configure the management point and distribution point.|Configure management points for the following options:<br /><br /> -   HTTPS<br />-   Allow client connections from the Internet<br />-   Allow mobile devices<br /><br /> Although distribution points are not required during the enrollment process, you must configure them to allow client connections from the Internet if you want to deploy software to these mobile devices after they are enrolled by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].|See the following procedure in this topic: [Configuring Management Points and Distribution Points for Mobile Devices](assetId:///b420da33-e374-4ebe-ba9f-3cdf870c3acf#BKMK_ConfigureSiteSystemsMobileDevices).|  
|**Step 6:** Configure the enrollment proxy point and the enrollment point.|You must install both these site system roles in the same site but you do not have to install them on the same site system server, or in the same Active Directory forest.|For more information about site system role placement and considerations, see the [Planning Where to Install Sites System Roles in the Hierarchy](assetId:///64aa34e1-c465-4eb8-820b-5c1702ab55ae#Plan_Where_to_Install_Sites) section in the [Planning for Site Systems in Configuration Manager](assetId:///64aa34e1-c465-4eb8-820b-5c1702ab55ae) topic.<br /><br /> To configure the enrollment proxy point and the enrollment point, see the following procedure in this topic: [Installing and Configuring the Enrollment Site Systems](assetId:///b420da33-e374-4ebe-ba9f-3cdf870c3acf#BKMK_HowtoInstallEnrollmentSiteSystems).|  
|**Step 7:** Optional: Install the Application Catalog web service point and the Application Catalog website point.|Install the Application Catalog web service point and the Application Catalog website point if you want to allow users to wipe their own mobile devices.|For more information about how to install and configure these site system roles, see [Configuring the Application Catalog and Software Center in Configuration Manager](assetId:///0fe91772-8c48-48b0-a78c-d0cc2795495e).|  
|**Step 8:** Optional: Install the reporting services point.|Install the reporting services point if you want to run reports for mobile devices.|For more information about how to install and configure the reporting services point, see [Configuring Reporting in Configuration Manager 2012](assetId:///7fd0d4f5-14e0-4ec7-b2e6-3b67487df555).|  
|**Step 9:** Configure client settings for mobile device enrollment.|Configure the default client settings if you want all users to be able to enroll mobile devices. Or, as a best practice, configure custom client settings to restrict the users who can enroll mobile devices.<br /><br /> If required, change the default values for the client polling schedule and hardware inventory client settings.|For more information about client settings, see [About Client Settings in Configuration Manager 2012](assetId:///4acd0c29-e453-4863-8194-e479263291c8).<br /><br /> For information about how to configure these client settings, see the following procedure in this topic: [Configuring the Client Settings for Mobile Device Enrollment](assetId:///b420da33-e374-4ebe-ba9f-3cdf870c3acf#BKMK_ConfigureClientSettingMobileDevices).|  
|**Step 10:** Enroll mobile devices.|Use the web browser on the mobile device to start enrollment.|See the following procedure in this topic: [Enrolling Mobile Devices](assetId:///b420da33-e374-4ebe-ba9f-3cdf870c3acf#BKMK_EnrollMobileDevices).|  
  
## Supplemental Procedures to Install the Client and Enroll Mobile Devices  
 Use the following information when the steps in the preceding table require supplemental procedures.  
  
###  <a name="BKMK_ConfigureSiteSystemsMobileDevices"></a> Step 5: Configuring Management Points and Distribution Points for Mobile Devices  
 This procedure configures existing management points and distribution points to support mobile devices that are enrolled by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. Before you start this procedure, make sure that the site system server that runs the management point and distribution point is configured with an Internet FQDN. In addition, these site system roles must be in a primary site.  
  
##### To configure management points and distribution points for mobile devices  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, expand **Site Configuration**, select **Servers and Site System Roles**, and then select the server that hosts the site system roles to configure.  
  
3.  In the details pane, right-click **Management point**, click **Role Properties**, and in the **Management Point Properties** dialog box, configure the following options, and then click **OK**:  
  
    1.  Select **HTTPS**.  
  
    2.  Select **Allow Internet-only client connections** or **Allow intranet and Internet client connections**. These options require that an Internet FQDN is specified in the site system properties.  
  
    3.  Select **Allow mobile devices to use this management point** ([!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] with no service pack) or **Allow mobile devices and Mac computers to use this management point** ([!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] SP1).  
  
4.  In the details pane, right-click **Distribution point**, click **Role Properties**, and in the **Distribution Point Properties** dialog box, configure the following options, and then click **OK**:  
  
    1.  Select **HTTPS**.  
  
    2.  Select **Allow Internet-only client connections** or **Allow intranet and Internet client connections**. These options require that an Internet FQDN is specified in the site system properties.  
  
    3.  Click **Import certificate**, browse to the exported client distribution point certificate file, and then specify the password.  
  
5.  Repeat steps 2 through 4 in this procedure for all management points and distribution points in primary sites that you will use with mobile devices.  
  
###  <a name="BKMK_HowtoInstallEnrollmentSiteSystems"></a> Step 6: Installing and Configuring the Enrollment Site Systems  
 These procedures configure the site system roles for mobile device enrollment. Choose one of these procedures, depending on whether you will install a new site system server for mobile device enrollment or use an existing site system server:  
  
-   [To install and configure the enrollment site systems: New site system server](assetId:///b420da33-e374-4ebe-ba9f-3cdf870c3acf#BKMK_HowtoInstallEnrollmentSiteSystems_new)  
  
-   [To install and configure the enrollment site systems: Existing site system server](assetId:///b420da33-e374-4ebe-ba9f-3cdf870c3acf#BKMK_HowtoInstallEnrollmentSiteSystems_existing)  
  
####  <a name="BKMK_HowtoInstallEnrollmentSiteSystems_new"></a> To install and configure the enrollment site systems: New site system server  
  
1.  In the Configuration Manager console, click **Administration**.  
  
2.  In the **Administration** workspace, expand **Site Configuration**, and click **Servers and Site System Roles**  
  
3.  On the **Home** tab, in the **Create** group, click **Create Site System Server**.  
  
4.  On the **General** page, specify the general settings for the site system, and then click **Next**.  
  
    > [!IMPORTANT]  
    >  Make sure that you specify the Internet FQDN, even if it is the same value as the intranet FQDN. Mobile devices that are enrolled by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] always connect to the Internet FQDN, even when they are on the intranet.  
  
5.  On the **System Role Selection** page, select **Enrollment proxy point** and **Enrollment point** from the list of available roles, and then click **Next**.  
  
6.  On the **Enrollment Proxy Point** page, review the settings and make any changes that you require, and then click **Next**.  
  
7.  On the **Enrollment Point Settings** page, review the settings and make any changes that you require, and then click **Next**.  
  
8.  Complete the wizard.  
  
####  <a name="BKMK_HowtoInstallEnrollmentSiteSystems_existing"></a> To install and configure the enrollment site systems: Existing site system server  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, expand **Site Configuration**, select **Servers and Site System Roles**, and then select the server that you want to use for mobile device enrollment.  
  
3.  On the **Home** tab, in the **Create** group, click **Add Site System Roles**.  
  
4.  On the **General** page, specify the general settings for the site system, and then click **Next**.  
  
    > [!IMPORTANT]  
    >  Make sure that you specify the Internet FQDN, even if it is the same value as the intranet FQDN. Mobile devices that are enrolled by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] always connect to the Internet FQDN, even when they are on the intranet.  
  
5.  On the **System Role Selection** page, select **Enrollment proxy point** and **Enrollment point** from the list of available roles, and then click **Next**.  
  
6.  On the **Enrollment Proxy Point** page, review the settings and make any changes that you require, and then click **Next**.  
  
7.  On the **Enrollment Point Settings** page, review the settings and make any changes that you require, and then click **Next**.  
  
8.  Complete the wizard.  
  
###  <a name="BKMK_ConfigureClientSettingMobileDevices"></a> Step 9: Configuring the Client Settings for Mobile Device Enrollment  
 The first procedure in this step configures the default client settings for mobile device enrollment and will apply to all users in hierarchy. If you want these settings to apply to only some users, create a custom user setting and assign it to a collection that contains users who you will allow to enroll their mobile devices.  
  
 The second procedure in this step configures the default client settings for the mobile device polling interval and hardware inventory to apply to all mobile devices in the hierarchy that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] enrolls. The hardware inventory settings also apply to client computers. If you want these settings to apply to only mobile devices or to selected mobile devices, create a custom device setting and assign it to a collection that contains the enrolled mobile devices that you want to configure with these settings.  
  
 For more information about how to create custom client settings, see [How to Create and Assign Custom Client Settings](assetId:///dcc11cdf-d87e-4931-9cd5-125bb8140d3e#BKMK_CustomClientSettings).  
  
##### To configure the default client settings for mobile device enrollment  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, click **Client Settings**.  
  
3.  Click **Default Client Settings**.  
  
4.  On the **Home** tab, in the **Properties** group, click **Properties**.  
  
5.  Select the **Mobile Devices** ([!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] with no service pack) or **Enrollment** ([!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] SP1 and [!INCLUDE[sccm2012r2_1](../System Center Configuration Manager/itokens/sccm2012r2_1_md.md)]) section, and then configure the following user settings:  
  
    -   For [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] with no service pack:  
  
        1.  **Allow users to enroll mobile devices:True**  
  
        2.  **Mobile device enrollment profile:** Click **Set Profile**.  
  
    -   For [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] SP1 and [!INCLUDE[sccm2012r2_1](../System Center Configuration Manager/itokens/sccm2012r2_1_md.md)]:  
  
        1.  **Allow users to enroll mobile devices and Mac computers:Yes**  
  
        2.  **Enrollment profile:** Click **Set Profile**.  
  
6.  In the **Mobile Device Enrollment Profile** dialog box or  **Enrollment Profile**, click **Create**.  
  
7.  In the  dialog box, enter a name for this mobile device enrollment profile, and then configure the **Management site code**. Select the [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] primary site that contains the management points that will manage these mobile devices.  
  
    > [!NOTE]  
    >  If you cannot select the site, check that at least one management point in the site is configured to support mobile devices.  
  
8.  Click **Add**.  
  
9. In the **Add Certification Authority for Mobile Devices** dialog box, select the certification authority (CA) server that will issue certificates to mobile devices, and then click **OK**.  
  
10. In the **Create Mobile Device Enrollment Profile** dialog box ([!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] with no service pack) or **Create Enrollment Profile** dialog box ([!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] SP1), select the mobile device certificate template that you created in Step 3, and then click **OK**.  
  
11. Click **OK** to close the dialog box, and then click **OK** to close the **Default Client Settings** dialog box.  
  
 Devices will be configured with these user settings when they next download client policy. To initiate policy retrieval for a single client, see the [Initiate Policy Retrieval for a Configuration Manager Client](assetId:///782a762c-7178-4fca-8613-4f1d125bb5e7#BKMK_PolicyRetrieval) section in the [How to Manage Clients in Configuration Manager](assetId:///782a762c-7178-4fca-8613-4f1d125bb5e7) topic.  
  
##### To configure the default client settings for the mobile device polling interval and hardware inventory  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, click **Client Settings**.  
  
3.  Click **Default Client Settings**.  
  
4.  On the **Home** tab, in the **Properties** group, click **Properties**.  
  
5.  To configure the client polling interval:  
  
    -   For [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] with no service pack: Select the **Mobile Devices** section, and configure the device setting for the polling interval.  
  
    -   For [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] SP1: Select the **Client Policy** section, and configure the device setting for the client policy polling interval.  
  
6.  Select the **Hardware Inventory** section, and then configure the following device settings that apply to mobile devices that are enrolled by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]:  
  
    1.  **Enable hardware inventory on clients**  
  
    2.  **Hardware inventory schedule**  
  
    3.  **Hardware inventory classes**  
  
    > [!NOTE]  
    >  For more information about hardware inventory, see [Hardware Inventory in Configuration Manager](assetId:///cda6d645-a7a8-496f-ba42-e61fe14dbfb1)  
  
7.  Click **OK** to close the **Default Client Settings** dialog box.  
  
###  <a name="BKMK_EnrollMobileDevices"></a> Step 10: Enrolling Mobile Devices  
 This procedure installs the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client on a mobile device, requests and installs a certificate for the mobile device, and assigns the client to the enrollment site in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
##### To enroll mobile devices  
  
-   To install the client and enroll a mobile device, open a web browser on the mobile device, and then type the following, where the FQDN is the Internet FQDN of a site system server that runs the enrollment proxy point: **https://<FQDN\>/EnrollmentServer**  
  
    > [!NOTE]  
    >  You can provide this hyperlink to users in an email message or on a web page.  
    >   
    >  If you have created the DNS alias of **configmgrenroll**, you can use this in your link instead of the server name. The benefit of using the alias in the link is that if the server changes, you must only update DNS rather than the link that you provided to users, and when you have more than one enrollment proxy server, DNS round robin provides some fault tolerance and load balancing.  
  
     The mobile device enrollment process prompts to enter a company email address and password. These credentials are required to authenticate the user to Active Directory Domain Services, which then authorizes the user to access the mobile device enrollment certificate template.  
  
    > [!TIP]  
    >  If the user does not have a company email account that is integrated with Active Directory Domain Services (for example, in a test environment), you can enter the UPN for the email address (or use *domain\user name*) format, and enter the password for the Active Directory account. However, the initial page does not accept the *domain\user name* format. To use this format, enter any value that is in the *user@domain.com* format, wait for this to fail the validation check, and then you can use the *domain\user name* format.  
  
 To verify that enrollment succeeded, update and view the collections that display mobile devices in the **Assets and Compliance** workspace, and view the reports for mobile devices.  
  
## See Also  
 [Configuring Client Deployment in Configuration Manager 2012](assetId:///72a6cd16-722d-4369-9c3a-965c49a78727)