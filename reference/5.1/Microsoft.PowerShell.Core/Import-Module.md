---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/import-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Module
ms.openlocfilehash: 78806f9fcfcdd0effa1599c46bfeecddb507722a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263594"
---
# Import-Module

## SAMMANFATTNING
Lägger till moduler i den aktuella sessionen.

## SYNTAX

### Namn (standard)

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-PassThru]
 [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] [<CommonParameters>]
```

### PSSession

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-PassThru]
 [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -PSSession <PSSession> [<CommonParameters>]
```

### CimSession

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-PassThru]
 [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

### FullyQualifiedName

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] [<CommonParameters>]
```

### FullyQualifiedNameAndPSSession

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -PSSession <PSSession> [<CommonParameters>]
```

### Sammansättning

```
Import-Module [-Global] [-Prefix <String>] [-Assembly] <Assembly[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-PassThru]
 [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber] [-Scope <String>]
 [<CommonParameters>]
```

### ModuleInfo

```
Import-Module [-Global] [-Prefix <String>] [-Function <String[]>] [-Cmdlet <String[]>]
 [-Variable <String[]>] [-Alias <String[]>] [-Force] [-PassThru] [-AsCustomObject]
 [-ModuleInfo] <PSModuleInfo[]> [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] [<CommonParameters>]
```

## BESKRIVNING

`Import-Module`Cmdleten lägger till en eller flera moduler i den aktuella sessionen. Från och med PowerShell 3,0 importeras installerade moduler automatiskt till sessionen när du använder kommandon eller providrar i modulen. Du kan dock fortfarande använda `Import-Module` kommandot för att importera en modul.
Du kan inaktivera automatisk modul import med hjälp av `$PSModuleAutoloadingPreference` Preference-variabeln. Mer information om `$PSModuleAutoloadingPreference` variabeln finns i [about_Preference_Variables](About/about_Preference_Variables.md).

En modul är ett paket som innehåller medlemmar som kan användas i PowerShell. Medlemmar inkluderar cmdlets, providrar, skript, funktioner, variabler och andra verktyg och filer. När en modul har importer ATS kan du använda-modulens medlemmar i sessionen. Mer information om moduler finns i [about_Modules](About/about_Modules.md).

Som standard `Import-Module` importerar alla medlemmar som modulen exporterar, men du kan använda **alias** , **funktion** , **cmdlet** och **variabel** parametrar för att begränsa vilka medlemmar som importeras. Parametern **NoClobber** förhindrar `Import-Module` import av medlemmar som har samma namn som medlemmar i den aktuella sessionen.

`Import-Module` importerar en modul endast till den aktuella sessionen. Om du vill importera modulen till varje ny session lägger du till ett `Import-Module` kommando i din PowerShell-profil. Mer information om profiler finns [about_Profiles](About/about_Profiles.md).

Du kan hantera fjärranslutna Windows-datorer som har PowerShell-fjärrkommunikation aktive rad genom att skapa en **PSSession** på fjärrdatorn. Använd sedan **PSSession** -parametern för `Import-Module` för att importera de moduler som är installerade på fjärrdatorn. Nu kan du använda de importerade kommandona i den aktuella sessionen. Kommandona körs implicit på fjärrdatorn.

Från och med Windows PowerShell 3,0 kan du använda `Import-Module` för att importera common information Model (CIM)-moduler, där cmdletarna definieras i cmdlet definition XML-filer (cdxlm). Med den här funktionen kan du använda cmdletar som implementeras i icke-hanterade kod sammansättningar, t. ex. sådana som skrivits i C++.

För fjärrdatorer som inte har PowerShell-fjärrkommunikation aktive rad, inklusive datorer som inte kör Windows operativ system, kan du använda **CIMSession** -parametern för `Import-Module` för att importera CIM-moduler från fjärrdatorn. De importerade kommandona körs implicit på fjärrdatorn. En **CIMSession** är en anslutning till Windows Management INSTRUMENTATION (WMI) på fjärrdatorn.

## EXEMPEL

### Exempel 1: importera medlemmarna i en modul till den aktuella sessionen

I det här exemplet importeras medlemmarna i **PSDiagnostics** -modulen till den aktuella sessionen.

```powershell
Import-Module -Name PSDiagnostics
```

### Exempel 2: importera alla moduler som anges av sökvägen till modulen

I det här exemplet importeras alla tillgängliga moduler i sökvägen som anges av `$env:PSModulePath` miljö variabeln till den aktuella sessionen.

```powershell
Get-Module -ListAvailable | Import-Module
```

### Exempel 3: Importera medlemmar i flera moduler till den aktuella sessionen

I det här exemplet importeras medlemmar av **PSDiagnostics** -och **DISM** -modulerna till den aktuella sessionen.

```powershell
$m = Get-Module -ListAvailable PSDiagnostics, Dism
Import-Module -ModuleInfo $m
```

