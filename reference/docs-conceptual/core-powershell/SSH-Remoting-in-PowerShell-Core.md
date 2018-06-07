# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="dac96-101">PowerShell fjärrkommunikation via SSH</span><span class="sxs-lookup"><span data-stu-id="dac96-101">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="dac96-102">Översikt</span><span class="sxs-lookup"><span data-stu-id="dac96-102">Overview</span></span>

<span data-ttu-id="dac96-103">PowerShell-fjärrkommunikation används normalt WinRM för anslutningen förhandling och datatransport.</span><span class="sxs-lookup"><span data-stu-id="dac96-103">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span>
<span data-ttu-id="dac96-104">SSH valdes för den här implementeringen för fjärrkommunikation eftersom den är nu tillgängliga för både Linux och Windows-plattformar och tillåter true flera plattformar PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="dac96-104">SSH was chosen for this remoting implementation since it is now available for both Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>
<span data-ttu-id="dac96-105">WinRM tillhandahåller dock även en robust värdmodell för PowerShell fjärrsessioner som den här implementeringen ännu inte.</span><span class="sxs-lookup"><span data-stu-id="dac96-105">However, WinRM also provides a robust hosting model for PowerShell remote sessions which this implementation does not yet do.</span></span>
<span data-ttu-id="dac96-106">Och det innebär att fjärrslutpunkten PowerShell-konfigurationen och JEA (Just tillräckligt Administration) ännu inte stöds i den här implementeringen.</span><span class="sxs-lookup"><span data-stu-id="dac96-106">And this means that PowerShell remote endpoint configuration and JEA (Just Enough Administration) is not yet supported in this implementation.</span></span>

<span data-ttu-id="dac96-107">PowerShell SSH fjärrkommunikation kan du göra enkla PowerShell-session fjärrkommunikation mellan Windows och Linux-datorer.</span><span class="sxs-lookup"><span data-stu-id="dac96-107">PowerShell SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span>
<span data-ttu-id="dac96-108">Detta görs genom att skapa en PowerShell värd process på måldatorn som en SSH-undersystem.</span><span class="sxs-lookup"><span data-stu-id="dac96-108">This is done by creating a PowerShell hosting process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="dac96-109">Detta kommer slutligen att ändras till en mer allmän värdmodell som liknar hur WinRM fungerar för att stödja slutpunktskonfiguration och JEA.</span><span class="sxs-lookup"><span data-stu-id="dac96-109">Eventually this will be changed to a more general hosting model similar to how WinRM works in order to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="dac96-110">New-PSSession, Enter-PSSession och Invoke-Command-cmdlets har nu en ny parameter som anger att underlätta nya fjärrkommunikation anslutningen</span><span class="sxs-lookup"><span data-stu-id="dac96-110">The New-PSSession, Enter-PSSession and Invoke-Command cmdlets now have a new parameter set to facilitate this new remoting connection</span></span>

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="dac96-111">Den här nya parameteruppsättning ändras troligen men nu kan du skapa SSH flertal PSSessions som du kan interagera med från kommandoraden eller anropa kommandon och skript på.</span><span class="sxs-lookup"><span data-stu-id="dac96-111">This new parameter set will likely change but for now allows you to create SSH PSSessions that you can interact with from the command line or invoke commands and scripts on.</span></span>
<span data-ttu-id="dac96-112">Du anger måldatorn med parametern värdnamn och ange användarnamn med användarnamnet.</span><span class="sxs-lookup"><span data-stu-id="dac96-112">You specify the target machine with the HostName parameter and provide the user name with UserName.</span></span>
<span data-ttu-id="dac96-113">När du kör cmdlet: arna interaktivt på kommandoraden PowerShell uppmanas du att ange ett lösenord.</span><span class="sxs-lookup"><span data-stu-id="dac96-113">When running the cmdlets interactively at the PowerShell command line you will be prompted for a password.</span></span>
<span data-ttu-id="dac96-114">Men du har också möjlighet att använda SSH-nyckelautentisering och ange en sökväg till filen för privat nyckel med parametern KeyFilePath.</span><span class="sxs-lookup"><span data-stu-id="dac96-114">But you also have the option to use SSH key authentication and provide a private key file path with the KeyFilePath parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="dac96-115">Allmänna inställningar</span><span class="sxs-lookup"><span data-stu-id="dac96-115">General setup information</span></span>

