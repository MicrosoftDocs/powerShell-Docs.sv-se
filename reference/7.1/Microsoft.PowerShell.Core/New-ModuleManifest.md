---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/02/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-modulemanifest?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ModuleManifest
ms.openlocfilehash: 5fbd197f6c22de0ca50b4d2b6b76a914b85f7120
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/03/2020
ms.locfileid: "93273555"
---
# New-ModuleManifest

## SAMMANFATTNING
Skapar ett nytt modul manifest.

## SYNTAX

### Alla

```
New-ModuleManifest [-Path] <String> [-NestedModules <Object[]>] [-Guid <Guid>] [-Author <String>]
 [-CompanyName <String>] [-Copyright <String>] [-RootModule <String>] [-ModuleVersion <Version>]
 [-Description <String>] [-ProcessorArchitecture <ProcessorArchitecture>]
 [-PowerShellVersion <Version>] [-CLRVersion <Version>] [-DotNetFrameworkVersion <Version>]
 [-PowerShellHostName <String>] [-PowerShellHostVersion <Version>] [-RequiredModules <Object[]>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-ScriptsToProcess <String[]>]
 [-RequiredAssemblies <String[]>] [-FileList <String[]>] [-ModuleList <Object[]>]
 [-FunctionsToExport <String[]>] [-AliasesToExport <String[]>] [-VariablesToExport <String[]>]
 [-CmdletsToExport <String[]>] [-DscResourcesToExport <String[]>] [-CompatiblePSEditions <String[]>]
 [-PrivateData <Object>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ReleaseNotes <String>] [-Prerelease <String>] [-RequireLicenseAcceptance]
 [-ExternalModuleDependencies <String[]>] [-HelpInfoUri <String>] [-PassThru]
 [-DefaultCommandPrefix <String>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## BESKRIVNING

`New-ModuleManifest`Cmdleten skapar en ny modul manifest `.psd1` fil (), fyller i sina värden och sparar manifest filen på den angivna sökvägen.

Module-författare kan använda denna cmdlet för att skapa ett manifest för sin modul. Ett modul manifest är en `.psd1` fil som innehåller en hash-tabell. Nycklar och värden i hash-tabellen beskriver modulens innehåll och attribut, definierar förutsättningarna och avgör hur komponenterna bearbetas. Manifest krävs inte för en modul.

`New-ModuleManifest` skapar ett manifest som innehåller alla ofta använda manifest nycklar, så att du kan använda standardutdata som en manifest mall. Om du vill lägga till eller ändra värden eller lägga till Modulnamn som denna cmdlet inte lägger till, öppnar du den resulterande filen i en text redigerare.

Varje parameter, förutom **sökväg** och **Passthru** , skapar en modul manifest nyckel och dess värde.
I ett modul manifest krävs bara nyckeln **ModuleVersion** . Om du utelämnar en parameter från kommandot, om du inte anger någon parameter från kommandot, `New-ModuleManifest` skapas en kommentar sträng för det associerade värdet som inte har någon påverkan.

I PowerShell 2,0 `New-ModuleManifest` uppmanas du att ange värdena för de vanligaste parametrarna som inte anges i kommandot, förutom de parameter värden som krävs. Från och med PowerShell 3,0 visas `New-ModuleManifest` endast när obligatoriska parameter värden inte har angetts.

Om du planerar att publicera modulen i PowerShell-galleriet måste manifestet innehålla värden för vissa egenskaper. Mer information finns i [obligatoriska metadata för objekt som publicerats till PowerShell-galleriet](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) i Galleri dokumentationen.

## EXEMPEL

### Exempel 1 – Skapa ett nytt modul manifest

Det här exemplet skapar ett nytt modul-manifest i filen som anges av parametern **Path** .
Parametern **Passthru** skickar utdata till pipelinen och till filen.

Utdata visar standardvärden för alla nycklar i manifestet.

```powershell
New-ModuleManifest -Path C:\ps-test\Test-Module\Test-Module.psd1 -PassThru
```

```Output
#
# Module manifest for module 'Test-Module'
#
# Generated by: ContosoAdmin
#
# Generated on: 7/12/2019
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '0.0.1'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'e1826c6e-c420-4eef-9ac8-185e3669ca6a'

# Author of this module
Author = 'ContosoAdmin'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) ContosoAdmin. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of Microsoft .NET Framework required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module.
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no functions to export.
FunctionsToExport = @()

