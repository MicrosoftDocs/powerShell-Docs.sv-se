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
# <a name="powershell-remoting-over-ssh"></a>PowerShell fjärrkommunikation via SSH

## <a name="overview"></a>Översikt

PowerShell-fjärrkommunikation använder normalt WinRM för anslutnings förhandling och data transport. SSH är nu tillgängligt för Linux-och Windows-plattformar och tillåter en PowerShell-fjärrkommunikation med multiplatform.

WinRM tillhandahåller en robust värd modell för PowerShell-fjärrsessioner. SSH-baserad fjärr kommunikation har för närvarande inte stöd för konfiguration av Fjärrslutpunkter och bara tillräckligt med administration (JEA).

Med SSH-fjärrkommunikation kan du utföra grundläggande PowerShell-sessioner mellan Windows-och Linux-datorer. SSH-fjärrkommunikation skapar en PowerShell-värd process på mål datorn som ett SSH-undersystem. Slutligen ska vi implementera en allmän värd modell som liknar WinRM för att stödja slut punkts konfiguration och JEA.

Cmdletarna `New-PSSession`, `Enter-PSSession`och `Invoke-Command` har nu en ny parameter som stöder denna nya fjärr anslutnings anslutning.

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Om du vill skapa en fjärrsession anger du mål datorn med parametern `HostName` och anger användar namnet med `UserName`. När du kör cmdletarna interaktivt, uppmanas du att ange ett lösen ord. Du kan också använda SSH-nyckel-autentisering med hjälp av en privat nyckel fil med parametern `KeyFilePath`.

## <a name="general-setup-information"></a>Allmän installations information

PowerShell 6 eller högre, och SSH måste vara installerat på alla datorer. Installera både SSH-klienten (`ssh.exe`) och Server (`sshd.exe`) så att du kan fjärrans luta till och från datorerna. OpenSSH för Windows är nu tillgängligt i Windows 10 version 1809 och Windows Server 2019. Mer information finns i [hantera Windows med openssh](/windows-server/administration/openssh/openssh_overview). För Linux installerar du SSH, inklusive sshd-servern, som är lämplig för din plattform. Du måste också installera PowerShell från GitHub för att hämta SSH-funktionen för fjärr kommunikation. SSH-servern måste konfigureras för att skapa ett SSH-undersystem som värd för en PowerShell-process på fjärrdatorn. Och du måste aktivera **lösen ord** eller **nyckelbaserad** autentisering.

## <a name="set-up-on-a-windows-computer"></a>Konfigurera på en Windows-dator