`Get-Module`Cmdlet: en hämtar modulen **PSDiagnostics** och **DISM** och sparar objekten i `$m` variabeln. **ListAvailable** -parametern krävs när du hämtar moduler som ännu inte har importer ATS till sessionen.

Parametern **ModuleInfo** i `Import-Module` används för att importera modulerna till den aktuella sessionen.

### Exempel 4: importera alla moduler som anges av en sökväg

I det här exemplet används en explicit sökväg för att identifiera den modul som ska importeras.

```powershell
Import-Module -Name c:\ps-test\modules\test -Verbose
```

```Output
VERBOSE: Loading module from path 'C:\ps-test\modules\Test\Test.psm1'.
VERBOSE: Exporting function 'my-parm'.
VERBOSE: Exporting function 'Get-Parameter'.
VERBOSE: Exporting function 'Get-Specification'.
VERBOSE: Exporting function 'Get-SpecDetails'.
```

Med hjälp av parametern **verbose** `Import-Module` kan du rapportera förloppet när modulen läses in.
Utan **verbose** -, **Passthru** -eller **AsCustomObject** -parametern `Import-Module` genererar inga utdata när en modul importeras.

### Exempel 5: begränsa modul medlemmar som importeras till en session

I det här exemplet visas hur du begränsar vilka modulblad som importeras till sessionen och kommandots effekter i sessionen. **Funktions** parametern begränsar de medlemmar som importeras från modulen. Du kan också använda parametrarna **alias** , **variabel** och **cmdlet** för att begränsa andra medlemmar som en modul importerar.

`Get-Module`Cmdlet: en hämtar det objekt som representerar **PSDiagnostics** -modulen. Egenskapen **ExportedCmdlets** visar alla cmdletar som modulen exporterar, även om de inte har importer ATS.

```powershell
Import-Module PSDiagnostics -Function Disable-PSTrace, Enable-PSTrace
(Get-Module PSDiagnostics).ExportedCommands
```

```Output
Key                          Value
---                          -----
Disable-PSTrace              Disable-PSTrace
Disable-PSWSManCombinedTrace Disable-PSWSManCombinedTrace
Disable-WSManTrace           Disable-WSManTrace
Enable-PSTrace               Enable-PSTrace
Enable-PSWSManCombinedTrace  Enable-PSWSManCombinedTrace
Enable-WSManTrace            Enable-WSManTrace
Get-LogProperties            Get-LogProperties
Set-LogProperties            Set-LogProperties
Start-Trace                  Start-Trace
Stop-Trace                   Stop-Trace
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                 Version    Source
-----------     ----                 -------    ------
Function        Disable-PSTrace      6.1.0.0    PSDiagnostics
Function        Enable-PSTrace       6.1.0.0    PSDiagnostics
```

Om du använder parametern **module** för `Get-Command` cmdleten visas de kommandon som har importer ATS från **PSDiagnostics** -modulen. Resultatet bekräftar att endast `Disable-PSTrace` `Enable-PSTrace` cmdletarna och har importer ATS.

### Exempel 6: importera medlemmarna i en modul och Lägg till ett prefix

Det här exemplet importerar **PSDiagnostics** -modulen till den aktuella sessionen, lägger till ett prefix till medlems namnen och visar sedan de förfasta medlems namnen. Parametern **prefix** för `Import-Module` lägger till **x** -prefixet till alla medlemmar som importeras från modulen. Prefixet gäller endast medlemmarna i den aktuella sessionen. Modulen ändras inte. Parametern **Passthru** returnerar ett modul-objekt som representerar den importerade modulen.

```powershell
Import-Module PSDiagnostics -Prefix x -PassThru
```

```Output
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     6.1.0.0    PSDiagnostics      {Disable-xPSTrace, Disable-xPSWSManCombinedTrace, Disable-xW...
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                                   Version    Source
-----------     ----                                   -------    ------
Function        Disable-xPSTrace                       6.1.0.0    PSDiagnostics
Function        Disable-xPSWSManCombinedTrace          6.1.0.0    PSDiagnostics
Function        Disable-xWSManTrace                    6.1.0.0    PSDiagnostics
Function        Enable-xPSTrace                        6.1.0.0    PSDiagnostics
Function        Enable-xPSWSManCombinedTrace           6.1.0.0    PSDiagnostics
Function        Enable-xWSManTrace                     6.1.0.0    PSDiagnostics
Function        Get-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Set-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Start-xTrace                           6.1.0.0    PSDiagnostics
Function        Stop-xTrace                            6.1.0.0    PSDiagnostics
```

`Get-Command` hämtar de medlemmar som har importer ATS från modulen. Utdata visar att modulens medlemmar är korrekt fasta.

### Exempel 7: Hämta och använda ett anpassat objekt