# Cmdlets to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no cmdlets to export.
CmdletsToExport = @()

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no aliases to export.
AliasesToExport = @()

# DSC resources to export from this module
# DscResourcesToExport = @()

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{

    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

        # Prerelease string of this module
        # Prerelease = ''

        # Flag to indicate whether the module requires explicit user acceptance for install/update/save
        # RequireLicenseAcceptance = $false

        # External dependent modules of this module
        # ExternalModuleDependencies = @()

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}
```

### Exempel 2 – Skapa ett nytt manifest med förkonfigurerade inställningar

Det här exemplet skapar ett nytt modul manifest. Den använder parametrarna **PowerShellVersion** och **AliasesToExport** för att lägga till värden i motsvarande manifest nycklar.

```powershell
New-ModuleManifest -PowerShellVersion 1.0 -AliasesToExport JKBC, DRC, TAC -Path C:\ps-test\ManifestTest.psd1
```

### Exempel 3 – skapa ett manifest som kräver andra moduler

I det här exemplet används ett sträng format för att ange namnet på **BitsTransfer** -modulen och hash-tabellens format för att ange namn, **GUID** och en version av **PSScheduledJob** -modulen.

```powershell
$moduleSettings = @{
  RequiredModules = ("BitsTransfer", @{
    ModuleName="PSScheduledJob"
    ModuleVersion="1.0.0.0";
    GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"
  })
  Path = 'C:\ps-test\ManifestTest.psd1'
}
New-ModuleManifest @moduleSettings
```

Det här exemplet visar hur du använder tabell formaten sträng och hash för parametern **ModuleList** , **RequiredModules** och **NestedModules** . Du kan kombinera strängar och hash-tabeller i samma parameter värde.

### Exempel 4 – skapa ett manifest som stöder uppdaterings bara hjälp

I det här exemplet används parametern **HelpInfoUri** för att skapa en **HelpInfoUri** -nyckel i modul manifestet. Värdet för parametern och nyckeln måste börja med **http** eller **https**. Det här värdet anger det uppdaterings bara hjälp systemet där du hittar HelpInfo XML-hjälpfil med uppdaterings information för modulen.

```powershell
$moduleSettings = @{
  HelpInfoUri = 'http://https://go.microsoft.com/fwlink/?LinkID=603'
  Path = 'C:\ps-test\ManifestTest.psd1'
}
New-ModuleManifest @moduleSettings
```

Information om uppdaterbar hjälp finns [about_Updatable_Help](./About/about_Updatable_Help.md).
Information om XML-HelpInfo finns i [stöd uppdaterings bar hjälp](/powershell/scripting/developer/module/supporting-updatable-help).

### Exempel 5 – hämta information om moduler

Det här exemplet visar hur du hämtar konfigurations värden för en modul. Värdena i modulens manifest visas i egenskaperna för objektet module.

`Get-Module`Cmdleten används för att hämta **Microsoft. PowerShell. Diagnostics** -modulen med **list** -parametern. Kommandot skickar modulen till `Format-List` cmdlet: en för att visa alla egenskaper och värden för objektet module.

```powershell
Get-Module Microsoft.PowerShell.Diagnostics -List | Format-List -Property *
```

```Output
LogPipelineExecutionDetails : False
Name                        : Microsoft.PowerShell.Diagnostics
Path                        : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Microsoft.PowerShell.Diagnostics\Micro
                              soft.PowerShell.Diagnostics.psd1
Definition                  :
Description                 :
Guid                        : ca046f10-ca64-4740-8ff9-2565dba61a4f
HelpInfoUri                 : https://go.microsoft.com/fwlink/?LinkID=210596
ModuleBase                  : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Microsoft.PowerShell.Diagnostics
PrivateData                 :
Version                     : 3.0.0.0
ModuleType                  : Manifest
Author                      : Microsoft Corporation
AccessMode                  : ReadWrite
ClrVersion                  : 4.0
CompanyName                 : Microsoft Corporation
Copyright                   : Microsoft Corporation. All rights reserved.
DotNetFrameworkVersion      :
ExportedFunctions           : {}
ExportedCmdlets             : {[Get-WinEvent, Get-WinEvent], [Get-Counter, Get-Counter], [Import-Counter,
                              Import-Counter], [Export-Counter, Export-Counter]...}
