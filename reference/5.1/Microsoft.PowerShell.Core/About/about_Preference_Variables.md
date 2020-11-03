---
description: Variabler som anpassar PowerShell-beteendet.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_preference_variables?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Preference_Variables
ms.openlocfilehash: 25677cf687349bf805b66a116d3b2f09d27037bd
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271508"
---
# <a name="about-preference-variables"></a>Om Preferences-variabler

## <a name="short-description"></a>Kort beskrivning

Variabler som anpassar PowerShell-beteendet.

## <a name="long-description"></a>Lång beskrivning

PowerShell innehåller en uppsättning variabler som gör att du kan anpassa dess beteende. Dessa inställningar fungerar som alternativ i GUI-baserade system.

Inställningarna för variabler påverkar PowerShell-operativsystemet och alla kommandon som körs i miljön. I många fall har cmdletarna parametrar som du kan använda för att åsidosätta inställnings beteendet för ett särskilt kommando.

I följande tabell visas inställningarna för variabler och standardvärden.

|             Variabel             |       Standardvärde       |
| -------------------------------- | ------------------------- |
| `$ConfirmPreference`             | Hög                      |
| `$DebugPreference`               | SilentlyContinue          |
| `$ErrorActionPreference`         | Fortsätt                  |
| `$ErrorView`                     | NormalView                |
| `$FormatEnumerationLimit`        | 4                         |
| `$InformationPreference`         | SilentlyContinue          |
| `$LogCommandHealthEvent`         | Falskt (ej loggad)        |
| `$LogCommandLifecycleEvent`      | Falskt (ej loggad)        |
| `$LogEngineHealthEvent`          | Sant (loggad)             |
| `$LogEngineLifecycleEvent`       | Sant (loggad)             |
| `$LogProviderLifecycleEvent`     | Sant (loggad)             |
| `$LogProviderHealthEvent`        | Sant (loggad)             |
| `$MaximumAliasCount`             | 4096                      |
| `$MaximumDriveCount`             | 4096                      |
| `$MaximumErrorCount`             | 256                       |
| `$MaximumFunctionCount`          | 4096                      |
| `$MaximumHistoryCount`           | 4096                      |
| `$MaximumVariableCount`          | 4096                      |
| `$OFS`                           | (Tecken avstånd ( `" "` )) |
| `$OutputEncoding`                | **ASCIIEncoding** -objekt  |
| `$ProgressPreference`            | Fortsätt                  |
| `$PSDefaultParameterValues`      | (Ingen-tom hash-tabell) |
| `$PSEmailServer`                 | (Ingen)                    |
| `$PSModuleAutoLoadingPreference` | Alla                       |
| `$PSSessionApplicationName`      | WSMan                     |
| `$PSSessionConfigurationName`    | `http://schemas.microsoft.com/powershell/Microsoft.PowerShell` |
| `$PSSessionOption`               | Se [$PSSessionOption](#pssessionoption) |
| `$Transcript`                    | (ingen)                    |
| `$VerbosePreference`             | SilentlyContinue          |
| `$WarningPreference`             | Fortsätt                  |
| `$WhatIfPreference`              | Falskt                     |

PowerShell innehåller följande miljövariabler som lagrar användar inställningar. Mer information om de här miljövariablerna finns [about_Environment_Variables](about_Environment_Variables.md).

- `env:PSExecutionPolicyPreference`
- `$env:PSModulePath`

> [!NOTE]
> Ändringar av preferens variabeln börjar bara gälla i skript och funktioner om dessa skript eller funktioner har definierats i samma omfång som den omfattning i vilken preferensen användes. Mer information finns i [about_Scopes](about_Scopes.md).

## <a name="working-with-preference-variables"></a>Arbeta med Preferences-variabler

I det här dokumentet beskrivs var och en av inställningarna för variabler.

Om du vill visa det aktuella värdet för en speciell inställnings variabel skriver du variabelns namn. Till exempel visar följande kommando `$ConfirmPreference` variabelns värde.

```powershell
 $ConfirmPreference
```

```Output
High
```

Om du vill ändra variabelns värde använder du en tilldelnings instruktion. Följande uttryck ändrar till exempel `$ConfirmPreference` parameterns värde till **medium**.

```powershell
$ConfirmPreference = "Medium"
```

De värden som du anger är bara för den aktuella PowerShell-sessionen. Om du vill göra variablerna effektiva i alla PowerShell-sessioner lägger du till dem i din PowerShell-profil. Mer information finns i [about_Profiles](about_Profiles.md).

## <a name="working-remotely"></a>Arbeta fjärran slutet

När du kör kommandon på en fjärrdator, omfattas fjärrkommandona bara av inställningarna som anges i fjärrdatorns PowerShell-klient. Om du till exempel kör ett fjärrkommando, avgör värdet för fjärrdatorns `$DebugPreference` variabel hur PowerShell svarar på fel sökning av meddelanden.

Mer information om fjärrkommandon finns i [about_Remote](about_Remote.md).

### <a name="confirmpreference"></a>\$ConfirmPreference

Anger om PowerShell automatiskt uppmanas att bekräfta innan en cmdlet eller funktion körs.

`$ConfirmPreference`Variabelns giltiga värden är **hög** , **medel** eller **låg**. Cmdlets och Functions tilldelas en risk för **hög** , **medel** eller **låg**. När värdet för `$ConfirmPreference` variabeln är mindre än eller lika med den risk som tilldelats till en cmdlet eller funktion, uppmanas du automatiskt att bekräfta innan du kör cmdleten eller funktionen.

Om värdet för `$ConfirmPreference` variabeln är **none** , uppmanar PowerShell aldrig automatiskt innan du kör en cmdlet eller funktion.

Ändra variabelns värde om du vill ändra ett bekräftelse beteende för alla cmdletar och funktioner i sessionen `$ConfirmPreference` .

Om du vill åsidosätta `$ConfirmPreference` för ett enda kommando använder du en cmdlets eller funktions **Confirm** -parameter. Om du vill begära bekräftelse använder du `-Confirm` . Använd om du vill ignorera bekräftelsen `-Confirm:$false` .

Giltiga värden för `$ConfirmPreference` :

- **Ingen** : PowerShell begär inte automatiskt. Om du vill begära bekräftelse av ett visst kommando använder du parametern **Confirm** för cmdleten eller funktionen.
- **Låg** : PowerShell uppmanas att bekräfta innan du kör cmdletar eller Functions med låg, medel eller hög risk.
- **Medium** : PowerShell upprättar en bekräftelse innan du kör cmdletar eller funktioner med medelhög eller hög risk.
- **Hög** : PowerShell uppmanas att bekräfta innan du kör cmdletar eller funktioner med hög risk.

#### <a name="detailed-explanation"></a>Detaljerad förklaring

PowerShell kan automatiskt uppmana dig att bekräfta innan du vidtar en åtgärd. Till exempel, när cmdlet eller funktion avsevärt påverkar systemet för att ta bort data eller använda en stor mängd system resurser.

```powershell
Remove-Item -Path C:\file.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\file.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [?] Help (default is "Y"):
```

Uppskattningen av risken är ett attribut för cmdleten eller funktionen som kallas **ConfirmImpact**. Användare kan inte ändra det.

Cmdlets och Functions som kan utgöra en risk för systemet har en **Confirm** -parameter som du kan använda för att begära eller ignorera bekräftelse för ett enda kommando.

Eftersom de flesta cmdletar och Functions använder standard risk värde, **ConfirmImpact** , av **medel** , och standardvärdet för `$ConfirmPreference` är **högt** , sker ingen automatisk bekräftelse. Du kan dock aktivera automatisk bekräftelse genom att ändra värdet `$ConfirmPreference` till **medel** eller **låg**.

#### <a name="examples"></a>Exempel

I det här exemplet visas effekterna av `$ConfirmPreference` variabelns standardvärde, **hög**. Det **höga** värdet bekräftar bara högrisk-cmdlets och functions. Eftersom de flesta cmdletar och funktioner är medelhög risk bekräftas de inte automatiskt och `Remove-Item` tar bort filen. Om `-Confirm` du lägger till i kommandot uppmanas användaren att bekräfta.

```powershell
$ConfirmPreference
```

```Output
High
```

```powershell
Remove-Item -Path C:\temp1.txt
```

Använd `-Confirm` för att begära bekräftelse.

```powershell
Remove-Item -Path C:\temp2.txt -Confirm
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend
[?] Help (default is "Y"):
```

I följande exempel visas effekterna av att ändra värdet för `$ConfirmPreference` till **medium**. Eftersom de flesta cmdletar och funktionen är medelhög risk bekräftas de automatiskt. Om du inte vill att bekräftelse meddelandet för ett enskilt kommando ska visas använder du **Confirm** -parametern med värdet `$false` .

```powershell
$ConfirmPreference = "Medium"
Remove-Item -Path C:\temp2.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend
[?] Help (default is "Y"):
```

```powershell
Remove-Item -Path C:\temp3.txt -Confirm:$false
```

### <a name="debugpreference"></a>\$DebugPreference

Fastställer hur PowerShell svarar på fel sökning av meddelanden som genereras av ett skript, en cmdlet eller en provider eller av ett `Write-Debug` kommando på kommando raden.

Vissa cmdletar visar fel söknings meddelanden, som vanligt vis är tekniska meddelanden som har utformats för programmerare och teknisk support personal. Fel sökning av meddelanden visas som standard inte, men du kan visa fel söknings meddelanden genom att ändra värdet för `$DebugPreference` .

Du kan använda den vanliga parametern för **fel sökning** för en cmdlet för att visa eller dölja fel söknings meddelanden för ett speciellt kommando. Mer information finns i [about_CommonParameters](about_CommonParameters.md).

Giltiga värden är följande:

- **Stop** : visar fel söknings meddelandet och stoppar körningen. Skriver ett fel till konsolen.
- **Fråga** : visar fel söknings meddelandet och du tillfrågas om du vill fortsätta. Om du lägger till en vanlig **fel söknings** parameter till ett kommando, och om kommandot har kon figurer ATS för att generera ett fel söknings meddelande, ändras värdet för `$DebugPreference` **Inquire** variabeln.
- **Fortsätt** : visar fel söknings meddelandet och fortsätter körningen.
- **SilentlyContinue** : (standard) ingen påverkan. Fel söknings meddelandet visas inte och körningen fortsätter utan avbrott.

#### <a name="examples"></a>Exempel

I följande exempel visas effekterna av att ändra värdena för `$DebugPreference` när ett `Write-Debug` kommando anges på kommando raden.
Ändringen påverkar alla fel söknings meddelanden, inklusive meddelanden som genereras av cmdlets och skript. I exemplen visas **fel söknings** parametern som visar eller döljer fel söknings meddelanden som är relaterade till ett enda kommando.

I det här exemplet visas effekterna av `$DebugPreference` variabelns standardvärde, **SilentlyContinue**. Som standard `Write-Debug` visas inte cmdletens fel söknings meddelande och bearbetningen fortsätter. När **fel söknings** parametern används åsidosätts inställningen för ett enda kommando. Användaren uppmanas att bekräfta.

```powershell
$DebugPreference
```

```Output
SilentlyContinue
```

```powershell
Write-Debug -Message "Hello, World"
```

```powershell
Write-Debug -Message "Hello, World" -Debug
```

```Output
DEBUG: Hello, World
Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend
[?] Help (default is "Y"):
```

I det här exemplet visas resultatet av `$DebugPreference` värdet **Continue** . Fel söknings meddelandet visas och kommandot fortsätter att bearbeta.

```powershell
$DebugPreference = "Continue"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
```

I det här exemplet används **fel söknings** parametern med värdet för `$false` att utelämna meddelandet för ett enda kommando. Fel söknings meddelandet visas inte.

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

I det här exemplet visas hur `$DebugPreference` du ställer in till **Stop** -värdet. Fel söknings meddelandet visas och kommandot stoppas.

```powershell
$DebugPreference = "Stop"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
Write-Debug : The running command stopped because the preference variable
 "DebugPreference" or common parameter is set to Stop: Hello, World
At line:1 char:1
+ Write-Debug -Message "Hello, World"
```

I det här exemplet används **fel söknings** parametern med värdet för `$false` att utelämna meddelandet för ett enda kommando. Fel söknings meddelandet visas inte och bearbetningen stoppas inte.

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

I det här exemplet visas en inverkan på `$DebugPreference` värdet för **frågan** . Fel söknings meddelandet visas och användaren uppmanas att bekräfta.

```powershell
$DebugPreference = "Inquire"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend
[?] Help (default is "Y"):
```

I det här exemplet används **fel söknings** parametern med värdet för `$false` att utelämna meddelandet för ett enda kommando. Fel söknings meddelandet visas inte och bearbetningen fortsätter.

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

### <a name="erroractionpreference"></a>\$ErrorActionPreference

Fastställer hur PowerShell svarar på ett icke-avslutande fel, ett fel som inte stoppar cmdlet-bearbetningen. Till exempel på kommando raden eller i ett skript, en cmdlet eller en provider, till exempel de fel som genereras av `Write-Error` cmdleten.

Du kan använda en cmdlets **ErrorAction** gemensamma parameter om du vill åsidosätta inställningen för ett speciellt kommando.

Giltiga värden är följande:

- **Fortsätt** : (standard) visar fel meddelandet och fortsätter att köra.
- **Ignore: ignorerar** fel meddelandet och fortsätter att köra kommandot. **Ignore** -värdet är avsett för användning per kommando, inte för användning som Sparad inställning. **Ignore** är inte ett giltigt värde för `$ErrorActionPreference` variabeln.
- **Fråga** : visar fel meddelandet och du tillfrågas om du vill fortsätta.
- **SilentlyContinue** : ingen påverkan. Fel meddelandet visas inte och körningen fortsätter utan avbrott.
- **Stop** : visar fel meddelandet och stoppar körningen. Förutom det fel som genereras genererar **Stop** -värdet ett ActionPreferenceStopException-objekt till fel strömmen.
  streama
- **Suspend** : pausar automatiskt ett arbets flödes jobb för att tillåta ytterligare undersökning. Efter undersökningen kan arbets flödet återupptas. **Suspend** -värdet är avsett för användning per kommando, inte för användning som Sparad inställning. **Suspend** är inte ett giltigt värde för `$ErrorActionPreference` variabeln.

`$ErrorActionPreference` och **ErrorAction** -parametern påverkar inte hur PowerShell svarar på att avsluta fel som stoppar cmdlet-bearbetningen. Mer information om den gemensamma parametern **ErrorAction** finns [about_CommonParameters](about_CommonParameters.md).

#### <a name="examples"></a>Exempel

I de här exemplen visas effekterna av de olika värdena i `$ErrorActionPreference` variabeln. Parametern **ErrorAction** används för att åsidosätta `$ErrorActionPreference` värdet.

Det här exemplet visar `$ErrorActionPreference` standardvärdet, **Fortsätt**. Ett icke-avslutande fel genereras. Meddelandet visas och bearbetningen fortsätter.

```powershell
# Change the ErrorActionPreference to 'Continue'
$ErrorActionPreference = 'Continue'
# Generate a non-terminating error and continue processing the script.
Write-Error -Message  'Test Error' ; Write-Host 'Hello World'
```

```Output
Write-Error -Message  'Test Error' ; Write-Host 'Hello World' : Test Error
    + CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
    + FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

Hello World
```

Det här exemplet visar `$ErrorActionPreference` standardvärdet, **fråga**. Ett fel genereras och en meddelande instruktion visas.

```powershell
# Change the ErrorActionPreference to 'Inquire'
$ErrorActionPreference = 'Inquire'
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
```

```Output
Confirm
Test Error
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

Det här exemplet visar `$ErrorActionPreference` uppsättningen till **SilentlyContinue**.
Fel meddelandet ignoreras.

```powershell
# Change the ErrorActionPreference to 'SilentlyContinue'
$ErrorActionPreference = 'SilentlyContinue'
# Generate an error message
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
# Error message is suppressed and script continues processing
```

```Output
Hello World
```

I det här exemplet visas `$ErrorActionPreference` mängden att **stoppa**. Det visar också det extra objekt som genererats till `$Error` variabeln.

```powershell
# Change the ErrorActionPreference to 'Stop'
$ErrorActionPreference = 'Stop'
# Error message is is generated and script stops processing
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'

# Show the ActionPreferenceStopException and the error generated
$Error[0]
$Error[1]
```

```Output
Write-Error -Message 'Test Error' ; Write-Host 'Hello World' : Test Error
At line:1 char:1
+ Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
    + FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

The running command stopped because the preference variable "ErrorActionPreference"
or common parameter is set to Stop: Test Error

Write-Error -Message 'Test Error' ; Write-Host 'Hello World' : Test Error
At line:1 char:1
+ Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
    + FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException
```

### <a name="errorview"></a>\$ErrorView

Anger visnings formatet för fel meddelanden i PowerShell.

Giltiga värden är följande:

- **NormalView** : (standard) en detaljerad vy som är avsedd för de flesta användare. Består av en beskrivning av felet och namnet på objektet som berörs av felet.
- **CategoryView** : en kortfattad, strukturerad vy utformad för produktions miljöer. Formatet är följande:

  {Category}: ({TargetName}: {TargetType}): [{Activity}], {orsak}

Mer information om fälten i **CategoryView** finns i [ErrorCategoryInfo](/dotnet/api/system.management.automation.errorcategoryinfo) -klassen.

#### <a name="examples"></a>Exempel

Det här exemplet visar hur ett fel visas när värdet för `$ErrorView` är standard, **NormalView**. `Get-ChildItem` används för att hitta en fil som inte finns.

```powershell
Get-ChildItem -Path C:\nofile.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\nofile.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path C:\nofile.txt
```

Det här exemplet visar hur samma fel visas när värdet för `$ErrorView` ändras till **CategoryView**.

```powershell
$ErrorView = "CategoryView"
Get-ChildItem -Path C:\nofile.txt
```

```Output
ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem], ItemNotFoundException
```

Det här exemplet visar att värdet för `$ErrorView` endast påverkar fel visningen. Den ändrar inte strukturen för det fel objekt som lagras i den `$Error` automatiska variabeln. Information om den `$Error` automatiska variabeln finns i [about_automatic_variables](about_Automatic_Variables.md).

Följande kommando tar objektet **ErrorRecord** associerat med det senaste felet i fel mat ris, **element 0** och formaterar alla fel objekts egenskaper i en lista.

```powershell
$Error[0] | Format-List -Property * -Force
```

```Output
PSMessageDetails      :
Exception             : System.Management.Automation.ItemNotFoundException:
                          Cannot find path 'C:\nofile.txt' because it does
                          not exist.
                        at System.Management.Automation.SessionStateInternal.
                          GetChildItems(String path, Boolean recurse, UInt32
                          depth, CmdletProviderContext context)
                        at System.Management.Automation.ChildItemCmdlet
                          ProviderIntrinsics.Get(String path, Boolean
                          recurse, UInt32 depth, CmdletProviderContext context)
                        at Microsoft.PowerShell.Commands.GetChildItemCommand.
                          ProcessRecord()
