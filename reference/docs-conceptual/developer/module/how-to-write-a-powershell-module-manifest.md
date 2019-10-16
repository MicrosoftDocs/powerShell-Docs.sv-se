---
title: Så här skriver du ett manifest för PowerShell-modulen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 1265855b82b0bfaa7b2717c8eb348b822c19f561
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357395"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>Skriva ett PowerShell-modulmanifest

När du har skrivit din Windows PowerShell-modul kan du välja att lägga till ett modul manifest. Ett modul manifest är en PowerShell-skriptfil som du kan använda för att inkludera information om modulen. Du kan till exempel beskriva författaren, ange filer i modulen (t. ex. kapslade moduler), köra skript för att anpassa användarens miljö, läsa in typ av format och formatera filer, definiera system krav och begränsa de medlemmar som modulen exporterar.

## <a name="creating-a-module-manifest"></a>Skapa ett modul manifest

Ett *modul manifest* är en Windows PowerShell-datafil (. psd1) som beskriver innehållet i en modul och bestämmer hur en modul bearbetas. Själva manifest filen är en textfil som innehåller en hash-tabell med nycklar och värden. Du länkar en manifest fil till en modul genom att namnge den på samma sätt som modulen och placera den i roten i modulens katalog.

För enkla moduler som bara innehåller en enda. psm1 eller binär sammansättning är ett modul-manifest valfritt. Vi rekommenderar dock att du använder ett modul manifest närhelst det är möjligt, eftersom de är användbara för att hjälpa dig att organisera din kod och underhålla versions information. Dessutom krävs ett modul manifest för att exportera en sammansättning som är installerad i Global Assembly Cache. Ett modul manifest krävs också för moduler som stöder den uppdaterbara hjälp funktionen. Det vill säga uppdaterings bara hjälp använder **HelpInfoUri** -nyckeln i modulen manifest för att hitta hjälp information (HelpInfo XML) som innehåller platsen för de uppdaterade hjälpfilerna för modulen. Mer information om uppdaterings bar hjälp finns i [support uppdaterings bara hjälp](./supporting-updatable-help.md).

### <a name="to-create-and-use-a-module-manifest"></a>Skapa och använda ett modul manifest

1. Om du vill skapa ett modul manifest har du flera alternativ:

   1. Skapa hash-tabellen direkt med den minsta information som krävs, och spara den i en. psd1-fil som har samma namn som modulen. När du har gjort det kan du öppna filen och lägga till lämpliga värden manuellt.

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. Eller så anropar du cmdleten [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) med ett eller flera av de standardvärden som angavs som parametrar. (Observera att endast namnet på filen krävs för att generera ett manifest, men.) Detta skapar ett modul manifest med alla manifest värden som du angav explicit och där resten innehåller lämpligt standardvärde.

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. Slutligen kan du också skapa en tom. psd1-fil och kopiera mallen längst ned i det här avsnittet till filen och fylla i relevanta värden. Det enda verkliga kravet i det här fallet är att se till att filen har samma namn som modulen.

2. Lägg till i alla ytterligare element i manifestet som du vill ha i filen.

   I allmänhet är detta förmodligen i vilken text redigerare som helst, till exempel Anteckningar. Detta är dock tekniskt sett en skript fil som innehåller kod, så du kanske vill redigera den i en faktisk skript-eller utvecklings miljö, till exempel Visual Studio Code. Observera att alla element i en manifest fil är valfria, förutom ModuleVersion-numret.

   Beskrivningar av nycklar och värden som du kan ha i ett modul manifest finns i avsnittet **manifest element** nedan. Mer information finns i parameter beskrivningar i cmdleten [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) .

3. Alternativt kan du välja att lägga till ytterligare kod i manifestet för modulen för att åtgärda eventuella scenarier som inte omfattas av manifest elementen för bas modulen.

   På grund av säkerhets problem kommer PowerShell bara att köra en liten delmängd av de tillgängliga åtgärderna i en modul manifest fil. I allmänhet kan du använda operatorerna **IF** , aritmetisk och jämförelse och de grundläggande PowerShell-datatyperna.

