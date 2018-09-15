---
title: Nyheter i PowerShell Core 6.1
description: Nya funktioner och ändringar som introducerades i PowerShell Core 6.1
ms.date: 09/13/2018
ms.openlocfilehash: b95b9dd504ea2a165a4689a3b28d2298644e5e68
ms.sourcegitcommit: aa41249f153bbc6e11667ade60c878980c15abc6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/14/2018
ms.locfileid: "45611530"
---
# <a name="whats-new-in-powershell-core-61"></a>Nyheter i PowerShell Core 6.1

Nedan visas ett urval av några av de nya funktioner och ändringar som har införts i PowerShell Core 6.1.

Det finns också **ton** av ”tråkiga” som gör att PowerShell snabbare och mer tillförlitliga (plus utbudet felkorrigeringar)!
En fullständig lista över ändringar, Kolla in vår [ändringsloggen på GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).

Och medan vi anropa vissa namn nedan tack till [alla community-deltagare](https://github.com/PowerShell/PowerShell/graphs/contributors) som möjligt den här versionen.

## <a name="net-core-21"></a>.NET core 2.1

PowerShell Core 6.1 flyttas till .NET Core 2.1 när den var [introducerades i maj](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), vilket resulterar i ett antal förbättringar i PowerShell, inklusive:

- prestandaförbättringar (se [nedan](#performance-improvements))
- Alpine Linux-support (förhandsversion)
- [Stöd för .NET-globala verktyg](/dotnet/core/tools/global-tools) – kommer snart att PowerShell
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a>Windows Compatibility Pack för .NET Core

På Windows, .NET-teamet levereras de [Windows Compatibility Pack för .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), en uppsättning sammansättningar som lägger till ett antal bort API: er till .NET Core för Windows.

Vi har lagt till Compatibility-Pack för Windows PowerShell Core 6.1 versionen så att alla moduler eller skript som använder dessa API: er kan använda dem som det är tillgängligt.

Windows Compatibility Pack gör det möjligt för PowerShell Core att använda **mer än 1900 cmdletar som levereras med Windows 10 oktober 2018 Update och Windows Server 2019**.

## <a name="support-for-application-whitelisting"></a>Stöd för listan över tillåtna program

PowerShell Core 6.1 har paritet med Windows PowerShell 5.1 stöd [AppLocker](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) och [Device Guard](https://docs.microsoft.com/en-us/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) listan över tillåtna program.
Listan över tillåtna program gör detaljerad kontroll över vilka-binärfiler ska kunna köras tillsammans med PowerShell [begränsad språkläge](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).

## <a name="performance-improvements"></a>Prestandaförbättringar

PowerShell Core 6.0 gjort några betydande förbättringar.
PowerShell Core 6.1 fortsätter att förbättra hastigheten på vissa åtgärder.

Till exempel `Group-Object` har sped med 66%:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| Tid (sek)   | 25.178                 | 19.653              | 6.641               |
| Hastigheter (%) | Saknas                    | 21.9%               | 66.2%               |

På samma sätt har sortering scenarier som den här förbättrats med mer än 15%:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| Tid (sek)   | 12.170                 | 8.493               | 7.08                |
| Hastigheter (%) | Saknas                    | 30,2%               | 16.6%               |

`Import-Csv` har också tagits sped avsevärt efter en regression från Windows PowerShell.
I följande exempel används ett test CSV med 26,616 sex kolumner:

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| Tid (sek)   | 0.441                  | 1.069               | 0.268                  |
| Hastigheter (%) | Saknas                    | -142.4%             | 74.9% (39.2. % från WPS) |

Till sist konvertering från JSON till `PSObject` har varit sped med mer än 50% sedan Windows PowerShell.
I följande exempel används en ~ 2MB test JSON-fil:

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| Tid (sek)   | 0.259                  | 0.577               | 0,125                  |
| Hastigheter (%) | Saknas                    | -122.8%             | 78.3% (51.7% från WPS) |

## <a name="check-system32-for-compatible-inbox-modules-on-windows"></a>Kontrollera `system32` för kompatibla inkorg moduler på Windows

Vi har uppdaterat ett antal inkorg PowerShell-moduler för att markera dem som kompatibel med PowerShell Core i Windows 10 1809 update och Windows Server 2019.

När PowerShell Core 6.1 startas automatiskt inkluderar `$windir\System32` som en del av den `PSModulePath` miljövariabeln.
Men det endast visar moduler att `Get-Module` och `Import-Module` om dess `CompatiblePSEdition` är markerad som kompatibel med `Core`.


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> Du kan se olika tillgängliga moduler beroende på vilka roller och funktioner installeras.

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

Du kan åsidosätta detta beteende om du vill visa alla moduler med den `-SkipEditionCheck` växla parametern.
Vi har även lagt till en `PSEdition` egenskap till tabellutdata.

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Desk      {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Desk      {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Desk      {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Desk      {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Desk      {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

Mer information om det här beteendet Kolla in [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).

## <a name="markdown-cmdlets-and-rendering"></a>Markdown-cmdletar och rendering

Markdown är en standard för att skapa läsbara klartext dokument med enkla format som kan återges i HTML-format.

Vi har lagt till vissa cmdlets i 6.1 så att du kan konvertera och rendera Markdown-dokument i konsolen, inklusive:

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

Till exempel `Show-Markdown` visas med en Markdown-fil i konsolen:

![Visa Markdown-exempel](./images/markdown_example.png)

Mer information om hur dessa cmdlets fungerar finns i [denna RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).

## <a name="experimental-feature-flags"></a>Experimentell funktion flaggor

Experimentell funktion flaggor kan du aktivera funktioner som inte har avslutats.
Dessa experimentella funktioner stöds inte och kan ha buggar.

Du kan läsa mer om den här funktionen i [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).

## <a name="web-cmdlet-improvements"></a>Förbättringar för Web-cmdlet

Tack vare @markekraus, en hela slew förbättringar har gjorts i vår webb-cmdletar: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)
och [ `Invoke-RestMethod` ](/powershell/module/microsoft.powershell.utility/invoke-restmethod).

- [PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) -standard kodning inställt UTF-8 för `application-json` svar
- [PR #6018](https://github.com/PowerShell/PowerShell/pull/6018)  -  `-SkipHeaderValidation` parametern så att `Content-Type` rubriker som inte är standardkompatibel
- [PR #5972](https://github.com/PowerShell/PowerShell/pull/5972)  -  `Form` parametern för förenklad `multipart/form-data` stöd
- [PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - kompatibla, skiftlägesokänslig hantering av nycklar för relationen
- [PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) – Lägg till `-Resume` parametern för web-cmdletar

## <a name="remoting-improvements"></a>Förbättringar för fjärrkommunikation

### <a name="powershell-direct-tries-to-use-powershell-core-first"></a>PowerShell Direct försöker först använda PowerShell Core

[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) är en funktion i PowerShell och Hyper-V som gör det möjligt att ansluta till en Hyper-V virtuell dator utan nätverksanslutning eller andra tjänster för fjärrhantering.

Tidigare var ansluten PowerShell Direct med hjälp av Windows PowerShell-instansen inkorg på den virtuella datorn.
Nu, PowerShell Direct först försöker ansluta med hjälp av alla tillgängliga `pwsh.exe` på den `PATH` miljövariabeln.
Om `pwsh.exe` är inte tillgänglig, PowerShell Direct faller tillbaka om du vill använda `powershell.exe`.

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a>`Enable-PSRemoting` skapar nu separata fjärrkommunikation slutpunkter för förhandsversioner

`Enable-PSRemoting` Nu skapar två fjärrkommunikation sessionskonfigurationer:

- En för den huvudsakliga versionen av PowerShell. Till exempel`PowerShell.6`. Den här slutpunkten kan förlita sig på mellan mindre versionsuppdateringar som sessionskonfigurationen ”systemomfattande” PowerShell 6
- En versionsspecifika sessionskonfiguration, till exempel: `PowerShell.6.1.0`

Detta är användbart om du vill ha flera PowerShell 6 versioner installerade och kan nås på samma dator.

Dessutom förhandsversioner av PowerShell nu få sina egna fjärrkommunikation sessionskonfigurationer efter körning i `Enable-PSRemoting` cmdlet:

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

Dina utdata kan skilja sig om du inte har konfigurerat WinRM innan.

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

Sedan kan du se separata PowerShell-sessionskonfigurationer för förhandsversionen och stabil bygger på PowerShell 6 och för varje specifik version.

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

### <a name="userhostport-syntax-supported-for-ssh"></a>`user@host:port` syntax som stöds för SSH

SSH-klienter normalt stöder en anslutningssträng i formatet `user@host:port`.
Med hjälp av SSH som ett protokoll för PowerShell-fjärrkommunikation, har vi lagt till stöd för det här formatet för anslutningssträngen:

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a>MSI-alternativet att lägga till snabbmenyn i explorer-gränssnittet på Windows

Tack vare @bergmeister, nu kan du aktivera en snabbmeny på Windows. Nu kan du öppna din systemomfattande installation av PowerShell 6.1 från valfri mapp i Windows Explorer:

![Shell-snabbmenyn för PowerShell 6](./images/shell_context_menu.png)

## <a name="goodies"></a>Godbitar

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a>”Kör som administratör” i listan över Windows genväg hopp

Tack vare @bergmeister, genvägen PowerShell Core jump-listan innehåller nu ”kör som administratör”:

![Kör som administratör i PowerShell 6 jump-listan](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a>`cd -` Returnerar föregående katalog

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

Dessutom `cd --` ändras till `$HOME`.

### `Test-Connection`

Tack vare @iSazonov, [ `Test-Connection` ](/powershell/module/microsoft.powershell.management/test-connection) cmdlet har varit portas till PowerShell Core.

### <a name="update-help-as-non-admin"></a>`Update-Help` som icke-administratörer

På allmän begäran `Update-Help` inte längre behöver köras som administratör.
`Update-Help` som standard nu sparar hjälper till att en användarspecifika mapp.

### <a name="new-methodsproperties-on-pscustomobject"></a>Nya metoder/egenskaper på `PSCustomObject`

Tack vare @iSazonov, vi har lagt till nya metoder och egenskaper som `PSCustomObject`.
`PSCustomObject` innehåller nu en `Count` / `Length` egenskap som ger antalet objekt.

Båda exemplen returnera `2` som antalet `PSCustomObjects` i samlingen.

```powershell
@(
[pscustomobject]@{foo = '1'},
[pscustomobject]@{bar = '2' }).Length
```

```powershell
@(
[pscustomobject]@{foo = '1'},
[pscustomobject]@{bar = '2' }).Count
```

Det här att fungera även `ForEach` och `Where` metoder som gör det möjligt att driva och filtrera på `PSCustomObject` objekt:

```powershell
@(
>> [pscustomobject]@{foo = 1},
>> [pscustomobject]@{foo = 2 }).ForEach({$_.foo+1})
```

```Output
2
3
```

```powershell
@(
>> [pscustomobject]@{foo = 1},
>> [pscustomobject]@{foo = 2 }).Where({$_.foo -gt 1})
```

```Output
foo
---
  2
```

### `Where-Object -Not`

Tack vare @SimonWahlin, vi har lagt till den `-Not` parameter `Where-Object`.
Du kan nu filtrera ett objekt på pipelinen för icke-förekomsten av en egenskap eller ett egenskapsvärde för null/tomt.

Det här kommandot returnerar till exempel alla tjänster som inte har några definierade beroende tjänster:

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a>`New-ModuleManifest` skapar ett BOM utan UTF-8-dokument

Med vår övergång till BOM utan UTF-8 i PowerShell 6.0 kan vi har uppdaterat den `New-ModuleManifest` cmdlet för att skapa ett BOM utan UTF-8-dokument i stället för en UTF-16 något.

### <a name="conversions-from-psmethod-to-delegate"></a>Konverteringar från PSMethod till ombud

Tack vare @powercode, vi nu stöd för konvertering av en `PSMethod` till ett ombud.
Du kan till exempel skicka `PSMethod` `[M]::DoubleStrLen` som ett ombud värde i `[M]::AggregateString`:

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

Mer information om den här ändringen finns [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).

### <a name="standard-deviation-in-measure-object"></a>Standardavvikelsen i `Measure-Object`

Tack vare @CloudyDino, vi har lagt till en `StandardDeviation` egenskap `Measure-Object`:

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

Tack vare @maybe-hello-world, `Get-PfxCertificate` har nu den `Password` parametern, som tar en `SecureString`. På så sätt kan du använda den icke-interaktivt:

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a>Borttagning av den `more` funktion

Tidigare levererat PowerShell en funktion i Windows som kallas `more` som omslutna `more.com`.
Funktionen har nu tagits bort.

Även den `help` funktionen ändrats till att använda `more.com` på Windows eller systemets standard personsökare anges av `$env:PAGER` på icke-Windows-plattformar.

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a>`cd DriveName:` Nu returnerar användare till den aktuella arbetskatalogen i den här enheten

Tidigare med hjälp av `Set-Location` eller `cd` att återgå till en PSDrive skickas användarna till standardplatsen för den här enheten.

Tack vare @mcbobke, användarna skickas nu till den senaste kända aktuella arbetskatalogen för den aktuella sessionen.

### <a name="windows-powershell-type-accelerators"></a>Acceleratorer för Windows PowerShell-typ

Vi inkluderat följande typ-acceleratorer för att göra det lättare att arbeta med sina respektive typer i Windows PowerShell:

- `[adsi]`: `System.DirectoryServices.DirectoryEntry`
- `[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`
- `[wmi]`: `System.Management.ManagementObject`
- `[wmiclass]`: `System.Management.ManagementClass`
- `[wmisearcher]`: `System.Management.ManagementObjectSearcher`

Dessa typ acceleratorer inkluderades inte i PowerShell 6, men har lagts till PowerShell 6.1 som körs på Windows.

Dessa typer är användbara enkelt konstruera AD och WMI-objekt.

Du kan till exempel fråga genom att använda LDAP:

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

Båda exemplen skapar du en Win32_OperatingSystem CIM-objekt:

```powershell
[wmi]"win32_operatingsystem=@"
[wmiclass]"win32_operatingsystem"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a>`-lp` alias för alla `-LiteralPath` parametrar

Tack vare @kvprasoon, nu har vi ett parameteralias `-lp` för alla inbyggda PowerShell-cmdletar som har en `-LiteralPath` parametern.

## <a name="breaking-changes"></a>Större ändringar

### <a name="msi-based-installation-paths-on-windows"></a>MSI-baserad installation sökvägar på Windows

På Windows installerar MSI-paketet nu till följande sökväg:

- `$env:ProgramFiles\PowerShell\6\` för att säkra installera 6.x
- `$env:ProgramFiles\PowerShell\6-preview\` för att installera förhandsversion 6.x

Den här ändringen gör att PowerShell Core kan vara uppdaterad/underhålls av Microsoft Update.

Mer information finns i [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a>Telemetri kan endast inaktiveras med en miljövariabel

PowerShell Core skickar grundläggande telemetridata till Microsoft när den startas. Data innehåller namn på operativsystem, operativsystemversion och PowerShell-version. Den här informationen gör det möjligt för oss att bättre förstå de miljöer där PowerShell används och gör det möjligt för oss att prioritera nya funktioner och korrigeringar.

Om du vill välja bort den här telemetrin, ange miljövariabeln `POWERSHELL_TELEMETRY_OPTOUT` till `true`, `yes`, eller `1`. Vi har inte längre stöd för borttagning av filen `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` att inaktivera telemetri.

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a>Tillåts inte grundläggande autentisering över HTTP i PowerShell-fjärrkommunikation för Unix-plattformar

Om du vill förhindra användning av okrypterade trafik kräver PowerShell-fjärrkommunikation på Unix-plattformar nu användningen av NTLM/förhandla eller HTTPS.

Mer information om dessa ändringar finns [PR #6799](https://github.com/PowerShell/PowerShell/pull/6799).

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a>Ta bort `VisualBasic` som ett språk som stöds i Add-Type

Tidigare kunde du kompilera Visual Basic kod med den `Add-Type` cmdlet.
Visual Basic används sällan med `Add-Type`. Vi har tagit bort den här funktionen för att minska storleken på PowerShell.

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a>Rensa användningsområden för `CommandTypes.Workflow` och `WorkflowInfoCleaned`

Mer information om dessa ändringar finns [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).
