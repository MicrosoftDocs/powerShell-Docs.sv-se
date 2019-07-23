---
title: PowerShell fjärrkommunikation via SSH
description: Fjärr kommunikation i PowerShell Core med SSH
ms.date: 08/14/2018
ms.openlocfilehash: d994a3888b9a372b803a65666634775a8905d63a
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372148"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="45035-103">PowerShell fjärrkommunikation via SSH</span><span class="sxs-lookup"><span data-stu-id="45035-103">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="45035-104">Översikt</span><span class="sxs-lookup"><span data-stu-id="45035-104">Overview</span></span>

<span data-ttu-id="45035-105">PowerShell-fjärrkommunikation använder normalt WinRM för anslutnings förhandling och data transport.</span><span class="sxs-lookup"><span data-stu-id="45035-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="45035-106">SSH är nu tillgängligt för Linux-och Windows-plattformar och tillåter en PowerShell-fjärrkommunikation med multiplatform.</span><span class="sxs-lookup"><span data-stu-id="45035-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="45035-107">WinRM tillhandahåller en robust värd modell för PowerShell-fjärrsessioner.</span><span class="sxs-lookup"><span data-stu-id="45035-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="45035-108">SSH-baserad fjärr kommunikation har för närvarande inte stöd för konfiguration av Fjärrslutpunkter och JEA (bara för tillräckligt med administration).</span><span class="sxs-lookup"><span data-stu-id="45035-108">SSH-based remoting doesn't currently support remote endpoint configuration and JEA (Just Enough Administration).</span></span>

