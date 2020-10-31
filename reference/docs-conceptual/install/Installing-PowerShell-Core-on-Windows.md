---
title: Installera PowerShell i Windows
description: Information om hur du installerar PowerShell på Windows
ms.date: 10/30/2020
ms.openlocfilehash: 1b341b496cef34a2a98afeac9d24f0a51e8dbda0
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142794"
---
# <a name="installing-powershell-on-windows"></a>Installera PowerShell i Windows

Det finns flera sätt att installera PowerShell i Windows.

## <a name="prerequisites"></a>Förutsättningar

Den senaste versionen av PowerShell stöds på Windows 7 SP1, Server 2008 R2 och senare versioner.

Om du vill aktivera PowerShell-fjärrkommunikation över WSMan måste följande krav vara uppfyllda:

- Installera [Universal C runtime](https://www.microsoft.com/download/details.aspx?id=50410) på Windows-versioner predating Windows 10. Den är tillgänglig via direkt hämtning eller Windows Update. Fullständigt installerade system har redan det här paketet installerat.
- Installera Windows Management Framework (WMF) 4,0 eller senare på Windows 7 och Windows Server 2008 R2. Mer information om WMF finns i [Översikt över WMF](/powershell/scripting/wmf/overview).

## <a name="download-the-installer-package"></a>Ladda ned installations paketet

Installera PowerShell på Windows genom att ladda ned installations paketet från vår GitHub- [releases][releases] -sida. Rulla ned till **till gångar** -avsnittet på sidan version. Avsnittet **till gångar** kan vara minimerat, så du kan behöva klicka för att expandera det.

## <a name="installing-the-msi-package"></a><a id="msi" />Installera MSI-paketet

MSI-filen ser ut så här `PowerShell-<version>-win-<os-arch>.msi` . Exempel:

- `PowerShell-7.0.3-win-x64.msi`
- `PowerShell-7.0.3-win-x86.msi`

När du har laddat ned dubbelklickar du på installations programmet och följer anvisningarna.

Installations programmet skapar en genväg på Start-menyn i Windows.

- Som standard installeras paketet på `$env:ProgramFiles\PowerShell\<version>`
- Du kan starta PowerShell via Start-menyn eller `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

> [!NOTE]
> PowerShell 7 installeras i en ny katalog och körs sida vid sida med Windows PowerShell 5,1. För PowerShell Core 6. x är PowerShell 7 en uppgradering på plats som tar bort PowerShell Core 6. x.
>
> - PowerShell 7 installeras för att `$env:ProgramFiles\PowerShell\7`
> - `$env:ProgramFiles\PowerShell\7`Mappen läggs till`$env:PATH`
> - `$env:ProgramFiles\PowerShell\6`Mappen tas bort
>
> Om du behöver köra PowerShell 6 sida vid sida med PowerShell 7 installerar du om PowerShell 6 med hjälp av [zip-installations](#zip) metoden.

### <a name="administrative-install-from-the-command-line"></a>Administrativ installation från kommando raden

MSI-paket kan installeras från kommando raden och gör det möjligt för administratörer att distribuera paket utan användar interaktion. MSI-paketet innehåller följande egenskaper för att kontrol lera installations alternativen:

- **ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** – den här egenskapen styr alternativet för att lägga till det **Öppna PowerShell** -objektet i snabb menyn i Utforskaren.
- **ENABLE_PSREMOTING** – den här egenskapen styr alternativet för att aktivera PowerShell-fjärrkommunikation under installationen.
- **REGISTER_MANIFEST** – den här egenskapen styr alternativet för registrering av Windows händelse loggnings manifestet.

I följande exempel visas hur du tyst installerar PowerShell med alla installations alternativ aktiverade.

```powershell
msiexec.exe /package PowerShell-7.0.3-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

En fullständig lista över kommando rads alternativ för `Msiexec.exe` finns i [kommando rads alternativ](/windows/desktop/Msi/command-line-options).

### <a name="registry-keys-created-during-installation"></a>Register nycklar som skapas under installationen

Från och med PowerShell 7,1 skapar MSI-paketet register nycklar som lagrar installations platsen och versionen av PowerShell. Dessa värden finns i `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>` . Värdet för `<GUID>` är unikt för varje build-typ (version eller förhands granskning), huvud version och arkitektur.

|    Frisläpp    | Arkitektur |                                          Registernyckel                                           |
| ------------- | :----------: | ----------------------------------------------------------------------------------------------- |
| 7.1. x-version |     x86      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\1d00683b-0f84-4db8-a64f-2f98ad42fe06` |
| 7.1. x-version |     x64      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\31ab5147-9a97-4452-8443-d9709f0516e1` |
| 7.1. x-förhandsgranskning |     x86      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\86abcfbd-1ccc-4a88-b8b2-0facfde29094` |
| 7.1. x-förhandsgranskning |     x64      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\39243d76-adaf-42b1-94fb-16ecf83237c8` |

Detta kan användas av administratörer och utvecklare för att hitta sökvägen till PowerShell. `<GUID>`Värdena är desamma för alla för hands versioner och del versioner. `<GUID>`Värdena ändras för varje större version.

## <a name="installing-the-msix-package"></a><a id="msix" />Installera MSIX-paketet

> [!NOTE]
> MSIX-paketet stöds inte officiellt för tillfället. Vi fortsätter att bygga paketet enbart för internt test ändamål.

Om du vill installera MSIX-paketet manuellt på en Windows 10-klient laddar du ned MSIX-paketet från vår GitHub [releases][releases] -sida. Rulla ned till **till gångar** -avsnittet i den version som du vill installera. Avsnittet till gångar kan vara minimerat, så du kan behöva klicka för att expandera det.

MSIX-filen ser ut så här – `PowerShell-<version>-win-<os-arch>.msix`

Du måste använda cmdleten för att installera paketet `Add-AppxPackage` .

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="installing-the-zip-package"></a><a id="zip" />Installera ZIP-paketet

Det finns PowerShell-Arkiv för att aktivera avancerade distributions scenarier. Ladda ned något av följande ZIP-arkiv från sidan [versioner][releases] .

- PowerShell-7.0.3-win-x64.zip
- PowerShell-7.0.3-win-x86.zip
- PowerShell-7.0.3-win-arm64.zip
- PowerShell-7.0.3-win-arm32.zip

Beroende på hur du laddar ned filen kan du behöva avblockera filen med hjälp av `Unblock-File` cmdleten. Zippa upp innehållet till valfri plats och kör `pwsh.exe` därifrån. Till skillnad från när du installerar MSI-paketen söker inte du efter krav i ZIP-arkivet. Se till att du uppfyller [kraven](#prerequisites)för fjärr kommunikation över WSMan för att fungera korrekt.

Använd den här metoden för att installera den ARM-baserade versionen av PowerShell på datorer som Microsoft Surface Pro X. För bästa resultat bör du installera PowerShell i till- `$env:ProgramFiles\PowerShell\7` mappen.

## <a name="deploying-on-windows-10-iot-enterprise"></a>Distribuera i Windows 10 IoT Enterprise

Windows 10 IoT Enterprise levereras med Windows PowerShell, som vi kan använda för att distribuera PowerShell 7.

1. Skapa `PSSession` till mål enhet

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

1. Kopiera ZIP-paketet till enheten

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

1. Anslut till enheten och Expandera arkivet

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

1. Konfigurera fjärr kommunikation till PowerShell 7

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because
   # it has to restart WinRM
   ```

1. Anslut till PowerShell 7-slutpunkt på enhet

   ```powershell
   # Be sure to use the -Configuration parameter. If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-windows-10-iot-core"></a>Distribuera på Windows 10 IoT Core

Windows 10 IoT Core lägger till Windows PowerShell när du inkluderar _IOT_POWERSHELL_ funktion som vi kan använda för att distribuera PowerShell 7. Stegen som definieras ovan för Windows 10 IoT Enterprise kan också följas av IoT Core.

För att lägga till den senaste PowerShell-versionen i leverans avbildningen använder du kommandot [import-PSCoreRelease][] för att inkludera paketet i workarea och lägga till _OPENSRC_POWERSHELL_ funktion i avbildningen.

> [!NOTE]
> Windows PowerShell läggs inte till i ARM64-arkitekturen när du tar med _IOT_POWERSHELL_ . Det innebär att zip-baserad installation inte fungerar. Du måste använda `Import-PSCoreRelease` kommandot för att lägga till det i avbildningen.

## <a name="deploying-on-nano-server"></a>Distribuera på Nano Server

Dessa instruktioner förutsätter att Nano-servern är ett "" "" "-"-OS som har en version av PowerShell som redan körs på den. Mer information finns i dokumentationen för [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) .

PowerShell-binärfiler kan distribueras med två olika metoder.

1. Offline – montera den virtuella hård disken för Nano Server och zippa upp innehållet i zip-filen till den valda platsen i den monterade avbildningen.
1. Överför zip-filen via en PowerShell-session online och packa upp den på den valda platsen.

I båda fallen behöver du paketet Windows 10 x64 ZIP release. Kör kommandona i en "administratör"-instans av PowerShell.

### <a name="offline-deployment-of-powershell"></a>Offline-distribution av PowerShell

1. Använd ditt favorit-zip-verktyg för att packa upp paketet till en katalog i den monterade Nano Server-avbildningen.
1. Demontera avbildningen och starta den.
1. Anslut till den inbyggda instansen av Windows PowerShell.
1. Följ instruktionerna för att skapa en fjärran sluten slut punkt med hjälp av ["en annan instans teknik"][].

### <a name="online-deployment-of-powershell"></a>Online-distribution av PowerShell

Distribuera PowerShell till Nano Server med hjälp av följande steg.

- Ansluta till den inbyggda instansen av Windows PowerShell

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
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- Om du vill använda WSMan-baserad fjärr kommunikation följer du anvisningarna för att skapa en slut punkt för fjärr kommunikation med hjälp av ["en annan instans teknik"][].

## <a name="install-as-a-net-global-tool"></a>Installera som ett globalt .NET-verktyg

Om du redan har installerat [.net Core SDK](/dotnet/core/sdk) är det enkelt att installera PowerShell som ett [globalt .net-verktyg](/dotnet/core/tools/global-tools).

```
dotnet tool install --global PowerShell
```

Installations programmet för dotNET-verktyget lägger till `$env:USERPROFILE\dotnet\tools` i din `$env:PATH` miljö variabel. Men det gränssnitt som körs har inte uppdaterats `$env:PATH` . Du kan starta PowerShell från ett nytt gränssnitt genom att skriva `pwsh` .

## <a name="install-powershell-via-winget"></a>Installera PowerShell via Winget

Med `winget` kommando rads verktyget kan utvecklare identifiera, installera, uppgradera, ta bort och konfigurera program på Windows 10-datorer. Det här verktyget är klient gränssnittet för Windows Package Manager-tjänsten.

> [!NOTE]
> `winget`Verktyget är för närvarande en för hands version. Alla planerade funktioner är inte tillgängliga för tillfället.
> Du bör inte använda den här metoden i ett scenario för produktions distribution. I [Winget] -dokumentationen finns en lista över system krav och installations anvisningar.

Följande kommandon kan användas för att installera PowerShell med de publicerade `winget` paketen:

1. Sök efter den senaste versionen av PowerShell

   ```powershell
   winget search Microsoft.PowerShell
   ```

   ```Output
   Name               Id                           Version
   ---------------------------------------------------------------
   PowerShell         Microsoft.PowerShell         7.0.3
   PowerShell-Preview Microsoft.PowerShell-Preview 7.1.0-preview.5
   ```

1. Installera en version av PowerShell med `--exact` parametern

   ```powershell
   winget install --name PowerShell --exact
   winget install --name PowerShell-Preview --exact
   ```

## <a name="how-to-create-a-remoting-endpoint"></a>Så här skapar du en fjärran sluten slut punkt

PowerShell stöder PowerShell Remoting-protokollet (PSRP) via både WSMan och SSH. Mer information finns i:

- [SSH-fjärrkommunikation i PowerShell Core][ssh-remoting]
- [WSMan-fjärrkommunikation i PowerShell Core][wsman-remoting]

## <a name="upgrading-an-existing-installation"></a>Uppgradera en befintlig installation

För bästa resultat vid uppgraderingen bör du använda samma installations metod som du använde när du först installerade PowerShell. Varje installations metod installerar PowerShell på en annan plats. Om du inte är säker på hur PowerShell installerades kan du jämföra den installerade platsen med paket informationen i den här artikeln. Om du har installerat via MSI-paketet visas den informationen i **program och funktioner** på kontroll panelen.

## <a name="installation-support"></a>Installations stöd

Microsoft stöder installations metoderna i det här dokumentet. Det kan finnas andra installations metoder som är tillgängliga från andra källor. Dessa verktyg och metoder kan fungera, men Microsoft stöder inte dessa metoder.

<!-- link references -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
[winget]: /windows/package-manager/winget
["en annan instans teknik"]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register
[Importera – PSCoreRelease]: https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease
