---
title: Installera PowerShell Core i Windows
description: Information om hur du installerar PowerShell core i Windows
ms.date: 08/06/2018
ms.openlocfilehash: c06eba06e376c3f795ab9c0fae9270cf6cf8f2ce
ms.sourcegitcommit: 36e4c79afda2ce11febd93951e143687245f0b50
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/02/2019
ms.locfileid: "73444453"
---
# <a name="installing-powershell-core-on-windows"></a>Installera PowerShell Core i Windows

Det finns flera sätt att installera PowerShell core i Windows.

> [!TIP]
> Om du redan har installerat [.net Core SDK](/dotnet/core/sdk) är det enkelt att installera PowerShell som ett [globalt .net-verktyg](/dotnet/core/tools/global-tools).
>
> ```
> dotnet tool install --global PowerShell
> ```

## <a name="prerequisites"></a>Förutsättningar

Om du vill aktivera PowerShell-fjärrkommunikation över WSMan måste följande krav vara uppfyllda:

- Installera [Universal C-körningen](https://www.microsoft.com/download/details.aspx?id=50410) på Windows-versioner före Windows 10. Den är tillgänglig via direkt hämtning eller Windows Update. Fullständigt uppdaterad (inklusive valfria paket) har system som stöds redan installerat.
- Installera Windows Management Framework (WMF) 4,0 eller senare på Windows 7 och Windows Server 2008 R2. Mer information om WMF finns i [Översikt över WMF](/powershell/wmf/overview).

## <a name="a-idmsi-installing-the-msi-package"></a><a id="msi" />installera MSI-paketet

Om du vill installera PowerShell på en Windows-klient eller Windows Server (fungerar på Windows 7 SP1, Server 2008 R2 och senare) laddar du ned MSI-paketet från vår GitHub [releases][releases] -sida. Rulla ned till **till gångar** -avsnittet i den version som du vill installera. Avsnittet till gångar kan vara minimerat, så du kan behöva klicka för att expandera det.

MSI-filen ser ut så här – `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

När du har laddat ned dubbelklickar du på installations programmet och följer anvisningarna.

Installations programmet skapar en genväg på Start-menyn i Windows.

- Som standard installeras paketet på `$env:ProgramFiles\PowerShell\<version>`
- Du kan starta PowerShell via Start-menyn eller `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

### <a name="administrative-install-from-the-command-line"></a>Administrativ installation från kommando raden

MSI-paket kan installeras från kommando raden. Detta gör att administratörer kan distribuera paket utan användar interaktion. MSI-paketet för PowerShell innehåller följande egenskaper för att kontrol lera installations alternativen:

- **ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** – den här egenskapen styr alternativet för att lägga till det **Öppna PowerShell** -objektet i snabb menyn i Utforskaren i Windows.
- **ENABLE_PSREMOTING** – den här egenskapen styr alternativet för att aktivera PowerShell-fjärrkommunikation under installationen.
- **REGISTER_MANIFEST** – den här egenskapen styr alternativet för registrering av Windows händelse loggnings manifestet.

I följande exempel visas hur du tyst installerar PowerShell Core med alla installations alternativ aktiverade.

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

En fullständig lista över kommando rads alternativ för msiexec. exe finns i [kommando rads alternativ](/windows/desktop/Msi/command-line-options).

## <a name="a-idzip-installing-the-zip-package"></a><a id="zip" />installation av ZIP-paketet

Det finns PowerShell-Arkiv för att aktivera avancerade distributions scenarier. Observera att när du använder ZIP-arkivet visas inte krav kontrollen som i MSI-paketet. Se till att du uppfyller [kraven](#prerequisites)för fjärr kommunikation över WSMan för att fungera korrekt.

## <a name="deploying-on-windows-iot"></a>Distribuera på Windows IoT

Windows IoT levereras redan med Windows PowerShell som vi ska använda för att distribuera PowerShell Core 6.

1. Skapa `PSSession` till mål enhet

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. Kopiera ZIP-paketet till enheten

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Anslut till enheten och Expandera arkivet

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. Konfigurera fjärr kommunikation till PowerShell Core 6

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Anslut till PowerShell Core 6-slutpunkt på enhet

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a>Distribuera på Nano Server

Dessa instruktioner förutsätter att en version av PowerShell redan körs på Nano Server-avbildningen och att den har genererats av [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).
Nano Server är ett "" "konsol löst" operativ system. Kärn binärfiler kan distribueras med två olika metoder.

1. Offline – montera den virtuella hård disken för Nano Server och zippa upp innehållet i zip-filen till den valda platsen i den monterade avbildningen.
2. Överför zip-filen via en PowerShell-session online och packa upp den på den valda platsen.

I båda fallen behöver du paketet Windows 10 x64 ZIP release och måste köra kommandona i en "administratör" PowerShell-instans.

### <a name="offline-deployment-of-powershell-core"></a>Offline-distribution av PowerShell Core

1. Använd ditt favorit-zip-verktyg för att packa upp paketet till en katalog i den monterade Nano Server-avbildningen.
2. Demontera avbildningen och starta den.
3. Anslut till inkorg-instansen av Windows PowerShell.
4. Följ instruktionerna för att skapa en fjärran sluten slut punkt med hjälp av ["en annan instans teknik"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>Online-distribution av PowerShell Core

Följande steg vägleder dig genom distributionen av PowerShell Core till en aktiv instans av Nano Server och konfigurationen av dess fjärrslutpunkt.

- Anslut till inkorg-instansen av Windows PowerShell

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

- Om du vill använda WSMan-baserad fjärr kommunikation följer du anvisningarna för att skapa en slut punkt för fjärr kommunikation med hjälp av ["en annan instans teknik"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="how-to-create-a-remoting-endpoint"></a>Så här skapar du en fjärran sluten slut punkt

PowerShell Core stöder PowerShell Remoting-protokollet (PSRP) via både WSMan och SSH. Mer information finns i följande avsnitt:

- [SSH-fjärrkommunikation i PowerShell Core][ssh-remoting]
- [WSMan-fjärrkommunikation i PowerShell Core][wsman-remoting]

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
