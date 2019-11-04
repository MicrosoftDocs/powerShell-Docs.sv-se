---
title: PowerShell fjärrkommunikation via SSH
description: Fjärr kommunikation i PowerShell Core med SSH
ms.date: 09/30/2019
ms.openlocfilehash: 0f2fb13010d62dec5b19b373a24a199bff22665d
ms.sourcegitcommit: 36e4c79afda2ce11febd93951e143687245f0b50
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/02/2019
ms.locfileid: "73444379"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="028b4-103">PowerShell fjärrkommunikation via SSH</span><span class="sxs-lookup"><span data-stu-id="028b4-103">PowerShell remoting over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="028b4-104">Översikt</span><span class="sxs-lookup"><span data-stu-id="028b4-104">Overview</span></span>

<span data-ttu-id="028b4-105">PowerShell-fjärrkommunikation använder normalt WinRM för anslutnings förhandling och data transport.</span><span class="sxs-lookup"><span data-stu-id="028b4-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="028b4-106">SSH är nu tillgängligt för Linux-och Windows-plattformar och tillåter en PowerShell-fjärrkommunikation med multiplatform.</span><span class="sxs-lookup"><span data-stu-id="028b4-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="028b4-107">WinRM tillhandahåller en robust värd modell för PowerShell-fjärrsessioner.</span><span class="sxs-lookup"><span data-stu-id="028b4-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="028b4-108">SSH-baserad fjärr kommunikation har för närvarande inte stöd för konfiguration av Fjärrslutpunkter och bara tillräckligt med administration (JEA).</span><span class="sxs-lookup"><span data-stu-id="028b4-108">SSH-based remoting doesn't currently support remote endpoint configuration and Just Enough Administration (JEA).</span></span>

<span data-ttu-id="028b4-109">Med SSH-fjärrkommunikation kan du utföra grundläggande PowerShell-sessioner mellan Windows-och Linux-datorer.</span><span class="sxs-lookup"><span data-stu-id="028b4-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux computers.</span></span> <span data-ttu-id="028b4-110">SSH-fjärrkommunikation skapar en PowerShell-värd process på mål datorn som ett SSH-undersystem.</span><span class="sxs-lookup"><span data-stu-id="028b4-110">SSH remoting creates a PowerShell host process on the target computer as an SSH subsystem.</span></span> <span data-ttu-id="028b4-111">Slutligen ska vi implementera en allmän värd modell som liknar WinRM för att stödja slut punkts konfiguration och JEA.</span><span class="sxs-lookup"><span data-stu-id="028b4-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="028b4-112">Cmdletarna `New-PSSession`, `Enter-PSSession`och `Invoke-Command` har nu en ny parameter som stöder denna nya fjärr anslutnings anslutning.</span><span class="sxs-lookup"><span data-stu-id="028b4-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="028b4-113">Om du vill skapa en fjärrsession anger du mål datorn med parametern `HostName` och anger användar namnet med `UserName`.</span><span class="sxs-lookup"><span data-stu-id="028b4-113">To create a remote session, you specify the target computer with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="028b4-114">När du kör cmdletarna interaktivt, uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="028b4-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="028b4-115">Du kan också använda SSH-nyckel-autentisering med hjälp av en privat nyckel fil med parametern `KeyFilePath`.</span><span class="sxs-lookup"><span data-stu-id="028b4-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="028b4-116">Allmän installations information</span><span class="sxs-lookup"><span data-stu-id="028b4-116">General setup information</span></span>

