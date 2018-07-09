
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="78e65-101">PowerShell fjärrkommunikation via SSH</span><span class="sxs-lookup"><span data-stu-id="78e65-101">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="78e65-102">Översikt</span><span class="sxs-lookup"><span data-stu-id="78e65-102">Overview</span></span>

<span data-ttu-id="78e65-103">PowerShell-fjärrkommunikation använder vanligen WinRM för förhandling för anslutning och dataöverföring.</span><span class="sxs-lookup"><span data-stu-id="78e65-103">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span>
<span data-ttu-id="78e65-104">SSH har valts för den här implementeringen av fjärrkörning eftersom det är nu tillgängliga för både Linux och Windows-plattformar och tillåter SANT PowerShell-fjärrkommunikation på flera plattformar.</span><span class="sxs-lookup"><span data-stu-id="78e65-104">SSH was chosen for this remoting implementation since it is now available for both Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>
<span data-ttu-id="78e65-105">WinRM tillhandahåller dock även en robust värdmodell för PowerShell fjärrsessioner som den här implementeringen inte gör ännu.</span><span class="sxs-lookup"><span data-stu-id="78e65-105">However, WinRM also provides a robust hosting model for PowerShell remote sessions which this implementation does not yet do.</span></span>
<span data-ttu-id="78e65-106">Och det innebär att PowerShell fjärrslutpunkten konfigurations- och JEA (Just Enough Administration) inte stöds ännu i den här implementeringen.</span><span class="sxs-lookup"><span data-stu-id="78e65-106">And this means that PowerShell remote endpoint configuration and JEA (Just Enough Administration) is not yet supported in this implementation.</span></span>

<span data-ttu-id="78e65-107">PowerShell SSH fjärrkommunikation kan du göra grundläggande session PowerShell-fjärrkommunikation mellan Windows och Linux-datorer.</span><span class="sxs-lookup"><span data-stu-id="78e65-107">PowerShell SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span>
<span data-ttu-id="78e65-108">Detta görs genom att skapa ett PowerShell som är värd för processen på måldatorn som ett SSH-undersystem.</span><span class="sxs-lookup"><span data-stu-id="78e65-108">This is done by creating a PowerShell hosting process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="78e65-109">Detta kommer så småningom att ändras till en mer allmän värdmodell som liknar hur WinRM fungerar för att stödja slutpunktskonfiguration och JEA.</span><span class="sxs-lookup"><span data-stu-id="78e65-109">Eventually this will be changed to a more general hosting model similar to how WinRM works in order to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="78e65-110">Den `New-PSSession`, `Enter-PSSession` och `Invoke-Command` cmdletarna har nu en ny parameter som anger att underlätta den här nya fjärrkommunikation-anslutningen</span><span class="sxs-lookup"><span data-stu-id="78e65-110">The `New-PSSession`, `Enter-PSSession` and `Invoke-Command` cmdlets now have a new parameter set to facilitate this new remoting connection</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="78e65-111">Den här nya parameteruppsättningen troligen kommer att förändras men nu kan du skapa SSH flertal PSSessions att du kan interagera med från kommandoraden eller anropa kommandon och skript på.</span><span class="sxs-lookup"><span data-stu-id="78e65-111">This new parameter set will likely change but for now allows you to create SSH PSSessions that you can interact with from the command line or invoke commands and scripts on.</span></span>
<span data-ttu-id="78e65-112">Du anger måldatorn med parametern värdnamn och ange användarnamn med användarnamnet.</span><span class="sxs-lookup"><span data-stu-id="78e65-112">You specify the target machine with the HostName parameter and provide the user name with UserName.</span></span>
<span data-ttu-id="78e65-113">När du kör cmdletarna interaktivt på PowerShell-kommandoraden uppmanas du att ange ett lösenord.</span><span class="sxs-lookup"><span data-stu-id="78e65-113">When running the cmdlets interactively at the PowerShell command line you will be prompted for a password.</span></span>
<span data-ttu-id="78e65-114">Men du har också möjlighet att använda SSH-nyckelautentisering och ange en sökväg till filen för privat nyckel med parametern KeyFilePath.</span><span class="sxs-lookup"><span data-stu-id="78e65-114">But you also have the option to use SSH key authentication and provide a private key file path with the KeyFilePath parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="78e65-115">Allmänna inställningar</span><span class="sxs-lookup"><span data-stu-id="78e65-115">General setup information</span></span>

