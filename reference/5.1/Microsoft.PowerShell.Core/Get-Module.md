---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Module
ms.openlocfilehash: 15a7d7e6488e4b3d11375649fdbc810e1aeb2b2f
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564364"
---
# Get-Module

## SAMMANFATTNING
Lista de moduler som har importer ATS i den aktuella sessionen eller som kan importeras från PSModulePath.

## SYNTAX

### Läst in (standard)

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [<CommonParameters>]
```

### Tillgängligt

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [-ListAvailable]
 [-PSEdition <String>] [-Refresh] [<CommonParameters>]
```

### PsSession

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-PSEdition <String>] [-Refresh] -PSSession <PSSession> [<CommonParameters>]
```

### CimSession

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable] [-Refresh]
 -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>] [<CommonParameters>]
```

## BESKRIVNING

`Get-Module`Cmdleten listar PowerShell-modulerna som har importer ATS, eller som kan importeras, i en PowerShell-session. Utan parametrar, `Get-Module` hämtar moduler som har importer ATS till den aktuella sessionen. Parametern **ListAvailable** används för att visa en lista över de moduler som är tillgängliga för import från Sök vägarna som anges i PSModulePath-miljövariabeln ( `$env:PSModulePath` ).

Module-objektet som `Get-Module` returnerar innehåller värdefull information om modulen. Du kan också skicka modulens objekt till andra cmdletar, till exempel- `Import-Module` och- `Remove-Module` cmdlet: ar.

`Get-Module` visar en lista över moduler, men importerar dem inte. Från och med Windows PowerShell 3,0 importeras moduler automatiskt när du använder ett kommando i modulen, men ett `Get-Module` kommando utlöser inte en automatisk import. Du kan också importera modulerna till sessionen med hjälp av `Import-Module` cmdleten.

Från och med Windows PowerShell 3,0 kan du hämta och importera moduler från fjärrsessioner till den lokala sessionen. Den här strategin använder funktionen implicit fjärr kommunikation i PowerShell och motsvarar att använda `Import-PSSession` cmdleten. När du använder kommandon i moduler som importer ATS från en annan session körs kommandona implicit i fjärrsessionen. Med den här funktionen kan du hantera fjärrdatorn från den lokala sessionen.

Från och med Windows PowerShell 3,0 kan du också använda `Get-Module` och `Import-Module` för att hämta och importera common information Model-moduler (CIM). CIM-moduler definierar cmdletar i CDXLM-filer (cmdlet definition XML). Med den här funktionen kan du använda cmdletar som implementeras i icke-hanterade kod sammansättningar, t. ex. sådana som skrivits i C++.

Implicit fjärr kommunikation kan användas för att hantera fjärrdatorer som har PowerShell-fjärrkommunikation aktive rad.
Skapa en **PSSession** på fjärrdatorn och Använd sedan **PSSession** -parametern för `Get-Module` för att hämta PowerShell-modulerna i fjärrsessionen. När du importerar en modul från fjärrsessionen körs de importerade kommandona i sessionen på fjärrdatorn.

Du kan använda en liknande strategi för att hantera datorer som inte har PowerShell-fjärrkommunikation aktive rad.
Detta inkluderar datorer som inte kör Windows-operativsystemet och datorer som har PowerShell men inte har PowerShell-fjärrkommunikation aktive rad.

Börja med att skapa en CIM-session på fjärrdatorn. En CIM-session är en anslutning till Windows Management Instrumentation (WMI) på fjärrdatorn. Använd sedan **CIMSession** -parametern för `Get-Module` för att hämta CIM-moduler från CIM-sessionen. När du importerar en CIM-modul med hjälp av `Import-Module` cmdleten och sedan kör de importerade kommandona, körs kommandona implicit på fjärrdatorn. Du kan använda den här WMI-och CIM-strategin för att hantera fjärrdatorn.

## EXEMPEL

### Exempel 1: Hämta moduler som importer ATS till den aktuella sessionen

```powershell
Get-Module
```

Det här kommandot hämtar moduler som har importer ATS till den aktuella sessionen.

### Exempel 2: Hämta installerade moduler och tillgängliga moduler

```powershell
Get-Module -ListAvailable
```

Detta kommando hämtar de moduler som är installerade på datorn och som kan importeras till den aktuella sessionen.