4. När du har skapat modul manifestet kan du testa det (för att bekräfta att alla sökvägar som beskrivs i manifestet är korrekta) med ett anrop till [test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest).

   `Test-ModuleManifest myModuleName.psd1`

5. Se till att modul manifestet finns på den översta nivån i katalogen som innehåller modulen.

   När du kopierar modulen till ett system och importerar den, kommer PowerShell att använda modul manifestet för att importera modulen.

6. Alternativt kan du direkt testa modul manifestet med ett anrop till [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) med punkt-källa själva manifestet.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Modul manifest element

I följande tabell beskrivs de element som du kan ha i ett modul manifest

|Element|Standard|Beskrivning|
|-------------|-------------|-----------------|
|RootModule<br /><br /> Typ: sträng|' '|Skriptbaserad modul eller binär modul som är associerad med det här manifestet. Tidigare versioner av PowerShell anropade det här elementet som ModuleToProcess.<br /><br /> Möjliga typer för rotnoden kan vara tomma (vilket gör denna till en **manifest** -modul), namnet på en psm1 (., som gör denna till en modul för **skript** ) eller namnet på en binär modul (. exe eller. dll, som gör denna till en **binär** modul). Om du placerar namnet på ett modul manifest (. psd1) eller en skript fil (. ps1) i det här elementet uppstår ett fel.|
|ModuleVersion<br /><br /> Typ: sträng|1.0|Versions nummer för den här modulen. Strängen måste kunna konverteras till [system. version]. Det vill säga #. #. #. #. #. `Import-Module` läser in den första modulen som den hittar på den **$psModulePath** som matchar namnet och har minst lika hög som en ModuleVersion, som `-MinimumVersion`-parameter. Om du vill importera en speciell version använder du parametern @ no__t-0 i stället.<br /><br /> Exempel: `ModuleVersion = '1.0'`|
|LED<br /><br /> Typ: sträng|GUID för automatiskt genererad|ID som används för att identifiera den här modulen unikt. Observera att du för närvarande inte kan importera en modul efter GUID.<br /><br /> Exempel: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|Skriver<br /><br /> Typ: sträng|Inga|Författare för den här modulen.<br /><br /> Exempel: `Author = 'AuthorNameHere'`|
|CompanyName<br /><br /> Typ: sträng|Okänt|Företaget eller leverantören för den här modulen.<br /><br /> Exempel: `CompanyName = 'Fabrikam'`|
|Copyright<br /><br /> Typ: sträng|(c) [currentYear] [Author]. Med ensamrätt.|Copyright-instruktion för den här modulen.<br /><br /> Exempel: `Copyright = '2016 AuthorName. All rights reserved.'`|
|Beskrivning<br /><br /> Typ: sträng|' '|Beskrivning av de funktioner som tillhandahålls av den här modulen.<br /><br /> Exempel: `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> Typ: sträng|' '|Lägsta version av Windows PowerShell-motorn som krävs för den här modulen. Aktuella giltiga värden är 1,0, 2,0, 3,0, 4,0 och 5,0.<br /><br /> Exempel: `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> Typ: sträng|' '|Anger namnet på Windows PowerShell-värden som krävs av modulen. Det här namnet tillhandahålls av Windows PowerShell. Om du vill hitta namnet på ett värd program skriver du följande i programmet: `$host.name`.<br /><br /> Exempel: `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> Typ: sträng|' '|Lägsta version av Windows PowerShell-värden som krävs för den här modulen.<br /><br /> Exempel: `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> Typ: sträng|' '|Lägsta version av Microsoft .NET Framework som krävs av den här modulen.<br /><br /> Exempel: `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> Typ: sträng|' '|Lägsta version av Common Language Runtime (CLR) som krävs för den här modulen.<br /><br /> Exempel: `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> Typ: sträng|' '|Processor arkitektur (ingen, x86, amd64) som krävs av den här modulen. Giltiga värden är x86, AMD64, IA64 och None (okänt eller ospecificerat).<br /><br /> Exempel: `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> Typ: [string []]|@()|Moduler som måste importeras till den globala miljön innan den här modulen importeras. Alla moduler som anges kommer att läsas in, om de inte redan har lästs in. (Vissa moduler kan till exempel redan läsas in av en annan modul.). Det är också möjligt att ange en angiven version som ska läsas in med hjälp av `RequiredVersion` i stället för `ModuleVersion`. När du använder `ModuleVersion` kommer det att läsa in den senaste versionen som är tillgänglig med minst den angivna versionen.<br /><br /> Exempel: `RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> Exempel: `RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> Typ: [string []]|@()|Sammansättningar som måste läsas in innan den här modulen importeras.<br /><br /> Observera att till skillnad från RequiredModules läser PowerShell in RequiredAssemblies om de inte redan har lästs in.|
|ScriptsToProcess<br /><br /> Typ: [string []]|@()|Skript (. ps1) filer som körs i anroparens sessionstillstånd när modulen importeras. Detta kan vara det globala sessionstillståndet eller, för kapslade moduler, sessionens tillstånd för en annan modul. Du kan använda dessa skript för att förbereda en miljö på samma sätt som du kan använda ett inloggnings skript.<br /><br /> Dessa skript körs innan någon av modulerna som anges i manifestet läses in.|
|TypesToProcess<br /><br /> Typ: [string []]|@()|Skriv filer (. ps1xml) som ska läsas in när du importerar den här modulen.|
|FormatsToProcess<br /><br /> Typ: [string []]|@()|Formatera filer (. ps1xml) som ska läsas in när modulen importeras.|
|NestedModules<br /><br /> Typ: [string []]|@()|Moduler som ska importeras som kapslade moduler i modulen som anges i RootModule/ModuleToProcess.<br /><br /> Att lägga till ett modulnamn i det här elementet liknar att anropa `Import-Module` inifrån ditt skript eller din sammansättnings kod. Den största skillnaden är att det är lättare att se vad du läser in här i manifest filen. Om en modul inte kan läsas in här, kommer du inte heller att ha läst in den faktiska modulen ännu.<br /><br /> Förutom andra moduler kan du också läsa in skript-filer (. ps1) här. De här filerna körs i kontexten för modulen root. (Detta motsvarar punkt ursprung i skriptet i modulen root.)|
|FunctionsToExport<br /><br /> Typ: [string []]|@()|Anger de funktioner som modulen exporterar (jokertecken tillåts men rekommenderas) till anroparens sessionstillstånd. Som standard exporteras inga funktioner. Du kan använda den här nyckeln för att visa en lista över de funktioner som exporteras av modulen.<br /><br /> Anroparens sessionstillstånd kan vara det globala sessionstillståndet eller, för kapslade moduler, sessionens tillstånd för en annan modul. Vid länkning av kapslade moduler exporteras alla funktioner som exporteras av en kapslad modul till det globala sessionstillståndet om inte en modul i kedjan begränsar funktionen med hjälp av FunctionsToExport-nyckeln.<br /><br /> Om manifestet även exporterar alias för funktionerna kan den här nyckeln ta bort funktioner vars alias visas i AliasesToExport-nyckeln, men den här nyckeln kan inte lägga till funktions Ali Aset i listan.|
|CmdletsToExport<br /><br /> Typ: [string []]|@()|Anger de cmdletar som modulen exporterar (jokertecken tillåts men rekommenderas). Som standard exporteras inga cmdletar. Du kan använda den här nyckeln för att visa en lista över de cmdletar som exporteras av modulen.<br /><br /> Anroparens sessionstillstånd kan vara det globala sessionstillståndet eller, för kapslade moduler, sessionens tillstånd för en annan modul. När du kedjar kapslade moduler exporteras alla cmdletar som exporteras av en kapslad modul till det globala sessionstillståndet, om inte en modul i kedjan begränsar cmdleten med hjälp av CmdletsToExport-nyckeln.<br /><br /> Om manifestet även exporterar alias för cmdletarna, kan den här nyckeln ta bort cmdletar vars alias visas i AliasesToExport-nyckeln, men den här nyckeln kan inte lägga till cmdlet-alias i listan.|
|VariablesToExport<br /><br /> Typ: sträng|'*'|Anger de variabler som modulen exporterar (jokertecken tillåts) till anroparens sessionstillstånd. Som standard exporteras alla variabler. Du kan använda den här nyckeln för att begränsa de variabler som exporteras av modulen.<br /><br /> Anroparens sessionstillstånd kan vara det globala sessionstillståndet eller, för kapslade moduler, sessionens tillstånd för en annan modul. När du kopplar kapslade moduler exporteras alla variabler som exporteras av en kapslad modul till det globala sessionstillståndet om inte en modul i kedjan begränsar variabeln med hjälp av VariablesToExport-nyckeln.<br /><br /> Om manifestet även exporterar alias för variablerna, kan den här nyckeln ta bort variabler vars alias visas i AliasesToExport-nyckeln, men den här nyckeln kan inte lägga till variabel Ali Aset i listan.|
|AliasesToExport<br /><br /> Typ: [string []]|@()|Anger de alias som modulen exporterar (jokertecken tillåts men rekommenderas) till anroparens sessionstillstånd. Som standard exporteras inga alias. Du kan använda den här nyckeln för att visa en lista över de alias som exporteras av modulen.<br /><br /> Anroparens sessionstillstånd kan vara det globala sessionstillståndet eller, för kapslade moduler, sessionens tillstånd för en annan modul. När du kedjar kapslade moduler exporteras alla alias som exporteras av en kapslad modul till det globala sessionstillståndet, om inte en modul i kedjan begränsar aliaset med hjälp av AliasesToExport-nyckeln.|
|ModuleList<br /><br /> Typ: [string []]|@()|Anger alla moduler som paketeras med den här modulen. Dessa moduler kan anges med namn (en kommaavgränsad sträng) eller som en hash-tabell med Modulnamn och GUID-nycklar. Hash-tabellen kan också ha en valfri ModuleVersion-nyckel. ModuleList-nyckeln är utformad för att fungera som en modul för inventering. De här modulerna bearbetas inte automatiskt.|
|FileList<br /><br /> Typ: [string []]|@()|Lista över alla filer som paketeras med den här modulen. Precis som med ModuleList är FileList att hjälpa dig som en inventerings lista och bearbetas inte på annat sätt.|
|PrivateData<br /><br /> Typ: [objekt]|@{...}|Anger eventuella privata data som måste skickas till den rotdomän som anges av nyckeln RootModule/ModuleToProcess.|
|HelpInfoURI<br /><br /> Typ: sträng|' '|HelpInfo-URI för den här modulen.|
|DefaultCommandPrefix<br /><br /> Typ: sträng|' '|Standardprefix för kommandon som exporteras från den här modulen. Åsidosätt standardprefixet med hjälp av `Import-Module`-prefix.|

## <a name="sample-module-manifest"></a>Manifest för exempel modul

I följande exempel på modul visas nycklar och standardvärden i ett modul manifest. Det här exemplet skapades med hjälp av cmdleten `New-ModuleManifest` i Windows PowerShell 3,0. När du skapar flera moduler kan du använda denna cmdlet för att skapa en manifest-mall som sedan kan ändras för olika moduler.

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 2019-10-09
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'b888e5a2-8578-4c0b-938d-0cd9b5b836ba'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2019 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
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

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-modul](./writing-a-windows-powershell-module.md)
