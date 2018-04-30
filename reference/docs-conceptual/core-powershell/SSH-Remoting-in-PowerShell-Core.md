# <a name="powershell-remoting-over-ssh"></a>PowerShell fjärrkommunikation via SSH

## <a name="overview"></a>Översikt

PowerShell-fjärrkommunikation används normalt WinRM för anslutningen förhandling och datatransport.
SSH valdes för den här implementeringen för fjärrkommunikation eftersom den är nu tillgängliga för både Linux och Windows-plattformar och tillåter true flera plattformar PowerShell-fjärrkommunikation.
WinRM tillhandahåller dock även en robust värdmodell för PowerShell fjärrsessioner som den här implementeringen ännu inte.
Och det innebär att fjärrslutpunkten PowerShell-konfigurationen och JEA (Just tillräckligt Administration) ännu inte stöds i den här implementeringen.

PowerShell SSH fjärrkommunikation kan du göra enkla PowerShell-session fjärrkommunikation mellan Windows och Linux-datorer.
Detta görs genom att skapa en PowerShell värd process på måldatorn som en SSH-undersystem.
Detta kommer slutligen att ändras till en mer allmän värdmodell som liknar hur WinRM fungerar för att stödja slutpunktskonfiguration och JEA.

New-PSSession, Enter-PSSession och Invoke-Command-cmdlets har nu en ny parameter som anger att underlätta nya fjärrkommunikation anslutningen

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Den här nya parameteruppsättning ändras troligen men nu kan du skapa SSH flertal PSSessions som du kan interagera med från kommandoraden eller anropa kommandon och skript på.
Du anger måldatorn med parametern värdnamn och ange användarnamn med användarnamnet.
När du kör cmdlet: arna interaktivt på kommandoraden PowerShell uppmanas du att ange ett lösenord.
Men du har också möjlighet att använda SSH-nyckelautentisering och ange en sökväg till filen för privat nyckel med parametern KeyFilePath.

## <a name="general-setup-information"></a>Allmänna inställningar

SSH är måste vara installerat på alla datorer.
Du bör installera både klient (ssh.exe) och server (sshd.exe) så att du kan experimentera med fjärrkommunikation till och från datorerna.
Du behöver installera för Windows [Win32 OpenSSH från GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).
För Linux behöver du installera SSH (inklusive sshd server) är lämpligt för din plattform.
Du måste också en senare version av PowerShell eller ett paket från GitHub med SSH-fjärrkommunikationsfunktionen.
SSH-undersystem som används för att upprätta en PowerShell-process på fjärrdatorn och SSH-server måste konfigureras för den.
Dessutom behöver du aktivera autentisering med lösenord och eventuellt viktiga autentisering.

## <a name="setup-on-windows-machine"></a>Installation på Windows-dator

1. Installera den senaste versionen av [PowerShell Core för Windows]
    - Berätta om den har stöd för SSH-fjärrkommunikation genom att titta på parameteruppsättningar för New-PSSession

    ```powershell
    PS> Get-Command New-PSSession -syntax
    New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
    ```

1. Installera senaste [Win32 OpenSSH] skapa från GitHub använder den [installation] instruktioner
1. Redigera filen sshd_config på den plats där du installerade Win32 OpenSSH
    - Kontrollera att lösenordsautentisering är aktiverat

    ```
    PasswordAuthentication yes
    ```

    - Lägga till en PowerShell-undersystemet post genom att ersätta `c:/program files/powershell/6.0.0/pwsh.exe` med rätt sökväg till den version som du vill använda

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    - Om du vill aktivera autentisering med nyckel

    ```
    PubkeyAuthentication yes
    ```

1. Starta om tjänsten sshd

    ```powershell
    Restart-Service sshd
    ```

1. Lägg till sökvägen där OpenSSH installeras på din sökväg Env variabel
    - Detta bör vara längs linjer `C:\Program Files\OpenSSH\`
    - Detta möjliggör ssh.exe ska finnas

## <a name="setup-on-linux-ubuntu-1404-machine"></a>Installationen på datorn för Linux (Ubuntu 14.04)

1. Installera senaste [PowerShell för Linux] skapa från GitHub
1. Installera [Ubuntu SSH] efter behov

    ```bash
    sudo apt install openssh-client
    sudo apt install openssh-server
    ```

1. Redigera filen sshd_config på plats /etc/ssh
    - Kontrollera att lösenordsautentisering är aktiverat

    ```
    PasswordAuthentication yes
    ```

    - Lägga till en PowerShell-undersystemet post

    ```
    Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
    ```

    - Om du vill aktivera autentisering med nyckel

    ```
    PubkeyAuthentication yes
    ```

1. Starta om tjänsten sshd

    ```bash
    sudo service sshd restart
    ```

## <a name="setup-on-macos-machine"></a>Installation på MacOS datorn

1. Installera senaste [PowerShell för MacOS] skapa
    - Se till att SSH fjärrkommunikation är aktiverad på följande sätt:
      - Öppna `System Preferences`
      - Klicka på `Sharing`
      - Kontrollera `Remote Login` -ska stå `Remote Login: On`
      - Tillåt åtkomst till behöriga användare
1. Redigera den `sshd_config` fil på plats `/private/etc/ssh/sshd_config`
    - Använd din favorit redigerare eller

    ```bash
    sudo nano /private/etc/ssh/sshd_config
    ```

    - Kontrollera att lösenordsautentisering är aktiverat

    ```
    PasswordAuthentication yes
    ```

    - Lägga till en PowerShell-undersystemet post

    ```
    Subsystem powershell /usr/local/bin/powershell -sshs -NoLogo -NoProfile
    ```

    - Om du vill aktivera autentisering med nyckel

    ```
    PubkeyAuthentication yes
    ```

1. Starta om tjänsten sshd

    ```bash
    sudo launchctl stop com.openssh.sshd
    sudo launchctl start com.openssh.sshd
    ```

## <a name="powershell-remoting-example"></a>Exempel på PowerShell-fjärrkommunikation

Det enklaste sättet att testa fjärrkommunikation är bara testa programmet på en enskild dator.
Här skapar jag en fjärrsession tillbaka till samma dator på en Linux-ruta.
Observera att jag använder PowerShell-cmdlets från en kommandorad så att vi se anvisningarna från SSH ber att verifiera värddatorn samt lösenordet på nytt.
Du kan göra det på en Windows-dator för fjärrkommunikation fungerar det och sedan remote mellan datorer genom att ändra värdnamnet.

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

### <a name="known-issues"></a>Kända problem

1. sudo-kommando fungerar inte i fjärrsessionen till Linux-datorn.

[PowerShell Core för Windows]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi
[Win32 OpenSSH]: https://github.com/PowerShell/Win32-OpenSSH
[installation]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[PowerShell för Linux]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#ubuntu-1404
[Ubuntu SSH]: https://help.ubuntu.com/lts/serverguide/openssh-server.html
[PowerShell för MacOS]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/macos.md#macos-1012