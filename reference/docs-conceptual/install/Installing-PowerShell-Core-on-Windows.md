---
title: Installera PowerShell Core i Windows
description: Information om att installera PowerShell Core i Windows
ms.date: 08/06/2018
ms.openlocfilehash: 5a3c43e27f0027cfbeeefab33b045e618e0ff045
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854368"
---
# <a name="installing-powershell-core-on-windows"></a>Installera PowerShell Core i Windows

Det finns flera sätt att installera PowerShell Core i Windows.

## <a name="prerequisites"></a>Förutsättningar

Om du vill aktivera PowerShell-fjärrkommunikation via WSMan, måste följande krav uppfyllas:

- Installera den [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) på Windows-versioner före Windows 10. Det är tillgängligt via direkt ladda ned eller Windows Update. Fullständigt uppdaterad (inklusive valfria paket) har system som stöds redan det installerat.
- Installera på Windows Management Framework (WMF) 4.0 eller senare på Windows 7 och Windows Server 2008 R2. Läs mer om WMF [WMF översikt](/powershell/wmf/overview).

## <a name="a-idmsi-installing-the-msi-package"></a><a id="msi" />Installerar MSI-paketet

Installera PowerShell på en Windows-klienten eller Windows Server (fungerar på Windows 7 SP1, Server 2008 R2 och senare), ladda ned MSI-paketet från vår GitHub [versioner] []-sida. Rulla ned till den **tillgångar** delen av den version som du vill installera. Vara kan dolda i tillgångar-avsnittet så att du kan behöva klicka på för att expandera den.

MSI-filen som ser ut så här- `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

När du har hämtat, dubbelklicka på installationsprogrammet och följ anvisningarna.

Installationsprogrammet skapar en genväg på Windows-startmenyn.

- Paketet installeras som standard till `$env:ProgramFiles\PowerShell\<version>`
- Du kan starta PowerShell via Start-menyn eller `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

### <a name="administrative-install-from-the-command-line"></a>Administrativ installation från kommandoraden

MSI-paket kan installeras från kommandoraden. Detta gör att administratörer kan distribuera paket utan interaktion från användaren. MSI-paketet för PowerShell innehåller följande egenskaper för att styra vilka installationsalternativ:

- **ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** -den här egenskapen styr alternativet för att lägga till den **öppna PowerShell** objekt till på snabbmenyn i Windows Explorer.
- **ENABLE_PSREMOTING** -den här egenskapen styr alternativ för att aktivera PowerShell-fjärrkommunikation under installationen.
- **REGISTER_MANIFEST** -den här egenskapen styr alternativ för att registrera Windows-händelseloggning manifestet.

I följande exempel visar hur du obevakat installera PowerShell Core med alla installationsalternativen aktiverat.

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

En fullständig lista över kommandoradsalternativ för Msiexec.exe Se [kommandoradsalternativ](/windows/desktop/Msi/command-line-options).

## <a name="a-idzip-installing-the-zip-package"></a><a id="zip" />Installerar ZIP-paketet

PowerShell binära ZIP-arkiv tillhandahålls för att aktivera avancerade scenarier. Observera att du inte får kravkontrollen som i MSI-paket när du använder ZIP-arkivet. För fjärrkommunikation via WSMan ska fungera korrekt, att se till att du har uppfyllt de [krav](#prerequisites).

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
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Anslut till enheten och expandera arkivet

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. Konfigurera fjärrkommunikation till PowerShell Core 6

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Ansluta till PowerShell Core 6-slutpunkten på enheten

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
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
4. Följ anvisningarna för att skapa en fjärrkommunikation slutpunkten med den [”en annan instans metod”](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

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

- Om du vill WSMan-baserad fjärrkommunikation följer du anvisningarna för att skapa en fjärrkommunikation slutpunkt med hjälp av den [”en annan instans metod”](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="how-to-create-a-remoting-endpoint"></a>Så här skapar du en slutpunkt för fjärrkommunikation

PowerShell Core stöder PowerShell fjärrkommunikation Protocol (PSRP) via WSMan- och SSH. Mer information finns i följande avsnitt:

- [SSH fjärrkommunikation i PowerShell Core] [ssh-fjärrkommunikation]
- [WSMan-fjärrkommunikation i PowerShell Core] [wsman-fjärrkommunikation]

<!-- [download-center]: TODO -->
[släpper]: https://github.com/PowerShell/PowerShell/releases [ssh-fjärrkommunikation]:... /Core-PowerShell/SSH-Remoting-in-PowerShell-Core.MD [wsman-fjärrkommunikation]:... /Core-PowerShell/wsman-Remoting-in-PowerShell-Core.MD [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
