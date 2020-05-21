---
title: Nyheter i PowerShell Core 6,1
description: Nya funktioner och ändringar som lanseras i PowerShell Core 6,1
ms.date: 09/13/2018
ms.openlocfilehash: 070ecb871003487e2f1ff7b0d56c44c562acaaf8
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565088"
---
# <a name="whats-new-in-powershell-core-61"></a>Nyheter i PowerShell Core 6,1

Nedan visas några av de viktigaste nya funktionerna och ändringarna som har introducerats i PowerShell Core 6,1.

Det finns också **massor** av "tråkigae-saker" som gör PowerShell snabbare och mer stabilt (plus massor och massor av fel korrigeringar)! En fullständig lista över ändringar finns [i vår ändringsloggen på GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).

Och vi kallar några namn nedan och tackar dig till [alla deltagare i communityn](https://github.com/PowerShell/PowerShell/graphs/contributors) som gjorde den här versionen möjlig.

## <a name="net-core-21"></a>.NET Core 2.1

PowerShell Core 6,1 flyttades till .NET Core 2,1 efter att den [släpptes i kan](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), vilket resulterar i ett antal förbättringar av PowerShell, inklusive:

- prestanda förbättringar (se [nedan](#performance-improvements))
- Stöd för Alpine Linux (för hands version)
- [Stöd för globalt .net-verktyg](/dotnet/core/tools/global-tools) – kommer snart till PowerShell
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a>Windows Compatibility Pack för .NET Core

I Windows levererade .NET-teamet [Windows Compatibility Pack för .net Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), en uppsättning sammansättningar som lägger till ett antal borttagna API: er tillbaka till .net core i Windows.

Vi har lagt till Windows-kompatibilitetspaketet till PowerShell Core 6,1-versionen så att moduler eller skript som använder dessa API: er kan vara beroende av att de är tillgängliga.

Windows-kompatibilitetspaketet gör det möjligt för PowerShell Core att använda **mer än 1900 cmdlets som levereras med Windows 10 oktober 2018 Update och Windows Server 2019**.

## <a name="support-for-application-whitelisting"></a>Stöd för program vit listning

PowerShell Core 6,1 har paritet med Windows PowerShell 5,1 som stöder [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) -och [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) -vit listning. Med Application vit listning kan du få detaljerad kontroll över vilka binärfiler som får köras med PowerShell- [begränsat språk läge](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).

## <a name="performance-improvements"></a>Prestandaförbättringar

PowerShell Core 6,0 gjorde några betydande prestanda förbättringar. PowerShell Core 6,1 fortsätter att förbättra hastigheten på vissa åtgärder.

Till exempel `Group-Object` har sped upp med 66%:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | Windows PowerShell 5,1 | PowerShell Core 6,0 | PowerShell Core 6,1 |
|--------------|------------------------|---------------------|---------------------|
| Tid (SEK)   | 25,178                 | 19,653              | 6,641               |
| Hastighets anslutning (%) | Ej tillämpligt                    | 21,9%               | 66,2%               |

På samma sätt har sorterings scenarier som det här förbättrats med mer än 15%:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | Windows PowerShell 5,1 | PowerShell Core 6,0 | PowerShell Core 6,1 |
|--------------|------------------------|---------------------|---------------------|
| Tid (SEK)   | 12,170                 | 8,493               | 7,08                |
| Hastighets anslutning (%) | Ej tillämpligt                    | 30,2%               | 16,6%               |

`Import-Csv`har också sped varit märkbart efter en regression från Windows PowerShell.
I följande exempel används en test-CSV med 26 616 rader och sex kolumner:

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | Windows PowerShell 5,1 | PowerShell Core 6,0 | PowerShell Core 6,1    |
|--------------|------------------------|---------------------|------------------------|
| Tid (SEK)   | 0,441                  | 1,069               | 0,268                  |
| Hastighets anslutning (%) | Ej tillämpligt                    | – 142,4%             | 74,9% (39,2% från WPS) |

Till sist har konverteringen från JSON till `PSObject` sped upp med mer än 50% sedan Windows PowerShell.
I följande exempel används ~ 2 MB test-JSON-fil:

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | Windows PowerShell 5,1 | PowerShell Core 6,0 | PowerShell Core 6,1    |
|--------------|------------------------|---------------------|------------------------|
| Tid (SEK)   | 0,259                  | 0,577               | 0,125                  |
| Hastighets anslutning (%) | Ej tillämpligt                    | – 122,8%             | 78,3% (51,7% från WPS) |

## <a name="check-system32-for-compatible-in-box-modules-on-windows"></a>Sök `system32` efter kompatibla moduler i rutan i Windows

I Windows 10 1809-uppdateringen och Windows Server 2019 har vi uppdaterat ett antal inbyggda PowerShell-moduler för att markera dem som kompatibla med PowerShell Core.

När PowerShell Core 6,1 startas tas den automatiskt med `$windir\System32` som en del av `PSModulePath` miljövariabeln. Det exponerar dock bara moduler för `Get-Module` och `Import-Module` om det `CompatiblePSEdition` är markerat som kompatibelt med `Core` .

```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> Du kan se olika tillgängliga moduler beroende på vilka roller och funktioner som är installerade.

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

Du kan åsidosätta det här beteendet för att visa alla moduler med hjälp av `-SkipEditionCheck` switch-parametern.
Vi har också lagt till en `PSEdition` egenskap i tabellens utdata.

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

Mer information om det här problemet finns i [PowerShell-RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).

## <a name="markdown-cmdlets-and-rendering"></a>Markdown-cmdletar och rendering

Markdown är en standard för att skapa läsbara klartext-dokument med grundläggande formatering som kan återges i HTML.

Vi har lagt till några cmdletar i 6,1 som gör det möjligt att konvertera och återge markdown-dokument i-konsolen, inklusive:

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

Återge till exempel `Show-Markdown` en MARKDOWN-fil i-konsolen:

![Visa markdown-exempel](media/What-s-New-in-PowerShell-Core-61/markdown_example.png)

Mer information om hur dessa cmdlets fungerar finns i [denna RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).

## <a name="experimental-feature-flags"></a>Experimentella funktions flaggor

Vi har aktiverat stöd för [experimentella funktioner][]. Detta gör att PowerShell-utvecklare kan leverera nya funktioner och få feedback innan designen är klar. På så sätt undviker vi att göra ändringar när designen utvecklas.

Använd `Get-ExperimentalFeature` för att hämta en lista över tillgängliga experimentella funktioner. Du kan aktivera eller inaktivera dessa funktioner med `Enable-ExperimentalFeature` och `Disable-ExperimentalFeature` .

Du kan lära dig mer om den här funktionen i [PowerShell-RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).

## <a name="web-cmdlet-improvements"></a>Förbättringar av webb-cmdlet

Till [@markekraus](https://github.com/markekraus) och med en hel sväng av förbättringar har gjorts i våra webb-cmdlets:[`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)
och [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod) .

- [PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) – standard kodningen anges till UTF-8 för `application-json` svar
- [PR-#6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation`parameter för att tillåta `Content-Type` huvuden som inte är standarder-kompatibla
- [PR-#5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form`parameter för stöd för förenklad `multipart/form-data` Support
- [PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) -kompatibel, SKIFT läges okänslig hantering av Relations nycklar
- [PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) – Lägg till `-Resume` parameter för webb-cmdletar

## <a name="remoting-improvements"></a>Förbättringar av fjärrkommunikation

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a>PowerShell Direct för behållare försöker använda PowerShell Core först

[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) är en funktion i PowerShell och Hyper-v som gör att du kan ansluta till en virtuell Hyper-V-dator eller-behållare utan nätverks anslutning eller andra tjänster för fjärrhantering.

Tidigare anslöt PowerShell Direct till med Windows PowerShell-instansen inkorg på behållaren. Nu försöker PowerShell Direct först ansluta med alla tillgängliga `pwsh.exe` på `PATH` miljö variabeln. Om `pwsh.exe` inte är tillgängligt går PowerShell Direct tillbaka till att använda `powershell.exe` .

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a>`Enable-PSRemoting`skapar nu separata Fjärrslutpunkter för för hands versioner

`Enable-PSRemoting`nu skapas två konfigurationer för fjärrsessioner:

- En för den högre versionen av PowerShell. Till exempel `PowerShell.6`. Den här slut punkten som kan förlita sig på en del versions uppdateringar som "system-bred" PowerShell 6-session konfiguration
- En version – en konfiguration av en speciell session, till exempel:`PowerShell.6.1.0`

Det här beteendet är användbart om du vill ha flera PowerShell 6-versioner installerade och tillgängliga på samma dator.

Dessutom hämtar för hands versioner av PowerShell sina egna konfigurationer för fjärrsessioner efter att du kört `Enable-PSRemoting` cmdleten:

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

Dina utdata kan vara olika om du inte har konfigurerat WinRM tidigare.

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

Sedan kan du se separata PowerShell-sessionsbaserade för för hands versionen och stabila versioner av PowerShell 6, och för varje enskild version.

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a>`user@host:port`syntax som stöds för SSH

SSH-klienter stöder vanligt vis en anslutnings sträng i formatet `user@host:port` . Med tillägget av SSH som ett protokoll för PowerShell-fjärrkommunikation har vi lagt till stöd för det här formatet för anslutnings strängen:

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a>MSI-alternativ för att lägga till Explorer Shell snabb menyn i Windows

Tack för [@bergmeister](https://github.com/bergmeister) kan du nu aktivera en snabb meny i Windows. Nu kan du öppna din systemomfattande installation av PowerShell 6,1 från valfri mapp i Utforskaren i Windows:

![Snabb menyn i Shell för PowerShell 6](media/What-s-New-in-PowerShell-Core-61/shell_context_menu.png)

## <a name="goodies"></a>Godbitar

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a>"Kör som administratör" i Windows Shortcuts snabb lista

Tack vare [@bergmeister](https://github.com/bergmeister) , innehåller PowerShell Core-genvägens snabb lista nu "kör som administratör":

![Kör som administratör i snabb listan för PowerShell 6](media/What-s-New-in-PowerShell-Core-61/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a>`cd -`återgår till föregående katalog

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

Eller på Linux:

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

Även `cd` och `cd --` ändra till `$HOME` .

### `Test-Connection`

Till [@iSazonov](https://github.com/iSazonov) och [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) med har cmdleten hamnat till PowerShell Core.

### <a name="update-help-as-non-admin"></a>`Update-Help`som icke-administratör

Efter populära behov `Update-Help` behöver inte längre köras som administratör. `Update-Help`nu ska vi använda standardinställningarna för att spara hjälp till en mapp med användar omfång.

### <a name="new-methodsproperties-on-pscustomobject"></a>Nya metoder/egenskaper på`PSCustomObject`

Tack för [@iSazonov](https://github.com/iSazonov) , har vi lagt till nya metoder och egenskaper för `PSCustomObject` . `PSCustomObject`innehåller nu en `Count` / `Length` egenskap som andra objekt.

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

Det här arbetet innehåller också `ForEach` och `Where` metoder som gör att du kan använda och filtrera efter `PSCustomObject` objekt:

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

Tack för @SimonWahlin , har vi lagt till- `-Not` parametern i `Where-Object` . Nu kan du filtrera ett objekt i pipelinen för att det inte finns någon egenskap, eller ett egenskaps värde som är null/tomt.

Det här kommandot returnerar till exempel alla tjänster som inte har några beroende tjänster definierade:

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a>`New-ModuleManifest`skapar ett struktur löst UTF-8-dokument

Med tanke på vår flytt till BOM-mindre UTF-8 i PowerShell 6,0 har vi uppdaterat `New-ModuleManifest` cmdleten för att skapa ett BOM-mindre UTF-8-dokument i stället för ett UTF-16 1.

### <a name="conversions-from-psmethod-to-delegate"></a>Konverteringar från PSMethod till delegate

Tack för [@powercode](https://github.com/powercode) har vi nu stöd för konverteringen av a `PSMethod` till ett ombud. På så sätt kan du göra saker som att skicka `PSMethod` `[M]::DoubleStrLen` som ett ombuds värde till `[M]::AggregateString` :

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

Om du vill ha mer information om den här ändringen kan du kolla in [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).

### <a name="standard-deviation-in-measure-object"></a>Standard avvikelse i`Measure-Object`

Tack för [@CloudyDino](https://github.com/CloudyDino) , har vi lagt till en `StandardDeviation` egenskap för `Measure-Object` :

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

Tack än [@maybe-hello-world](https://github.com/maybe-hello-world) , `Get-PfxCertificate` har nu `Password` parametern, som tar en `SecureString` . På så sätt kan du använda den icke-interaktivt:

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a>Borttagning av `more` funktionen

Tidigare levererade PowerShell en funktion i Windows `more` som har omslutits `more.com` . Funktionen har nu tagits bort.

`help`Funktionen ändrades också till att användas `more.com` i Windows eller systemets standard-pager som anges av `$env:PAGER` på andra plattformar än Windows-plattformar.

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a>`cd DriveName:`returnerar nu användare till den aktuella arbets katalogen i den enheten

Tidigare har du använt `Set-Location` eller `cd` för att återgå till en PSDrive som har skickat användare till standard platsen för den enheten.

Till [@mcbobke](https://github.com/mcbobke) och med skickas nu användare till den senast kända aktuella arbets katalogen för sessionen.

### <a name="windows-powershell-type-accelerators"></a>Windows PowerShell-typ acceleratorer

I Windows PowerShell inkluderade vi följande typ acceleratorer för att göra det enklare att arbeta med sina respektive typer:

- `[adsi]`: `System.DirectoryServices.DirectoryEntry`
- `[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`
- `[wmi]`: `System.Management.ManagementObject`
- `[wmiclass]`: `System.Management.ManagementClass`
- `[wmisearcher]`: `System.Management.ManagementObjectSearcher`

Dessa typ acceleratorer inkluderades inte i PowerShell 6, men har lagts till i PowerShell 6,1 som körs i Windows.

De här typerna är användbara för att enkelt konstruera AD-och WMI-objekt.

Du kan till exempel fråga med LDAP:

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

I följande exempel skapas ett Win32_OperatingSystem CIM-objekt:

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

Det här exemplet returnerar ett ManagementClass-objekt för Win32_OperatingSystem-klassen.

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a>`-lp`alias för alla `-LiteralPath` parametrar

[@kvprasoon](https://github.com/kvprasoon)Vi har nu ett parameter Ali Aset `-lp` för alla inbyggda PowerShell-cmdletar som har en `-LiteralPath` parameter.

## <a name="breaking-changes"></a>Icke-bakåtkompatibla ändringar

### <a name="msi-based-installation-paths-on-windows"></a>MSI-baserade installations Sök vägar i Windows

I Windows installeras nu MSI-paketet på följande sökväg:

- `$env:ProgramFiles\PowerShell\6\`för en stabil installation av 6. x
- `$env:ProgramFiles\PowerShell\6-preview\`för för hands version av 6. x

Den här ändringen ser till att PowerShell-kärnan kan uppdateras/servas av Microsoft Update.

Mer information finns i PowerShell- [RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a>Telemetri kan bara inaktive ras med en miljö variabel

PowerShell-kärnan skickar grundläggande telemetridata till Microsoft när den startas. Datan innehåller operativ systemets namn, OS-version och PowerShell-version. Med den här informationen kan vi bättre förstå de miljöer där PowerShell används och göra det möjligt för oss att prioritera nya funktioner och korrigeringar.

Om du vill inaktivera den här Telemetrin ställer du in miljövariabeln `POWERSHELL_TELEMETRY_OPTOUT` på `true` , `yes` eller `1` . Vi stöder inte längre borttagning av filen `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` för att inaktivera telemetri.

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a>Otillåten grundläggande autentisering över HTTP i PowerShell-fjärrkommunikation på UNIX-plattformar

För att förhindra användning av okrypterad trafik, kräver PowerShell-fjärrkommunikation på UNIX-plattformar att NTLM/Negotiate eller HTTPS används nu.

Mer information om dessa ändringar finns i [problem #6779](https://github.com/PowerShell/PowerShell/issues/6779).

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a>Borttaget `VisualBasic` som ett språk som stöds i tilläggs typen

Tidigare kunde du kompilera Visual Basic kod med hjälp av `Add-Type` cmdleten. Visual Basic användes sällan med `Add-Type` . Vi har tagit bort den här funktionen för att minska storleken på PowerShell.

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a>Rensade användning av `CommandTypes.Workflow` och`WorkflowInfoCleaned`

Mer information om dessa ändringar finns i [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).

### <a name="group-object-now-sorts-the-groups"></a>Gruppera objekt sorterar nu grupperna

Som en del av prestanda förbättringen `Group-Object` returnerar nu en sorterad lista över grupperna.
Även om du inte bör förlita dig på ordern, kan du bryta den här ändringen om du ville ha den första gruppen. Vi beslutade att den här prestanda förbättringen var värt förändringen eftersom effekten av att vara beroende av tidigare beteende är låg.

Mer information om den här ändringen finns i [problem #7409](https://github.com/PowerShell/PowerShell/issues/7409).

<!-- URL references -->
[Experimentella funktioner]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
