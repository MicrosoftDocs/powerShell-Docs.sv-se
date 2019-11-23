---
title: Installera PowerShell Core i Windows
description: Information about installing PowerShell Core on Windows
ms.date: 08/06/2018
ms.openlocfilehash: 00a1d8064a3c1ec6608a46415bbabb8d98d880f0
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416778"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="a6d35-103">Installera PowerShell Core i Windows</span><span class="sxs-lookup"><span data-stu-id="a6d35-103">Installing PowerShell Core on Windows</span></span>

<span data-ttu-id="a6d35-104">There are multiple ways to install PowerShell Core in Windows.</span><span class="sxs-lookup"><span data-stu-id="a6d35-104">There are multiple ways to install PowerShell Core in Windows.</span></span>

> [!TIP]
> <span data-ttu-id="a6d35-105">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it’s easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="a6d35-105">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it’s easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>
>
> ```
> dotnet tool install --global PowerShell
> ```

## <a name="prerequisites"></a><span data-ttu-id="a6d35-106">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="a6d35-106">Prerequisites</span></span>

<span data-ttu-id="a6d35-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span><span class="sxs-lookup"><span data-stu-id="a6d35-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="a6d35-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span><span class="sxs-lookup"><span data-stu-id="a6d35-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="a6d35-109">It is available via direct download or Windows Update.</span><span class="sxs-lookup"><span data-stu-id="a6d35-109">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="a6d35-110">Fully patched (including optional packages), supported systems will already have this installed.</span><span class="sxs-lookup"><span data-stu-id="a6d35-110">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="a6d35-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="a6d35-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="a6d35-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="a6d35-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="a6d35-113"><a id="msi" />Installing the MSI package</span><span class="sxs-lookup"><span data-stu-id="a6d35-113"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="a6d35-114">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][releases] page.</span><span class="sxs-lookup"><span data-stu-id="a6d35-114">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="a6d35-115">Scroll down to the **Assets** section of the Release you want to install.</span><span class="sxs-lookup"><span data-stu-id="a6d35-115">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="a6d35-116">The Assets section may be collapsed, so you may need to click to expand it.</span><span class="sxs-lookup"><span data-stu-id="a6d35-116">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="a6d35-117">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="a6d35-117">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="a6d35-118">Once downloaded, double-click the installer and follow the prompts.</span><span class="sxs-lookup"><span data-stu-id="a6d35-118">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="a6d35-119">The installer creates a shortcut in the Windows Start Menu.</span><span class="sxs-lookup"><span data-stu-id="a6d35-119">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="a6d35-120">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="a6d35-120">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="a6d35-121">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="a6d35-121">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="a6d35-122">Administrative install from the command line</span><span class="sxs-lookup"><span data-stu-id="a6d35-122">Administrative install from the command line</span></span>

<span data-ttu-id="a6d35-123">MSI packages can be installed from the command line.</span><span class="sxs-lookup"><span data-stu-id="a6d35-123">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="a6d35-124">This allows administrators to deploy packages without user interaction.</span><span class="sxs-lookup"><span data-stu-id="a6d35-124">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="a6d35-125">The MSI package for PowerShell includes the following properties to control the installation options:</span><span class="sxs-lookup"><span data-stu-id="a6d35-125">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="a6d35-126">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="a6d35-126">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="a6d35-127">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span><span class="sxs-lookup"><span data-stu-id="a6d35-127">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="a6d35-128">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span><span class="sxs-lookup"><span data-stu-id="a6d35-128">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="a6d35-129">The following examples shows how to silently install PowerShell Core with all the install options enabled.</span><span class="sxs-lookup"><span data-stu-id="a6d35-129">The following examples shows how to silently install PowerShell Core with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="a6d35-130">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="a6d35-130">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idmsix-installing-the-msix-package"></a><span data-ttu-id="a6d35-131"><a id="msix" />Installing the MSIX package</span><span class="sxs-lookup"><span data-stu-id="a6d35-131"><a id="msix" />Installing the MSIX package</span></span>

