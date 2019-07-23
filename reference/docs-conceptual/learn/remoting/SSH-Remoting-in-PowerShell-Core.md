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
# <a name="powershell-remoting-over-ssh"></a>PowerShell fjärrkommunikation via SSH

## <a name="overview"></a>Översikt

PowerShell-fjärrkommunikation använder normalt WinRM för anslutnings förhandling och data transport. SSH är nu tillgängligt för Linux-och Windows-plattformar och tillåter en PowerShell-fjärrkommunikation med multiplatform.

WinRM tillhandahåller en robust värd modell för PowerShell-fjärrsessioner. SSH-baserad fjärr kommunikation har för närvarande inte stöd för konfiguration av Fjärrslutpunkter och JEA (bara för tillräckligt med administration).

Med SSH-fjärrkommunikation kan du utföra grundläggande PowerShell-sessioner mellan Windows-och Linux-datorer. SSH-fjärrkommunikation skapar en PowerShell-värd process på mål datorn som ett SSH-undersystem. Slutligen ska vi implementera en allmän värd modell som liknar WinRM för att stödja slut punkts konfiguration och JEA.

Cmdletarna `Enter-PSSession` ,och`Invoke-Command` har nu en ny parameter inställd för att stödja den här nya fjärr anslutnings anslutningen. `New-PSSession`

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Om du vill skapa en fjärrsession anger du mål datorn med `HostName` parametern och anger användar namnet med. `UserName` När du kör cmdletarna interaktivt, uppmanas du att ange ett lösen ord. Du kan också använda SSH-nyckel-autentisering med hjälp av en privat nyckel `KeyFilePath` fil med parametern.

## <a name="general-setup-information"></a>Allmän installations information

SSH måste vara installerat på alla datorer. Installera både SSH-klienten (`ssh.exe`) och servern (`sshd.exe`) så att du kan fjärrans luta till och från datorerna. OpenSSH för Windows är nu tillgängligt i Windows 10 version 1809 och Windows Server 2019. Mer information finns i [openssh för Windows](/windows-server/administration/openssh/openssh_overview). För Linux installerar du SSH (inklusive sshd-servern) som är lämplig för din plattform. Du måste också installera PowerShell Core från GitHub för att hämta SSH-funktionen för fjärr kommunikation. SSH-servern måste konfigureras för att skapa ett SSH-undersystem som värd för en PowerShell-process på fjärrdatorn. Du måste också konfigurera aktivera lösen ord eller nyckelbaserad autentisering.

## <a name="set-up-on-windows-machine"></a>Konfigurera på Windows-dator

1. Installera den senaste versionen av [PowerShell Core för Windows](../../install/installing-powershell-core-on-windows.md#msi)

   - Du kan se om den har stöd för SSH-fjärrkommunikation genom att titta på parameter uppsättningarna för`New-PSSession`

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. Installera de senaste Win32-OpenSSH. Installations anvisningar finns i [installation av openssh](/windows-server/administration/openssh/openssh_install_firstuse).
3. Redigera filen `sshd_config` som finns på `$env:ProgramData\ssh`.

   - Se till att lösenordsautentisering är aktiverat

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > Det finns ett fel i OpenSSH för Windows som förhindrar att utrymmen fungerar i under systemets körbara sökvägar. Mer information finns i [det här GitHub-problemet](https://github.com/PowerShell/Win32-OpenSSH/issues/784).

     En lösning är att skapa en symlink till installations katalogen för PowerShell som inte innehåller blank steg:

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     och ange det sedan i under systemet:

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - Aktivera nyckel autentisering om du vill

     ```
     PubkeyAuthentication yes
     ```

4. Starta om sshd-tjänsten

   ```powershell
   Restart-Service sshd
   ```

5. Lägg till sökvägen där OpenSSH är installerat i din PATH-miljö variabel. Till exempel `C:\Program Files\OpenSSH\`. Den här posten tillåter att SSH. exe hittas.

## <a name="set-up-on-linux-ubuntu-1604-machine"></a>Konfigurera på Linux-datorn (Ubuntu 16,04)

1. Installera den senaste versionen av [PowerShell Core för Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604) från GitHub
2. Installera [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) vid behov

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. Redigera sshd_config-filen på plats/etc/ssh

   - Se till att lösenordsautentisering är aktiverat

   ```
   PasswordAuthentication yes
   ```

   - Lägg till en PowerShell-delsystem post

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - Aktivera nyckel autentisering om du vill

   ```
   PubkeyAuthentication yes
   ```

4. Starta om sshd-tjänsten

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a>Konfigurera på MacOS-datorn

1. Installera den senaste [PowerShell-kärnan för MacOS](../../install/installing-powershell-core-on-macos.md) -version

   - Se till att SSH-fjärrkommunikation är aktiverat genom att följa dessa steg:
     - Inställningar`System Preferences`
     - Klicka på`Sharing`
     - Kontroll `Remote Login` – bör stå`Remote Login: On`
     - Tillåt åtkomst till lämpliga användare

2. `sshd_config` Redigera filen på plats`/private/etc/ssh/sshd_config`

   - Använd din favorit redigerare eller

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - Se till att lösenordsautentisering är aktiverat

     ```
     PasswordAuthentication yes
     ```

   - Lägg till en PowerShell-delsystem post

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - Aktivera nyckel autentisering om du vill

     ```
     PubkeyAuthentication yes
     ```

3. Starta om sshd-tjänsten

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a>Autentisering

PowerShell-fjärrkommunikation via SSH är beroende av autentiserings utbyte mellan SSH-klienten och SSH-tjänsten och implementerar inte några autentiseringsscheman. Det innebär att alla konfigurerade autentiseringsscheman, inklusive Multi-Factor Authentication, hanteras av SSH och oberoende av PowerShell. Du kan till exempel konfigurera SSH-tjänsten så att den kräver autentisering med offentlig nyckel och eng ång slö sen ord för ytterligare säkerhet. Konfiguration av Multi-Factor Authentication omfattas inte av den här dokumentationen. Läs dokumentationen för SSH om hur du konfigurerar Multi-Factor Authentication på rätt sätt och verifierar att den fungerar utanför PowerShell innan du försöker använda den med PowerShell-fjärrkommunikation.

## <a name="powershell-remoting-example"></a>Exempel på PowerShell-fjärrkommunikation

Det enklaste sättet att testa fjärr kommunikation är att testa den på en enda dator. I det här exemplet skapar vi en fjärrsession tillbaka till samma Linux-dator. Vi använder PowerShell-cmdlets interaktivt så vi ser frågor från SSH som ber om att verifiera värddatorn och uppmanas att ange ett lösen ord. Du kan göra samma sak på en Windows-dator för att säkerställa att fjärr kommunikation fungerar. Fjärranslut sedan mellan datorer genom att ändra värd namnet.

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

### <a name="known-issues"></a>Kända problem

Kommandot sudo fungerar inte i fjärrsession till Linux-datorn.

## <a name="see-also"></a>Se även

[PowerShell Core för Windows](../../install/installing-powershell-core-on-windows.md#msi)

[PowerShell Core för Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[PowerShell Core för MacOS](../../install/installing-powershell-core-on-macos.md)

[OpenSSH för Windows](/windows-server/administration/openssh/openssh_overview)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