`Get-Module` söker efter tillgängliga moduler i sökvägen som anges av variabeln **$env:P smodulepath** -miljövariabeln. Mer information om **PSModulePath** finns i [about_Modules](About/about_Modules.md) och [about_Environment_Variables](About/about_Environment_Variables.md).

### Exempel 3: Hämta alla exporterade filer

```powershell
Get-Module -ListAvailable -All
```

Det här kommandot hämtar alla exporterade filer för alla tillgängliga moduler.

### Exempel 4: Hämta en modul med dess fullständigt kvalificerade namn

```powershell
$FullyQualifedName = @{ModuleName="Microsoft.PowerShell.Management";ModuleVersion="3.1.0.0"}
Get-Module -FullyQualifiedName $FullyQualifedName | Format-Table -Property Name,Version
```

```Output
Name                             Version
----                             -------
Microsoft.PowerShell.Management  3.1.0.0
```

Detta kommando hämtar modulen **Microsoft. PowerShell. Management** genom att ange det fullständigt kvalificerade namnet på modulen med hjälp av parametern **FullyQualifiedName** . Kommandot rör sedan resultatet i `Format-Table` cmdleten för att formatera resultatet som en tabell med **namn** och **version** som kolumn rubriker.

### Exempel 5: Hämta egenskaper för en modul

```powershell
Get-Module | Get-Member -MemberType Property | Format-Table Name
```

```Output
Name
----
AccessMode
Author
ClrVersion
CompanyName
Copyright
Definition
Description
DotNetFrameworkVersion
ExportedAliases
ExportedCmdlets
ExportedCommands
ExportedFormatFiles
ExportedFunctions
ExportedTypeFiles
ExportedVariables
ExportedWorkflows
FileList
Guid
HelpInfoUri
LogPipelineExecutionDetails
ModuleBase
ModuleList
ModuleType
Name
NestedModules
OnRemove
Path
PowerShellHostName
PowerShellHostVersion
PowerShellVersion
PrivateData
ProcessorArchitecture
RequiredAssemblies
RequiredModules
RootModule
Scripts
SessionState
Version
```

Det här kommandot hämtar egenskaperna för det **PSModuleInfo** -objekt som `Get-Module` returneras. Det finns ett objekt för varje modul-fil.

Du kan använda egenskaperna för att formatera och filtrera modulens objekt. Mer information om egenskaperna finns i PSModuleInfo- [Egenskaper](/dotnet/api/system.management.automation.psmoduleinfo).

Utdata innehåller de nya egenskaperna, till exempel **författare** och **företags namn**, som introducerades i Windows PowerShell 3,0.

### Exempel 6: gruppera alla moduler efter namn

```powershell
Get-Module -ListAvailable -All | Format-Table -Property Name, Moduletype, Path -Groupby Name
```

```Output
Name: AppLocker

Name      ModuleType Path
----      ---------- ----
AppLocker   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\AppLocker\AppLocker.psd1


   Name: Appx

Name ModuleType Path
---- ---------- ----
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\en-US\Appx.psd1
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psd1
Appx     Script C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psm1


   Name: BestPractices

Name          ModuleType Path
----          ---------- ----
BestPractices   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BestPractices\BestPractices.psd1


   Name: BitsTransfer

Name         ModuleType Path
----         ---------- ----
BitsTransfer   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BitsTransfer\BitsTransfer.psd1
```

Det här kommandot hämtar alla modulblad, både importerade och tillgängliga, och grupperar dem efter modulnamn. På så sätt kan du se de module-filer som varje skript exporterar.

### Exempel 7: Visa innehållet i ett modul-manifest

Dessa kommandon visar innehållet i modulens manifest för Windows PowerShell-modulen **BitsTransfer** .

Moduler måste inte ha MANIFEST-filer. När de har en manifest fil, krävs manifest filen bara för att inkludera ett versions nummer. Manifest filen innehåller dock ofta användbar information om en modul, dess krav och dess innehåll.

```powershell
# First command
$m = Get-Module -list -Name BitsTransfer

# Second command
Get-Content $m.Path
```