<span data-ttu-id="dac96-116">SSH är måste vara installerat på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="dac96-116">SSH is required to be installed on all machines.</span></span>
<span data-ttu-id="dac96-117">Du bör installera både klient (ssh.exe) och server (sshd.exe) så att du kan experimentera med fjärrkommunikation till och från datorerna.</span><span class="sxs-lookup"><span data-stu-id="dac96-117">You should install both client (ssh.exe) and server (sshd.exe) so that you can experiment with remoting to and from the machines.</span></span>
<span data-ttu-id="dac96-118">Du behöver installera för Windows [Win32 OpenSSH från GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="dac96-118">For Windows you will need to install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="dac96-119">För Linux behöver du installera SSH (inklusive sshd server) är lämpligt för din plattform.</span><span class="sxs-lookup"><span data-stu-id="dac96-119">For Linux you will need to install SSH (including sshd server) appropriate to your platform.</span></span>
<span data-ttu-id="dac96-120">Du måste också en senare version av PowerShell eller ett paket från GitHub med SSH-fjärrkommunikationsfunktionen.</span><span class="sxs-lookup"><span data-stu-id="dac96-120">You will also need a recent PowerShell build or package from GitHub having the SSH remoting feature.</span></span>
<span data-ttu-id="dac96-121">SSH-undersystem som används för att upprätta en PowerShell-process på fjärrdatorn och SSH-server måste konfigureras för den.</span><span class="sxs-lookup"><span data-stu-id="dac96-121">SSH subsystems is used to establish a PowerShell process on the remote machine and the SSH server will need to be configured for that.</span></span>
<span data-ttu-id="dac96-122">Dessutom behöver du aktivera autentisering med lösenord och eventuellt viktiga autentisering.</span><span class="sxs-lookup"><span data-stu-id="dac96-122">In addition you will need to enable password authentication and optionally key based authentication.</span></span>

## <a name="setup-on-windows-machine"></a><span data-ttu-id="dac96-123">Installation på Windows-dator</span><span class="sxs-lookup"><span data-stu-id="dac96-123">Setup on Windows Machine</span></span>

1. <span data-ttu-id="dac96-124">Installera den senaste versionen av [PowerShell Core för Windows]</span><span class="sxs-lookup"><span data-stu-id="dac96-124">Install the latest version of [PowerShell Core for Windows]</span></span>
    - <span data-ttu-id="dac96-125">Berätta om den har stöd för SSH-fjärrkommunikation genom att titta på parameteruppsättningar för New-PSSession</span><span class="sxs-lookup"><span data-stu-id="dac96-125">You can tell if it has the SSH remoting support by looking at the parameter sets for New-PSSession</span></span>

    ```powershell
    PS> Get-Command New-PSSession -syntax
    New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
    ```

1. <span data-ttu-id="dac96-126">Installera senaste [Win32-OpenSSH] skapa från GitHub använder den [installation] instruktioner</span><span class="sxs-lookup"><span data-stu-id="dac96-126">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
1. <span data-ttu-id="dac96-127">Redigera filen sshd_config på den plats där du installerade Win32 OpenSSH</span><span class="sxs-lookup"><span data-stu-id="dac96-127">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>
    - <span data-ttu-id="dac96-128">Kontrollera att lösenordsautentisering är aktiverat</span><span class="sxs-lookup"><span data-stu-id="dac96-128">Make sure password authentication is enabled</span></span>

    ```
    PasswordAuthentication yes
    ```

    - <span data-ttu-id="dac96-129">Lägga till en PowerShell-undersystemet post genom att ersätta `c:/program files/powershell/6.0.0/pwsh.exe` med rätt sökväg till den version som du vill använda</span><span class="sxs-lookup"><span data-stu-id="dac96-129">Add a PowerShell subsystem entry, replace `c:/program files/powershell/6.0.0/pwsh.exe` with the correct path to the version you want to use</span></span>

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    - <span data-ttu-id="dac96-130">Om du vill aktivera autentisering med nyckel</span><span class="sxs-lookup"><span data-stu-id="dac96-130">Optionally enable key authentication</span></span>

    ```
    PubkeyAuthentication yes
    ```

1. <span data-ttu-id="dac96-131">Starta om tjänsten sshd</span><span class="sxs-lookup"><span data-stu-id="dac96-131">Restart the sshd service</span></span>

    ```powershell
    Restart-Service sshd
    ```

1. <span data-ttu-id="dac96-132">Lägg till sökvägen där OpenSSH installeras på din sökväg Env variabel</span><span class="sxs-lookup"><span data-stu-id="dac96-132">Add the path where OpenSSH is installed to your Path Env Variable</span></span>
    - <span data-ttu-id="dac96-133">Detta bör vara längs linjer `C:\Program Files\OpenSSH\`</span><span class="sxs-lookup"><span data-stu-id="dac96-133">This should be along the lines of `C:\Program Files\OpenSSH\`</span></span>
    - <span data-ttu-id="dac96-134">Detta möjliggör ssh.exe ska finnas</span><span class="sxs-lookup"><span data-stu-id="dac96-134">This allows for the ssh.exe to be found</span></span>

## <a name="setup-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="dac96-135">Installationen på datorn för Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="dac96-135">Setup on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="dac96-136">Installera senaste [PowerShell för Linux] skapa från GitHub</span><span class="sxs-lookup"><span data-stu-id="dac96-136">Install the latest [PowerShell for Linux] build from GitHub</span></span>
1. <span data-ttu-id="dac96-137">Installera [Ubuntu SSH] efter behov</span><span class="sxs-lookup"><span data-stu-id="dac96-137">Install [Ubuntu SSH] as needed</span></span>

    ```bash
    sudo apt install openssh-client
    sudo apt install openssh-server
    ```

1. <span data-ttu-id="dac96-138">Redigera filen sshd_config på plats /etc/ssh</span><span class="sxs-lookup"><span data-stu-id="dac96-138">Edit the sshd_config file at location /etc/ssh</span></span>
    - <span data-ttu-id="dac96-139">Kontrollera att lösenordsautentisering är aktiverat</span><span class="sxs-lookup"><span data-stu-id="dac96-139">Make sure password authentication is enabled</span></span>

    ```
    PasswordAuthentication yes
    ```

    - <span data-ttu-id="dac96-140">Lägga till en PowerShell-undersystemet post</span><span class="sxs-lookup"><span data-stu-id="dac96-140">Add a PowerShell subsystem entry</span></span>

    ```
    Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
    ```

    - <span data-ttu-id="dac96-141">Om du vill aktivera autentisering med nyckel</span><span class="sxs-lookup"><span data-stu-id="dac96-141">Optionally enable key authentication</span></span>

    ```
    PubkeyAuthentication yes
    ```

1. <span data-ttu-id="dac96-142">Starta om tjänsten sshd</span><span class="sxs-lookup"><span data-stu-id="dac96-142">Restart the sshd service</span></span>

    ```bash
    sudo service sshd restart
    ```

## <a name="setup-on-macos-machine"></a><span data-ttu-id="dac96-143">Installation på MacOS datorn</span><span class="sxs-lookup"><span data-stu-id="dac96-143">Setup on MacOS Machine</span></span>

1. <span data-ttu-id="dac96-144">Installera senaste [PowerShell för MacOS] skapa</span><span class="sxs-lookup"><span data-stu-id="dac96-144">Install the latest [PowerShell for MacOS] build</span></span>
    - <span data-ttu-id="dac96-145">Se till att SSH fjärrkommunikation är aktiverad på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="dac96-145">Make sure SSH Remoting is enabled by following these steps:</span></span>
      - <span data-ttu-id="dac96-146">Öppna `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="dac96-146">Open `System Preferences`</span></span>
      - <span data-ttu-id="dac96-147">Klicka på `Sharing`</span><span class="sxs-lookup"><span data-stu-id="dac96-147">Click on `Sharing`</span></span>
      - <span data-ttu-id="dac96-148">Kontrollera `Remote Login` -ska stå `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="dac96-148">Check `Remote Login` - Should say `Remote Login: On`</span></span>
      - <span data-ttu-id="dac96-149">Tillåt åtkomst till behöriga användare</span><span class="sxs-lookup"><span data-stu-id="dac96-149">Allow access to appropriate users</span></span>
1. <span data-ttu-id="dac96-150">Redigera den `sshd_config` fil på plats `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="dac96-150">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>
    - <span data-ttu-id="dac96-151">Använd din favorit redigerare eller</span><span class="sxs-lookup"><span data-stu-id="dac96-151">Use your favorite editor or</span></span>

    ```bash
    sudo nano /private/etc/ssh/sshd_config
    ```

    - <span data-ttu-id="dac96-152">Kontrollera att lösenordsautentisering är aktiverat</span><span class="sxs-lookup"><span data-stu-id="dac96-152">Make sure password authentication is enabled</span></span>

    ```
    PasswordAuthentication yes
    ```

    - <span data-ttu-id="dac96-153">Lägga till en PowerShell-undersystemet post</span><span class="sxs-lookup"><span data-stu-id="dac96-153">Add a PowerShell subsystem entry</span></span>

    ```
    Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
    ```

    - <span data-ttu-id="dac96-154">Om du vill aktivera autentisering med nyckel</span><span class="sxs-lookup"><span data-stu-id="dac96-154">Optionally enable key authentication</span></span>

    ```
    PubkeyAuthentication yes
    ```

1. <span data-ttu-id="dac96-155">Starta om tjänsten sshd</span><span class="sxs-lookup"><span data-stu-id="dac96-155">Restart the sshd service</span></span>

    ```bash
    sudo launchctl stop com.openssh.sshd
    sudo launchctl start com.openssh.sshd
    ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="dac96-156">Exempel på PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="dac96-156">PowerShell Remoting Example</span></span>

<span data-ttu-id="dac96-157">Det enklaste sättet att testa fjärrkommunikation är bara testa programmet på en enskild dator.</span><span class="sxs-lookup"><span data-stu-id="dac96-157">The easiest way to test remoting is to just try it on a single machine.</span></span>
<span data-ttu-id="dac96-158">Här skapar jag en fjärrsession tillbaka till samma dator på en Linux-ruta.</span><span class="sxs-lookup"><span data-stu-id="dac96-158">Here I will create a remote session back to the same machine on a Linux box.</span></span>
<span data-ttu-id="dac96-159">Observera att jag använder PowerShell-cmdlets från en kommandorad så att vi se anvisningarna från SSH ber att verifiera värddatorn samt lösenordet på nytt.</span><span class="sxs-lookup"><span data-stu-id="dac96-159">Notice that I am using PowerShell cmdlets from a command prompt so we see prompts from SSH asking to verify the host computer as well as password prompts.</span></span>
<span data-ttu-id="dac96-160">Du kan göra det på en Windows-dator för fjärrkommunikation fungerar det och sedan remote mellan datorer genom att ändra värdnamnet.</span><span class="sxs-lookup"><span data-stu-id="dac96-160">You can do the same thing on a Windows machine to ensure remoting is working there and then remote between machines by simply changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
PS /home/TestUser> $session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:

PS /home/TestUser> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available

PS /home/TestUser> Enter-PSSession $session

[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession

PS /home/TestUser> Invoke-Command $session -ScriptBlock { Get-Process powershell }

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1


#
# Linux to Windows
#
PS /home/TestUser> Enter-PSSession -HostName WinVM1 -UserName PTestName
PTestName@WinVM1s password:

[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver

Microsoft Windows [Version 10.0.10586]

[WinVM1]: PS C:\Users\PTestName\Documents>

#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.

PS C:\Users\PSUser\Documents> $session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
PS C:\Users\PSUser\Documents> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available


PS C:\Users\PSUser\Documents> Enter-PSSession -Session $session
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

### <a name="known-issues"></a><span data-ttu-id="dac96-161">Kända problem</span><span class="sxs-lookup"><span data-stu-id="dac96-161">Known Issues</span></span>

1. <span data-ttu-id="dac96-162">sudo-kommando fungerar inte i fjärrsessionen till Linux-datorn.</span><span class="sxs-lookup"><span data-stu-id="dac96-162">sudo command does not work in remote session to Linux machine.</span></span>

[PowerShell Core för Windows]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi
[PowerShell Core for Windows]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi
[Win32-OpenSSH]: https://github.com/PowerShell/Win32-OpenSSH/releases
[Win32 OpenSSH]: https://github.com/PowerShell/Win32-OpenSSH/releases
[Installation]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[installation]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[PowerShell för Linux]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#ubuntu-1404
[PowerShell for Linux]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#ubuntu-1404
[Ubuntu SSH]: https://help.ubuntu.com/lts/serverguide/openssh-server.html
[PowerShell för MacOS]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/macos.md#macos-1012
[PowerShell for MacOS]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/macos.md#macos-1012