Det här exemplet visar hur du hämtar och använder det anpassade objektet som returnerades av **import-module**.

Anpassade objekt innehåller syntetiska medlemmar som representerar var och en av de importerade modulerna medlemmar. Till exempel konverteras cmdletarna och funktionerna i en modul till skript metoder för det anpassade objektet.

Anpassade objekt är användbara i skript. De är också användbara när flera importerade objekt har samma namn. Användning av skript metoden för ett objekt motsvarar att ange det fullständigt kvalificerade namnet på en importerad medlem, inklusive dess modulnamn.

Parametern **AsCustomObject** kan bara användas när du importerar en-skript-modul. Används `Get-Module` för att avgöra vilka av de tillgängliga modulerna som är en skriptbaserad modul.

```powershell
Get-Module -List | Format-Table -Property Name, ModuleType -AutoSize
```

```Output
Name          ModuleType
----          ----------
Show-Calendar     Script
BitsTransfer    Manifest
PSDiagnostics   Manifest
TestCmdlets       Script
...
```

```powershell
$a = Import-Module -Name Show-Calendar -AsCustomObject -Passthru
$a | Get-Member
```

```Output
    TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
Show-Calendar ScriptMethod System.Object Show-Calendar();
```

```powershell
$a."Show-Calendar"()
```

Skript modulen **show-Calendar** importeras med parametern **AsCustomObject** för att begära ett anpassat objekt och parametern **Passthru** för att returnera objektet. Det resulterande anpassade objektet sparas i `$a` variabeln.

`$a`Variabeln är skickas till `Get-Member` cmdleten för att visa egenskaper och metoder för det sparade objektet. Utdata visar skript metoden **show-Calendar** .

Om du vill anropa skript metoden **show-Calendar** måste metod namnet omges av citat tecken, eftersom namnet innehåller ett bindestreck.

### Exempel 8: importera en modul igen till samma session

Det här exemplet visar hur du använder **Force** -parametern i `Import-Module` när du importerar om en modul till samma session. Parametern **Force** tar bort den inlästa modulen och importerar den sedan igen.

```powershell
Import-Module PSDiagnostics
Import-Module PSDiagnostics -Force -Prefix PS
```

Det första kommandot importerar **PSDiagnostics** -modulen. Det andra kommandot importerar modulen igen, den här gången med hjälp av parametern **prefix** .

Utan **Force** -parametern innehåller sessionen två kopior av varje **PSDiagnostics** -cmdlet, en med standard namnet och en med det förfasta namnet.

### Exempel 9: kör kommandon som har dolts av importerade kommandon

Det här exemplet visar hur du kör kommandon som har dolts av importerade kommandon. Modulen **TestModule** innehåller en funktion med namnet `Get-Date` som returnerar året och dagen på året.

```powershell
Get-Date
```

```Output
Thursday, August 15, 2019 2:26:12 PM
```

```powershell
Import-Module TestModule
Get-Date
```

```Output
19227
```

```powershell
Get-Command Get-Date -All | Format-Table -Property CommandType, Name, ModuleName -AutoSize
```

```Output
CommandType     Name         ModuleName
-----------     ----         ----------
Function        Get-Date     TestModule
Cmdlet          Get-Date     Microsoft.PowerShell.Utility
```

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

```Output
Thursday, August 15, 2019 2:28:31 PM
```

Den första `Get-Date` cmdleten returnerar ett **datetime** -objekt med det aktuella datumet. När du har importerat modulen **TestModule** `Get-Date` returnerar året och dagen.

Använda **alla** -parametrar för `Get-Command` Visa alla `Get-Date` kommandon i sessionen. Resultaten visar att det finns två `Get-Date` kommandon i sessionen, en funktion från modulen **TestModule** och en cmdlet från **Microsoft. PowerShell. Utility** -modulen.

Eftersom funktioner prioriteras över cmdletar `Get-Date` körs funktionen från **TestModule** -modulen i stället för `Get-Date` cmdleten. Om du vill köra den ursprungliga versionen av `Get-Date` måste du kvalificera kommandots namn med modulnamnet.

Mer information om kommando prioritet i PowerShell finns [about_Command_Precedence](about/about_Command_Precedence.md).

### Exempel 10: importera en lägsta version av en modul

I det här exemplet importeras modulen **PowerShellGet** . Den använder **MinimumVersion** -parametern för `Import-Module` för att importera version 2.0.0 eller större av modulen.

```powershell
Import-Module -Name PowerShellGet -MinimumVersion 2.0.0
```

Du kan också använda parametern **RequiredVersion** för att importera en viss version av en modul eller använda parametrarna **module** och **version** för `#Requires` nyckelordet för att kräva en viss version av en modul i ett skript.

### Exempel 11: importera med ett fullständigt kvalificerat namn

I det här exemplet importeras en angiven version av en modul med hjälp av FullyQualifiedName.

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Name, Version