ExportedCommands            : {[Get-WinEvent, Get-WinEvent], [Get-Counter, Get-Counter], [Import-Counter,
                              Import-Counter], [Export-Counter, Export-Counter]...}
FileList                    : {}
ModuleList                  : {}
NestedModules               : {}
PowerShellHostName          :
PowerShellHostVersion       :
PowerShellVersion           : 3.0
ProcessorArchitecture       : None
Scripts                     : {}
RequiredAssemblies          : {}
RequiredModules             : {}
RootModule                  :
ExportedVariables           : {}
ExportedAliases             : {}
ExportedWorkflows           : {}
SessionState                :
OnRemove                    :
ExportedFormatFiles         : {C:\Windows\system32\WindowsPowerShell\v1.0\Event.format.ps1xml,
                              C:\Windows\system32\WindowsPowerShell\v1.0\Diagnostics.format.ps1xml}
ExportedTypeFiles           : {C:\Windows\system32\WindowsPowerShell\v1.0\GetEvent.types.ps1xml}
```

## PARAMETRAR

### -AliasesToExport

Anger de alias som modulen exporterar. Jokertecken är tillåtna.

Du kan använda den här parametern för att begränsa de alias som exporteras av modulen. Det kan ta bort alias från listan över exporterade alias, men det går inte att lägga till alias i listan.

Om du utelämnar den här parametern `New-ModuleManifest` skapar en **AliasesToExport** -nyckel med värdet `*` (alla), vilket innebär att alla alias som definierats i modulen exporteras av manifestet.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### – Författare

Anger modulens författare.

Om du utelämnar den här parametern `New-ModuleManifest` skapar en **författar** nyckel med namnet på den aktuella användaren.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Name of the current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -CmdletsToExport

Anger de cmdletar som modulen exporterar. Jokertecken är tillåtna.

Du kan använda den här parametern för att begränsa de cmdletar som exporteras av modulen. Den kan ta bort cmdletar från listan över exporterade cmdlets, men det går inte att lägga till cmdletar i listan.

Om du utelämnar den här parametern `New-ModuleManifest` skapar en **CmdletsToExport** -nyckel med värdet `*` (alla), vilket innebär att alla cmdletar som definierats i modulen exporteras av manifestet.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### -Företags namn

Identifierar företaget eller leverantören som skapade modulen.

Om du utelämnar den här parametern `New-ModuleManifest` skapar en **företags namn** nyckel med värdet "okänd".

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: "Unknown"
Accept pipeline input: False
Accept wildcard characters: False
```

### -CompatiblePSEditions

Anger modulens kompatibla PSEditions. Information om PSEdition finns i [moduler med kompatibla PowerShell-versioner](/powershell/scripting/gallery/concepts/module-psedition-support).

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Desktop, Core

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Copyright

Anger en Copyright-instruktion för modulen.

Om du utelämnar den här parametern `New-ModuleManifest` skapar en **Copyright** -nyckel med värdet `(c) <year> <username>. All rights reserved.` där `<year>` är det aktuella året och `<username>` är värdet för **författar** nyckeln.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: (c) <year> <username>. All rights reserved.
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultCommandPrefix

Anger ett prefix som är anpassningsprefix till substantiven för alla kommandon i modulen när de importeras till en session. Ange en prefixlängd. Prefix förhindrar att kommando namns konflikter i en användares session.

Module-användare kan åsidosätta det här prefixet genom att ange parametern **prefix** för `Import-Module` cmdleten.

Den här parametern introducerades i PowerShell 3,0.

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

### -Beskrivning

Beskriver innehållet i modulen.

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

### -DotNetFrameworkVersion

Anger den lägsta version av Microsoft .NET Framework som modulen kräver.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DscResourcesToExport

Anger de DSC-resurser (Desired State Configuration) som modulen exporterar. Jokertecken är tillåtna.

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

### -ExternalModuleDependencies

En lista över externa moduler som den här modulen är beroende av.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – FileList

Anger alla objekt som ingår i modulen.

Den här nyckeln är utformad för att fungera som en modul. Filerna som anges i nyckeln inkluderas när modulen publiceras, men inga funktioner exporteras automatiskt.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatsToProcess

Anger de formateringsattribut ( `.ps1xml` ) som körs när modulen importeras.

När du importerar en modul kör PowerShell `Update-FormatData` cmdleten med de angivna filerna.
Eftersom filer som inte är begränsade påverkar formateringen alla sessionstillstånd i sessionen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FunctionsToExport

Anger de funktioner som modulen exporterar. Jokertecken är tillåtna.

Du kan använda den här parametern för att begränsa de funktioner som exporteras av modulen. Den kan ta bort funktioner från listan över exporterade alias, men det går inte att lägga till funktioner i listan.

Om du utelämnar den här parametern `New-ModuleManifest` skapar en **FunctionsToExport** -nyckel med värdet `*` (alla), vilket innebär att alla funktioner som definierats i modulen exporteras av manifestet.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### -GUID

Anger en unik identifierare för modulen. **GUID** kan användas för att skilja mellan moduler med samma namn.

Om du utelämnar den här parametern `New-ModuleManifest` skapar en **GUID** -nyckel i manifestet och genererar ett **GUID** för värdet.

Om du vill skapa ett nytt **GUID** i PowerShell skriver du `[guid]::NewGuid()` .

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: A GUID generated for the module
Accept pipeline input: False
Accept wildcard characters: False
```

### -HelpInfoUri

Anger Internet adressen för HelpInfo XML-filen för modulen. Ange en Uniform Resource Identifier (URI) som börjar med **http** eller **https**.

XML-filen HelpInfo stöder den uppdaterbara hjälp funktionen som introducerades i PowerShell 3,0. Den innehåller information om platsen för nedladdnings bara hjälpfiler för modulen och versions numren för de senaste hjälpfilerna för varje språk som stöds.

Information om uppdaterbar hjälp finns [about_Updatable_Help](./About/about_Updatable_Help.md).
Information om XML-HelpInfo finns i [stöd uppdaterings bar hjälp](/powershell/scripting/developer/module/supporting-updatable-help).

Den här parametern introducerades i PowerShell 3,0.

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

### – IconUri

Anger URL-adressen till en ikon för modulen. Den angivna ikonen visas på Galleri webb sidan för modulen.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LicenseUri

Anger URL: en för licens villkoren för modulen.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModuleList

Visar alla moduler som ingår i den här modulen.

Ange varje Modulnamn som en sträng eller som en hash-tabell med **Modulnamn** och **ModuleVersion** -nycklar. Hash-tabellen kan också ha en valfri **GUID** -nyckel. Du kan kombinera strängar och hash-tabeller i parametervärdet.

Den här nyckeln är utformad för att fungera som en modul. Modulerna som anges i värdet för den här nyckeln bearbetas inte automatiskt.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – ModuleVersion

Anger modulens version.

Den här parametern är inte obligatorisk, men en **ModuleVersion** -nyckel krävs i manifestet. Om du utelämnar den här parametern `New-ModuleManifest` skapar en **ModuleVersion** -nyckel med värdet 1,0.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1.0
Accept pipeline input: False
Accept wildcard characters: False
```

### -NestedModules

Anger skript moduler ( `.psm1` ) och binära moduler ( `.dll` ) som importeras till modulens sessionstillstånd. Filerna i **NestedModules** -nyckeln körs i den ordning som de är listade i värdet.

Ange varje Modulnamn som en sträng eller som en hash-tabell med **Modulnamn** och **ModuleVersion** -nycklar. Hash-tabellen kan också ha en valfri **GUID** -nyckel. Du kan kombinera strängar och hash-tabeller i parametervärdet.

Kapslade moduler innehåller vanligt vis kommandon som rot modulen behöver för intern bearbetning.
Som standard exporteras kommandon i kapslade moduler från modulens sessionstillstånd till anroparens sessionstillstånd, men modulen root kan begränsa vilka kommandon som exporteras. Till exempel genom att använda ett `Export-ModuleMember` kommando.

Kapslade moduler i sessionens sessionstillstånd är tillgängliga för modulen root, men de returneras inte av ett `Get-Module` kommando i anroparens sessionstillstånd.

Skript ( `.ps1` ) som anges i **NestedModules** -nyckeln körs i modulens sessionstillstånd, inte i anroparens sessionstillstånd. Om du vill köra ett skript i anroparens sessionstillstånd, visar du skript filens namn i värdet för nyckeln **ScriptsToProcess** i manifestet.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – PassThru

Skriver manifestet för den resulterande modulen till-konsolen och skapar en `.psd1` fil. Som standard genererar denna cmdlet inga utdata.

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

### -Path

Anger sökvägen och fil namnet för det nya modul manifestet. Ange en sökväg och ett fil namn med ett `.psd1` fil namns tillägg, till exempel `$pshome\Modules\MyModule\MyModule.psd1` . Parametern **Path** måste anges.

Om du anger sökvägen till en befintlig fil `New-ModuleManifest` ersätts filen utan varning om inte filen har attributet skrivskyddad.

Manifestet ska finnas i modulens katalog och manifest filens namn ska vara samma som modulens katalog namn, men med ett `.psd1` fil namns tillägg.

> [!NOTE]
> Du kan inte använda variabler, t `$PSHOME` . ex. eller `$HOME` , som svar på en prompt för värdet för en **Sök vägs** parameter. Om du vill använda en variabel inkluderar du parametern **Path** i kommandot.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PowerShellHostName

Anger namnet på PowerShell-värdservern som modulen kräver. Ange namnet på värd programmet, till exempel **Windows PowerShell ISE värd** eller **ConsoleHost**. Jokertecken är inte tillåtna.

Om du vill hitta namnet på ett värd program skriver du i programmet `$Host.Name` .

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

### -PowerShellHostVersion

Anger den lägsta versionen av PowerShell-värd programmet som fungerar med modulen. Ange ett versions nummer, till exempel 1,1.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – PowerShellVersion

Anger den lägsta version av PowerShell som fungerar med den här modulen. Du kan till exempel ange 1,0, 2,0 eller 3,0 som parameter värde.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -För hands version

För hands versions sträng för den här modulen. Om du lägger till en för hands versions sträng identifieras modulen som en för hands version. När modulen publiceras till PowerShell-galleriet används dessa data för att identifiera för hands versions paket. För att hämta för hands paket från galleriet måste du använda parametern **AllowPrerelease** med PowerShellGet-kommandona,, `Find-Module` `Install-Module` `Update-Module` och `Save-Module` .

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

### -PrivateData

Anger data som skickas till modulen när den importeras.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProcessorArchitecture

Anger den processor arkitektur som modulen kräver. Giltiga värden är x86, AMD64, IA64, MSIL och None (okänd eller ospecificerad).