<span data-ttu-id="78e65-116">SSH är måste vara installerat på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="78e65-116">SSH is required to be installed on all machines.</span></span>
<span data-ttu-id="78e65-117">Du bör installera både klienten (`ssh.exe`) och server (`sshd.exe`) så att du kan experimentera med fjärrkommunikation till och från datorerna.</span><span class="sxs-lookup"><span data-stu-id="78e65-117">You should install both client (`ssh.exe`) and server (`sshd.exe`) so that you can experiment with remoting to and from the machines.</span></span>
<span data-ttu-id="78e65-118">För Windows kommer du behöva installera [Win32-OpenSSH från GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="78e65-118">For Windows you will need to install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="78e65-119">För Linux behöver installera SSH (inklusive sshd-servern) lämpligt för din plattform.</span><span class="sxs-lookup"><span data-stu-id="78e65-119">For Linux you will need to install SSH (including sshd server) appropriate to your platform.</span></span>
<span data-ttu-id="78e65-120">Du måste också en senaste PowerShell-version eller ett paket från GitHub med SSH-fjärrkommunikationsfunktionen.</span><span class="sxs-lookup"><span data-stu-id="78e65-120">You will also need a recent PowerShell build or package from GitHub having the SSH remoting feature.</span></span>
<span data-ttu-id="78e65-121">SSH-undersystem som används för att upprätta en PowerShell-process på fjärrdatorn och SSH-servern måste konfigureras för den.</span><span class="sxs-lookup"><span data-stu-id="78e65-121">SSH subsystems is used to establish a PowerShell process on the remote machine and the SSH server will need to be configured for that.</span></span>
<span data-ttu-id="78e65-122">Du måste dessutom aktivera lösenordsautentisering och du kan också baserat nyckelautentisering.</span><span class="sxs-lookup"><span data-stu-id="78e65-122">In addition you will need to enable password authentication and optionally key based authentication.</span></span>

## <a name="setup-on-windows-machine"></a><span data-ttu-id="78e65-123">Installera på Windows-dator</span><span class="sxs-lookup"><span data-stu-id="78e65-123">Setup on Windows Machine</span></span>

1. <span data-ttu-id="78e65-124">Installera den senaste versionen av [PowerShell Core för Windows]</span><span class="sxs-lookup"><span data-stu-id="78e65-124">Install the latest version of [PowerShell Core for Windows]</span></span>
   - <span data-ttu-id="78e65-125">Berätta om den har stöd för SSH-fjärrkommunikation genom att titta på parameteruppsättningar för `New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="78e65-125">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="78e65-126">Installera den senaste versionen av [Win32-OpenSSH] från GitHub med hjälp av [installationsinstruktionerna]</span><span class="sxs-lookup"><span data-stu-id="78e65-126">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
3. <span data-ttu-id="78e65-127">Redigera sshd_config-filen på den plats där du installerade Win32 OpenSSH</span><span class="sxs-lookup"><span data-stu-id="78e65-127">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>
   - <span data-ttu-id="78e65-128">Kontrollera att lösenordsautentisering är aktiverad</span><span class="sxs-lookup"><span data-stu-id="78e65-128">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    > [!NOTE]
    <span data-ttu-id="78e65-129">Det finns en bugg i OpenSSH för Windows som förhindrar att blanksteg fungerar i undersystemet körbara sökvägar.</span><span class="sxs-lookup"><span data-stu-id="78e65-129">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span>
    <span data-ttu-id="78e65-130">Se [problemet på GitHub för mer information](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="78e65-130">See [this issue on GitHub for more information](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

    <span data-ttu-id="78e65-131">En lösning är att skapa en symlink till installationskatalogen för Powershell som inte innehåller blanksteg:</span><span class="sxs-lookup"><span data-stu-id="78e65-131">One solution is to create a symlink to the Powershell installation directory that does not contain spaces:</span></span>

    ```powershell
    mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.0"
    ```

    <span data-ttu-id="78e65-132">och sedan ange den i undersystemet:</span><span class="sxs-lookup"><span data-stu-id="78e65-132">and then enter it in the subsystem:</span></span>

    ```
    Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
    ```

   ```
   Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="78e65-133">Du kan också aktivera nyckelautentisering</span><span class="sxs-lookup"><span data-stu-id="78e65-133">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="78e65-134">Starta om tjänsten sshd</span><span class="sxs-lookup"><span data-stu-id="78e65-134">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="78e65-135">Lägga till sökvägen där OpenSSH installeras på din sökväg Env variabel</span><span class="sxs-lookup"><span data-stu-id="78e65-135">Add the path where OpenSSH is installed to your Path Env Variable</span></span>
   - <span data-ttu-id="78e65-136">Detta bör vara längs linjer `C:\Program Files\OpenSSH\`</span><span class="sxs-lookup"><span data-stu-id="78e65-136">This should be along the lines of `C:\Program Files\OpenSSH\`</span></span>
   - <span data-ttu-id="78e65-137">Det möjliggör ssh.exe som ska returneras</span><span class="sxs-lookup"><span data-stu-id="78e65-137">This allows for the ssh.exe to be found</span></span>

## <a name="setup-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="78e65-138">Installationsprogrammet på dator för Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="78e65-138">Setup on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="78e65-139">Installera den senaste versionen av [PowerShell Core för Linux] från GitHub</span><span class="sxs-lookup"><span data-stu-id="78e65-139">Install the latest [PowerShell Core for Linux] build from GitHub</span></span>
2. <span data-ttu-id="78e65-140">Installera [Ubuntu SSH] vid behov</span><span class="sxs-lookup"><span data-stu-id="78e65-140">Install [Ubuntu SSH] as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="78e65-141">Redigera sshd_config-filen på plats /etc/ssh</span><span class="sxs-lookup"><span data-stu-id="78e65-141">Edit the sshd_config file at location /etc/ssh</span></span>
   - <span data-ttu-id="78e65-142">Kontrollera att lösenordsautentisering är aktiverad</span><span class="sxs-lookup"><span data-stu-id="78e65-142">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="78e65-143">Lägga till en post för PowerShell-undersystemet</span><span class="sxs-lookup"><span data-stu-id="78e65-143">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="78e65-144">Du kan också aktivera nyckelautentisering</span><span class="sxs-lookup"><span data-stu-id="78e65-144">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="78e65-145">Starta om tjänsten sshd</span><span class="sxs-lookup"><span data-stu-id="78e65-145">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="setup-on-macos-machine"></a><span data-ttu-id="78e65-146">Konfigurera i Mac OS-dator</span><span class="sxs-lookup"><span data-stu-id="78e65-146">Setup on MacOS Machine</span></span>

1. <span data-ttu-id="78e65-147">Installera den senaste versionen av [PowerShell Core för MacOS]</span><span class="sxs-lookup"><span data-stu-id="78e65-147">Install the latest [PowerShell Core for MacOS] build</span></span>
   - <span data-ttu-id="78e65-148">Kontrollera att SSH-fjärrkommunikation är aktiverat genom att följa dessa steg:</span><span class="sxs-lookup"><span data-stu-id="78e65-148">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="78e65-149">Öppna `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="78e65-149">Open `System Preferences`</span></span>
     - <span data-ttu-id="78e65-150">Klicka på `Sharing`</span><span class="sxs-lookup"><span data-stu-id="78e65-150">Click on `Sharing`</span></span>
     - <span data-ttu-id="78e65-151">Kontrollera `Remote Login` -ska stå `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="78e65-151">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="78e65-152">Tillåt åtkomst till rätt användare</span><span class="sxs-lookup"><span data-stu-id="78e65-152">Allow access to appropriate users</span></span>
2. <span data-ttu-id="78e65-153">Redigera den `sshd_config` fil på plats `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="78e65-153">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>
   - <span data-ttu-id="78e65-154">Använda din favoritredigerare eller</span><span class="sxs-lookup"><span data-stu-id="78e65-154">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="78e65-155">Kontrollera att lösenordsautentisering är aktiverad</span><span class="sxs-lookup"><span data-stu-id="78e65-155">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="78e65-156">Lägga till en post för PowerShell-undersystemet</span><span class="sxs-lookup"><span data-stu-id="78e65-156">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="78e65-157">Du kan också aktivera nyckelautentisering</span><span class="sxs-lookup"><span data-stu-id="78e65-157">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="78e65-158">Starta om tjänsten sshd</span><span class="sxs-lookup"><span data-stu-id="78e65-158">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="78e65-159">Exempel på PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="78e65-159">PowerShell Remoting Example</span></span>

<span data-ttu-id="78e65-160">Det enklaste sättet att testa fjärrkommunikation är att testa den på en enda dator.</span><span class="sxs-lookup"><span data-stu-id="78e65-160">The easiest way to test remoting is to just try it on a single machine.</span></span>
<span data-ttu-id="78e65-161">Här skapar jag en fjärrsession tillbaka till samma dator på en Linux-ruta.</span><span class="sxs-lookup"><span data-stu-id="78e65-161">Here I will create a remote session back to the same machine on a Linux box.</span></span>
<span data-ttu-id="78e65-162">Observera att jag använder PowerShell-cmdletar från en kommandotolk, så vi se meddelanden från SSH där du ombeds att kontrollera värddator samt frågor för lösenord.</span><span class="sxs-lookup"><span data-stu-id="78e65-162">Notice that I am using PowerShell cmdlets from a command prompt so we see prompts from SSH asking to verify the host computer as well as password prompts.</span></span>
<span data-ttu-id="78e65-163">Du kan göra samma sak på en Windows-dator fjärrkommunikation fungerar det och sedan remote mellan datorer genom att ändra värdnamnet.</span><span class="sxs-lookup"><span data-stu-id="78e65-163">You can do the same thing on a Windows machine to ensure remoting is working there and then remote between machines by simply changing the host name.</span></span>

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
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available
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

### <a name="known-issues"></a><span data-ttu-id="78e65-164">Kända problem</span><span class="sxs-lookup"><span data-stu-id="78e65-164">Known Issues</span></span>

- <span data-ttu-id="78e65-165">sudo-kommando fungerar inte i fjärrsession till Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="78e65-165">sudo command does not work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="78e65-166">Se även</span><span class="sxs-lookup"><span data-stu-id="78e65-166">See Also</span></span>

[<span data-ttu-id="78e65-167">PowerShell Core för Windows</span><span class="sxs-lookup"><span data-stu-id="78e65-167">PowerShell Core for Windows</span></span>](../setup/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="78e65-168">PowerShell Core för Linux</span><span class="sxs-lookup"><span data-stu-id="78e65-168">PowerShell Core for Linux</span></span>](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="78e65-169">PowerShell Core för MacOS</span><span class="sxs-lookup"><span data-stu-id="78e65-169">PowerShell Core for MacOS</span></span>](../setup/installing-powershell-core-on-macos.md)

[<span data-ttu-id="78e65-170">Win32-OpenSSH</span><span class="sxs-lookup"><span data-stu-id="78e65-170">Win32 OpenSSH</span></span>](https://github.com/PowerShell/Win32-OpenSSH/releases)

[<span data-ttu-id="78e65-171">installationen</span><span class="sxs-lookup"><span data-stu-id="78e65-171">installation</span></span>](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[<span data-ttu-id="78e65-172">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="78e65-172">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)