---
title: PowerShell fjärrkommunikation via SSH
description: Fjärrkommunikation i PowerShell Core med hjälp av SSH
ms.date: 08/14/2018
ms.openlocfilehash: 0605e2400ab23a5ca97910621a59a64d19a80bde
ms.sourcegitcommit: b235c58b34d23317076540631f5cf83f1f309c0d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45557115"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="c7ced-103">PowerShell fjärrkommunikation via SSH</span><span class="sxs-lookup"><span data-stu-id="c7ced-103">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="c7ced-104">Översikt</span><span class="sxs-lookup"><span data-stu-id="c7ced-104">Overview</span></span>

<span data-ttu-id="c7ced-105">PowerShell-fjärrkommunikation använder vanligen WinRM för förhandling för anslutning och dataöverföring.</span><span class="sxs-lookup"><span data-stu-id="c7ced-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="c7ced-106">SSH är nu tillgängligt för Linux och Windows-plattformar och tillåter SANT PowerShell-fjärrkommunikation på flera plattformar.</span><span class="sxs-lookup"><span data-stu-id="c7ced-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="c7ced-107">WinRM tillhandahåller en robust värdmodell för fjärrsessioner i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c7ced-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="c7ced-108">som den här implementeringen SSH-baserad fjärrkommunikation för närvarande inte stöd för fjärrslutpunkten konfigurations- och JEA (Just Enough Administration).</span><span class="sxs-lookup"><span data-stu-id="c7ced-108">which this implementation SSH-based remoting doesn't currently support remote endpoint configuration and JEA (Just Enough Administration).</span></span>

<span data-ttu-id="c7ced-109">SSH-fjärrkommunikation kan du göra grundläggande session PowerShell-fjärrkommunikation mellan Windows och Linux-datorer.</span><span class="sxs-lookup"><span data-stu-id="c7ced-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="c7ced-110">SSH-fjärrkommunikation skapar en värdprocess för PowerShell på måldatorn som ett SSH-undersystem.</span><span class="sxs-lookup"><span data-stu-id="c7ced-110">SSH Remoting creates a PowerShell host process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="c7ced-111">Slutligen ska vi implementera en allmän värdmodell, liknar WinRM för slutpunktskonfiguration och JEA.</span><span class="sxs-lookup"><span data-stu-id="c7ced-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="c7ced-112">Den `New-PSSession`, `Enter-PSSession`, och `Invoke-Command` cmdletarna har nu en ny parameter som angetts för den här nya fjärrkommunikation-anslutningen.</span><span class="sxs-lookup"><span data-stu-id="c7ced-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="c7ced-113">Om du vill skapa en fjärrsession, anger du den target-datorn med den `HostName` parametern och ange användarnamnet med `UserName`.</span><span class="sxs-lookup"><span data-stu-id="c7ced-113">To create a remote session, you specify the target machine with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="c7ced-114">När du kör cmdletarna interaktivt, uppmanas du ett lösenord.</span><span class="sxs-lookup"><span data-stu-id="c7ced-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="c7ced-115">Du kan också använda SSH-nyckelautentisering med hjälp av en privat nyckelfil med den `KeyFilePath` parametern.</span><span class="sxs-lookup"><span data-stu-id="c7ced-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="c7ced-116">Allmänna inställningar</span><span class="sxs-lookup"><span data-stu-id="c7ced-116">General setup information</span></span>

<span data-ttu-id="c7ced-117">SSH måste installeras på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="c7ced-117">SSH must be installed on all machines.</span></span> <span data-ttu-id="c7ced-118">Installera både SSH-klienten (`ssh.exe`) och server (`sshd.exe`) så att du kan fjärransluta till och från datorerna.</span><span class="sxs-lookup"><span data-stu-id="c7ced-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the machines.</span></span> <span data-ttu-id="c7ced-119">För Windows, installera [Win32-OpenSSH från GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="c7ced-119">For Windows, install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="c7ced-120">För Linux, installera SSH (inklusive sshd-servern) lämpligt för din plattform.</span><span class="sxs-lookup"><span data-stu-id="c7ced-120">For Linux, install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="c7ced-121">Du måste också installera PowerShell Core från GitHub för att hämta SSH-fjärrkommunikationsfunktionen.</span><span class="sxs-lookup"><span data-stu-id="c7ced-121">You also need to install PowerShell Core from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="c7ced-122">SSH-servern måste konfigureras för att skapa ett SSH-undersystem som värd för en PowerShell-process på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c7ced-122">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote machine.</span></span> <span data-ttu-id="c7ced-123">Du måste också konfigurera aktivera lösenord eller en nyckel för autentisering.</span><span class="sxs-lookup"><span data-stu-id="c7ced-123">You also must configure enable password or key-based authentication.</span></span>