<span data-ttu-id="028b4-117">PowerShell 6 eller högre, och SSH måste vara installerat på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="028b4-117">PowerShell 6 or higher, and SSH must be installed on all computers.</span></span> <span data-ttu-id="028b4-118">Installera både SSH-klienten (`ssh.exe`) och Server (`sshd.exe`) så att du kan fjärrans luta till och från datorerna.</span><span class="sxs-lookup"><span data-stu-id="028b4-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the computers.</span></span> <span data-ttu-id="028b4-119">OpenSSH för Windows är nu tillgängligt i Windows 10 version 1809 och Windows Server 2019.</span><span class="sxs-lookup"><span data-stu-id="028b4-119">OpenSSH for Windows is now available in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="028b4-120">Mer information finns i [hantera Windows med openssh](/windows-server/administration/openssh/openssh_overview).</span><span class="sxs-lookup"><span data-stu-id="028b4-120">For more information, see [Manage Windows with OpenSSH](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="028b4-121">För Linux installerar du SSH, inklusive sshd-servern, som är lämplig för din plattform.</span><span class="sxs-lookup"><span data-stu-id="028b4-121">For Linux, install SSH, including sshd server, that's appropriate for your platform.</span></span> <span data-ttu-id="028b4-122">Du måste också installera PowerShell från GitHub för att hämta SSH-funktionen för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="028b4-122">You also need to install PowerShell from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="028b4-123">SSH-servern måste konfigureras för att skapa ett SSH-undersystem som värd för en PowerShell-process på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="028b4-123">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote computer.</span></span> <span data-ttu-id="028b4-124">Och du måste aktivera **lösen ord** eller **nyckelbaserad** autentisering.</span><span class="sxs-lookup"><span data-stu-id="028b4-124">And, you must enable **password** or **key-based** authentication.</span></span>

## <a name="set-up-on-a-windows-computer"></a><span data-ttu-id="028b4-125">Konfigurera på en Windows-dator</span><span class="sxs-lookup"><span data-stu-id="028b4-125">Set up on a Windows computer</span></span>

