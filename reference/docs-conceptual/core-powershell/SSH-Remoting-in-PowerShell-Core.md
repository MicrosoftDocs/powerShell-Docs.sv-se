---
title: PowerShell fjärrkommunikation via SSH
description: Fjärrkommunikation i PowerShell Core med hjälp av SSH
ms.date: 08/14/2018
ms.openlocfilehash: 451a55a588381cc9bec265895b2bfad6b6f6e73c
ms.sourcegitcommit: a652b12a0b87cdd0c8eb76381ae015467dd7b8cd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/18/2018
ms.locfileid: "46134288"
---
# <a name="powershell-remoting-over-ssh"></a>PowerShell fjärrkommunikation via SSH

## <a name="overview"></a>Översikt

PowerShell-fjärrkommunikation använder vanligen WinRM för förhandling för anslutning och dataöverföring. SSH är nu tillgängligt för Linux och Windows-plattformar och tillåter SANT PowerShell-fjärrkommunikation på flera plattformar.

WinRM tillhandahåller en robust värdmodell för fjärrsessioner i PowerShell. som den här implementeringen SSH-baserad fjärrkommunikation för närvarande inte stöd för fjärrslutpunkten konfigurations- och JEA (Just Enough Administration).

SSH-fjärrkommunikation kan du göra grundläggande session PowerShell-fjärrkommunikation mellan Windows och Linux-datorer. SSH-fjärrkommunikation skapar en värdprocess för PowerShell på måldatorn som ett SSH-undersystem.
Slutligen ska vi implementera en allmän värdmodell, liknar WinRM för slutpunktskonfiguration och JEA.

Den `New-PSSession`, `Enter-PSSession`, och `Invoke-Command` cmdletarna har nu en ny parameter som angetts för den här nya fjärrkommunikation-anslutningen.

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Om du vill skapa en fjärrsession, anger du den target-datorn med den `HostName` parametern och ange användarnamnet med `UserName`. När du kör cmdletarna interaktivt, uppmanas du ett lösenord. Du kan också använda SSH-nyckelautentisering med hjälp av en privat nyckelfil med den `KeyFilePath` parametern.

## <a name="general-setup-information"></a>Allmänna inställningar

SSH måste installeras på alla datorer. Installera både SSH-klienten (`ssh.exe`) och server (`sshd.exe`) så att du kan fjärransluta till och från datorerna. För Windows, installera [Win32-OpenSSH från GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).
För Linux, installera SSH (inklusive sshd-servern) lämpligt för din plattform. Du måste också installera PowerShell Core från GitHub för att hämta SSH-fjärrkommunikationsfunktionen. SSH-servern måste konfigureras för att skapa ett SSH-undersystem som värd för en PowerShell-process på fjärrdatorn. Du måste också konfigurera aktivera lösenord eller en nyckel för autentisering.

## <a name="set-up-on-windows-machine"></a>Ställa in på Windows-dator

1. Installera den senaste versionen av [PowerShell Core för Windows]

   - Berätta om den har stöd för SSH-fjärrkommunikation genom att titta på parameteruppsättningar för `New-PSSession`

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. Installera den senaste versionen av [Win32-OpenSSH] från GitHub med hjälp av [installationsinstruktionerna]
3. Redigera sshd_config-filen på den plats där du installerade Win32 OpenSSH

   - Kontrollera att lösenordsautentisering är aktiverad

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6.0.4/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > Det finns en bugg i OpenSSH för Windows som förhindrar att blanksteg fungerar i undersystemet körbara sökvägar. Mer information finns i [problemet GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).

     En lösning är att skapa en symlink till installationskatalogen för Powershell som saknar blanksteg:

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.4"
     ```

     och sedan ange den i undersystemet:

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - Du kan också aktivera nyckelautentisering

     ```
     PubkeyAuthentication yes
     ```

4. Starta om tjänsten sshd

   ```powershell
   Restart-Service sshd
   ```

5. Lägga till sökvägen där OpenSSH installeras till sökvägen för miljövariabeln. Till exempel `C:\Program Files\OpenSSH\`. Den här posten kan ssh.exe ska finnas.

## <a name="set-up-on-linux-ubuntu-1404-machine"></a>Ställa in på datorn för Linux (Ubuntu 14.04)

1. Installera den senaste versionen av [PowerShell Core för Linux] från GitHub
2. Installera [Ubuntu SSH] vid behov

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. Redigera sshd_config-filen på plats /etc/ssh

   - Kontrollera att lösenordsautentisering är aktiverad

   ```
   PasswordAuthentication yes
   ```

   - Lägga till en post för PowerShell-undersystemet

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - Du kan också aktivera nyckelautentisering

   ```
   PubkeyAuthentication yes
   ```

4. Starta om tjänsten sshd

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a>Ställa in på Mac OS-dator

1. Installera den senaste versionen av [PowerShell Core för MacOS]

   - Kontrollera att SSH-fjärrkommunikation är aktiverat genom att följa dessa steg:
     - Öppna `System Preferences`
     - Klicka på `Sharing`
     - Kontrollera `Remote Login` -ska stå `Remote Login: On`
     - Tillåt åtkomst till rätt användare

2. Redigera den `sshd_config` fil på plats `/private/etc/ssh/sshd_config`

   - Använda din favoritredigerare eller

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - Kontrollera att lösenordsautentisering är aktiverad

     ```
     PasswordAuthentication yes
     ```

   - Lägga till en post för PowerShell-undersystemet

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - Du kan också aktivera nyckelautentisering

     ```
     PubkeyAuthentication yes
     ```

3. Starta om tjänsten sshd

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a>Autentisering

PowerShell fjärrkommunikation via SSH är beroende av autentiseringsutbytet mellan SSH-klient och SSH-tjänsten och implementerar inte alla autentiseringsscheman själva.
Det innebär att alla konfigurerade autentiseringsmetoder, inklusive Multi-Factor authentication hanteras av SSH- och oberoende av PowerShell.
Du kan till exempel konfigurera SSH-tjänsten för att kräva autentisering med offentlig nyckel som ett engångslösenord för ökad säkerhet.
Konfigurationen av Multi-Factor authentication ligger utanför omfånget för den här dokumentationen.
I dokumentationen för SSH på hur du konfigurerar multifaktorautentisering och verifiera den fungerar utanför PowerShell innan du försöker använda den med PowerShell-fjärrkommunikation korrekt.

## <a name="powershell-remoting-example"></a>Exempel på PowerShell-fjärrkommunikation

Det enklaste sättet att testa fjärrkommunikation är att testa den på en enda dator. I det här exemplet skapar vi en fjärrsession tillbaka till samma Linux-dator. Vi använder PowerShell cmdlets interaktivt så ser vi uppmanar från SSH där du ombeds att verifiera värddatorn och fråga om ett lösenord. Du kan göra samma sak på en Windows-dator fjärrkommunikation fungerar. Sedan remote mellan datorer genom att ändra värdnamnet.

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

### <a name="known-issues"></a>Kända problem

Sudo-kommando fungerar inte i fjärrsession till Linux-dator.

## <a name="see-also"></a>Se även

[PowerShell Core för Windows](../setup/installing-powershell-core-on-windows.md#msi)

[PowerShell Core för Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[PowerShell Core för MacOS](../setup/installing-powershell-core-on-macos.md)

[Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)

[installationen](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