## <a name="set-up-on-windows-machine"></a><span data-ttu-id="c7ced-124">Ställa in på Windows-dator</span><span class="sxs-lookup"><span data-stu-id="c7ced-124">Set up on Windows Machine</span></span>

1. <span data-ttu-id="c7ced-125">Installera den senaste versionen av [PowerShell Core för Windows]</span><span class="sxs-lookup"><span data-stu-id="c7ced-125">Install the latest version of [PowerShell Core for Windows]</span></span>

   - <span data-ttu-id="c7ced-126">Berätta om den har stöd för SSH-fjärrkommunikation genom att titta på parameteruppsättningar för `New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="c7ced-126">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="c7ced-127">Installera den senaste versionen av [Win32-OpenSSH] från GitHub med hjälp av [installationsinstruktionerna]</span><span class="sxs-lookup"><span data-stu-id="c7ced-127">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
3. <span data-ttu-id="c7ced-128">Redigera sshd_config-filen på den plats där du installerade Win32 OpenSSH</span><span class="sxs-lookup"><span data-stu-id="c7ced-128">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>

   - <span data-ttu-id="c7ced-129">Kontrollera att lösenordsautentisering är aktiverad</span><span class="sxs-lookup"><span data-stu-id="c7ced-129">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6.0.4/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="c7ced-130">Det finns en bugg i OpenSSH för Windows som förhindrar att blanksteg fungerar i undersystemet körbara sökvägar.</span><span class="sxs-lookup"><span data-stu-id="c7ced-130">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="c7ced-131">Mer information finns i [problemet GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="c7ced-131">For more information, see [this GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="c7ced-132">En lösning är att skapa en symlink till installationskatalogen för Powershell som saknar blanksteg:</span><span class="sxs-lookup"><span data-stu-id="c7ced-132">One solution is to create a symlink to the Powershell installation directory that doesn't have spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.4"
     ```

     <span data-ttu-id="c7ced-133">och sedan ange den i undersystemet:</span><span class="sxs-lookup"><span data-stu-id="c7ced-133">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="c7ced-134">Du kan också aktivera nyckelautentisering</span><span class="sxs-lookup"><span data-stu-id="c7ced-134">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="c7ced-135">Starta om tjänsten sshd</span><span class="sxs-lookup"><span data-stu-id="c7ced-135">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="c7ced-136">Lägga till sökvägen där OpenSSH installeras till sökvägen för miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="c7ced-136">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="c7ced-137">Till exempel `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="c7ced-137">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="c7ced-138">Den här posten kan ssh.exe ska finnas.</span><span class="sxs-lookup"><span data-stu-id="c7ced-138">This entry allows for the ssh.exe to be found.</span></span>

## <a name="set-up-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="c7ced-139">Ställa in på datorn för Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="c7ced-139">Set up on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="c7ced-140">Installera den senaste versionen av [PowerShell Core för Linux] från GitHub</span><span class="sxs-lookup"><span data-stu-id="c7ced-140">Install the latest [PowerShell Core for Linux] build from GitHub</span></span>
2. <span data-ttu-id="c7ced-141">Installera [Ubuntu SSH] vid behov</span><span class="sxs-lookup"><span data-stu-id="c7ced-141">Install [Ubuntu SSH] as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="c7ced-142">Redigera sshd_config-filen på plats /etc/ssh</span><span class="sxs-lookup"><span data-stu-id="c7ced-142">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="c7ced-143">Kontrollera att lösenordsautentisering är aktiverad</span><span class="sxs-lookup"><span data-stu-id="c7ced-143">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="c7ced-144">Lägga till en post för PowerShell-undersystemet</span><span class="sxs-lookup"><span data-stu-id="c7ced-144">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="c7ced-145">Du kan också aktivera nyckelautentisering</span><span class="sxs-lookup"><span data-stu-id="c7ced-145">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="c7ced-146">Starta om tjänsten sshd</span><span class="sxs-lookup"><span data-stu-id="c7ced-146">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a><span data-ttu-id="c7ced-147">Ställa in på Mac OS-dator</span><span class="sxs-lookup"><span data-stu-id="c7ced-147">Set up on MacOS Machine</span></span>

1. <span data-ttu-id="c7ced-148">Installera den senaste versionen av [PowerShell Core för MacOS]</span><span class="sxs-lookup"><span data-stu-id="c7ced-148">Install the latest [PowerShell Core for MacOS] build</span></span>

   - <span data-ttu-id="c7ced-149">Kontrollera att SSH-fjärrkommunikation är aktiverat genom att följa dessa steg:</span><span class="sxs-lookup"><span data-stu-id="c7ced-149">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="c7ced-150">Öppna `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="c7ced-150">Open `System Preferences`</span></span>
     - <span data-ttu-id="c7ced-151">Klicka på `Sharing`</span><span class="sxs-lookup"><span data-stu-id="c7ced-151">Click on `Sharing`</span></span>
     - <span data-ttu-id="c7ced-152">Kontrollera `Remote Login` -ska stå `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="c7ced-152">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="c7ced-153">Tillåt åtkomst till rätt användare</span><span class="sxs-lookup"><span data-stu-id="c7ced-153">Allow access to appropriate users</span></span>

2. <span data-ttu-id="c7ced-154">Redigera den `sshd_config` fil på plats `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="c7ced-154">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="c7ced-155">Använda din favoritredigerare eller</span><span class="sxs-lookup"><span data-stu-id="c7ced-155">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="c7ced-156">Kontrollera att lösenordsautentisering är aktiverad</span><span class="sxs-lookup"><span data-stu-id="c7ced-156">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="c7ced-157">Lägga till en post för PowerShell-undersystemet</span><span class="sxs-lookup"><span data-stu-id="c7ced-157">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="c7ced-158">Du kan också aktivera nyckelautentisering</span><span class="sxs-lookup"><span data-stu-id="c7ced-158">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="c7ced-159">Starta om tjänsten sshd</span><span class="sxs-lookup"><span data-stu-id="c7ced-159">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="c7ced-160">Autentisering</span><span class="sxs-lookup"><span data-stu-id="c7ced-160">Authentication</span></span>