1. Installera den senaste versionen av PowerShell, se [Installera PowerShell Core på Windows](../../install/installing-powershell-core-on-windows.md#msi).

   Du kan kontrol lera att PowerShell har stöd för SSH-fjärrhantering genom att Visa `New-PSSession` parameter uppsättningar. Observera att det finns parameter uppsättnings namn som börjar med **SSH**. Parameter uppsättningarna inkluderar **SSH** -parametrar.

   ```powershell
   (Get-Command New-PSSession).ParameterSets.Name
   ```

   ```Output
   Name
   ----
   SSHHost
   SSHHostHashParam
   ```

1. Installera de senaste Win32-OpenSSH. Installations anvisningar finns i [komma igång med openssh](/windows-server/administration/openssh/openssh_install_firstuse).

   > [!NOTE]
   > Om du vill ställa in PowerShell som standard gränssnitt för OpenSSH, se [Konfigurera Windows för openssh](/windows-server/administration/openssh/openssh_server_configuration).

1. Redigera `sshd_config`-filen som finns på `$env:ProgramData\ssh`.

   Se till att lösenordsautentisering är aktiverat:

   ```
   PasswordAuthentication yes
   ```

   Skapa SSH-undersystemet som är värd för en PowerShell-process på fjärrdatorn:

   ```
   Subsystem powershell c:/progra~1/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   > [!NOTE]
   > Du måste använda det korta 8,3-namnet för alla fil Sök vägar som innehåller blank steg. Det finns ett fel i OpenSSH för Windows som förhindrar att utrymmen fungerar i under systemets körbara sökvägar. Mer information finns i det här [GitHub-problemet](https://github.com/PowerShell/Win32-OpenSSH/issues/784).
   >
   > Det korta 8,3-namnet för mappen `Program Files` i Windows är vanligt vis `Progra~1`. Du kan dock använda följande kommando för att se till att:
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

   Du kan också aktivera nyckel autentisering:

   ```
   PubkeyAuthentication yes
   ```

   Mer information finns i [Hantera openssh-nycklar](/windows-server/administration/openssh/openssh_keymanagement).

1. Starta om **sshd** -tjänsten.

   ```powershell
   Restart-Service sshd
   ```

1. Lägg till sökvägen där OpenSSH är installerat i din PATH-miljö variabel. Till exempel `C:\Program Files\OpenSSH\`. Den här posten gör att `ssh.exe` kan hittas.

## <a name="set-up-on-an-ubuntu-1604-linux-computer"></a>Konfigurera på en Ubuntu 16,04 Linux-dator

1. Installera den senaste versionen av PowerShell, se [Installera PowerShell Core på Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604).
1. Installera [Ubuntu openssh-server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. Redigera `sshd_config`-filen på plats `/etc/ssh`.

   Se till att lösenordsautentisering är aktiverat:

   ```
   PasswordAuthentication yes
   ```

   Lägg till en PowerShell-under Systems post:

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   Du kan också aktivera nyckel autentisering:

   ```
   PubkeyAuthentication yes
   ```

1. Starta om **sshd** -tjänsten.

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-a-macos-computer"></a>Konfigurera på en macOS-dator

1. Installera den senaste versionen av PowerShell, se [Installera PowerShell Core på MacOS](../../install/installing-powershell-core-on-macos.md).

   Se till att SSH-fjärrkommunikation är aktiverat genom att följa dessa steg:

   1. Öppna `System Preferences`.
   1. Klicka på `Sharing`.
   1. Markera `Remote Login` för att ange `Remote Login: On`.
   1. Tillåt åtkomst till lämpliga användare.

1. Redigera `sshd_config`-filen på plats `/private/etc/ssh/sshd_config`.

   Använd en text redigerare som **nano**:

   ```bash
   sudo nano /private/etc/ssh/sshd_config
   ```

   Se till att lösenordsautentisering är aktiverat:

   ```
   PasswordAuthentication yes
   ```

   Lägg till en PowerShell-under Systems post:

   ```
   Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   Du kan också aktivera nyckel autentisering:

   ```
   PubkeyAuthentication yes
   ```

1. Starta om **sshd** -tjänsten.

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a>Autentisering

PowerShell-fjärrkommunikation via SSH är beroende av autentiserings utbyte mellan SSH-klienten och SSH-tjänsten och implementerar inte några autentiseringsscheman. Resultatet är att alla konfigurerade autentiseringsscheman, inklusive Multi-Factor Authentication, hanteras av SSH och oberoende av PowerShell. Du kan till exempel konfigurera SSH-tjänsten så att den kräver autentisering med offentlig nyckel och eng ång slö sen ord för ytterligare säkerhet. Konfiguration av Multi-Factor Authentication omfattas inte av den här dokumentationen. Läs dokumentationen för SSH om hur du konfigurerar Multi-Factor Authentication på rätt sätt och verifierar att den fungerar utanför PowerShell innan du försöker använda den med PowerShell-fjärrkommunikation.

## <a name="powershell-remoting-example"></a>Exempel på PowerShell-fjärrkommunikation

Det enklaste sättet att testa fjärr kommunikation är att testa den på en enda dator. I det här exemplet skapar vi en fjärrsession tillbaka till samma Linux-dator. Vi använder PowerShell-cmdletar interaktivt så vi ser frågor från SSH som ber om att verifiera värddatorn och uppmanas att ange ett lösen ord. Du kan göra samma sak på en Windows-dator för att säkerställa att fjärr kommunikation fungerar. Sedan kan du fjärrans luta mellan datorer genom att ändra värd namnet.

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

### <a name="known-issues"></a>Kända problem

Kommandot **sudo** fungerar inte i en fjärran sluten session till en Linux-dator.

## <a name="see-also"></a>Se även

[Installera PowerShell Core på Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[Installera PowerShell Core på macOS](../../install/installing-powershell-core-on-macos.md)

[Installera PowerShell Core på Windows](../../install/installing-powershell-core-on-windows.md#msi)

[Hantera Windows med OpenSSH](/windows-server/administration/openssh/openssh_overview)

[Hantera OpenSSH-nycklar](/windows-server/administration/openssh/openssh_keymanagement)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