<span data-ttu-id="a6d35-132">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span><span class="sxs-lookup"><span data-stu-id="a6d35-132">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="a6d35-133">Scroll down to the **Assets** section of the Release you want to install.</span><span class="sxs-lookup"><span data-stu-id="a6d35-133">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="a6d35-134">The Assets section may be collapsed, so you may need to click to expand it.</span><span class="sxs-lookup"><span data-stu-id="a6d35-134">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="a6d35-135">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="a6d35-135">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="a6d35-136">Once downloaded, you cannot simply double-click on the installer as this package requires use of un-virtualized resources.</span><span class="sxs-lookup"><span data-stu-id="a6d35-136">Once downloaded, you cannot simply double-click on the installer as this package requires use of un-virtualized resources.</span></span>  <span data-ttu-id="a6d35-137">To install, you must use the `Add-AppxPackage` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="a6d35-137">To install, you must use the `Add-AppxPackage` cmdlet:</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="a6d35-138"><a id="zip" />Installing the ZIP package</span><span class="sxs-lookup"><span data-stu-id="a6d35-138"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="a6d35-139">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span><span class="sxs-lookup"><span data-stu-id="a6d35-139">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="a6d35-140">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span><span class="sxs-lookup"><span data-stu-id="a6d35-140">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="a6d35-141">For remoting over WSMan to work properly, ensure that you have met the [prerequisites](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="a6d35-141">For remoting over WSMan to work properly, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="a6d35-142">Deploying on Windows IoT</span><span class="sxs-lookup"><span data-stu-id="a6d35-142">Deploying on Windows IoT</span></span>

<span data-ttu-id="a6d35-143">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="a6d35-143">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="a6d35-144">Create `PSSession` to target device</span><span class="sxs-lookup"><span data-stu-id="a6d35-144">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="a6d35-145">Copy the ZIP package to the device</span><span class="sxs-lookup"><span data-stu-id="a6d35-145">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="a6d35-146">Connect to the device and expand the archive</span><span class="sxs-lookup"><span data-stu-id="a6d35-146">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="a6d35-147">Setup remoting to PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="a6d35-147">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="a6d35-148">Connect to PowerShell Core 6 endpoint on device</span><span class="sxs-lookup"><span data-stu-id="a6d35-148">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="a6d35-149">Deploying on Nano Server</span><span class="sxs-lookup"><span data-stu-id="a6d35-149">Deploying on Nano Server</span></span>

<span data-ttu-id="a6d35-150">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="a6d35-150">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="a6d35-151">Nano Server is a "headless" OS.</span><span class="sxs-lookup"><span data-stu-id="a6d35-151">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="a6d35-152">Core binaries can be deploy using two different methods.</span><span class="sxs-lookup"><span data-stu-id="a6d35-152">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="a6d35-153">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span><span class="sxs-lookup"><span data-stu-id="a6d35-153">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="a6d35-154">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span><span class="sxs-lookup"><span data-stu-id="a6d35-154">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="a6d35-155">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span><span class="sxs-lookup"><span data-stu-id="a6d35-155">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="a6d35-156">Offline Deployment of PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="a6d35-156">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="a6d35-157">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span><span class="sxs-lookup"><span data-stu-id="a6d35-157">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="a6d35-158">Unmount the image and boot it.</span><span class="sxs-lookup"><span data-stu-id="a6d35-158">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="a6d35-159">Connect to the inbox instance of Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a6d35-159">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="a6d35-160">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="a6d35-160">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="a6d35-161">Online Deployment of PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="a6d35-161">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="a6d35-162">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span><span class="sxs-lookup"><span data-stu-id="a6d35-162">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="a6d35-163">Connect to the inbox instance of Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6d35-163">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="a6d35-164">Copy the file to the Nano Server instance</span><span class="sxs-lookup"><span data-stu-id="a6d35-164">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="a6d35-165">Enter the session</span><span class="sxs-lookup"><span data-stu-id="a6d35-165">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="a6d35-166">Extract the ZIP file</span><span class="sxs-lookup"><span data-stu-id="a6d35-166">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="a6d35-167">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="a6d35-167">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="a6d35-168">How to create a remoting endpoint</span><span class="sxs-lookup"><span data-stu-id="a6d35-168">How to create a remoting endpoint</span></span>

<span data-ttu-id="a6d35-169">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span><span class="sxs-lookup"><span data-stu-id="a6d35-169">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="a6d35-170">Mer information finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="a6d35-170">For more information, see:</span></span>

- <span data-ttu-id="a6d35-171">[SSH Remoting in PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="a6d35-171">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="a6d35-172">[WSMan Remoting in PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="a6d35-172">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