1. <span data-ttu-id="028b4-126">Installera den senaste versionen av PowerShell, se [Installera PowerShell Core på Windows](../../install/installing-powershell-core-on-windows.md#msi).</span><span class="sxs-lookup"><span data-stu-id="028b4-126">Install the latest version of PowerShell, see [Installing PowerShell Core on Windows](../../install/installing-powershell-core-on-windows.md#msi).</span></span>

   <span data-ttu-id="028b4-127">Du kan kontrol lera att PowerShell har stöd för SSH-fjärrhantering genom att Visa `New-PSSession` parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="028b4-127">You can confirm that PowerShell has SSH remoting support by listing the `New-PSSession` parameter sets.</span></span> <span data-ttu-id="028b4-128">Observera att det finns parameter uppsättnings namn som börjar med **SSH**.</span><span class="sxs-lookup"><span data-stu-id="028b4-128">You'll notice there are parameter set names that begin with **SSH**.</span></span> <span data-ttu-id="028b4-129">Parameter uppsättningarna inkluderar **SSH** -parametrar.</span><span class="sxs-lookup"><span data-stu-id="028b4-129">Those parameter sets include **SSH** parameters.</span></span>

   ```powershell
   (Get-Command New-PSSession).ParameterSets.Name
   ```

   ```Output
   Name
   ----
   SSHHost
   SSHHostHashParam
   ```

1. <span data-ttu-id="028b4-130">Installera de senaste Win32-OpenSSH.</span><span class="sxs-lookup"><span data-stu-id="028b4-130">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="028b4-131">Installations anvisningar finns i [komma igång med openssh](/windows-server/administration/openssh/openssh_install_firstuse).</span><span class="sxs-lookup"><span data-stu-id="028b4-131">For installation instructions, see [Getting started with OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>

   > [!NOTE]
   > <span data-ttu-id="028b4-132">Om du vill ställa in PowerShell som standard gränssnitt för OpenSSH, se [Konfigurera Windows för openssh](/windows-server/administration/openssh/openssh_server_configuration).</span><span class="sxs-lookup"><span data-stu-id="028b4-132">If you want to set PowerShell as the default shell for OpenSSH, see [Configuring Windows for OpenSSH](/windows-server/administration/openssh/openssh_server_configuration).</span></span>

1. <span data-ttu-id="028b4-133">Redigera `sshd_config`-filen som finns på `$env:ProgramData\ssh`.</span><span class="sxs-lookup"><span data-stu-id="028b4-133">Edit the `sshd_config` file located at `$env:ProgramData\ssh`.</span></span>

   <span data-ttu-id="028b4-134">Se till att lösenordsautentisering är aktiverat:</span><span class="sxs-lookup"><span data-stu-id="028b4-134">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="028b4-135">Skapa SSH-undersystemet som är värd för en PowerShell-process på fjärrdatorn:</span><span class="sxs-lookup"><span data-stu-id="028b4-135">Create the SSH subsystem that hosts a PowerShell process on the remote computer:</span></span>

   ```
   Subsystem powershell c:/progra~1/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   > [!NOTE]
   > <span data-ttu-id="028b4-136">Du måste använda det korta 8,3-namnet för alla fil Sök vägar som innehåller blank steg.</span><span class="sxs-lookup"><span data-stu-id="028b4-136">You must use the 8.3 short name for any file paths that contain spaces.</span></span> <span data-ttu-id="028b4-137">Det finns ett fel i OpenSSH för Windows som förhindrar att utrymmen fungerar i under systemets körbara sökvägar.</span><span class="sxs-lookup"><span data-stu-id="028b4-137">There's a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="028b4-138">Mer information finns i det här [GitHub-problemet](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="028b4-138">For more information, see this [GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>
   >
   > <span data-ttu-id="028b4-139">Det korta 8,3-namnet för mappen `Program Files` i Windows är vanligt vis `Progra~1`.</span><span class="sxs-lookup"><span data-stu-id="028b4-139">The 8.3 short name for the `Program Files` folder in Windows is usually `Progra~1`.</span></span> <span data-ttu-id="028b4-140">Du kan dock använda följande kommando för att se till att:</span><span class="sxs-lookup"><span data-stu-id="028b4-140">However, you can use the following command to make sure:</span></span>
   >
   > ```powershell
   > Get-CimInstance Win32_Directory -Filter 'Name="C:\\Program Files"' |
   >   Select-Object EightDotThreeFileName
   > ```
   >
   > ```Output
   > EightDotThreeFileName
   > ---------------------
   > c:\progra~1
   > ```

   <span data-ttu-id="028b4-141">Du kan också aktivera nyckel autentisering:</span><span class="sxs-lookup"><span data-stu-id="028b4-141">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

   <span data-ttu-id="028b4-142">Mer information finns i [Hantera openssh-nycklar](/windows-server/administration/openssh/openssh_keymanagement).</span><span class="sxs-lookup"><span data-stu-id="028b4-142">For more information, see [Managing OpenSSH Keys](/windows-server/administration/openssh/openssh_keymanagement).</span></span>

1. <span data-ttu-id="028b4-143">Starta om **sshd** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="028b4-143">Restart the **sshd** service.</span></span>

   ```powershell
   Restart-Service sshd
   ```

1. <span data-ttu-id="028b4-144">Lägg till sökvägen där OpenSSH är installerat i din PATH-miljö variabel.</span><span class="sxs-lookup"><span data-stu-id="028b4-144">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="028b4-145">Till exempel `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="028b4-145">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="028b4-146">Den här posten gör att `ssh.exe` kan hittas.</span><span class="sxs-lookup"><span data-stu-id="028b4-146">This entry allows for the `ssh.exe` to be found.</span></span>

## <a name="set-up-on-an-ubuntu-1604-linux-computer"></a><span data-ttu-id="028b4-147">Konfigurera på en Ubuntu 16,04 Linux-dator</span><span class="sxs-lookup"><span data-stu-id="028b4-147">Set up on an Ubuntu 16.04 Linux computer</span></span>

1. <span data-ttu-id="028b4-148">Installera den senaste versionen av PowerShell, se [Installera PowerShell Core på Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604).</span><span class="sxs-lookup"><span data-stu-id="028b4-148">Install the latest version of PowerShell, see [Installing PowerShell Core on Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604).</span></span>
1. <span data-ttu-id="028b4-149">Installera [Ubuntu openssh-server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).</span><span class="sxs-lookup"><span data-stu-id="028b4-149">Install [Ubuntu OpenSSH Server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. <span data-ttu-id="028b4-150">Redigera `sshd_config`-filen på plats `/etc/ssh`.</span><span class="sxs-lookup"><span data-stu-id="028b4-150">Edit the `sshd_config` file at location `/etc/ssh`.</span></span>

   <span data-ttu-id="028b4-151">Se till att lösenordsautentisering är aktiverat:</span><span class="sxs-lookup"><span data-stu-id="028b4-151">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="028b4-152">Lägg till en PowerShell-under Systems post:</span><span class="sxs-lookup"><span data-stu-id="028b4-152">Add a PowerShell subsystem entry:</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   <span data-ttu-id="028b4-153">Du kan också aktivera nyckel autentisering:</span><span class="sxs-lookup"><span data-stu-id="028b4-153">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="028b4-154">Starta om **sshd** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="028b4-154">Restart the **sshd** service.</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-a-macos-computer"></a><span data-ttu-id="028b4-155">Konfigurera på en macOS-dator</span><span class="sxs-lookup"><span data-stu-id="028b4-155">Set up on a macOS computer</span></span>

1. <span data-ttu-id="028b4-156">Installera den senaste versionen av PowerShell, se [Installera PowerShell Core på MacOS](../../install/installing-powershell-core-on-macos.md).</span><span class="sxs-lookup"><span data-stu-id="028b4-156">Install the latest version of PowerShell, see [Installing PowerShell Core on macOS](../../install/installing-powershell-core-on-macos.md).</span></span>

   <span data-ttu-id="028b4-157">Se till att SSH-fjärrkommunikation är aktiverat genom att följa dessa steg:</span><span class="sxs-lookup"><span data-stu-id="028b4-157">Make sure SSH Remoting is enabled by following these steps:</span></span>

   1. <span data-ttu-id="028b4-158">Öppna `System Preferences`.</span><span class="sxs-lookup"><span data-stu-id="028b4-158">Open `System Preferences`.</span></span>
   1. <span data-ttu-id="028b4-159">Klicka på `Sharing`.</span><span class="sxs-lookup"><span data-stu-id="028b4-159">Click on `Sharing`.</span></span>
   1. <span data-ttu-id="028b4-160">Markera `Remote Login` för att ange `Remote Login: On`.</span><span class="sxs-lookup"><span data-stu-id="028b4-160">Check `Remote Login` to set `Remote Login: On`.</span></span>
   1. <span data-ttu-id="028b4-161">Tillåt åtkomst till lämpliga användare.</span><span class="sxs-lookup"><span data-stu-id="028b4-161">Allow access to the appropriate users.</span></span>

1. <span data-ttu-id="028b4-162">Redigera `sshd_config`-filen på plats `/private/etc/ssh/sshd_config`.</span><span class="sxs-lookup"><span data-stu-id="028b4-162">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`.</span></span>

   <span data-ttu-id="028b4-163">Använd en text redigerare som **nano**:</span><span class="sxs-lookup"><span data-stu-id="028b4-163">Use a text editor such as **nano**:</span></span>

   ```bash
   sudo nano /private/etc/ssh/sshd_config
   ```

   <span data-ttu-id="028b4-164">Se till att lösenordsautentisering är aktiverat:</span><span class="sxs-lookup"><span data-stu-id="028b4-164">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="028b4-165">Lägg till en PowerShell-under Systems post:</span><span class="sxs-lookup"><span data-stu-id="028b4-165">Add a PowerShell subsystem entry:</span></span>

   ```
   Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   <span data-ttu-id="028b4-166">Du kan också aktivera nyckel autentisering:</span><span class="sxs-lookup"><span data-stu-id="028b4-166">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="028b4-167">Starta om **sshd** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="028b4-167">Restart the **sshd** service.</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="028b4-168">Autentisering</span><span class="sxs-lookup"><span data-stu-id="028b4-168">Authentication</span></span>

<span data-ttu-id="028b4-169">PowerShell-fjärrkommunikation via SSH är beroende av autentiserings utbyte mellan SSH-klienten och SSH-tjänsten och implementerar inte några autentiseringsscheman.</span><span class="sxs-lookup"><span data-stu-id="028b4-169">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and doesn't implement any authentication schemes itself.</span></span> <span data-ttu-id="028b4-170">Resultatet är att alla konfigurerade autentiseringsscheman, inklusive Multi-Factor Authentication, hanteras av SSH och oberoende av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="028b4-170">The result is that any configured authentication schemes including multi-factor authentication are handled by SSH and independent of PowerShell.</span></span> <span data-ttu-id="028b4-171">Du kan till exempel konfigurera SSH-tjänsten så att den kräver autentisering med offentlig nyckel och eng ång slö sen ord för ytterligare säkerhet.</span><span class="sxs-lookup"><span data-stu-id="028b4-171">For example, you can configure the SSH service to require public key authentication and a one-time password for added security.</span></span> <span data-ttu-id="028b4-172">Konfiguration av Multi-Factor Authentication omfattas inte av den här dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="028b4-172">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span> <span data-ttu-id="028b4-173">Läs dokumentationen för SSH om hur du konfigurerar Multi-Factor Authentication på rätt sätt och verifierar att den fungerar utanför PowerShell innan du försöker använda den med PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="028b4-173">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="028b4-174">Exempel på PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="028b4-174">PowerShell remoting example</span></span>

<span data-ttu-id="028b4-175">Det enklaste sättet att testa fjärr kommunikation är att testa den på en enda dator.</span><span class="sxs-lookup"><span data-stu-id="028b4-175">The easiest way to test remoting is to try it on a single computer.</span></span> <span data-ttu-id="028b4-176">I det här exemplet skapar vi en fjärrsession tillbaka till samma Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="028b4-176">In this example, we create a remote session back to the same Linux computer.</span></span> <span data-ttu-id="028b4-177">Vi använder PowerShell-cmdletar interaktivt så vi ser frågor från SSH som ber om att verifiera värddatorn och uppmanas att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="028b4-177">We're using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="028b4-178">Du kan göra samma sak på en Windows-dator för att säkerställa att fjärr kommunikation fungerar.</span><span class="sxs-lookup"><span data-stu-id="028b4-178">You can do the same thing on a Windows computer to ensure remoting is working.</span></span> <span data-ttu-id="028b4-179">Sedan kan du fjärrans luta mellan datorer genom att ändra värd namnet.</span><span class="sxs-lookup"><span data-stu-id="028b4-179">Then, remote between computers by changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```Output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```Output
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```Output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~16.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```Output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1
```

```powershell
#
# Linux to Windows
#
Enter-PSSession -HostName WinVM1 -UserName PTestName
```

```Output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```Output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```Output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```Output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```Output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```Output
[WinVM2]: PS C:\Users\PSRemoteUser\Documents> $PSVersionTable

Name                           Value
----                           -----
PSEdition                      Core
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
SerializationVersion           1.1.0.1
BuildVersion                   3.0.0.0
CLRVersion
PSVersion                      6.0.0-alpha
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
GitCommitId                    v6.0.0-alpha.17


[WinVM2]: PS C:\Users\PSRemoteUser\Documents>
```

### <a name="known-issues"></a><span data-ttu-id="028b4-180">Kända problem</span><span class="sxs-lookup"><span data-stu-id="028b4-180">Known issues</span></span>

<span data-ttu-id="028b4-181">Kommandot **sudo** fungerar inte i en fjärran sluten session till en Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="028b4-181">The **sudo** command doesn't work in a remote session to a Linux computer.</span></span>

## <a name="see-also"></a><span data-ttu-id="028b4-182">Se även</span><span class="sxs-lookup"><span data-stu-id="028b4-182">See also</span></span>

[<span data-ttu-id="028b4-183">Installera PowerShell Core på Linux</span><span class="sxs-lookup"><span data-stu-id="028b4-183">Installing PowerShell Core on Linux</span></span>](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[<span data-ttu-id="028b4-184">Installera PowerShell Core på macOS</span><span class="sxs-lookup"><span data-stu-id="028b4-184">Installing PowerShell Core on macOS</span></span>](../../install/installing-powershell-core-on-macos.md)

[<span data-ttu-id="028b4-185">Installera PowerShell Core på Windows</span><span class="sxs-lookup"><span data-stu-id="028b4-185">Installing PowerShell Core on Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="028b4-186">Hantera Windows med OpenSSH</span><span class="sxs-lookup"><span data-stu-id="028b4-186">Manage Windows with OpenSSH</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="028b4-187">Hantera OpenSSH-nycklar</span><span class="sxs-lookup"><span data-stu-id="028b4-187">Managing OpenSSH Keys</span></span>](/windows-server/administration/openssh/openssh_keymanagement)

[<span data-ttu-id="028b4-188">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="028b4-188">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
