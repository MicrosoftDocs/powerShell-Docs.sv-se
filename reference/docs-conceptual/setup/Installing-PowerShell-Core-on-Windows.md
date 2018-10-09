---
title: Installera PowerShell Core i Windows
description: Information om att installera PowerShell Core i Windows
ms.date: 08/06/2018
ms.openlocfilehash: 2b21908c38796117308f2ac1219db00ff9086408
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850987"
---
# <a name="installing-powershell-core-on-windows"></a>Installera PowerShell Core i Windows

## <a name="msi"></a>MSI

Installera PowerShell på en Windows-klienten eller Windows Server (fungerar på Windows 7 SP1, Server 2008 R2 och senare), ladda ned MSI-paketet från vår GitHub [släpper][] sidan.

MSI-filen som ser ut så här- `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

När du har hämtat, dubbelklicka på installationsprogrammet och följ anvisningarna.

Det finns en genväg som placeras på Start-menyn vid installationen.

- Paketet installeras som standard till `$env:ProgramFiles\PowerShell\<version>`
- Du kan starta PowerShell via Start-menyn eller `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

### <a name="prerequisites"></a>Förutsättningar

Om du vill aktivera PowerShell-fjärrkommunikation via WSMan, måste följande krav uppfyllas:

- Installera den [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) på Windows-versioner före Windows 10.
  Det är tillgängligt via direkt ladda ned eller Windows Update.
  Fullständigt uppdaterad (inklusive valfria paket) har system som stöds redan det installerat.
- Installera på Windows Management Framework (WMF) 4.0 eller senare på Windows 7 och Windows Server 2008 R2.

## <a name="zip"></a>ZIP

PowerShell binära ZIP-arkiv tillhandahålls för att aktivera avancerade scenarier.
Observera att du inte får kravkontrollen som i MSI-paket när du använder ZIP-arkivet.
Så för fjärrkommunikation via WSMan ska fungera korrekt på Windows-versioner före Windows 10, du måste se till att den [krav](#prerequisites) är uppfyllda.

## <a name="deploying-on-windows-iot"></a>Distribuera på Windows IoT

Windows IoT levereras med Windows PowerShell som ska användas för att distribuera PowerShell Core 6.

1. Skapa `PSSession` till målenheten

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. Kopiera ZIP-paketet till enheten

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.1.0-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Anslut till enheten och expandera arkivet

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.1.0-win-arm32.zip
   ```

4. Konfigurera fjärrkommunikation till PowerShell Core 6

   ```powershell
   Set-Location .\PowerShell-6.1.0-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Ansluta till PowerShell Core 6-slutpunkten på enheten

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.1.0
   ```

## <a name="deploying-on-nano-server"></a>Distribuera på Nano Server

Dessa instruktioner förutsätter att en version av PowerShell körs redan på Nano Server-avbildningen och att den har genererats av den [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).
Nano Server är ett ”fjärradministrering” operativsystem. Grundläggande binärfiler kan du distribuera med två olika metoder.

1. Offline - montera den virtuella Hårddisken Nano Server och packa upp innehållet i zip-filen till den valda platsen i den monterade avbildningen.
2. Online - överför zip-filen via en PowerShell-Session och packa upp den på den valda platsen.

I båda fallen måste versionen för Windows 10 x64 ZIP paketera och kommer att behöva köra kommandona i ett ”administratör” PowerShell-instansen.

### <a name="offline-deployment-of-powershell-core"></a>Offline distribution av PowerShell Core

1. Använd din favorit zip-verktyg för att packa upp paketet till en katalog i den monterade avbildningen Nano Server.
2. Demontera avbildningen och starta den.
3. Anslut till Inkorgen instans av Windows PowerShell.
4. Följ anvisningarna för att skapa en fjärrkommunikation slutpunkten med den [”en annan instans metod”](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>Online distribution av PowerShell Core

Följande steg beskriver hur du distributionen av PowerShell Core till en pågående instans av Nano Server och konfigurationen av dess fjärrslutpunkten.

- Ansluta till Inkorgen instans av Windows PowerShell

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- Kopiera filen till Nano Server-instansen

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- Ange sessionen

  ```powershell
  Enter-PSSession $session
  ```

- Extrahera ZIP-filen

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- Om du vill WSMan-baserad fjärrkommunikation följer du anvisningarna för att skapa en fjärrkommunikation slutpunkt med hjälp av den [”en annan instans metod”](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instruktioner för att skapa en slutpunkt för fjärrkommunikation

PowerShell Core stöder PowerShell fjärrkommunikation Protocol (PSRP) via WSMan- och SSH.
Mer information finns i följande avsnitt:

- [SSH fjärrkommunikation i PowerShell Core][ssh-remoting]
- [WSMan-fjärrkommunikation i PowerShell Core][wsman-remoting]

## <a name="artifact-installation-instructions"></a>Instruktioner för Installation av artefakt

Vi publicerar ett arkiv med CoreCLR bitar varje CI-version med [AppVeyor][].

Installera PowerShell Core från CoreCLR artefakten:

1. Ladda ned ZIP-paketet från **artefakter** fliken för specifika versionen.
2. Avblockera ZIP-filen: Högerklicka i Utforskaren -> Egenskaper -> Kontrollera 'Avblockera' box -> tillämpa
3. Extrahera zipfilen till `bin` directory
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[släpper]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