<span data-ttu-id="c7ced-161">PowerShell fjärrkommunikation via SSH är beroende av autentiseringsutbytet mellan SSH-klient och SSH-tjänsten och implementerar inte alla autentiseringsscheman själva.</span><span class="sxs-lookup"><span data-stu-id="c7ced-161">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and does not implement any authentication schemes itself.</span></span>
<span data-ttu-id="c7ced-162">Det innebär att alla konfigurerade autentiseringsmetoder, inklusive Multi-Factor authentication hanteras av SSH- och oberoende av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c7ced-162">This means that any configured authentication schemes including multi-factor authentication is handled by SSH and independent of PowerShell.</span></span>
<span data-ttu-id="c7ced-163">Du kan till exempel konfigurera SSH-tjänsten för att kräva autentisering med offentlig nyckel som ett engångslösenord för ökad säkerhet.</span><span class="sxs-lookup"><span data-stu-id="c7ced-163">For example, you can configure the SSH service to require public key authentication as well as a one-time password for added security.</span></span>
<span data-ttu-id="c7ced-164">Konfigurationen av Multi-Factor authentication ligger utanför omfånget för den här dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="c7ced-164">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span>
<span data-ttu-id="c7ced-165">I dokumentationen för SSH på hur du konfigurerar multifaktorautentisering och verifiera den fungerar utanför PowerShell innan du försöker använda den med PowerShell-fjärrkommunikation korrekt.</span><span class="sxs-lookup"><span data-stu-id="c7ced-165">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="authentication"></a><span data-ttu-id="c7ced-166">Autentisering</span><span class="sxs-lookup"><span data-stu-id="c7ced-166">Authentication</span></span>

<span data-ttu-id="c7ced-167">PowerShell fjärrkommunikation via SSH är beroende av autentiseringsutbytet mellan SSH-klient och SSH-tjänsten och implementerar inte alla autentiseringsscheman själva.</span><span class="sxs-lookup"><span data-stu-id="c7ced-167">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and does not implement any authentication schemes itself.</span></span>
<span data-ttu-id="c7ced-168">Det innebär att alla konfigurerade autentiseringsmetoder, inklusive Multi-Factor authentication hanteras av SSH- och oberoende av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c7ced-168">This means that any configured authentication schemes including multi-factor authentication is handled by SSH and independent of PowerShell.</span></span>
<span data-ttu-id="c7ced-169">Du kan till exempel konfigurera SSH-tjänsten för att kräva autentisering med offentlig nyckel som ett engångslösenord för ökad säkerhet.</span><span class="sxs-lookup"><span data-stu-id="c7ced-169">For example, you can configure the SSH service to require public key authentication as well as a one-time password for added security.</span></span>
<span data-ttu-id="c7ced-170">Konfigurationen av Multi-Factor authentication ligger utanför omfånget för den här dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="c7ced-170">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span>
<span data-ttu-id="c7ced-171">I dokumentationen för SSH på hur du konfigurerar multifaktorautentisering och verifiera den fungerar utanför PowerShell innan du försöker använda den med PowerShell-fjärrkommunikation korrekt.</span><span class="sxs-lookup"><span data-stu-id="c7ced-171">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="authentication"></a><span data-ttu-id="c7ced-172">Autentisering</span><span class="sxs-lookup"><span data-stu-id="c7ced-172">Authentication</span></span>

