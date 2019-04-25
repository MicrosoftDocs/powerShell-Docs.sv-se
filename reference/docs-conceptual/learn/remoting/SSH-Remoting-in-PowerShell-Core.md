---
title: PowerShell fjärrkommunikation via SSH
description: Fjärrkommunikation i PowerShell Core med hjälp av SSH
ms.date: 08/14/2018
ms.openlocfilehash: 1d7bcb69c7e784bf745cb5c2633106ea53f6226a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086399"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="023e5-103">PowerShell fjärrkommunikation via SSH</span><span class="sxs-lookup"><span data-stu-id="023e5-103">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="023e5-104">Översikt</span><span class="sxs-lookup"><span data-stu-id="023e5-104">Overview</span></span>

<span data-ttu-id="023e5-105">PowerShell-fjärrkommunikation använder vanligen WinRM för förhandling för anslutning och dataöverföring.</span><span class="sxs-lookup"><span data-stu-id="023e5-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="023e5-106">SSH är nu tillgängligt för Linux och Windows-plattformar och tillåter SANT PowerShell-fjärrkommunikation på flera plattformar.</span><span class="sxs-lookup"><span data-stu-id="023e5-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="023e5-107">WinRM tillhandahåller en robust värdmodell för fjärrsessioner i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="023e5-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="023e5-108">SSH-baserad fjärrkommunikation stöd för närvarande inte fjärrslutpunkten konfigurations- och JEA (Just Enough Administration).</span><span class="sxs-lookup"><span data-stu-id="023e5-108">SSH-based remoting doesn't currently support remote endpoint configuration and JEA (Just Enough Administration).</span></span>

<span data-ttu-id="023e5-109">SSH-fjärrkommunikation kan du göra grundläggande session PowerShell-fjärrkommunikation mellan Windows och Linux-datorer.</span><span class="sxs-lookup"><span data-stu-id="023e5-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="023e5-110">SSH-fjärrkommunikation skapar en värdprocess för PowerShell på måldatorn som ett SSH-undersystem.</span><span class="sxs-lookup"><span data-stu-id="023e5-110">SSH Remoting creates a PowerShell host process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="023e5-111">Slutligen ska vi implementera en allmän värdmodell, liknar WinRM för slutpunktskonfiguration och JEA.</span><span class="sxs-lookup"><span data-stu-id="023e5-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="023e5-112">Den `New-PSSession`, `Enter-PSSession`, och `Invoke-Command` cmdletarna har nu en ny parameter som angetts för den här nya fjärrkommunikation-anslutningen.</span><span class="sxs-lookup"><span data-stu-id="023e5-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="023e5-113">Om du vill skapa en fjärrsession, anger du den target-datorn med den `HostName` parametern och ange användarnamnet med `UserName`.</span><span class="sxs-lookup"><span data-stu-id="023e5-113">To create a remote session, you specify the target machine with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="023e5-114">När du kör cmdletarna interaktivt, uppmanas du ett lösenord.</span><span class="sxs-lookup"><span data-stu-id="023e5-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="023e5-115">Du kan också använda SSH-nyckelautentisering med hjälp av en privat nyckelfil med den `KeyFilePath` parametern.</span><span class="sxs-lookup"><span data-stu-id="023e5-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="023e5-116">Allmänna inställningar</span><span class="sxs-lookup"><span data-stu-id="023e5-116">General setup information</span></span>

<span data-ttu-id="023e5-117">SSH måste installeras på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="023e5-117">SSH must be installed on all machines.</span></span> <span data-ttu-id="023e5-118">Installera både SSH-klienten (`ssh.exe`) och server (`sshd.exe`) så att du kan fjärransluta till och från datorerna.</span><span class="sxs-lookup"><span data-stu-id="023e5-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the machines.</span></span> <span data-ttu-id="023e5-119">OpenSSH för Windows är nu prestandaalternativen i Windows 10 build 1809 och Windows Server 2019.</span><span class="sxs-lookup"><span data-stu-id="023e5-119">OpenSSH for Windows is now availabe in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="023e5-120">Mer information finns i [OpenSSH för Windows](/windows-server/administration/openssh/openssh_overview).</span><span class="sxs-lookup"><span data-stu-id="023e5-120">For more information, see [OpenSSH for Windows](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="023e5-121">För Linux, installera SSH (inklusive sshd-servern) lämpligt för din plattform.</span><span class="sxs-lookup"><span data-stu-id="023e5-121">For Linux, install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="023e5-122">Du måste också installera PowerShell Core från GitHub för att hämta SSH-fjärrkommunikationsfunktionen.</span><span class="sxs-lookup"><span data-stu-id="023e5-122">You also need to install PowerShell Core from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="023e5-123">SSH-servern måste konfigureras för att skapa ett SSH-undersystem som värd för en PowerShell-process på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="023e5-123">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote machine.</span></span> <span data-ttu-id="023e5-124">Du måste också konfigurera aktivera lösenord eller en nyckel för autentisering.</span><span class="sxs-lookup"><span data-stu-id="023e5-124">You also must configure enable password or key-based authentication.</span></span>

## <a name="set-up-on-windows-machine"></a><span data-ttu-id="023e5-125">Ställa in på Windows-dator</span><span class="sxs-lookup"><span data-stu-id="023e5-125">Set up on Windows Machine</span></span>

1. <span data-ttu-id="023e5-126">Installera den senaste versionen av [PowerShell Core för Windows](../../install/installing-powershell-core-on-windows.md#msi)</span><span class="sxs-lookup"><span data-stu-id="023e5-126">Install the latest version of [PowerShell Core for Windows](../../install/installing-powershell-core-on-windows.md#msi)</span></span>

   - <span data-ttu-id="023e5-127">Berätta om den har stöd för SSH-fjärrkommunikation genom att titta på parameteruppsättningar för `New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="023e5-127">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="023e5-128">Installera den senaste Win32-OpenSSH.</span><span class="sxs-lookup"><span data-stu-id="023e5-128">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="023e5-129">Installationsanvisningar finns i [Installation av OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span><span class="sxs-lookup"><span data-stu-id="023e5-129">For installation instructions, see [Installation of OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>
3. <span data-ttu-id="023e5-130">Redigera den `sshd_config` -filen på `$env:ProgramData\ssh`.</span><span class="sxs-lookup"><span data-stu-id="023e5-130">Edit the `sshd_config` file located at `$env:ProgramData\ssh`.</span></span>

   - <span data-ttu-id="023e5-131">Kontrollera att lösenordsautentisering är aktiverad</span><span class="sxs-lookup"><span data-stu-id="023e5-131">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="023e5-132">Det finns en bugg i OpenSSH för Windows som förhindrar att blanksteg fungerar i undersystemet körbara sökvägar.</span><span class="sxs-lookup"><span data-stu-id="023e5-132">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="023e5-133">Mer information finns i [problemet GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="023e5-133">For more information, see [this GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="023e5-134">En lösning är att skapa en symlink till installationskatalogen för PowerShell som saknar blanksteg:</span><span class="sxs-lookup"><span data-stu-id="023e5-134">One solution is to create a symlink to the PowerShell installation directory that doesn't have spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     <span data-ttu-id="023e5-135">och sedan ange den i undersystemet:</span><span class="sxs-lookup"><span data-stu-id="023e5-135">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="023e5-136">Du kan också aktivera nyckelautentisering</span><span class="sxs-lookup"><span data-stu-id="023e5-136">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="023e5-137">Starta om tjänsten sshd</span><span class="sxs-lookup"><span data-stu-id="023e5-137">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="023e5-138">Lägga till sökvägen där OpenSSH installeras till sökvägen för miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="023e5-138">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="023e5-139">Till exempel `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="023e5-139">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="023e5-140">Den här posten kan ssh.exe ska finnas.</span><span class="sxs-lookup"><span data-stu-id="023e5-140">This entry allows for the ssh.exe to be found.</span></span>

## <a name="set-up-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="023e5-141">Ställa in på datorn för Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="023e5-141">Set up on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="023e5-142">Installera senast [PowerShell Core för Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1404) skapa från GitHub</span><span class="sxs-lookup"><span data-stu-id="023e5-142">Install the latest [PowerShell Core for Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1404) build from GitHub</span></span>
2. <span data-ttu-id="023e5-143">Installera [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) efter behov</span><span class="sxs-lookup"><span data-stu-id="023e5-143">Install [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="023e5-144">Redigera sshd_config-filen på plats /etc/ssh</span><span class="sxs-lookup"><span data-stu-id="023e5-144">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="023e5-145">Kontrollera att lösenordsautentisering är aktiverad</span><span class="sxs-lookup"><span data-stu-id="023e5-145">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="023e5-146">Lägga till en post för PowerShell-undersystemet</span><span class="sxs-lookup"><span data-stu-id="023e5-146">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="023e5-147">Du kan också aktivera nyckelautentisering</span><span class="sxs-lookup"><span data-stu-id="023e5-147">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="023e5-148">Starta om tjänsten sshd</span><span class="sxs-lookup"><span data-stu-id="023e5-148">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a><span data-ttu-id="023e5-149">Ställa in på Mac OS-dator</span><span class="sxs-lookup"><span data-stu-id="023e5-149">Set up on MacOS Machine</span></span>

1. <span data-ttu-id="023e5-150">Installera senast [PowerShell Core för MacOS](../../install/installing-powershell-core-on-macos.md) skapa</span><span class="sxs-lookup"><span data-stu-id="023e5-150">Install the latest [PowerShell Core for MacOS](../../install/installing-powershell-core-on-macos.md) build</span></span>

   - <span data-ttu-id="023e5-151">Kontrollera att SSH-fjärrkommunikation är aktiverat genom att följa dessa steg:</span><span class="sxs-lookup"><span data-stu-id="023e5-151">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="023e5-152">Öppna `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="023e5-152">Open `System Preferences`</span></span>
     - <span data-ttu-id="023e5-153">Klicka på `Sharing`</span><span class="sxs-lookup"><span data-stu-id="023e5-153">Click on `Sharing`</span></span>
     - <span data-ttu-id="023e5-154">Kontrollera `Remote Login` -ska stå `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="023e5-154">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="023e5-155">Tillåt åtkomst till rätt användare</span><span class="sxs-lookup"><span data-stu-id="023e5-155">Allow access to appropriate users</span></span>

2. <span data-ttu-id="023e5-156">Redigera den `sshd_config` fil på plats `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="023e5-156">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="023e5-157">Använda din favoritredigerare eller</span><span class="sxs-lookup"><span data-stu-id="023e5-157">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="023e5-158">Kontrollera att lösenordsautentisering är aktiverad</span><span class="sxs-lookup"><span data-stu-id="023e5-158">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="023e5-159">Lägga till en post för PowerShell-undersystemet</span><span class="sxs-lookup"><span data-stu-id="023e5-159">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="023e5-160">Du kan också aktivera nyckelautentisering</span><span class="sxs-lookup"><span data-stu-id="023e5-160">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="023e5-161">Starta om tjänsten sshd</span><span class="sxs-lookup"><span data-stu-id="023e5-161">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="023e5-162">Autentisering</span><span class="sxs-lookup"><span data-stu-id="023e5-162">Authentication</span></span>

<span data-ttu-id="023e5-163">PowerShell fjärrkommunikation via SSH är beroende av autentiseringsutbytet mellan SSH-klient och SSH-tjänsten och implementerar inte alla autentiseringsscheman själva.</span><span class="sxs-lookup"><span data-stu-id="023e5-163">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and does not implement any authentication schemes itself.</span></span>
<span data-ttu-id="023e5-164">Det innebär att alla konfigurerade autentiseringsmetoder, inklusive Multi-Factor authentication hanteras av SSH- och oberoende av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="023e5-164">This means that any configured authentication schemes including multi-factor authentication is handled by SSH and independent of PowerShell.</span></span>
<span data-ttu-id="023e5-165">Du kan till exempel konfigurera SSH-tjänsten för att kräva autentisering med offentlig nyckel som ett engångslösenord för ökad säkerhet.</span><span class="sxs-lookup"><span data-stu-id="023e5-165">For example, you can configure the SSH service to require public key authentication as well as a one-time password for added security.</span></span>
<span data-ttu-id="023e5-166">Konfigurationen av Multi-Factor authentication ligger utanför omfånget för den här dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="023e5-166">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span>
<span data-ttu-id="023e5-167">I dokumentationen för SSH på hur du konfigurerar multifaktorautentisering och verifiera den fungerar utanför PowerShell innan du försöker använda den med PowerShell-fjärrkommunikation korrekt.</span><span class="sxs-lookup"><span data-stu-id="023e5-167">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="023e5-168">Exempel på PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="023e5-168">PowerShell Remoting Example</span></span>

<span data-ttu-id="023e5-169">Det enklaste sättet att testa fjärrkommunikation är att testa den på en enda dator.</span><span class="sxs-lookup"><span data-stu-id="023e5-169">The easiest way to test remoting is to try it on a single machine.</span></span> <span data-ttu-id="023e5-170">I det här exemplet skapar vi en fjärrsession tillbaka till samma Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="023e5-170">In this example, we create a remote session back to the same Linux machine.</span></span> <span data-ttu-id="023e5-171">Vi använder PowerShell cmdlets interaktivt så ser vi uppmanar från SSH där du ombeds att verifiera värddatorn och fråga om ett lösenord.</span><span class="sxs-lookup"><span data-stu-id="023e5-171">We are using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="023e5-172">Du kan göra samma sak på en Windows-dator fjärrkommunikation fungerar.</span><span class="sxs-lookup"><span data-stu-id="023e5-172">You can do the same thing on a Windows machine to ensure remoting is working.</span></span> <span data-ttu-id="023e5-173">Sedan remote mellan datorer genom att ändra värdnamnet.</span><span class="sxs-lookup"><span data-stu-id="023e5-173">Then remote between machines by changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```output
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```output
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

```output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```output
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

### <a name="known-issues"></a><span data-ttu-id="023e5-174">Kända problem</span><span class="sxs-lookup"><span data-stu-id="023e5-174">Known Issues</span></span>

<span data-ttu-id="023e5-175">Sudo-kommando fungerar inte i fjärrsession till Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="023e5-175">The sudo command doesn't work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="023e5-176">Se även</span><span class="sxs-lookup"><span data-stu-id="023e5-176">See Also</span></span>

[<span data-ttu-id="023e5-177">PowerShell Core för Windows</span><span class="sxs-lookup"><span data-stu-id="023e5-177">PowerShell Core for Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="023e5-178">PowerShell Core för Linux</span><span class="sxs-lookup"><span data-stu-id="023e5-178">PowerShell Core for Linux</span></span>](../../install/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="023e5-179">PowerShell Core för MacOS</span><span class="sxs-lookup"><span data-stu-id="023e5-179">PowerShell Core for MacOS</span></span>](../../install/installing-powershell-core-on-macos.md)

[<span data-ttu-id="023e5-180">OpenSSH för Windows</span><span class="sxs-lookup"><span data-stu-id="023e5-180">OpenSSH for Windows</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="023e5-181">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="023e5-181">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