```Output
@ {
    GUID               = "{8FA5064B-8479-4c5c-86EA-0D311FE48875}"
    Author             = "Microsoft Corporation"
    CompanyName        = "Microsoft Corporation"
    Copyright          = "Microsoft Corporation. All rights reserved."
    ModuleVersion      = "1.0.0.0"
    Description        = "Windows PowerShell File Transfer Module"
    PowerShellVersion  = "2.0"
    CLRVersion         = "2.0"
    NestedModules      = "Microsoft.BackgroundIntelligentTransfer.Management"
    FormatsToProcess   = "FileTransfer.Format.ps1xml"
    RequiredAssemblies = Join-Path $psScriptRoot "Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll"
}
```

Det första kommandot hämtar PSModuleInfo-objektet som representerar BitsTransfer-modulen. Objektet sparas i `$m` variabeln.

Det andra kommandot använder `Get-Content` cmdleten för att hämta innehållet i manifest filen på den angivna sökvägen. Den använder punkt notation för att hämta sökvägen till manifest filen, som lagras i objektets Sök vägs egenskap. Utdata visar innehållet i modulens manifest.

### Exempel 8: Visa filer i modulens katalog

```powershell
dir (Get-Module -ListAvailable FileTransfer).ModuleBase
```

```Output
Directory: C:\Windows\system32\WindowsPowerShell\v1.0\Modules\FileTransfer
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/16/2008  12:36 PM            en-US
-a---        11/19/2008  11:30 PM      16184 FileTransfer.Format.ps1xml
-a---        11/20/2008  11:30 PM       1044 FileTransfer.psd1
-a---        12/16/2008  12:20 AM     108544 Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll
```

Det här kommandot visar filerna i modulens katalog. Detta är ett annat sätt att avgöra vad som finns i en modul innan du importerar den. Vissa moduler kan ha hjälpfiler eller ReadMe-filer som beskriver modulen.

### Exempel 9: Hämta moduler som är installerade på en dator

```powershell
$s = New-PSSession -ComputerName Server01

Get-Module -PSSession $s -ListAvailable
```

De här kommandona hämtar de moduler som är installerade på den Server01 datorn.

Det första kommandot använder `New-PSSession` cmdleten för att skapa en **PSSession** på Server01-datorn. Kommandot sparar **PSSession** i variabeln $s.

Det andra kommandot använder parametrarna **PSSession** och **ListAvailable** för `Get-Module` för att hämta modulerna i **PSSession** i `$s` variabeln.

Om du rör moduler från andra sessioner till `Import-Module` cmdlet: en `Import-Module` importerar modulen till den aktuella sessionen med hjälp av funktionen implicit fjärr kommunikation. Detta motsvarar att använda `Import-PSSession` cmdleten. Du kan använda cmdlets från modulen i den aktuella sessionen, men kommandon som använder dessa cmdlets kör i själva verket fjärrsessionen. Mer information finns i [`Import-Module`](Import-Module.md) och [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md) .

### Exempel 10: hantera en dator som inte kör Windows operativ system