<span data-ttu-id="c7ced-173">PowerShell fjärrkommunikation via SSH är beroende av autentiseringsutbytet mellan SSH-klient och SSH-tjänsten och implementerar inte alla autentiseringsscheman själva.</span><span class="sxs-lookup"><span data-stu-id="c7ced-173">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and does not implement any authentication schemes itself.</span></span>
<span data-ttu-id="c7ced-174">Det innebär att alla konfigurerade autentiseringsmetoder, inklusive Multi-Factor authentication hanteras av SSH- och oberoende av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c7ced-174">This means that any configured authentication schemes including multi-factor authentication is handled by SSH and independent of PowerShell.</span></span>
<span data-ttu-id="c7ced-175">Du kan till exempel konfigurera SSH-tjänsten för att kräva autentisering med offentlig nyckel som ett engångslösenord för ökad säkerhet.</span><span class="sxs-lookup"><span data-stu-id="c7ced-175">For example, you can configure the SSH service to require public key authentication as well as a one-time password for added security.</span></span>
<span data-ttu-id="c7ced-176">Konfigurationen av Multi-Factor authentication ligger utanför omfånget för den här dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="c7ced-176">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span>
<span data-ttu-id="c7ced-177">I dokumentationen för SSH på hur du konfigurerar multifaktorautentisering och verifiera den fungerar utanför PowerShell innan du försöker använda den med PowerShell-fjärrkommunikation korrekt.</span><span class="sxs-lookup"><span data-stu-id="c7ced-177">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="c7ced-178">Exempel på PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="c7ced-178">PowerShell Remoting Example</span></span>

<span data-ttu-id="c7ced-179">Det enklaste sättet att testa fjärrkommunikation är att testa den på en enda dator.</span><span class="sxs-lookup"><span data-stu-id="c7ced-179">The easiest way to test remoting is to try it on a single machine.</span></span> <span data-ttu-id="c7ced-180">I det här exemplet skapar vi en fjärrsession tillbaka till samma Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="c7ced-180">In this example, we create a remote session back to the same Linux machine.</span></span> <span data-ttu-id="c7ced-181">Vi använder PowerShell cmdlets interaktivt så ser vi uppmanar från SSH där du ombeds att verifiera värddatorn och fråga om ett lösenord.</span><span class="sxs-lookup"><span data-stu-id="c7ced-181">We are using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="c7ced-182">Du kan göra samma sak på en Windows-dator fjärrkommunikation fungerar.</span><span class="sxs-lookup"><span data-stu-id="c7ced-182">You can do the same thing on a Windows machine to ensure remoting is working.</span></span> <span data-ttu-id="c7ced-183">Sedan remote mellan datorer genom att ändra värdnamnet.</span><span class="sxs-lookup"><span data-stu-id="c7ced-183">Then remote between machines by changing the host name.</span></span>

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

### <a name="known-issues"></a><span data-ttu-id="c7ced-184">Kända problem</span><span class="sxs-lookup"><span data-stu-id="c7ced-184">Known Issues</span></span>

<span data-ttu-id="c7ced-185">Sudo-kommando fungerar inte i fjärrsession till Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="c7ced-185">The sudo command doesn't work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7ced-186">Se även</span><span class="sxs-lookup"><span data-stu-id="c7ced-186">See Also</span></span>

[<span data-ttu-id="c7ced-187">PowerShell Core för Windows</span><span class="sxs-lookup"><span data-stu-id="c7ced-187">PowerShell Core for Windows</span></span>](../setup/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="c7ced-188">PowerShell Core för Linux</span><span class="sxs-lookup"><span data-stu-id="c7ced-188">PowerShell Core for Linux</span></span>](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="c7ced-189">PowerShell Core för MacOS</span><span class="sxs-lookup"><span data-stu-id="c7ced-189">PowerShell Core for MacOS</span></span>](../setup/installing-powershell-core-on-macos.md)

[<span data-ttu-id="c7ced-190">Win32-OpenSSH</span><span class="sxs-lookup"><span data-stu-id="c7ced-190">Win32 OpenSSH</span></span>](https://github.com/PowerShell/Win32-OpenSSH/releases)

[<span data-ttu-id="c7ced-191">installationen</span><span class="sxs-lookup"><span data-stu-id="c7ced-191">installation</span></span>](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[<span data-ttu-id="c7ced-192">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="c7ced-192">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
