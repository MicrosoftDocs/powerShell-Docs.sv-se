# <a name="installing-powershell-core-on-windows"></a>Installera PowerShell Core i Windows

## <a name="msi"></a>MSI

Installera PowerShell på en Windows-klienten eller Windows Server (fungerar på Server 2008 R2, Windows 7 SP1 och senare), ladda ned MSI-paketet från vår GitHub [släpper][] sidan.

MSI-filen ser ut så här-`PowerShell-6.0.0.<buildversion>.<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

När du har hämtat, dubbelklickar du på installationsprogrammet och följ anvisningarna.

Det finns en genväg som placerats i Start-menyn vid installationen.

* Paketet installeras som standard till`$env:ProgramFiles\PowerShell\`
* Du kan starta PowerShell via Start-menyn eller`$env:ProgramFiles\PowerShell\pwsh.exe`

### <a name="prerequisites"></a>Förutsättningar

Om du vill aktivera PowerShell-fjärrkommunikation över WSMan, måste följande krav uppfyllas:

* Installera den [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) på Windows-versioner före Windows 10.
  Det är tillgängligt via direkt hämta eller Windows Update.
  Korrigerade fullständigt (inklusive valfria paket), har stöds system redan det installeras.
* Installera Windows Management Framework (WMF) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) eller senare ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) på Windows 7 och Windows Server 2008 R2.

## <a name="zip"></a>ZIP-

PowerShell binära ZIP-arkiv som aktivera avancerade distribueringsscenarier.
Observera att du inte får kravkontrollen som MSI-paket när du använder ZIP-arkivet.
Så i ordning för fjärrkörning via WSMan ska fungera på Windows-versioner före Windows 10, måste du kontrollera att den [krav](#prerequisites) är uppfyllda.

## <a name="deploying-on-nano-server"></a>Distribuera på Nano Server

Dessa instruktioner förutsätter att en version av PowerShell körs redan på Nano Server-avbildning och har genererats av den [Nano Server Image Builder](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).
Nano Server är ett ”fjärradministrerade” operativsystem och distribution av PowerShell Core binärfiler kan inträffa på två olika sätt:

1. Offline - Montera VHD: N Nano Server och packa upp innehållet i zip-filen till den valda platsen i den monterade avbildningen.
1. Online - överför zip-filen via en PowerShell-Session och packa upp den på den valda platsen.

I båda fallen måste Windows 10 x64 Zip-versionen paketera och måste köra kommandona i ett ”administratör” PowerShell-instansen.

### <a name="offline-deployment-of-powershell-core"></a>Offline distribution av PowerShell Core

1. Använd din favorit zip-verktyg för att packa upp paketet till en katalog i den monterade avbildningen Nano Server.
1. Demontera avbildningen och starta den.
1. Anslut till Inkorgen instans av Windows PowerShell.
1. Följ instruktionerna för att skapa en fjärrkommunikation slutpunkten med hjälp av den [en annan instans metod](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>Online distribution av PowerShell Core

Följande steg vägleder dig genom distributionen av PowerShell Core till en instans som körs av Nano Server och konfigurationen av dess fjärrslutpunkten.

* Ansluta till Inkorgen instans av Windows PowerShell

```powershell
$session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
```

* Kopiera filen till Nano Server-instansen

```powershell
Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
```

* Ange sessionen

```powershell
Enter-PSSession $session
```

* Extrahera Zip-filen

```powershell
# Insert the appropriate version.
Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
```

* Om du vill WSMan-baserad remoting, följ instruktionerna för att skapa ett fjärrkommunikation slutpunkt med det [en annan instans metod](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instruktioner för att skapa en slutpunkt för fjärrkommunikation

PowerShell Core stöder PowerShell fjärrkommunikation Protocol (PSRP) över SSH- och WSMan. Mer information finns i följande avsnitt:

* [SSH fjärrkommunikation i PowerShell Core][ssh-remoting]
* [WSMan-fjärrkommunikation i PowerShell Core][wsman-remoting]

## <a name="artifact-installation-instructions"></a>Installationsinstruktioner för artefakt

Vi publicerar ett arkiv med CoreCLR bitar på varje CI-version med [AppVeyor][].

## <a name="coreclr-artifacts"></a>CoreCLR artefakter

* Hämta zip-paketet från **artefakter** fliken för en viss version.
* Avblockera zip-filen: Högerklicka i Utforskaren -> Egenskaper -> Kontrollera 'Avblockera' box -> tillämpa
* Extrahera zipfilen till `bin` directory
* `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[släpper]: https://github.com/PowerShell/PowerShell/releases
[signing]: ../../tools/Sign-Package.ps1
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