Med kommandona i det här exemplet kan du hantera lagrings systemen på en fjärrdator som inte kör Windows-operativsystemet.
I det här exemplet, eftersom datorns administratör har installerat WMI-providern för modul identifiering, kan CIM-kommandon använda standardvärdena, som är utformade för providern.

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Get-Module -CimSession $cs -Name Storage | Import-Module
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
Get-Disk
```

```Output
Number Friendly Name              OperationalStatus          Total Size Partition Style
------ -------------              -----------------          ---------- ---------------
0      Virtual HD ATA Device      Online                          40 GB MBR
```

Det första kommandot använder `New-CimSession` cmdleten för att skapa en session på RSDGF03-fjärrdatorn. Sessionen ansluter till WMI på fjärrdatorn. Kommandot sparar CIM-sessionen i `$cs` variabeln.

Det andra kommandot använder CIM-sessionen i `$cs` variabeln för att köra ett `Get-Module` kommando på RSDGF03-datorn. Kommandot använder name-parametern för att ange Storage-modulen. Kommandot använder en pipeline-operator (|) för att skicka modulen till `Import-Module` cmdleten, som importerar den till den lokala sessionen.

Det tredje kommandot kör `Get-Command` cmdleten i `Get-Disk` kommandot i modulen Storage.
När du importerar en CIM-modul till den lokala sessionen konverterar PowerShell de CDXLM-filer som representerar CIM-modulen till PowerShell-skript, som visas som funktioner i den lokala sessionen.

Det fjärde kommandot kör `Get-Disk` kommandot. Även om kommandot skrivs i den lokala sessionen körs det implicit på den fjärrdator som den importerades från. Kommandot hämtar objekt från fjärrdatorn och returnerar dem till den lokala sessionen.

## PARAMETRAR

### – Alla

Anger att denna cmdlet hämtar alla moduler i varje modul, inklusive kapslade moduler, manifest (. psd1)-filer, skriptfiler (. psm1) och binärfiler (. dll) för filer. Utan den här parametern `Get-Module` hämtas bara standardmodulen i varje modul-mapp.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Loaded, Available
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimNamespace

Anger namn området för en alternativ CIM-provider som exponerar CIM-moduler. Standardvärdet är namn området för WMI-providern för modul identifiering.

Använd den här parametern för att hämta CIM-moduler från datorer och enheter som inte kör Windows operativ system.

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

Använd den här parametern för att hämta CIM-moduler från datorer och enheter som inte kör Windows operativ system.

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

Anger en CIM-session på fjärrdatorn. Ange en variabel som innehåller CIM-sessionen eller ett kommando som hämtar CIM-sessionen, till exempel ett [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) -kommando.

`Get-Module` använder CIM-sessionen för att hämta moduler från fjärrdatorn. När du importerar modulen med hjälp av `Import-Module` cmdleten och använder kommandona från den importerade modulen i den aktuella sessionen, körs de kommandon som faktiskt körs på fjärrdatorn.

Du kan använda den här parametern för att hämta moduler från datorer och enheter som inte kör Windows-operativsystemet och datorer som har PowerShell, men som inte har PowerShell-fjärrkommunikation aktive rad.

Parametern **CimSession** hämtar alla moduler i **CimSession**. Du kan dock endast importera CIM-baserade och CDXLM-baserade moduler (cmdlet definition XML).

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

### -FullyQualifiedName

Anger moduler med namn som anges i form av **ModuleSpecification** -objekt. Se avsnittet anmärkningar i [ModuleSpecification-konstruktorn (hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).

**FullyQualifiedModule** -parametern accepterar till exempel ett modulnamn som anges i något av följande format:

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

**Modulnamn** och **ModuleVersion** krävs, men **GUID** är valfritt. Det går inte att ange parametern **FullyQualifiedModule** i samma kommando som en **modul** -parameter. de två parametrarna kan inte anges samtidigt.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – ListAvailable

Anger att denna cmdlet hämtar alla installerade moduler. `Get-Module` hämtar moduler i sökvägar som anges i miljövariabeln **PSModulePath** . Utan den här parametern `Get-Module` hämtas bara de moduler som båda anges i miljövariabeln **PSModulePath** och som läses in i den aktuella sessionen. **ListAvailable** returnerar inte information om moduler som inte finns i miljövariabeln **PSModulePath** , även om modulerna har lästs in i den aktuella sessionen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: True (Available), False (PsSession, CimSession)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger namn eller namn mönster för moduler som denna cmdlet hämtar. Jokertecken är tillåtna. Du kan också skicka namnen till `Get-Module` . Det går inte att ange parametern **FullyQualifiedName** i samma kommando som en **namn** parameter.

**Namnet** kan inte acceptera ett modul-GUID som värde.
Om du vill returnera moduler genom att ange ett GUID använder du **FullyQualifiedName** i stället.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### – PSEdition

Hämtar de moduler som stöder den angivna versionen av PowerShell.

De acceptabla värdena för den här parametern är:

- Skrivbord
- Kärna

Get-Module cmdleten kontrollerar egenskapen **CompatiblePSEditions** för **PSModuleInfo** -objektet för det angivna värdet och returnerar bara de moduler som har angetts.

> [!NOTE]
>
> - **Desktop Edition:** bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows Desktop.
> - **Core Edition:** bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.

```yaml
Type: System.String
Parameter Sets: PsSession, Available
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – PSSession

Hämtar modulerna i den angivna användar hanterade PowerShell-sessionen (**PSSession**). Ange en variabel som innehåller sessionen, ett kommando som hämtar sessionen, till exempel ett `Get-PSSession` kommando eller ett kommando som skapar sessionen, till exempel ett `New-PSSession` kommando.

När sessionen är ansluten till en fjärrdator måste du ange parametern **ListAvailable** .

Ett `Get-Module` kommando som använder parametern **PSSession** är detsamma som att använda `Invoke-Command` cmdleten för att köra ett `Get-Module -ListAvailable` kommando i en **PSSession**.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PsSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Uppdatera