<span data-ttu-id="45035-109">Med SSH-fjärrkommunikation kan du utföra grundläggande PowerShell-sessioner mellan Windows-och Linux-datorer.</span><span class="sxs-lookup"><span data-stu-id="45035-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="45035-110">SSH-fjärrkommunikation skapar en PowerShell-värd process på mål datorn som ett SSH-undersystem.</span><span class="sxs-lookup"><span data-stu-id="45035-110">SSH Remoting creates a PowerShell host process on the target machine as an SSH subsystem.</span></span> <span data-ttu-id="45035-111">Slutligen ska vi implementera en allmän värd modell som liknar WinRM för att stödja slut punkts konfiguration och JEA.</span><span class="sxs-lookup"><span data-stu-id="45035-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="45035-112">Cmdletarna `Enter-PSSession` ,och`Invoke-Command` har nu en ny parameter inställd för att stödja den här nya fjärr anslutnings anslutningen. `New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="45035-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="45035-113">Om du vill skapa en fjärrsession anger du mål datorn med `HostName` parametern och anger användar namnet med. `UserName`</span><span class="sxs-lookup"><span data-stu-id="45035-113">To create a remote session, you specify the target machine with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="45035-114">När du kör cmdletarna interaktivt, uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="45035-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="45035-115">Du kan också använda SSH-nyckel-autentisering med hjälp av en privat nyckel `KeyFilePath` fil med parametern.</span><span class="sxs-lookup"><span data-stu-id="45035-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="45035-116">Allmän installations information</span><span class="sxs-lookup"><span data-stu-id="45035-116">General setup information</span></span>

<span data-ttu-id="45035-117">SSH måste vara installerat på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="45035-117">SSH must be installed on all machines.</span></span> <span data-ttu-id="45035-118">Installera både SSH-klienten (`ssh.exe`) och servern (`sshd.exe`) så att du kan fjärrans luta till och från datorerna.</span><span class="sxs-lookup"><span data-stu-id="45035-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the machines.</span></span> <span data-ttu-id="45035-119">OpenSSH för Windows är nu tillgängligt i Windows 10 version 1809 och Windows Server 2019.</span><span class="sxs-lookup"><span data-stu-id="45035-119">OpenSSH for Windows is now available in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="45035-120">Mer information finns i [openssh för Windows](/windows-server/administration/openssh/openssh_overview).</span><span class="sxs-lookup"><span data-stu-id="45035-120">For more information, see [OpenSSH for Windows](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="45035-121">För Linux installerar du SSH (inklusive sshd-servern) som är lämplig för din plattform.</span><span class="sxs-lookup"><span data-stu-id="45035-121">For Linux, install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="45035-122">Du måste också installera PowerShell Core från GitHub för att hämta SSH-funktionen för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="45035-122">You also need to install PowerShell Core from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="45035-123">SSH-servern måste konfigureras för att skapa ett SSH-undersystem som värd för en PowerShell-process på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="45035-123">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote machine.</span></span> <span data-ttu-id="45035-124">Du måste också konfigurera aktivera lösen ord eller nyckelbaserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="45035-124">You also must configure enable password or key-based authentication.</span></span>

## <a name="set-up-on-windows-machine"></a><span data-ttu-id="45035-125">Konfigurera på Windows-dator</span><span class="sxs-lookup"><span data-stu-id="45035-125">Set up on Windows Machine</span></span>

1. <span data-ttu-id="45035-126">Installera den senaste versionen av [PowerShell Core för Windows](../../install/installing-powershell-core-on-windows.md#msi)</span><span class="sxs-lookup"><span data-stu-id="45035-126">Install the latest version of [PowerShell Core for Windows](../../install/installing-powershell-core-on-windows.md#msi)</span></span>

   - <span data-ttu-id="45035-127">Du kan se om den har stöd för SSH-fjärrkommunikation genom att titta på parameter uppsättningarna för`New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="45035-127">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="45035-128">Installera de senaste Win32-OpenSSH.</span><span class="sxs-lookup"><span data-stu-id="45035-128">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="45035-129">Installations anvisningar finns i [installation av openssh](/windows-server/administration/openssh/openssh_install_firstuse).</span><span class="sxs-lookup"><span data-stu-id="45035-129">For installation instructions, see [Installation of OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>
3. <span data-ttu-id="45035-130">Redigera filen `sshd_config` som finns på `$env:ProgramData\ssh`.</span><span class="sxs-lookup"><span data-stu-id="45035-130">Edit the `sshd_config` file located at `$env:ProgramData\ssh`.</span></span>

   - <span data-ttu-id="45035-131">Se till att lösenordsautentisering är aktiverat</span><span class="sxs-lookup"><span data-stu-id="45035-131">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="45035-132">Det finns ett fel i OpenSSH för Windows som förhindrar att utrymmen fungerar i under systemets körbara sökvägar.</span><span class="sxs-lookup"><span data-stu-id="45035-132">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="45035-133">Mer information finns i [det här GitHub-problemet](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="45035-133">For more information, see [this GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="45035-134">En lösning är att skapa en symlink till installations katalogen för PowerShell som inte innehåller blank steg:</span><span class="sxs-lookup"><span data-stu-id="45035-134">One solution is to create a symlink to the PowerShell installation directory that doesn't have spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     <span data-ttu-id="45035-135">och ange det sedan i under systemet:</span><span class="sxs-lookup"><span data-stu-id="45035-135">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="45035-136">Aktivera nyckel autentisering om du vill</span><span class="sxs-lookup"><span data-stu-id="45035-136">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="45035-137">Starta om sshd-tjänsten</span><span class="sxs-lookup"><span data-stu-id="45035-137">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="45035-138">Lägg till sökvägen där OpenSSH är installerat i din PATH-miljö variabel.</span><span class="sxs-lookup"><span data-stu-id="45035-138">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="45035-139">Till exempel `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="45035-139">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="45035-140">Den här posten tillåter att SSH. exe hittas.</span><span class="sxs-lookup"><span data-stu-id="45035-140">This entry allows for the ssh.exe to be found.</span></span>

## <a name="set-up-on-linux-ubuntu-1604-machine"></a><span data-ttu-id="45035-141">Konfigurera på Linux-datorn (Ubuntu 16,04)</span><span class="sxs-lookup"><span data-stu-id="45035-141">Set up on Linux (Ubuntu 16.04) Machine</span></span>

1. <span data-ttu-id="45035-142">Installera den senaste versionen av [PowerShell Core för Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604) från GitHub</span><span class="sxs-lookup"><span data-stu-id="45035-142">Install the latest [PowerShell Core for Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604) build from GitHub</span></span>
2. <span data-ttu-id="45035-143">Installera [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) vid behov</span><span class="sxs-lookup"><span data-stu-id="45035-143">Install [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="45035-144">Redigera sshd_config-filen på plats/etc/ssh</span><span class="sxs-lookup"><span data-stu-id="45035-144">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="45035-145">Se till att lösenordsautentisering är aktiverat</span><span class="sxs-lookup"><span data-stu-id="45035-145">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="45035-146">Lägg till en PowerShell-delsystem post</span><span class="sxs-lookup"><span data-stu-id="45035-146">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="45035-147">Aktivera nyckel autentisering om du vill</span><span class="sxs-lookup"><span data-stu-id="45035-147">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="45035-148">Starta om sshd-tjänsten</span><span class="sxs-lookup"><span data-stu-id="45035-148">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a><span data-ttu-id="45035-149">Konfigurera på MacOS-datorn</span><span class="sxs-lookup"><span data-stu-id="45035-149">Set up on MacOS Machine</span></span>

1. <span data-ttu-id="45035-150">Installera den senaste [PowerShell-kärnan för MacOS](../../install/installing-powershell-core-on-macos.md) -version</span><span class="sxs-lookup"><span data-stu-id="45035-150">Install the latest [PowerShell Core for MacOS](../../install/installing-powershell-core-on-macos.md) build</span></span>

   - <span data-ttu-id="45035-151">Se till att SSH-fjärrkommunikation är aktiverat genom att följa dessa steg:</span><span class="sxs-lookup"><span data-stu-id="45035-151">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="45035-152">Inställningar`System Preferences`</span><span class="sxs-lookup"><span data-stu-id="45035-152">Open `System Preferences`</span></span>
     - <span data-ttu-id="45035-153">Klicka på`Sharing`</span><span class="sxs-lookup"><span data-stu-id="45035-153">Click on `Sharing`</span></span>
     - <span data-ttu-id="45035-154">Kontroll `Remote Login` – bör stå`Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="45035-154">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="45035-155">Tillåt åtkomst till lämpliga användare</span><span class="sxs-lookup"><span data-stu-id="45035-155">Allow access to appropriate users</span></span>

2. <span data-ttu-id="45035-156">`sshd_config` Redigera filen på plats`/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="45035-156">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="45035-157">Använd din favorit redigerare eller</span><span class="sxs-lookup"><span data-stu-id="45035-157">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="45035-158">Se till att lösenordsautentisering är aktiverat</span><span class="sxs-lookup"><span data-stu-id="45035-158">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="45035-159">Lägg till en PowerShell-delsystem post</span><span class="sxs-lookup"><span data-stu-id="45035-159">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="45035-160">Aktivera nyckel autentisering om du vill</span><span class="sxs-lookup"><span data-stu-id="45035-160">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="45035-161">Starta om sshd-tjänsten</span><span class="sxs-lookup"><span data-stu-id="45035-161">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="45035-162">Autentisering</span><span class="sxs-lookup"><span data-stu-id="45035-162">Authentication</span></span>

<span data-ttu-id="45035-163">PowerShell-fjärrkommunikation via SSH är beroende av autentiserings utbyte mellan SSH-klienten och SSH-tjänsten och implementerar inte några autentiseringsscheman.</span><span class="sxs-lookup"><span data-stu-id="45035-163">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and does not implement any authentication schemes itself.</span></span> <span data-ttu-id="45035-164">Det innebär att alla konfigurerade autentiseringsscheman, inklusive Multi-Factor Authentication, hanteras av SSH och oberoende av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45035-164">This means that any configured authentication schemes including multi-factor authentication is handled by SSH and independent of PowerShell.</span></span> <span data-ttu-id="45035-165">Du kan till exempel konfigurera SSH-tjänsten så att den kräver autentisering med offentlig nyckel och eng ång slö sen ord för ytterligare säkerhet.</span><span class="sxs-lookup"><span data-stu-id="45035-165">For example, you can configure the SSH service to require public key authentication as well as a one-time password for added security.</span></span> <span data-ttu-id="45035-166">Konfiguration av Multi-Factor Authentication omfattas inte av den här dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="45035-166">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span> <span data-ttu-id="45035-167">Läs dokumentationen för SSH om hur du konfigurerar Multi-Factor Authentication på rätt sätt och verifierar att den fungerar utanför PowerShell innan du försöker använda den med PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="45035-167">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="45035-168">Exempel på PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="45035-168">PowerShell Remoting Example</span></span>

<span data-ttu-id="45035-169">Det enklaste sättet att testa fjärr kommunikation är att testa den på en enda dator.</span><span class="sxs-lookup"><span data-stu-id="45035-169">The easiest way to test remoting is to try it on a single machine.</span></span> <span data-ttu-id="45035-170">I det här exemplet skapar vi en fjärrsession tillbaka till samma Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="45035-170">In this example, we create a remote session back to the same Linux machine.</span></span> <span data-ttu-id="45035-171">Vi använder PowerShell-cmdlets interaktivt så vi ser frågor från SSH som ber om att verifiera värddatorn och uppmanas att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="45035-171">We are using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="45035-172">Du kan göra samma sak på en Windows-dator för att säkerställa att fjärr kommunikation fungerar.</span><span class="sxs-lookup"><span data-stu-id="45035-172">You can do the same thing on a Windows machine to ensure remoting is working.</span></span> <span data-ttu-id="45035-173">Fjärranslut sedan mellan datorer genom att ändra värd namnet.</span><span class="sxs-lookup"><span data-stu-id="45035-173">Then remote between machines by changing the host name.</span></span>

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
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~16.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

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

### <a name="known-issues"></a><span data-ttu-id="45035-174">Kända problem</span><span class="sxs-lookup"><span data-stu-id="45035-174">Known Issues</span></span>

<span data-ttu-id="45035-175">Kommandot sudo fungerar inte i fjärrsession till Linux-datorn.</span><span class="sxs-lookup"><span data-stu-id="45035-175">The sudo command doesn't work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="45035-176">Se även</span><span class="sxs-lookup"><span data-stu-id="45035-176">See Also</span></span>

[<span data-ttu-id="45035-177">PowerShell Core för Windows</span><span class="sxs-lookup"><span data-stu-id="45035-177">PowerShell Core for Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="45035-178">PowerShell Core för Linux</span><span class="sxs-lookup"><span data-stu-id="45035-178">PowerShell Core for Linux</span></span>](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[<span data-ttu-id="45035-179">PowerShell Core för MacOS</span><span class="sxs-lookup"><span data-stu-id="45035-179">PowerShell Core for MacOS</span></span>](../../install/installing-powershell-core-on-macos.md)

[<span data-ttu-id="45035-180">OpenSSH för Windows</span><span class="sxs-lookup"><span data-stu-id="45035-180">OpenSSH for Windows</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="45035-181">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="45035-181">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