TargetObject          : C:\nofile.txt
CategoryInfo          : ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem],
                          ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,
                          Microsoft.PowerShell.Commands.GetChildItemCommand
ErrorDetails          :
InvocationInfo        : System.Management.Automation.InvocationInfo
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo : {0, 1}
```

### <a name="formatenumerationlimit"></a>\$FormatEnumerationLimit

Anger hur många räknade objekt som ska ingå i en visning. Den här variabeln påverkar inte underliggande objekt, bara visningen. När värdet för `$FormatEnumerationLimit` är färre än antalet uppräknade objekt lägger PowerShell till en ellips ( `...` ) för att visa objekt som inte visas.

**Giltiga värden** : heltal ( `Int32` )

**Standardvärde** : 4

#### <a name="examples"></a>Exempel

Det här exemplet visar hur du använder `$FormatEnumerationLimit` variabeln för att förbättra visningen av räknade objekt.

Kommandot i det här exemplet genererar en tabell som visar alla tjänster som körs på datorn i två grupper: en för att **köra** tjänster och en för **stoppade** tjänster. Den använder ett `Get-Service` kommando för att hämta alla tjänster och skickar sedan resultaten via pipelinen till `Group-Object` cmdleten, som grupperar resultaten efter tjänst status.

Resultatet är en tabell som visar statusen i kolumnen **namn** och processerna i kolumnen **grupp** . Om du vill ändra kolumn etiketterna använder du en hash-tabell, se [about_Hash_Tables](about_Hash_Tables.md). Mer information finns i exemplen i [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).

Hitta det aktuella värdet för `$FormatEnumerationLimit` .

```powershell
$FormatEnumerationLimit
```

```Output
4
```

Lista alla tjänster grupperade efter **status**. Det finns högst fyra tjänster som anges i kolumnen **grupp** för varje status `$FormatEnumerationLimit` , eftersom har värdet **4**.

```powershell
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv...}
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart...}
```

Öka värdet för till 1000 för att öka antalet objekt i listan `$FormatEnumerationLimit` . **1000** Använd `Get-Service` och `Group-Object` för att Visa tjänsterna.

```powershell
$FormatEnumerationLimit = 1000
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec...
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc...
```

Använd `Format-Table` med parametern **wrap** för att visa listan över tjänster.

```powershell
Get-Service | Group-Object -Property Status | Format-Table -Wrap
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec,
                  Client for NFS, CryptSvc, DcomLaunch, Dhcp, dmserver,
                  Dnscache, ERSvc, Eventlog, EventSystem, FwcAgent, helpsvc,
                  HidServ, IISADMIN, InoRPC, InoRT, InoTask, lanmanserver,
                  lanmanworkstation, LmHosts, MDM, Netlogon, Netman, Nla,
                  NtLmSsp, PlugPlay, PolicyAgent, ProtectedStorage, RasMan,
                  RemoteRegistry, RpcSs, SamSs, Schedule, seclogon, SENS,
                  SharedAccess, ShellHWDetection, SMT PSVC, Spooler,
                  srservice, SSDPSRV, stisvc, TapiSrv, TermService, Themes,
                  TrkWks, UMWdf, W32Time, W3SVC, WebClient, winmgmt, wscsvc,
                  wuauserv, WZCSVC, zzInterix}