```yaml
Type: System.Reflection.ProcessorArchitecture
Parameter Sets: (All)
Aliases:
Accepted values: None, MSIL, X86, IA64, Amd64, Arm

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProjectUri

Anger webb adressen till en webb sida om projektet.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReleaseNotes

Anger viktig information.

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

### -RequiredAssemblies

Anger de Assembly ( `.dll` )-filer som modulen kräver. Ange sammansättnings fil namnen.
PowerShell läser in de angivna sammansättningarna innan du uppdaterar typer eller format, importerar kapslade moduler eller importerar filen som anges i värdet för nyckeln **RootModule** .

Använd den här parametern för att visa en lista över alla sammansättningar som modulen kräver, inklusive sammansättningar som måste läsas in för att uppdatera all formatering eller skriva filer som listas i **FormatsToProcess** -eller **TypesToProcess** -nycklarna, även om dessa sammansättningar också visas som binära moduler i **NestedModules** -nyckeln.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredModules

Anger moduler som måste vara i det globala sessionstillståndet. Om de moduler som krävs inte är i det globala sessionstillståndet importeras de av PowerShell. Om de moduler som krävs inte är tillgängliga, `Import-Module` Miss lyckas kommandot.

Ange varje Modulnamn som en sträng eller som en hash-tabell med **Modulnamn** och **ModuleVersion** -nycklar. Hash-tabellen kan också ha en valfri **GUID** -nyckel. Du kan kombinera strängar och hash-tabeller i parametervärdet.

I PowerShell 2,0 `Import-Module` importerar de nödvändiga modulerna automatiskt. Den verifierar bara att de nödvändiga modulerna är i det globala sessionstillståndet.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequireLicenseAcceptance

Flagga för att ange om modulen kräver explicit användar godkännande för installation, uppdatering, orsave.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RootModule

Anger modulens primära eller rot fil. Ange fil namnet för ett skript ( `.ps1` ), en skriptbaserad modul ( `.psm1` ), ett modul manifest ( `.psd1` ), en sammansättning ( `.dll` ), en XML-fil () för cmdlet-definition ( `.cdxml` ) eller ett arbets flöde ( `.xaml` ). När modulen importeras importeras medlemmar som exporteras från rot-modul filen till anroparens sessionstillstånd.

Om en modul har en manifest fil och ingen rot fil har angetts i **RootModule** -nyckeln blir manifestet den primära filen för modulen och modulen blir en manifest-modul (ModuleType = manifest).

För att exportera medlemmar från `.psm1` eller `.dll` filer i en modul som har ett manifest, måste namnen på filerna anges i värdena för **RootModule** -eller **NestedModules** -nycklarna i manifestet. Annars exporteras inte deras medlemmar.

> [!NOTE]
> I PowerShell 2,0 kallades den här nyckeln för **ModuleToProcess**. Du kan använda **RootModule** -parameter namnet eller dess **ModuleToProcess** -alias.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ModuleToProcess

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptsToProcess

Anger skript ( `.ps1` )-filer som körs i anroparens sessionstillstånd när modulen importeras.
Du kan använda dessa skript för att förbereda en miljö, precis som du kan använda ett inloggnings skript.

Använd nyckeln **NestedModules** för att ange skript som körs i modulens sessionstillstånd.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Taggar

Anger en matris med taggar.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypesToProcess

Anger de typ filer ( `.ps1xml` ) som körs när modulen importeras.

När du importerar modulen kör PowerShell `Update-TypeData` cmdleten med de angivna filerna.
Eftersom filtypen inte är begränsad, påverkar de alla sessionstillstånd i sessionen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VariablesToExport

Anger de variabler som modulen exporterar. Jokertecken är tillåtna.

Du kan använda den här parametern för att begränsa de variabler som exporteras av modulen. Den kan ta bort variabler från listan över exporterade variabler, men det går inte att lägga till variabler i listan.

Om du utelämnar den här parametern `New-ModuleManifest` skapar en **VariablesToExport** -nyckel med värdet `*` (alla), vilket innebär att alla variabler som definierats i modulen exporteras av manifestet.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Visar vad som händer om `New-ModuleManifest` körs. Cmdleten körs inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ClrVersion

Anger den lägsta versionen av CLR (Common Language Runtime) för Microsoft .NET Framework som modulen kräver.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### Ingen eller system. String

Som standard `New-ModuleManifest` genererar inga utdata. Men om du använder parametern **Passthru** genereras ett **system. String** -objekt som representerar modulens manifest.

## ANTECKNINGAR

`New-ModuleManifest` Om du kör på Windows-och icke-Windows-plattformar skapas modul manifest ( `.psd1` )-filer som är kodade som **UTF8NoBOM**.

Manifest för moduler är vanligt vis valfria. Men ett modul manifest krävs för att exportera en sammansättning som är installerad i Global Assembly Cache.

Om du vill lägga till eller ändra filer i `$pshome\Modules` katalogen startar du PowerShell med alternativet **Kör som administratör** .

> [!NOTE]
> Från och med PowerShell 6,2 försöker PowerShell läsa in alla DLL-filer som anges i egenskapen **filelist** för modul manifestet. Inbyggda dll: er är i **filelist** som inte kan läsas in i processen och felet ignoreras. Alla hanterade DLL-filer läses in i processen. Det här beteendet har tagits bort i PowerShell 7,1.

I PowerShell 2,0 var många parametrar i `New-ModuleManifest` obligatoriska, trots att de inte krävdes i ett modul manifest. Från och med PowerShell 3,0 är bara parametern **Path** obligatorisk.

En session är en instans av PowerShell-körnings miljön. En session kan ha ett eller flera sessionstillstånd. Som standard har en session endast ett globalt sessionstillstånd, men varje importerad modul har sitt eget sessionstillstånd. Sessionstillstånd gör att kommandona i en modul kan köras utan att det globala sessionstillståndet påverkas.

Anroparens sessionstillstånd är det sessionstillstånd som en modul importeras till. Normalt refererar det till det globala sessionstillståndet, men när en modul importerar kapslade moduler, är anroparen modulen och anroparens sessionstillstånd är modulens sessionstillstånd.

## RELATERADE LÄNKAR

[Exportera – ModuleMember](Export-ModuleMember.md)

[Hämta modul](Get-Module.md)

[Importera-modul](Import-Module.md)

[Ny modul](New-Module.md)

[Ta bort modul](Remove-Module.md)

[Test-ModuleManifest](Test-ModuleManifest.md)

[about_Modules](./About/about_Modules.md)