Name          Version
----          -------
PowerShellGet 2.2.1
PowerShellGet 2.1.3
PowerShellGet 2.1.2
PowerShellGet 1.0.0.1

PS> Import-Module -FullyQualifiedName @{ModuleName = 'PowerShellGet'; ModuleVersion = '2.1.3' }
```

### Exempel 12: importera med en fullständigt kvalificerad sökväg

I det här exemplet importeras en särskild version av en modul med hjälp av den fullständigt kvalificerade sökvägen.

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Path

Path
----
C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1
C:\program files\powershell\6\Modules\PowerShellGet\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\2.1.2\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1

PS> Import-Module -Name 'C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1'
```

### Exempel 13: importera en modul från en fjärran sluten dator

Det här exemplet visar hur du använder `Import-Module` cmdleten för att importera en modul från en fjärrdator.
Det här kommandot använder funktionen implicit fjärr kommunikation i PowerShell.

När du importerar moduler från en annan session kan du använda cmdletarna i den aktuella sessionen.
Kommandon som använder cmdletarna körs dock i fjärrsessionen.

```powershell
$s = New-PSSession -ComputerName Server01
Get-Module -PSSession $s -ListAvailable -Name NetSecurity
```

```Output
ModuleType Name             ExportedCommands
---------- ----             ----------------
Manifest   NetSecurity      {New-NetIPsecAuthProposal, New-NetIPsecMainModeCryptoProposal, New-Ne...
```

```powershell
Import-Module -PSSession $s -Name NetSecurity
Get-Command -Module NetSecurity -Name Get-*Firewall*
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Get-NetFirewallAddressFilter                       NetSecurity
Function        Get-NetFirewallApplicationFilter                   NetSecurity
Function        Get-NetFirewallInterfaceFilter                     NetSecurity
Function        Get-NetFirewallInterfaceTypeFilter                 NetSecurity
Function        Get-NetFirewallPortFilter                          NetSecurity
Function        Get-NetFirewallProfile                             NetSecurity
Function        Get-NetFirewallRule                                NetSecurity
Function        Get-NetFirewallSecurityFilter                      NetSecurity
Function        Get-NetFirewallServiceFilter                       NetSecurity
Function        Get-NetFirewallSetting                             NetSecurity
```

```powershell
Get-NetFirewallRule -DisplayName "Windows Remote Management*" |
  Format-Table -Property DisplayName, Name -AutoSize
```

```Output
DisplayName                                              Name
-----------                                              ----
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP-PUBLIC
Windows Remote Management - Compatibility Mode (HTTP-In) WINRM-HTTP-Compat-In-TCP
```

`New-PSSession` skapar en fjärrsession ( **PSSession** ) till Server01-datorn. **PSSession** sparas i `$s` variabeln.