41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc,
                  ClipSrv, clr_optimization_v2.0.50727_32, COMSysApp,
                  CronService, dmadmin, FastUserSwitchingCompatibility,
                  HTTPFilter, ImapiService, Mapsvc, Messenger, mnmsrvc,
                  MSDTC, MSIServer, msvsmon80, NetDDE, NetDDEdsdm, NtmsSvc,
                  NVSvc, ose, RasAuto, RDSessMgr, RemoteAccess, RpcLocator,
                  SCardSvr, SwPrv, SysmonLog, TlntSvr, upnphost, UPS, VSS,
                  WmdmPmSN, Wmi, WmiApSrv, xmlprov}
```

### <a name="informationpreference"></a>\$InformationPreference

Med `$InformationPreference` variabeln kan du ange inställningar för informations ström som du vill ska visas för användarna. Mer specifikt, informations meddelanden som du har lagt till i kommandon eller skript genom att lägga till [Write-information-](xref:Microsoft.PowerShell.Utility.Write-Information) cmdleten. Om parametern **InformationAction** används åsidosätts värdet för `$InformationPreference` variabeln. `Write-Information` introducerades i PowerShell 5,0.

Giltiga värden är följande:

- **Stop** : stoppar ett kommando eller skript vid en förekomst av `Write-Information` kommandot.
- **Fråga** : visar det informations meddelande som du anger i ett `Write-Information` kommando och frågar om du vill fortsätta.
- **Fortsätt** : visar informations meddelandet och fortsätter att köra.
- **Pausa** : pausar automatiskt ett arbets flödes jobb när ett `Write-Information` kommando har utförts, så att användarna kan se meddelandena innan de fortsätter. Arbets flödet kan återupptas på användarens eget gottfinnande.
- **SilentlyContinue** : (standard) ingen påverkan. Informations meddelandena visas inte och skriptet fortsätter utan avbrott.

### <a name="logevent"></a>\$Log *-händelse

Variablerna **Log * Event** Preferences avgör vilka typer av händelser som skrivs till PowerShell-händelseloggen i Loggboken. Som standard loggas bara motor-och leverantörs händelser. Men du kan använda variablerna **Log * Event** Preference för att anpassa din logg, till exempel loggnings händelser för kommandon.

Variablerna **Log * Event** Preferences är följande:

- `$LogCommandHealthEvent`: Loggar fel och undantag vid kommando initiering och bearbetning. Standardvärdet är `$false` (inte loggat).
- `$LogCommandLifecycleEvent`: Loggar start och stopp av kommandon och kommando pipeliner och säkerhets undantag vid kommando identifiering. Standardvärdet är `$false` (inte loggat).
- `$LogEngineHealthEvent`: Loggar fel och fel i sessioner. Standardvärdet är `$true` (loggas).
- `$LogEngineLifecycleEvent`: Loggar öppnande och stängning av sessioner. Standardvärdet är `$true` (loggas).
- `$LogProviderHealthEvent`: Loggar leverantörs fel, t. ex. läsnings-och skrivfel, fel söknings fel och anrops fel. Standardvärdet är `$true` (loggas).
- `$LogProviderLifecycleEvent`: Loggar lägger till och tar bort PowerShell-leverantörer. Standardvärdet är `$true` (loggas). Information om PowerShell-leverantörer finns [about_Providers](about_Providers.md).

Om du vill aktivera en **log *-händelse** skriver du variabeln med värdet `$true` , till exempel:

```powershell
$LogCommandLifeCycleEvent = $true
```

Om du vill inaktivera en händelse typ skriver du variabeln med värdet `$false` , till exempel:

```powershell
$LogCommandLifeCycleEvent = $false
```

De händelser som du aktiverar gäller endast för den aktuella PowerShell-konsolen. Om du vill tillämpa konfigurationen på alla-konsoler sparar du variabel inställningarna i din PowerShell-profil. Mer information finns i [about_Profiles](about_Profiles.md).

### <a name="maximumaliascount"></a>\$MaximumAliasCount

Anger hur många alias som tillåts i en PowerShell-session. Standardvärdet är **4096** och det bör vara tillräckligt för de flesta användnings områden. Du kan anpassa efter `$MaximumAliasCount` dina behov.

**Giltiga värden** : 1024-32768 ( `Int32` )

**Standard** : 4096

Om du vill räkna alias i systemet skriver du:

```powershell
(Get-Alias).count
```

### <a name="maximumdrivecount"></a>\$MaximumDriveCount

Anger hur många PowerShell-enheter som tillåts i en specifik session. Till exempel fil system enheter och data lager som exponeras av PowerShell-leverantörer och visas som enheter, till exempel `Alias:` enheterna och `HKLM:` .

**Giltiga värden** : 1024-32768 ( `Int32` )

**Standard** : 4096

Om du vill räkna alias i systemet skriver du:

```powershell
(Get-PSDrive).count
```

### <a name="maximumerrorcount"></a>\$MaximumErrorCount

Anger hur många fel som sparas i fel historiken för sessionen.

**Giltiga värden** : 256-32768 ( `Int32` )

**Standard** : 256

Objekt som representerar varje kvarhållet fel lagras i den `$Error` automatiska variabeln. `$Error` innehåller en matris med fel post objekt. Det senaste felet är det första objektet i matrisen `$Error[0]` .

Om du vill räkna felen i systemet använder du `$Error` matrisens **Count** -egenskap.

```powershell
$Error.count
```

Om du vill visa ett fel använder du `[0]` mat ris notationen för att se det senaste felet.

```powershell
$Error[0]
```

Om du vill visa det äldsta kvarhållna felet skriver du:

```powershell
$Error[($Error.Count -1]
```

Parametern **Force** åsidosätter den särskilda formateringen för **ErrorRecord** -objekt och återgår till det konventionella formatet. Om du vill visa egenskaperna för **ErrorRecord** -objektet skriver du följande kommando:

```powershell
$Error[0] | Format-List -Property * -Force
```

I det här exemplet `$Error.Count` visas antalet fel. Om du vill ta bort alla fel från fel historiken använder du `Clear` metoden i fel mat ris.

```powershell
$Error.Count
```

```Output
17
```

```powershell
$Error.Clear()
$Error.Count
```

```Output
0
```

Om du vill hitta alla egenskaper och metoder för en felmatris använder du `Get-Member` cmdleten med dess **InputObject** -parameter. När du använder **InputObject** -parametern `Get-Member` visas egenskaper och metoder för samlingen.

```powershell
Get-Member -InputObject $Error
```

När du rör en samling objekt till `Get-Member` , `Get-Member` visar egenskaper och metoder för objekten i samlingen.

```powershell
$Error | Get-Member
```

### <a name="maximumfunctioncount"></a>\$MaximumFunctionCount

Anger hur många funktioner som tillåts i en specifik session.

**Giltiga värden** : 1024-32768 ( `Int32` )

**Standard** : 4096

Om du vill se funktionerna i din session använder du PowerShell- `Function:` enheten som exponeras av PowerShell- `Function` providern. Om du vill ha mer information om `Function` providern [about_Function_Provider](about_Function_Provider.md).

Om du vill visa en lista över funktionerna i den aktuella sessionen skriver du:

```powershell
Get-ChildItem Function:
```

Om du vill räkna funktionerna i den aktuella sessionen skriver du:

```powershell
(Get-ChildItem Function:).Count
```

### <a name="maximumhistorycount"></a>\$MaximumHistoryCount

Anger hur många kommandon som sparas i kommando historiken för den aktuella sessionen.

**Giltiga värden** : 1-32768 ( `Int32` )

**Standard** : 4096

Om du vill ta reda på hur många kommandon som har sparats i kommando historiken skriver du:

```powershell
(Get-History).Count
```

Använd cmdleten om du vill se de kommandon som sparats i din tidigare session `Get-History` . Mer information finns i [about_History](about_History.md).

### <a name="maximumvariablecount"></a>\$MaximumVariableCount

Anger hur många variabler som tillåts i en specifik session, inklusive automatiska variabler, Preference-variabler och variabler som du skapar i kommandon och skript.

**Giltiga värden** : 1024-32768 ( `Int32` )

**Standard** : 4096

Om du vill se variablerna i sessionen använder du `Get-Variable` cmdleten och funktionerna i PowerShell- `Variable:` enheten och PowerShell- `Variable` providern. Mer information finns i [about_Variable_Provider](about_Variable_Provider.md).

Om du vill hitta det aktuella antalet variabler i systemet skriver du:

```powershell
(Get-Variable).Count
```

### <a name="ofs"></a>\$OFS

Utgående fält avgränsare (OFS) anger det tecken som avgränsar elementen i en matris som konverteras till en sträng.

**Giltiga värden** : vilken sträng som helst.

**Standard** : utrymme

`$OFS`Variabeln finns inte som standard och utdatafilen avgränsare är ett blank steg, men du kan lägga till den här variabeln och ange den som valfri sträng. Du kan ändra värdet för `$OFS` i sessionen genom att skriva `$OFS="<value>"` .

> [!NOTE]
> Om du förväntar dig att standardvärdet för ett blank steg ( `" "` ) i ditt skript, modul eller konfigurations utdata är förvarat bör du se till att `$OFS` standardvärdet inte har ändrats någon annan stans i koden.

#### <a name="examples"></a>Exempel

Det här exemplet visar att ett blank steg används för att avgränsa värdena när en matris konverteras till en sträng. I det här fallet lagras en matris med heltal i en variabel och variabeln omvandlas sedan som en sträng.

```powershell
$array = 1,2,3,4
[string]$array
```

```Output
1 2 3 4
```

Om du vill ändra avgränsaren lägger du till `$OFS` variabeln genom att tilldela det ett värde.
Variabeln måste ha namnet `$OFS` .

```powershell
$OFS = "+"
[string]$array
```

```Output
1+2+3+4
```

För att återställa standard beteendet kan du tilldela ett blank steg ( `" "` ) till värdet för `$OFS` eller ta bort variabeln. Följande kommandon tar bort variabeln och kontrollerar att avgränsaren är ett blank steg.

```powershell
Remove-Variable OFS
[string]$array
```

```Output
1 2 3 4
```

### <a name="outputencoding"></a>\$OutputEncoding

Anger tecken kodnings metoden som PowerShell använder när den skickar text till andra program.

Om ett program till exempel returnerar Unicode-strängar till PowerShell kan du behöva ändra värdet till **UnicodeEncoding** för att skicka tecknen korrekt.

Giltiga värden är följande: objekt som härletts från en kodnings klass, till exempel **ASCIIEncoding** , **SBCSCodePageEncoding** , **UTF7Encoding** , **UTF8Encoding** , **UTF32Encoding** och **UnicodeEncoding**.

**Standard** : ASCIIEncoding-objekt (system. text. ASCIIEncoding)

#### <a name="examples"></a>Exempel

Det här exemplet visar hur du gör Windows **findstr.exe** kommandot fungerar i PowerShell på en dator som är lokaliserad för ett språk som använder Unicode-tecken, t. ex. kinesiska.

Det första kommandot hittar värdet för `$OutputEncoding` . Eftersom värdet är ett encoding-objekt visas endast dess **EncodingName** -egenskap.

```powershell
$OutputEncoding.EncodingName
```

I det här exemplet används ett **findstr.exe** -kommando för att söka efter två kinesiska tecken som finns i `Test.txt` filen. När den här **findstr.exe** kommandot körs i kommando tolken i Windows ( **cmd.exe** ), hittar **findstr.exe** tecknen i text filen. Men när du kör samma **findstr.exe** kommando i PowerShell, hittas inte tecknen eftersom PowerShell skickar dem till **findstr.exe** i ASCII-text, i stället för i Unicode-text.

```powershell
findstr <Unicode-characters>
```

Om du vill att kommandot ska fungera i PowerShell ställer du in värdet på `$OutputEncoding` värdet för **OutputEncoding** -egenskapen i-konsolen, som baseras på det språk som valts för Windows. Eftersom **OutputEncoding** är en statisk egenskap i-konsolen använder du dubbla kolon ( `::` ) i kommandot.

```powershell
$OutputEncoding = [console]::OutputEncoding
$OutputEncoding.EncodingName
```

```Output
OEM United States
```

När kodningen har ändrats hittar **findstr.exe** kommandot Unicode-tecknen.

```powershell
findstr <Unicode-characters>
```

```Output
test.txt:         <Unicode-characters>
```

### <a name="progresspreference"></a>\$ProgressPreference

Fastställer hur PowerShell svarar på förlopps uppdateringar som genereras av ett skript, en cmdlet eller en provider, till exempel de förlopps indikatorer som genereras av cmdleten [Write-Progress](xref:Microsoft.PowerShell.Utility.Write-Progress) .
`Write-Progress`Cmdleten skapar förlopps indikatorer som visar ett kommandos status.

Giltiga värden är följande:

- **Stop** : visar inte förlopps indikatorn. I stället visas ett fel meddelande och det slutar att köras.
- **Fråga** : visar inte förlopps indikatorn. Kräver behörighet att fortsätta. Om du svarar med `Y` eller `A` visas förlopps indikatorn.
- **Fortsätt** : (standard) visar förlopps indikatorn och fortsätter med körningen.
- **SilentlyContinue** : kör kommandot, men visar inte förlopps indikatorn.

### <a name="psemailserver"></a>\$PSEmailServer

Anger standard-e-postservern som används för att skicka e-postmeddelanden. Den här preferens variabeln används av cmdletar som skickar e-post, till exempel cmdleten [send-](xref:Microsoft.PowerShell.Utility.Send-MailMessage) mail.

### <a name="psdefaultparametervalues"></a>\$PSDefaultParameterValues

Anger standardvärden för parametrarna för cmdlets och Advanced functions.
Värdet för `$PSDefaultParameterValues` är en hash-tabell där nyckeln består av cmdlet-namnet och parameter namnet avgränsat med kolon ( `:` ). Värdet är ett anpassat standardvärde som du anger.

`$PSDefaultParameterValues` introducerades i PowerShell 3,0.

Mer information om den här preferens variabeln finns [about_Parameters_Default_Values](about_Parameters_Default_Values.md).

### <a name="psmoduleautoloadingpreference"></a>\$PSModuleAutoloadingPreference

Aktiverar och inaktiverar automatisk import av moduler i sessionen. **All** är standard. Oavsett variabelns värde kan du importera en modul med [import-modulen](xref:Microsoft.PowerShell.Core.Import-Module) .

Giltiga värden är:

- **Alla** : moduler importeras automatiskt vid första användning. Om du vill importera en modul kan du hämta eller använda valfritt kommando i modulen. Använd till exempel `Get-Command`.
- **ModuleQualified** : moduler importeras automatiskt när en användare använder det module-kvalificerade namnet för ett kommando i modulen. Till exempel, om användaren skriver `MyModule\MyCommand` , importerar PowerShell modulen modulen **modul** .
- **Ingen** : automatisk import av moduler är inaktive rad i sessionen. Använd cmdleten om du vill importera en modul `Import-Module` .

Mer information om automatisk import av moduler finns i [about_Modules](about_Modules.md).

### <a name="pssessionapplicationname"></a>\$PSSessionApplicationName

Anger standard program namnet för ett fjärrkommando som använder hanterings teknik för webb tjänster (WS-Management). Mer information finns i [om Windows Remote Management](/windows/win32/winrm/about-windows-remote-management).

Systemets standard program namn är `WSMAN` , men du kan använda den här preferens variabeln för att ändra standardvärdet.

Program namnet är den sista noden i en anslutnings-URI. Till exempel är program namnet i följande exempel-URI `WSMAN` .

`http://Server01:8080/WSMAN`

Standard program namnet används när fjärrkommandot inte anger en anslutnings-URI eller ett program namn.

**WinRM** -tjänsten använder program namnet för att välja en lyssnare som ska betjäna anslutningsbegäran. Parameterns värde ska matcha värdet på egenskapen **URLPrefix** för en lyssnare på fjärrdatorn.

Om du vill åsidosätta system standard och värdet för den här variabeln och välja ett annat program namn för en viss session använder du parametrarna **ConnectionURI** eller **ApplicationName** för cmdletarna [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [RETUR-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)eller [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) .

`$PSSessionApplicationName`Variabeln Preference anges på den lokala datorn, men anger en lyssnare på fjärrdatorn. Om det program namn som du anger inte finns på fjärrdatorn Miss lyckas kommandot för att upprätta sessionen.

### <a name="pssessionconfigurationname"></a>\$PSSessionConfigurationName

Anger standard konfigurationen för sessionen som används för **PSSessions** som skapats i den aktuella sessionen.

Den här preferens variabeln ställs in på den lokala datorn, men anger en sessionsinformation som finns på fjärrdatorn.

Värdet för `$PSSessionConfigurationName` variabeln är en fullständigt kvalificerad resurs-URI.

Standardvärdet `http://schemas.microsoft.com/PowerShell/microsoft.PowerShell` anger konfigurationen av **Microsoft. PowerShell** -sessionen på fjärrdatorn.

Om du bara anger ett konfigurations namn är följande schema-URI anpassningsprefix:

`http://schemas.microsoft.com/PowerShell/`

Du kan åsidosätta standardvärdet och välja en annan sessionsinformation för en viss session med hjälp av parametern **ConfigurationName** i `New-PSSession` `Enter-PSSession` cmdletarna,, eller `Invoke-Command` .

Du kan när som helst ändra värdet för den här variabeln. När du gör det måste du komma ihåg att den konfiguration av sessionen som du väljer måste finnas på fjärrdatorn. Om den inte gör det Miss lyckas kommandot för att skapa en session som använder konfigurationen av sessionen.

Den här preferens variabeln avgör inte vilka konfigurationer för lokal session som används när fjärranslutna användare skapar en session som ansluter till den här datorn.
Du kan dock använda behörigheterna för de lokala session-konfigurationerna för att avgöra vilka användare som kan använda dem.

### <a name="pssessionoption"></a>\$PSSessionOption

Fastställer standardvärden för avancerade användar alternativ i en fjärrsession.
Dessa alternativ inställningar åsidosätter systemets standardvärden för session-alternativ.

`$PSSessionOption`Variabeln innehåller ett **PSSessionOption** -objekt. Mer information finns i [system. Management. Automation. Remoting. PSSessionOption](/dotnet/api/system.management.automation.remoting.pssessionoption).
Varje egenskap för objektet representerar ett session-alternativ. Egenskapen **nocompression** aktiverar till exempel data komprimering under sessionen.

Som standard `$PSSessionOption` innehåller variabeln ett **PSSessionOption** -objekt med standardvärdena för alla alternativ, som du ser nedan.

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
IncludePortInSPN                  : False
OutputBufferingMode               : None
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : -00:00:00.0010000
```

Beskrivningar av dessa alternativ och mer information finns i [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption). Mer information om fjärrkommandon och sessioner finns i [about_Remote](about_Remote.md) och [about_PSSessions](about_PSSessions.md).

Om du vill ändra värdet på `$PSSessionOption` variabeln Preference använder du `New-PSSessionOption` cmdleten för att skapa ett **PSSessionOption** -objekt med de alternativ värden som du föredrar. Spara utdata i en variabel som kallas `$PSSessionOption` .

```powershell
$PSSessionOption = New-PSSessionOption -NoCompression
```

Om du vill använda `$PSSessionOption` variabeln Preference i varje PowerShell-session lägger du till ett `New-PSSessionOption` kommando som skapar `$PSSessionOption` variabeln i din PowerShell-profil. Mer information finns i [about_Profiles](about_Profiles.md).

Du kan ange anpassade alternativ för en viss fjärrsession. De alternativ som du anger prioriteras framför systemets standardinställningar och värdet för Preference- `$PSSessionOption` variabeln.

Om du vill ange alternativ för anpassade sessioner använder du `New-PSSessionOption` cmdleten för att skapa ett **PSSessionOption** -objekt. Använd sedan **PSSessionOption** -objektet som värdet för parametern **SessionOption** i cmdletar som skapar en session, till exempel, `New-PSSession` `Enter-PSSession` och `Invoke-Command` .

### <a name="transcript"></a>$Transcript

Används av `Start-Transcript` för att ange namn och plats för avskrifts filen. Om du inte anger något värde för parametern **Path** `Start-Transcript` använder sökvägen i värdet för den `$Transcript` globala variabeln. Om du inte har skapat den här variabeln `Start-Transcript` lagras avskrifterna i `$Home\My Documents` katalogen som `\PowerShell_transcript.<time-stamp>.txt` filer.

### <a name="verbosepreference"></a>\$VerbosePreference

Fastställer hur PowerShell svarar på utförliga meddelanden som genereras av ett skript, en cmdlet eller en provider, till exempel de meddelanden som genereras av [Write-Verbose-](xref:Microsoft.PowerShell.Utility.Write-Verbose) cmdleten.
Utförliga meddelanden beskriver de åtgärder som utförs för att köra ett kommando.

Som standard visas inte utförliga meddelanden, men du kan ändra det här beteendet genom att ändra värdet för `$VerbosePreference` .

Du kan använda den **utförliga** gemensamma parametern för en cmdlet för att visa eller dölja utförliga meddelanden för ett speciellt kommando. Mer information finns i [about_CommonParameters](about_CommonParameters.md).

Giltiga värden är följande:

- **Stop** : visar utförligt meddelande och ett fel meddelande och sedan slutar att köra.
- **Fråga** : visar utförligt meddelande och visar en uppmaning som frågar om du vill fortsätta.
- **Fortsätt** : visar utförligt meddelande och fortsätter sedan med körningen.
- **SilentlyContinue** : (standard) visar inte utförligt meddelande. Fortsätter att köra.

#### <a name="examples"></a>Exempel

I de här exemplen visas effekterna av de olika värdena i `$VerbosePreference` och **verbose** -parametern för att åsidosätta Preference-värdet.

Det här exemplet visar resultatet av **SilentlyContinue** -värdet, som är standardvärdet. Kommandot använder **meddelande** parametern, men skriver inte ett meddelande till PowerShell-konsolen.

```powershell
Write-Verbose -Message "Verbose message test."
```

När den **utförliga** parametern används, skrivs meddelandet.

```powershell
Write-Verbose -Message "Verbose message test." -Verbose
```

```Output
VERBOSE: Verbose message test.
```

Det här exemplet visar resultatet av värdet **Continue** . `$VerbosePreference`Variabeln är inställd på att **fortsätta** och meddelandet visas.

```powershell
$VerbosePreference = "Continue"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
```

I det här exemplet används **verbose** -parametern med värdet `$false` som åsidosätter **Continue** -värdet. Meddelandet visas inte.

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

Det här exemplet visar resultatet av **stopp** värdet. `$VerbosePreference`Variabeln har angetts till **stoppa** och meddelandet visas. Kommandot har stoppats.

```powershell
$VerbosePreference = "Stop"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
Write-Verbose : The running command stopped because the preference variable
  "VerbosePreference" or common parameter is set to Stop: Verbose message test.
At line:1 char:1
+ Write-Verbose -Message "Verbose message test."
```

I det här exemplet används **verbose** -parametern med värdet `$false` som åsidosätter **stopp** värdet. Meddelandet visas inte.

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

I det här exemplet visas resultatet av **förfrågning** svärdet. `$VerbosePreference`Variabeln är inställd på **fråga**. Meddelandet visas och användaren uppmanas att bekräfta.

```powershell
$VerbosePreference = "Inquire"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend
[?] Help (default is "Y"):
```

I det här exemplet används **verbose** -parametern med värdet `$false` som åsidosätter värdet för **förfrågan** . Användaren tillfrågas inte och meddelandet visas inte.

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

### <a name="warningpreference"></a>\$WarningPreference

Fastställer hur PowerShell svarar på varnings meddelanden som genereras av ett skript, en cmdlet eller en provider, till exempel de meddelanden som genereras av cmdleten [Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning) .

Som standard visas varnings meddelanden och körningen fortsätter, men du kan ändra det här beteendet genom att ändra värdet för `$WarningPreference` .

Du kan använda parametern **WarningAction** common för en cmdlet för att avgöra hur PowerShell svarar på varningar från ett visst kommando. Mer information finns i [about_CommonParameters](about_CommonParameters.md).

Giltiga värden är följande:

- **Stop** : visar varnings meddelandet och ett fel meddelande och slutar sedan att köra.
- **Fråga** : visar varnings meddelandet och frågar sedan om behörighet att fortsätta.
- **Fortsätt** : (standard) visar varnings meddelandet och fortsätter sedan att köra.
- **SilentlyContinue** : visar inte varnings meddelandet. Fortsätter att köra.

#### <a name="examples"></a>Exempel

I de här exemplen visas effekterna av de olika värdena i `$WarningPreference` .
Parametern **WarningAction** åsidosätter Preference-värdet.

I det här exemplet visas resultatet av standardvärdet, **Fortsätt**.

```powershell
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
```

I det här exemplet används parametern **WarningAction** med värdet **SilentlyContinue** för att förhindra varningen. Meddelandet visas inte.

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

I det här exemplet ändras `$WarningPreference` variabeln till **SilentlyContinue** -värdet. Meddelandet visas inte.

```powershell
$WarningPreference = "SilentlyContinue"
$m = "This action can delete data."
Write-Warning -Message $m
```

I det här exemplet används parametern **WarningAction** för att stoppa när en varning genereras.

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Stop
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m -WarningAction Stop
```

Det här exemplet ändrar `$WarningPreference` variabeln till **fråge** värdet. Användaren uppmanas att bekräfta.

```powershell
$WarningPreference = "Inquire"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend
[?] Help (default is "Y"):
```

I det här exemplet används parametern **WarningAction** med värdet **SilentlyContinue**. Kommandot fortsätter att köras och inget meddelande visas.

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

Det här exemplet ändrar `$WarningPreference` värdet för att **stoppa**.

```powershell
$WarningPreference = "Stop"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m
```

I det här exemplet används **WarningAction** med **frågans** värde. Användaren tillfrågas när en varning inträffar.

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Inquire
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend
[?] Help (default is "Y"):
```

### <a name="whatifpreference"></a>\$WhatIfPreference

Bestämmer om **whatIf** automatiskt aktive ras för varje kommando som stöder det. När **whatIf** är aktiverat rapporterar cmdleten den förväntade resultatet av kommandot, men kör inte kommandot.

Giltiga värden är följande:

- **Falskt** ( **0** , ej aktiverat): (standard) **whatIf** aktive ras inte automatiskt. Använd cmdletens **whatIf** -parameter om du vill aktivera det manuellt.
- **Sant** ( **1** , aktive rad): **whatIf** aktive ras automatiskt för alla kommandon som stöder det. Användare kan använda parametern **whatIf** med värdet **false** för att inaktivera den manuellt, till exempel `-WhatIf:$false` .

#### <a name="examples"></a>Exempel

I de här exemplen visas effekterna av de olika värdena i `$WhatIfPreference` .
De visar hur du använder parametern **whatIf** för att åsidosätta Preference-värdet för ett speciellt kommando.

Det här exemplet visar resultatet av `$WhatIfPreference` variabeln som angetts till standardvärdet, **false**. Används `Get-ChildItem` för att kontrol lera att filen finns.
`Remove-Item` tar bort filen. När filen har tagits bort kan du kontrol lera borttagningen med `Get-ChildItem` .

```powershell
Get-ChildItem -Path .\test.txt
Remove-Item -Path ./test.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           9/13/2019    10:53             10 test.txt
```

```powershell
Get-ChildItem -Path .\test.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -File test.txt
```

Det här exemplet visar effekterna av att använda parametern **whatIf** när värdet för `$WhatIfPreference` är **false**.

Kontrol lera att filen finns.

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

Använd parametern **whatIf** för att avgöra resultatet av försöket att ta bort filen.

```powershell
Remove-Item -Path .\test2.txt -WhatIf
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
``````

Kontrol lera att filen inte har tagits bort.

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

I det här exemplet visas resultatet av `$WhatIfPreference` variabeln som anges till värdet, **Sant**. När du använder `Remove-Item` för att ta bort en fil visas filens sökväg, men filen tas inte bort.

Försök att ta bort en fil. Ett meddelande visas om vad som skulle hända om `Remove-Item` kördes, men filen inte tas bort.

```powershell
$WhatIfPreference = "True"
Remove-Item -Path .\test2.txt
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
```

Används `Get-ChildItem` för att kontrol lera att filen inte har tagits bort.

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

I det här exemplet visas hur du tar bort en fil när värdet `$WhatIfPreference` är **True**. Den använder parametern **whatIf** med värdet `$false` . Används `Get-ChildItem` för att kontrol lera att filen har tagits bort.

```powershell
Remove-Item -Path .\test2.txt -WhatIf:$false
Get-ChildItem -Path .\test2.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test2.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path .\test2.txt
```

Följande är exempel på den `Get-Process` cmdlet som inte stöder **whatIf** och `Stop-Process` som stöder **whatIf**. `$WhatIfPreference`Variabelns värde är **Sant**.

`Get-Process` stöder inte **whatIf**. När kommandot körs visas **Winword** -processen.

```powershell
Get-Process -Name Winword
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    130   119.84     173.38       8.39   15024   4 WINWORD
```

`Stop-Process` stöder **whatIf**. **Winword** -processen har inte stoppats.

```powershell
Stop-Process -Name Winword
```

```Output
What if: Performing the operation "Stop-Process" on target "WINWORD (15024)".
```

Du kan åsidosätta `Stop-Process` **whatIf** -beteendet med hjälp av parametern **whatIf** med värdet `$false` . **Winword** -processen har stoppats.

```powershell
Stop-Process -Name Winword -WhatIf:$false
```

Använd om du vill kontrol lera att **Winword** -processen har stoppats `Get-Process` .

```powershell
Get-Process -Name Winword
```

```Output
Get-Process : Cannot find a process with the name "Winword".
  Verify the process name and call the cmdlet again.
At line:1 char:1
+ Get-Process -Name Winword
```

## <a name="see-also"></a>Se även

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_CommonParameters](about_CommonParameters.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Profiles](about_Profiles.md)

[about_Remote](about_Remote.md)

[about_Scopes](about_Scopes.md)

[about_Variables](about_Variables.md)
