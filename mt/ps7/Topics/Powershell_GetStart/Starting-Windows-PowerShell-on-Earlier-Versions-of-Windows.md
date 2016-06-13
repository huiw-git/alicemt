---
title: Starting Windows PowerShell on Earlier Versions of Windows
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
---
# Starting Windows PowerShell on Earlier Versions of Windows
This section explains how to start [!INCLUDE[wps_2](../../Tokens/wps_2_md.md)] and [!INCLUDE[mshgraphicalhost](../../Tokens/mshgraphicalhost_md.md)] on [!INCLUDE[win7_client_firstref](../../Tokens/win7_client_firstref_md.md)], [!INCLUDE[win7_server_firstref](../../Tokens/win7_server_firstref_md.md)], and [!INCLUDE[lserver](../../Tokens/lserver_md.md)]. It also explains how to enable the optional feature for [!INCLUDE[mshgraphicalhostshort](../../Tokens/mshgraphicalhostshort_md.md)] in [!INCLUDE[psversion2](../../Tokens/psversion2_md.md)] on [!INCLUDE[win7_server_firstref](../../Tokens/win7_server_firstref_md.md)] and [!INCLUDE[lserver](../../Tokens/lserver_md.md)].

To install [!INCLUDE[psversion4](../../Tokens/psversion4_md.md)] on supported systems, download and install [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881). For more information, see [Installing Windows PowerShell](../../Topics/Powershell_GetStart/Installing-Windows-PowerShell.md).

To install [!INCLUDE[psversion3](../../Tokens/psversion3_md.md)] on supported systems, download and install [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290). For more information, see [Installing Windows PowerShell](../../Topics/Powershell_GetStart/Installing-Windows-PowerShell.md).

## How to Start [!INCLUDE[mshshort](../../Tokens/mshshort_md.md)] on Earlier Versions of Windows
Use any of the following methods to start the installed version of [!INCLUDE[psversion3](../../Tokens/psversion3_md.md)], or [!INCLUDE[psversion4](../../Tokens/psversion4_md.md)], where applicable.

#### From the Start Menu

-   Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.

-   From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.

#### At the Command Prompt

-   In Cmd.exe, [!INCLUDE[wps_2](../../Tokens/wps_2_md.md)], or [!INCLUDE[wps_2](../../Tokens/wps_2_md.md)] ISE, to start [!INCLUDE[wps_2](../../Tokens/wps_2_md.md)], type:

    ```
    PowerShell
    ```

    You can also use the parameters of the PowerShell.exe program to customize the session. For more information, see [PowerShell.exe Command-Line Help](../Topic/PowerShell.exe%20Command-Line%20Help.md).

#### With Administrative privileges ("Run as administrator")

1.  Click **Start**, type **PowerShell**, right\-click **Windows PowerShell**, and then click **Run as administrator**.

## How to Start [!INCLUDE[mshgraphicalhostshort](../../Tokens/mshgraphicalhostshort_md.md)] on Earlier Releases of Windows
Use any of the following methods to start [!INCLUDE[mshgraphicalhostshort](../../Tokens/mshgraphicalhostshort_md.md)].

#### From the Start Menu

-   Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.

-   From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.

#### At the Command Prompt

-   In Cmd.exe, [!INCLUDE[wps_2](../../Tokens/wps_2_md.md)], or [!INCLUDE[wps_2](../../Tokens/wps_2_md.md)] ISE, to start [!INCLUDE[wps_2](../../Tokens/wps_2_md.md)], type:

    ```
    PowerShell_ISE
    ```

    or

    ```
    ISE
    ```

#### With Administrative privileges ("Run as administrator")

1.  Click **Start**, type **ISE**, right\-click **Windows PowerShell ISE**, and then click **Run as administrator**.

## How to Enable [!INCLUDE[mshgraphicalhostshort](../../Tokens/mshgraphicalhostshort_md.md)] on Earlier Releases of Windows
In [!INCLUDE[psversion4](../../Tokens/psversion4_md.md)] and [!INCLUDE[psversion3](../../Tokens/psversion3_md.md)], [!INCLUDE[mshgraphicalhostshort](../../Tokens/mshgraphicalhostshort_md.md)] is enabled by default on all versions of Windows. If it is not already enabled, Windows Management Framework 4.0 or [!INCLUDE[ps_wmf_3.0](../../Tokens/ps_wmf_3.0_md.md)] enables it.

In [!INCLUDE[psversion2](../../Tokens/psversion2_md.md)], [!INCLUDE[mshgraphicalhostshort](../../Tokens/mshgraphicalhostshort_md.md)] is enabled by default on [!INCLUDE[win7_client_secondref](../../Tokens/win7_client_secondref_md.md)]. However, on [!INCLUDE[win7_server_secondref](../../Tokens/win7_server_secondref_md.md)] and [!INCLUDE[lserver](../../Tokens/lserver_md.md)], it is an optional feature.

To enable [!INCLUDE[mshgraphicalhostshort](../../Tokens/mshgraphicalhostshort_md.md)] in [!INCLUDE[psversion2](../../Tokens/psversion2_md.md)] on [!INCLUDE[win7_server_secondref](../../Tokens/win7_server_secondref_md.md)] or [!INCLUDE[lserver](../../Tokens/lserver_md.md)], use the following procedure.

#### To enable [!INCLUDE[mshgraphicalhost](../../Tokens/mshgraphicalhost_md.md)]

1.  Start Server Manager.

2.  Click **Features** and then click **Add Features**.

3.  In Select Features, click [!INCLUDE[mshgraphicalhost](../../Tokens/mshgraphicalhost_md.md)].