`Get-Module`Om du kör med parametern **PSSession** ser du att **netsecurity** -modulen är installerad och tillgänglig på fjärrdatorn. Det här kommandot motsvarar att använda `Invoke-Command` cmdleten för att köra `Get-Module` kommandot i fjärrsessionen. Exempel: (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`

Om `Import-Module` du kör med **PSSession** -parametern importeras **netsecurity** -modulen från fjärrdatorn till den aktuella sessionen. `Get-Command`Cmdleten används för att hämta kommandon som börjar med **Get** -och include- **brandväggen** från modulen **netsecurity** . Utdata bekräftar att modulen och dess cmdlets har importer ATS till den aktuella sessionen.

Därefter `Get-NetFirewallRule` hämtar cmdlet Windows Remote Management brand Väggs regler på Server01-datorn. Detta motsvarar att använda `Invoke-Command` cmdleten för att köras `Get-NetFirewallRule` i fjärrsessionen.

### Exempel 14: Hantera lagring på en fjärrdator utan operativ systemet Windows

I det här exemplet har administratören för datorn installerat modulen för modul identifiering, som gör att du kan använda CIM-kommandon som är utformade för providern.

`New-CimSession`Cmdleten skapar en session på den fjärranslutna datorn med namnet RSDGF03. Sessionen ansluter till WMI-tjänsten på fjärrdatorn. CIM-sessionen sparas i `$cs` variabeln.
`Import-Module` använder **CimSession** i `$cs` för att importera modulen **Storage** CIM från RSDGF03-datorn.

`Get-Command`Cmdleten visar `Get-Disk` kommandot i modulen **Storage** . När du importerar en CIM-modul till den lokala sessionen konverterar PowerShell CDXLM-filerna för varje kommando till PowerShell-skript, som visas som funktioner i den lokala sessionen.

Trots `Get-Disk` att det har skrivits i den lokala sessionen körs cmdleten implicit på den fjärrdator som den importerades från. Kommandot returnerar objekt från fjärrdatorn till den lokala sessionen.

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Import-Module -CimSession $cs -Name Storage
# Importing a CIM module, converts the CDXML files for each command into PowerShell scripts.
# These appear as functions in the local session.
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
# Use implicit remoting to query disks on the remote computer from which the module was imported.
Get-Disk
```

```Output
Number Friendly Name           OperationalStatus  Total Size Partition Style
------ -------------           -----------------  ---------- ---------------
0      Virtual HD ATA Device   Online                  40 GB MBR
```

## PARAMETRAR

### -Alias

Anger alias som denna cmdlet importerar från modulen till den aktuella sessionen. Ange en kommaavgränsad lista över alias. Jokertecken är tillåtna.

Vissa moduler exporterar automatiskt markerade alias till sessionen när du importerar modulen.
Med den här parametern kan du välja bland de exporterade aliasen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### – Argument List

Anger en matris med argument, eller parameter värden, som skickas till en skript-modul under `Import-Module` kommandot. Den här parametern är endast giltig när du importerar en-skript-modul.

Du kan också referera till parametern **argument List** med dess alias, **argument**. Mer information om beteendet för **argument List** finns [about_Splatting](about/about_Splatting.md#splatting-with-arrays).

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsCustomObject

Anger att denna cmdlet returnerar ett anpassat objekt med medlemmar som representerar medlemmar i den importerade modulen. Den här parametern är endast giltig för skript moduler.

När du använder **AsCustomObject** -parametern `Import-Module` importerar modulen medlemmar till sessionen och returnerar sedan ett **PSCustomObject** -objekt i stället för ett **PSModuleInfo** -objekt. Du kan spara det anpassade objektet i en variabel och använda punkt notation för att anropa medlemmarna.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Sammansättning

Anger en matris med sammansättnings objekt. Denna cmdlet importerar de cmdlets och providers som implementeras i de angivna sammansättnings objekten. Ange en variabel som innehåller sammansättnings objekt eller ett kommando som skapar sammansättnings objekt. Du kan också skicka ett sammansättnings objekt till `Import-Module` .

När du använder den här parametern importeras bara de cmdlets och providers som implementeras av de angivna sammansättningarna. Om modulen innehåller andra filer importeras de inte, och du kanske saknar viktiga medlemmar i modulen. Använd den här parametern för att felsöka och testa modulen, eller när du uppmanas att använda den av modulens författare.

```yaml
Type: System.Reflection.Assembly[]
Parameter Sets: Assembly
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -CimNamespace

Anger namn området för en alternativ CIM-provider som exponerar CIM-moduler. Standardvärdet är namn området för WMI-providern för modul identifiering.

Använd den här parametern för att importera CIM-moduler från datorer och enheter som inte kör ett Windows-operativsystem.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimResourceUri

Anger en alternativ plats för CIM-moduler. Standardvärdet är resurs-URI för WMI-providern för module-identifiering på fjärrdatorn.

Använd den här parametern för att importera CIM-moduler från datorer och enheter som inte kör ett Windows-operativsystem.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Uri
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – CimSession

Anger en CIM-session på fjärrdatorn. Ange en variabel som innehåller CIM-sessionen eller ett kommando som hämtar CIM-sessionen, till exempel ett [Get-CimSession](../CimCmdlets/Get-CimSession.md) -kommando.

`Import-Module` använder CIM-sessionen för att importera moduler från fjärrdatorn till den aktuella sessionen. När du använder kommandona från den importerade modulen i den aktuella sessionen körs kommandona på fjärrdatorn.

Du kan använda den här parametern för att importera moduler från datorer och enheter som inte kör Windows-operativsystemet och Windows-datorer som har PowerShell, men som inte har PowerShell-fjärrkommunikation aktive rad.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: CimSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Cmdlet

Anger en matris med cmdletar som denna cmdlet importerar från modulen till den aktuella sessionen.
Jokertecken är tillåtna.

Vissa moduler exporterar automatiskt valda cmdlets till sessionen när du importerar modulen.
Med den här parametern kan du välja bland de exporterade cmdletarna.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -DisableNameChecking

Anger att denna cmdlet undertrycker meddelandet som varnar dig när du importerar en cmdlet eller funktion vars namn innehåller ett ej godkänt verb eller ett otillåtet Character.

Som standard visas följande varnings meddelande när en modul som du importerar exporterar cmdlets eller Functions som har icke-godkända verb i sina namn:

> Varning! vissa importerade kommando namn innehåller icke-godkända verb som kan göra dem mindre synliga. Använd verbose-parametern för mer information eller Skriv Get-Verb om du vill visa en lista över godkända verb.

Det här meddelandet är bara en varning. Den kompletta modulen importeras fortfarande, inklusive kommandon som inte överensstämmer. Även om meddelandet visas för modulen användare, bör namngivnings problemet åtgärdas av den som skapade modulen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Den här parametern gör att en modul läses in eller läses in ovanpå den aktuella.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedName

Anger modulens fullständigt kvalificerade namn som en hash-tabell. Värdet kan vara en kombination av strängar och hash-tabeller. Hash-tabellen har följande nycklar.

- `ModuleName` - **Krävs** Anger namnet på modulen.
- `GUID` - **Valfritt** Anger modulens GUID.
- Du **måste** också ange en av de tre nycklarna nedan. Nycklarna kan inte användas tillsammans.
  - `ModuleVersion` -Anger en minsta godtagbar version av modulen.
  - `RequiredVersion` -Anger en exakt, obligatorisk version av modulen.
  - `MaximumVersion` -Anger den högsta godkända versionen av modulen.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName, FullyQualifiedNameAndPSSession
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – Funktion

Anger en matris med funktioner som denna cmdlet importerar från modulen till den aktuella sessionen.
Jokertecken är tillåtna. Vissa moduler exporterar automatiskt markerade funktioner till sessionen när du importerar modulen. Med den här parametern kan du välja bland de exporterade funktionerna.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### – Global

Anger att denna cmdlet importerar moduler till det globala sessionstillståndet så att de är tillgängliga för alla kommandon i sessionen.

Som standard, när `Import-Module` cmdlet anropas från kommando tolken, skript filen eller script block, importeras alla kommandon till det globala sessionstillståndet.

Vid anrop från en annan modul `Import-Module` importerar cmdlet kommandon i en modul, inklusive kommandon från kapslade moduler, till den anropande modulens sessionstillstånd.

> [!TIP]
> Undvik att anropa inifrån `Import-Module` en modul. Deklarera i stället mål-modulen som en kapslad modul i den överordnade modulens manifest. Att deklarera kapslade moduler gör det enklare att identifiera beroenden.

Den **globala** parametern motsvarar **omfattnings** parametern med värdet **Global**.

Om du vill begränsa vilka kommandon som en modul exporterar, använder du ett `Export-ModuleMember` kommando i modulen script.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – MaximumVersion

Anger en högsta version. Den här cmdleten importerar bara en version av modulen som är mindre än eller lika med det angivna värdet. Om ingen version kvalificeras `Import-Module` returneras ett fel.

```yaml
Type: System.String
Parameter Sets: Name, PSSession, CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – MinimumVersion

Anger en lägsta version. Den här cmdleten importerar bara en version av modulen som är större än eller lika med det angivna värdet. Använd **MinimumVersion** parameter namn eller dess alias, **version**. Om ingen version kvalificeras `Import-Module` genererar ett fel.

Om du vill ange en exakt version använder du parametern **RequiredVersion** . Du kan också använda **modul** -och **versions** parametrar för **#Requires** nyckelordet för att kräva en speciell version av en modul i ett skript.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession
Aliases: Version

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModuleInfo

Anger en matris med modul-objekt som ska importeras. Ange en variabel som innehåller modulens objekt, eller ett kommando som hämtar modulens objekt, till exempel följande kommando: `Get-Module -ListAvailable` . Du kan också skicka modul objekt till `Import-Module` .

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Anger namnen på de moduler som ska importeras. Ange namnet på modulen eller namnet på en fil i modulen, till exempel en,, eller en `.psd1` `.psm1` `.dll` `.ps1` fil. Fil Sök vägar är valfria. Jokertecken är inte tillåtna. Du kan också skicka namn och fil namn för moduler till `Import-Module` .

Om du utelämnar en sökväg `Import-Module` söker du efter modulen i Sök vägarna som sparats i `$env:PSModulePath` miljö variabeln.

Ange bara modulnamnet när det är möjligt. När du anger ett fil namn importeras bara de medlemmar som implementeras i den filen. Om modulen innehåller andra filer importeras de inte, och du kanske saknar viktiga medlemmar i modulen.

```yaml
Type: System.String[]
Parameter Sets: Name, PSSession, CimSession
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### -NoClobber

Förhindrar att du importerar kommandon som har samma namn som befintliga kommandon i den aktuella sessionen. Som standard `Import-Module` importerar alla exporterade module-kommandon.

Kommandon som har samma namn kan dölja eller ersätta kommandon i sessionen. Använd **prefix** -eller **NoClobber** -parametrarna för att undvika kommando namns konflikter i en session. Mer information om namn konflikter och kommando prioritet finns i "moduler och namn konflikter" i [about_Modules](about/about_Modules.md) och [about_Command_Precedence](about/about_Command_Precedence.md).

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – PassThru

Returnerar ett objekt som representerar det objekt som du arbetar med. Som standard genererar denna cmdlet inga utdata.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Prefix

Anger ett prefix som denna cmdlet lägger till i Substantiv i namnen på importerade modul medlemmar.

Använd den här parametern för att undvika namn konflikter som kan uppstå när olika medlemmar i sessionen har samma namn. Den här parametern ändrar inte modulen och påverkar inte filer som modulen importerar för eget bruk. Dessa kallas kapslade moduler. Denna cmdlet påverkar bara namnen på medlemmar i den aktuella sessionen.

Om du till exempel anger prefixet UTC och sedan importerar en `Get-Date` cmdlet, är cmdleten känd i sessionen som `Get-UTCDate` och den förväxlas inte med den ursprungliga `Get-Date` cmdleten.

Värdet för den här parametern prioriteras över **DefaultCommandPrefix** -egenskapen för modulen, som anger standardprefixet.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – PSSession

Anger en PowerShell- **PSSession** (User-Managed session) från vilken denna cmdlet importerar moduler till den aktuella sessionen. Ange en variabel som innehåller ett **PSSession** eller ett kommando som hämtar en **PSSession** , till exempel ett `Get-PSSession` kommando.

När du importerar en modul från en annan session till den aktuella sessionen kan du använda cmdletar från modulen i den aktuella sessionen, precis som du skulle använda cmdlets från en lokal modul. Kommandon som använder fjärrcmdlets körs i fjärrsessionen, men fjärrinformationen hanteras i bakgrunden av PowerShell.

Den här parametern använder funktionen implicit fjärr kommunikation i PowerShell. Det motsvarar att använda `Import-PSSession` cmdleten för att importera specifika moduler från en session.

`Import-Module` Det går inte att importera PowerShell Core-moduler från en annan session. PowerShell Core-modulerna har namn som inleds med Microsoft. PowerShell.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PSSession, FullyQualifiedNameAndPSSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – RequiredVersion

Anger en version av modulen som denna cmdlet importerar. Om versionen inte är installerad `Import-Module` genererar ett fel.

Som standard `Import-Module` importerar modulen utan att kontrol lera versions numret.

Om du vill ange en lägsta version använder du parametern **MinimumVersion** . Du kan också använda **modul** -och **versions** parametrar för **#Requires** nyckelordet för att kräva en speciell version av en modul i ett skript.

Den här parametern introducerades i Windows PowerShell 3,0.

Skript som använder **RequiredVersion** för att importera moduler som ingår i befintliga versioner av Windows operativ system körs inte automatiskt i framtida versioner av Windows operativ system. Detta beror på att PowerShell-modulens versions nummer i framtida versioner av Windows operativ system är högre än versions nummer för modul i befintliga versioner av Windows operativ system.

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Omfattning

Anger ett omfång där denna cmdlet importerar modulen.

De acceptabla värdena för den här parametern är:

- **Global**. Tillgängligt för alla kommandon i sessionen. Motsvarar den **globala** parametern.
- **Lokal**. Endast tillgängligt i det aktuella omfånget.

Som standard, när `Import-Module` cmdlet anropas från kommando tolken, skript filen eller script block, importeras alla kommandon till det globala sessionstillståndet. Du kan använda parametern **-scope** med värdet **lokalt** för att importera modulens innehåll till skriptet eller script block-omfånget.

Vid anrop från en annan modul `Import-Module` importerar cmdlet kommandon i en modul, inklusive kommandon från kapslade moduler, till anroparens sessionstillstånd. Ange `-Scope Global` eller `-Global` anger att denna cmdlet importerar moduler till det globala sessionstillståndet så att de är tillgängliga för alla kommandon i sessionen.

Den **globala** parametern motsvarar **omfattnings** parametern med värdet global.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Local, Global

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Variabel

Anger en matris med variabler som denna cmdlet importerar från modulen till den aktuella sessionen.
Ange en lista med variabler. Jokertecken är tillåtna.

Vissa moduler exporterar automatiskt markerade variabler till sessionen när du importerar modulen.
Med den här parametern kan du välja bland de exporterade variablerna.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String, system. Management. Automation. PSModuleInfo, system. Reflection. Assembly

Du kan skicka vidare ett modulnamn, module-objekt eller Assembly-objekt till denna cmdlet.

## UTDATA

### Ingen, system. Management. Automation. PSModuleInfo eller system. Management. Automation. PSCustomObject

`Import-Module`Genererar inga utdata som standard. Om du anger parametern **Passthru** genererar cmdleten ett **system. Management. Automation. PSModuleInfo** -objekt som representerar modulen. Om du anger parametern **AsCustomObject** genereras ett **PSCustomObject** -objekt.

## ANTECKNINGAR

- Innan du kan importera en modul måste modulen vara installerad på den lokala datorn. Därför måste modul katalogen kopieras till en katalog som är tillgänglig för den lokala datorn. Mer information finns i [about_Modules](About/about_Modules.md).

  Du kan också använda parametrarna **PSSession** och **CIMSession** för att importera moduler som är installerade på fjärrdatorer. Kommandon som använder cmdletarna i dessa moduler körs dock i fjärrsessionen på fjärrdatorn.

- Om du importerar medlemmar med samma namn och samma typ i din session, använder PowerShell medlemmen som importer ATS sist som standard. Variabler och alias ersätts och originalen är inte tillgängliga. Funktioner, cmdletar och providrar är bara skuggade av de nya medlemmarna. De kan nås genom att kvalificera kommando namnet med namnet på dess snapin-modul, modul eller funktions Sök väg.

- Använd cmdleten för att uppdatera formaterings data för kommandon som har importer ATS från en modul `Update-FormatData` . `Update-FormatData` uppdaterar också formaterings data för kommandon i sessionen som har importer ATS från moduler. Om format filen för en modul ändras kan du köra ett `Update-FormatData` kommando för att uppdatera formateringen för importerade kommandon. Du behöver inte importera modulen igen.

- Från och med Windows PowerShell 3,0 paketeras de grundläggande kommandon som installeras med PowerShell i moduler. I Windows PowerShell 2,0 och i värd program som skapar äldre sessioner i senare versioner av PowerShell, paketeras huvud kommandona i snapin-moduler ( **PSSnapins** ). Undantaget är **Microsoft. PowerShell. Core** , som alltid är en snapin-modul. Fjärrsessioner, till exempel de som startas av `New-PSSession` cmdleten, är äldre sessioner som inkluderar grundläggande snapin-moduler.

  Information om **CreateDefault2** -metoden som skapar nyare sessioner med Core-moduler finns i [CreateDefault2-metoden](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).

- `Import-Module` Det går inte att importera PowerShell Core-moduler från en annan session. PowerShell Core-modulerna har namn som börjar med `Microsoft.PowerShell` .

- I Windows PowerShell 2,0 fylldes några av egenskapsvärdena för objektet modul, till exempel egenskapsvärdena **ExportedCmdlets** och **NestedModules** , inte förrän modulen importerades och var inte tillgänglig på det modul-objekt som parametern **Passthru** returnerar. I Windows PowerShell 3,0 fylls alla egenskaps värden i modulen.

- Om du försöker importera en modul som innehåller sammansättningar med blandat läge som inte är kompatibla med Windows PowerShell 3,0 `Import-Module` returnerar ett fel meddelande som liknar följande.

  > Import-Module: blandad läges sammansättning har skapats mot version "v 2.0.50727" av körningen och kan inte läsas in i 4,0-körningsmiljön utan ytterligare konfigurations information.

  Det här felet uppstår när en modul som är avsedd för Windows PowerShell 2,0 innehåller minst en sammansättning med blandade moduler, det vill säga en sammansättning som innehåller både hanterad och icke-hanterad kod, till exempel C++ och C#.

  Om du vill importera en modul som innehåller sammansättningar med blandat läge startar du Windows PowerShell 2,0 med hjälp av följande kommando och försöker sedan `Import-Module` igen.

  `PowerShell.exe -Version 2.0`

- Om du vill använda funktionen CIM-sessionen måste fjärrdatorn ha WS-Management fjärr anslutning och Windows Management Instrumentation (WMI), som är Microsofts implementering av Common Information Model (CIM) standard. Datorn måste också ha WMI-providern för modul identifiering eller en alternativ CIM-provider som har samma grundläggande funktioner.

  Du kan använda funktionen för CIM-sessionen på datorer som inte kör ett Windows-operativsystem och på Windows-datorer som har PowerShell, men inte har PowerShell-fjärrkommunikation aktive rad.

  Du kan också använda CIM-parametrarna för att hämta CIM-moduler från datorer där PowerShell-fjärrkommunikation är aktiverat, inklusive den lokala datorn. När du skapar en CIM-session på den lokala datorn använder PowerShell DCOM, i stället för WMI, för att skapa sessionen.

- Som standard `Import-Module` importerar moduler i det globala omfånget även när de anropas från ett underordnat omfång. Omfattningen på den översta nivån och alla underordnade omfattningar har åtkomst till modulens exporterade element.

  I ett underordnat omfång `-Scope Local` begränsar importen till det omfånget och alla dess underordnade omfång. Överordnade omfattningar ser inte de importerade medlemmarna.

  > [!NOTE]
  > `Get-Module` visar alla moduler som lästs in i den aktuella sessionen. Detta inkluderar moduler som lästs in lokalt i ett underordnat omfång. Använd `Get-Command -Module modulename` för att se vilka medlemmar som läses in i det aktuella omfånget.

  Om modulen innehåller klass-och uppräknings definitioner, använder du `using module` i början av skriptet. Detta importerar skripten, inklusive klass-och uppräknings definitioner. Mer information finns i [about_Using](About/about_Using.md).

## RELATERADE LÄNKAR

[Exportera – ModuleMember](Export-ModuleMember.md)

[Hämta modul](Get-Module.md)

[Ny modul](New-Module.md)

[Ta bort modul](Remove-Module.md)