Anger att denna cmdlet uppdaterar cacheminnet för installerade kommandon. Kommandots cacheminne skapas när sessionen startar. Den gör det möjligt för `Get-Command` cmdleten att hämta kommandon från moduler som inte importeras till sessionen.

Den här parametern är utformad för utvecklings-och testnings scenarier där innehållet i moduler har ändrats sedan sessionen startades.

När du anger parametern **Refresh** i ett kommando måste du ange **ListAvailable**.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka pipe-modulnamn till denna cmdlet.

## UTDATA

### System. Management. Automation. PSModuleInfo

Denna cmdlet returnerar objekt som representerar moduler.
När du anger parametern **ListAvailable** `Get-Module` returnerar ett **ModuleInfoGrouping** -objekt, som är en typ av **PSModuleInfo** -objekt som har samma egenskaper och metoder.

## ANTECKNINGAR

- Från och med Windows PowerShell 3,0 paketeras kärn kommandona som ingår i PowerShell i moduler. Undantaget är **Microsoft. PowerShell. Core**, som är en snapin-modul (**PSSnapin**). Som standard läggs bara snapin-modulen **Microsoft. PowerShell. Core** till i sessionen. Moduler importeras automatiskt vid första användningen och du kan använda `Import-Module` cmdleten för att importera dem.

- I Windows PowerShell 2,0 och i värd program som skapar äldre sessioner i senare versioner av PowerShell, paketeras huvud kommandona i snapin-moduler (**PSSnapins**). Undantaget är **Microsoft. PowerShell. Core**, som alltid är en snapin-modul. Fjärrsessioner, till exempel de som startas av `New-PSSession` cmdleten, är äldre sessioner som inkluderar grundläggande snapin-moduler.

  Information om **CreateDefault2** -metoden som skapar nyare sessioner med Core-moduler finns i CreateDefault2- [metoden](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).

- `Get-Module` hämtar endast moduler i platser som lagras i värdet för **PSModulePath** -miljövariabeln ($env:P smodulepath). `Import-Module`Cmdleten kan importera moduler på andra platser, men du kan inte använda `Get-Module` cmdleten för att hämta dem.

- Från och med PowerShell 3,0 har nya egenskaper också lagts till i objektet som returnerar och `Get-Module` gör det lättare att lära sig om moduler, även innan de importeras. Alla egenskaper fylls i före importen. Dessa inkluderar **ExportedCommands**-, **ExportedCmdlets** -och **ExportedFunctions** -egenskaperna som visar de kommandon som modulen exporterar.

- Parametern **ListAvailable** hämtar endast välformulerade moduler, det vill säga mappar som innehåller minst en fil vars bas namn är samma som namnet på mappen module. Bas namnet är namnet utan fil namns tillägget. Mappar som innehåller filer som har olika namn anses vara behållare, men inte moduler.

  Om du vill hämta moduler som har implementerats som DLL-filer, men som inte är omslutna i en modul, anger du både **ListAvailable** och **alla** parametrar.

- Om du vill använda funktionen CIM-sessionen måste fjärrdatorn ha WS-Management fjärr anslutning och Windows Management Instrumentation (WMI), som är Microsofts implementering av Common Information Model (CIM) standard. Datorn måste också ha WMI-providern för modul identifiering eller en alternativ WMI-provider som har samma grundläggande funktioner.

  Du kan använda funktionen för CIM-sessionen på datorer som inte kör Windows-operativsystemet och på Windows-datorer med PowerShell, men inte har PowerShell-fjärrkommunikation aktive rad.

  Du kan också använda CIM-parametrarna för att hämta CIM-moduler från datorer där PowerShell-fjärrkommunikation är aktiverat. Detta inkluderar den lokala datorn. När du skapar en CIM-session på den lokala datorn använder PowerShell DCOM, i stället för WMI, för att skapa sessionen.

## RELATERADE LÄNKAR

[Get-CimSession](../CimCmdlets/Get-CimSession.md)

[New-CimSession](../CimCmdlets/New-CimSession.md)

[about_Modules](About/about_Modules.md)

[Get-PSSession](Get-PSSession.md)

[Importera-modul](Import-Module.md)

[Importera – PSSession](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[New-PSSession](New-PSSession.md)

[Ta bort modul](Remove-Module.md)
