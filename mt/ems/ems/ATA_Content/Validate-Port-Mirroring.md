---
title: "Validate Port Mirroring"
ms.custom: 
  - ATA
ms.date: 07/22/2016
ms.prod: identity-ata
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ebd41719-c91a-4fdd-bcab-2affa2a2cace
caps.latest.revision: 24
author: karthikaraman
manager: jeffgilb
---
# Validate Port Mirroring
The following steps walk you through the process for validating that port mirroring is properly configured.

1.  Install [Microsoft Network Monitor 3.4](http://www.microsoft.com/download/details.aspx?id=4865) or another network sniffing tool.

    > [!IMPORTANT]
    > Do not install Microsoft Message Analyzer, or any other traffic capture software on the ATA Gateway.

2.  Open Network Monitor and create a new capture tab.

    1.  Select only the **Capture** network adapter or the network adapter that is connected to the switch port that is configured as the port mirroring destination.

    2.  Ensure that P-Mode is enabled.

    3.  Click **New Capture**.

        ![The steps to create a new capture for ATA Port Mirroring](../../ems/ATA_Content/media/ATA-Port-Mirroring-Capture.jpg "ATA Port Mirroring Capture")

3.  In the Display Filter window, enter the following filter: **KerberosV5 OR LDAP** and then click **Apply**.

    ![ATA Port Mirroring filter settings for the capture](../../ems/ATA_Content/media/ATA-Port-Mirroring-filter-settings.jpg "ATA Port Mirroring filter settings")

4.  Click **Start** to start the capture session. If you do not see traffic to and from the domain controller, review your port mirroring configuration.

    > [!NOTE]
    > It is important to make sure you see traffic to and from the domain controllers.
    > 
    > ![Traffic to and from the domain controller](../../ems/ATA_Content/media/ATA-Port-Mirroring-Capture-traffic.jpg "ATA Port Mirroring Capture traffic")

## See Also
[Configure Port Mirroring](../../ems/ATA_Content/Configure-Port-Mirroring.md)
 [For support, check out our forum!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)

