---
title: Hur du skriver ett Manifest för PowerShell-modulen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 93a8c11099a9883127bca87422e1acaebfd2c093
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082308"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>Skriva ett PowerShell-modulmanifest

Du har en gång skrivit din Windows PowerShell-modul, du kan du lägga till ett modulmanifest. Ett modulmanifest är en PowerShell-skriptfil som du kan använda med information om modulen. Du kan till exempel beskriver författaren, ange filer i modulen (till exempel kapslade moduler), köra skript för att anpassa användarens miljö, typ och formateras, definiera systemkrav och begränsa de medlemmar som modulen exporterar.

## <a name="creating-a-module-manifest"></a>Skapa ett modulmanifest

En *modulmanifestet* är en Windows PowerShell-datafil (.psd1) som beskriver innehållet i en modul och avgör hur en modul har bearbetats. Manifestfilen själva är en textfil som innehåller en hash-tabell över nycklar och värden. Du kan länka en manifestfil till en modul genom att namnge det samma som modulen och placera den i roten av modul-katalog.

För enkel moduler som innehåller en enda .psm1 eller binär sammansättningen är ett modulmanifest valfritt. Det rekommenderas dock att du använder ett modulmanifest när det är möjligt eftersom de är användbara för att organisera din kod och underhålla versionsinformation. Ett modulmanifest är dessutom krävs för att exportera en sammansättning som är installerad i den globala sammansättningscachen. Ett modulmanifest krävs också för moduler som har stöd för uppdateringsbar hjälp-funktionen. Det vill säga uppdateringsbar hjälp använder den **HelpInfoUri** nyckeln i modulmanifestet att hitta hjälpfilen information (HelpInfo XML) som innehåller platsen för de uppdaterade hjälpfilerna för modulen. Mer information om uppdateringsbar hjälp finns i [stöd för uppdateringsbar hjälp](./supporting-updatable-help.md).

### <a name="to-create-and-use-a-module-manifest"></a>Du skapar och använder ett modulmanifest

1. Om du vill skapa ett modulmanifest, har du flera alternativ:

   1. Direkt skapa hash-tabellen med minimal informationen som krävs och spara den till en .psd1-fil som har samma namn som din modul. När du har gjort det, kan du öppna filen och lägga till i lämpliga värden manuellt.

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. Eller Ring den [New ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet, med en eller flera standardvärden skickas som parametrar. (Observera att den endast filens namn krävs för att generera ett manifest, men.) Detta skapar ett modulmanifest med alla manifest värden du angav inget uttryckligen anges och resten som innehåller lämpligt standardvärde.

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. Slutligen kan du också skapa en tom .psd1-fil och kopiera mallen längst ned i det här avsnittet i filen och Fyll i relevanta värden. Endast verkliga krav är i det här fallet att se till att filen har samma namn som modulen.

2. Lägg till i övriga element i manifest som du vill ha i filen.

   Generellt sett görs detta förmodligen i den textredigerare som du föredrar, till exempel Anteckningar. Men det är tekniskt sett en skriptfil som innehåller kod, så kan du redigera den i en faktiska skript- eller utvecklingsmiljö, till exempel PowerShell ISE. Igen, Observera att alla element i en manifestfil är valfritt, förutom ModuleVersion-nummer.

   Beskrivningar av nycklar och värden som du kan ha i ett modulmanifest finns i den **modulen Manifest element** nedan. Mer information finns i parametern beskrivningarna i den [New ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet.

3. Alternativt kan du lägga till ytterligare kod till din modulmanifestet att åtgärda alla scenarier som inte omfattas av Basmodul manifest element.

   Av säkerhetsskäl körs PowerShell bara en liten delmängd av de tillgängliga åtgärderna i en modul manifestfil. I allmänhet bör du använda den **om** instruktionen, aritmetiska och jämförelse operatorer och grundläggande PowerShell-datatyper.

4. När du har skapat din modulmanifestet kan du testa den (för att bekräfta att alla sökvägar som beskrivs i manifestet är korrigera) med ett anrop till [Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest).

   `Test-ModuleManifest myModuleName.psd1`

5. Var noga med att din modulmanifestet finns i den översta nivån i den katalog som innehåller din modul.

   När du kopierar din modul på ett system och importera den, använder PowerShell modulmanifestet för att importera din modul.

6. Du kan också du kan testa din modulmanifestet med ett anrop till direkt [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) av dot-källa manifestet själva.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Modulen Manifest element

I följande tabell beskrivs de element som du kan ha i ett modulmanifest

|Element|Standard|Beskrivning|
|-------------|-------------|-----------------|
|RootModule<br /><br /> Typ: sträng|' '|Modulen eller binär modulen skriptfilen som är associerade med den här manifestet. Tidigare versioner av PowerShell kallas det här elementet i ModuleToProcess.<br /><br /> Möjliga typer för rot-modulen kan vara tom (som kommer att göra detta en **Manifest** modulen), namnet på en skriptmodul (.psm1, vilket gör detta en **skriptet** modulen), eller namnet på en binär modul (.exe eller .dll, som har en **binära** modul). Placera namnet på ett modulmanifest (.psd1) eller en skriptfil (.ps1) i det här elementet genereras ett fel inträffar.|
|ModuleVersion<br /><br /> Typ: sträng|1.0|Versionsnumret för den här modulen. Strängen måste kunna konverteras till [System.Version]. Det vill säga ' #. #. #. #. #'. `Import-Module` läser in den första modulen som hittas på den **$psModulePath** som matchar namnet och har minst så mycket ett ModuleVersion som den `-MinimumVersion` parametern. Om du vill importera en specifik version, använda den`-RequiredVersion` parameter, i stället.<br /><br /> Exempel: `ModuleVersion = '1.0'`|
|GUID<br /><br /> Typ: sträng|Automatiskt skapade GUID|ID som används för att identifiera den här modulen. Observera att du för närvarande inte kan importera en modul med GUID.<br /><br /> Exempel: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|Författare<br /><br /> Typ: sträng|Inga|Författare till den här modulen.<br /><br /> Exempel: `Author = 'AuthorNameHere'`|
|CompanyName<br /><br /> Typ: sträng|Okänt|Företags- eller leverantören av den här modulen.<br /><br /> Exempel: `CompanyName = 'Fabrikam'`|
|Copyright<br /><br /> Typ: sträng|(c) [currentYear] [redigera]. Med ensamrätt.|Om upphovsrätt för den här modulen.<br /><br /> Exempel: `Copyright = '2016 AuthorName. All rights reserved.'`|
|Beskrivning<br /><br /> Typ: sträng|' '|Beskrivning av funktionerna i den här modulen.<br /><br /> Exempel: `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> Typ: sträng|' '|Lägsta version av Windows PowerShell-motorn som krävs av den här modulen. Aktuella giltiga värden är 1.0, 2.0, 3.0, 4.0 och 5.0.<br /><br /> Exempel: `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> Typ: sträng|' '|Anger namnet på Windows PowerShell-värden som krävs av modulen. Det här namnet kommer från Windows PowerShell. För att hitta namnet på en värdprogram i programmet, skriver du: `$host.name` .<br /><br /> Exempel: `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> Typ: sträng|' '|Lägsta version av Windows PowerShell-värden som krävs av den här modulen.<br /><br /> Exempel: `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> Typ: sträng|' '|Lägsta version av Microsoft .NET Framework krävs av den här modulen.<br /><br /> Exempel: `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> Typ: sträng|' '|Lägsta version av common language runtime (CLR) krävs av den här modulen.<br /><br /> Exempel: `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> Typ: sträng|' '|Processorarkitektur (ingen, X86, Amd64) krävs av den här modulen. Giltiga värden är x86 AMD64 IA64, och inget (okänt eller odefinierat).<br /><br /> Exempel: `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> Typ: [string []]|@()|Moduler som måste importeras till den globala miljön innan du importerar den här modulen. Alla moduler som anges, såvida inte har redan lästs in läses in. (Till exempel vissa moduler kan redan läsas av en annan modul.). Det är också möjligt att ange en specifik version att läsa in med hjälp av `RequiredVersion` snarare än `ModuleVersion`. När du använder `ModuleVersion` det laddas den senaste versionen som är tillgängliga med ett minimum på den angivna versionen.<br /><br /> Exempel: `RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> Exempel: `RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> Typ: [string []]|@()|Sammansättningar som måste läsas innan du importerar den här modulen.<br /><br /> Observera att till skillnad från RequiredModules, PowerShell att läsa in RequiredAssemblies om de inte redan lästs in.|
|ScriptsToProcess<br /><br /> Typ: [string []]|@()|(.Ps1) skriptfiler som körs i uppringarens sessionstillstånd när modulen har importerats. Detta kan vara den globala sessionen tillstånd eller, för kapslade moduler, sessionstillstånd för en annan modul. Du kan använda skripten för att förbereda en miljö, precis som du använder ett inloggningsskript.<br /><br /> Dessa skript körs innan någon av de moduler som anges i manifestet har lästs in.|
|TypesToProcess<br /><br /> Type: [Object[]]|@()|Skriv filer (.ps1xml) som ska läsas in när du importerar den här modulen.|
|FormatsToProcess<br /><br /> Type: [Object[]]|@()|Formatera filer (.ps1xml) som ska läsas in när du importerar den här modulen.|
|NestedModules<br /><br /> Type: [Object[]]|@()|Moduler för att importera som kapslade moduler i den modul som anges i RootModule/ModuleToProcess.<br /><br /> Att lägga till ett Modulnamn i det här elementet påminner om att anropa `Import-Module` från i din kod med skript eller sammansättningen. Den största skillnaden är att det är lättare att se vad du läser in här i manifestfilen. Även om det inte går att läsa in här en modul, du kommer inte ännu har läst in dina faktiska modulen.<br /><br /> Förutom andra moduler kan du även läsa in (.ps1) skriptfiler hit. Dessa filer körs i kontexten för rot-modulen. (Detta motsvarar punkt sourcing skriptet i din rotmodul.)|
|FunctionsToExport<br /><br /> Typ: Sträng|'*'|Anger de funktioner som modulen exporterar (jokertecken tecken tillåts) anroparens sessionstillstånd. Som standard exporteras alla funktioner. Du kan använda den här nyckeln för att begränsa funktionerna som exporteras av modulen.<br /><br /> Uppringarens sessionstillstånd kan vara den globala sessionen tillstånd eller, för kapslade moduler, sessionstillstånd för en annan modul. När länkning kapslade moduler, kommer alla funktioner som exporteras av en kapslad modul att exporteras till globala sessionens tillstånd om inte en modul i kedjan begränsar funktionen med hjälp av FunctionsToExport-nyckeln.<br /><br /> Om manifestet exporterar också alias för, den här nyckeln kan ta bort funktioner vars alias listas i nyckeln AliasesToExport, men den här nyckeln kan inte lägga till funktionsalias i listan.|
|CmdletsToExport<br /><br /> Typ: Sträng|'*'|Anger de cmdletar som modulen exporterar (jokertecken tecken tillåts). Som standard exporteras alla cmdletar. Du kan använda den här nyckeln för att begränsa de cmdletar som exporteras av modulen.<br /><br /> Uppringarens sessionstillstånd kan vara den globala sessionen tillstånd eller, för kapslade moduler, sessionstillstånd för en annan modul. När du länkning kapslade moduler exporteras alla cmdletar som exporteras av en kapslad modul slutligen till globala sessionens tillstånd om inte en modul i kedjan begränsar cmdlet: en med hjälp av CmdletsToExport-nyckeln.<br /><br /> Om manifestet exporterar också alias för cmdlets, den här nyckeln kan ta bort cmdletar vars alias listas i nyckeln AliasesToExport, men den här nyckeln kan inte lägga till cmdlet-alias i listan.|
|VariablesToExport<br /><br /> Typ: Sträng|'*'|Anger de variabler som modulen exporterar (jokertecken tecken tillåts) anroparens sessionstillstånd. Som standard exporteras alla variabler. Du kan använda den här nyckeln för att begränsa de variabler som exporteras av modulen.<br /><br /> Uppringarens sessionstillstånd kan vara den globala sessionen tillstånd eller, för kapslade moduler, sessionstillstånd för en annan modul. När du länkning kapslade moduler, kommer alla variabler som exporteras av en kapslad modul att exporteras till globala sessionens tillstånd om inte en modul i kedjan begränsar variabeln med hjälp av VariablesToExport-nyckeln.<br /><br /> Om manifestet exporterar också alias för för variablerna, den här nyckeln kan ta bort variabler vars alias listas i nyckeln AliasesToExport, men den här nyckeln kan inte lägga till variabeln alias i listan.|
|AliasesToExport<br /><br /> Typ: Sträng|'*'|Anger alias som modulen exporterar (jokertecken tecken tillåts) anroparens sessionstillstånd. Som standard exporteras alla alias. Du kan använda den här nyckeln för att begränsa de alias som exporteras av modulen.<br /><br /> Uppringarens sessionstillstånd kan vara den globala sessionen tillstånd eller, för kapslade moduler, sessionstillstånd för en annan modul. När du länkning kapslade moduler exporteras alla alias som exporteras av en kapslad modul slutligen till globala sessionens tillstånd om inte en modul i kedjan begränsar alias med hjälp av AliasesToExport-nyckeln.|
|ModuleList<br /><br /> Typ: [string []]|@()|Anger alla moduler som är packade med den här modulen. Dessa moduler kan anges efter namn (en kommaavgränsad sträng) eller som en hashtabell med ModuleName och GUID-nycklar. Hash-tabellen kan också ha en valfri ModuleVersion-nyckel. Nyckeln ModuleList är utformade att fungera som en modul inventering. Dessa moduler bearbetas inte automatiskt.|
|FileList<br /><br /> Typ: [string []]|@()|Lista över alla filer som är späckad med den här modulen. Som med ModuleList, FileList är att hjälpa dig som en lagerlista och annars bearbetas inte.|
|PrivateData<br /><br /> Typ: [objekt]|' '|Anger alla privata data som ska skickas till rotmodul som anges av nyckeln RootModule/ModuleToProcess.|
|HelpInfoURI<br /><br /> Typ: sträng|' '|HelpInfo URI för den här modulen.|
|DefaultCommandPrefix<br /><br /> Typ: sträng|' '|Standardprefix för kommandon som exporteras från den här modulen. Åsidosätt standard prefix med `Import-Module` -Prefix.|

## <a name="sample-module-manifest"></a>Exemplet Modulmanifestet

Följande exempel modulmanifestet visar nycklar och standardvärden i ett modulmanifest. Det här exemplet har skapats med hjälp av den `New-ModuleManifest` cmdlet i Windows PowerShell 3.0. När du skapar flera moduler kan använda du denna cmdlet för att skapa ett manifest mall som sedan kan ändras för olika moduler.

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 1/24/2012
#

@{

# Script module or binary module file associated with this manifest
#RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = 'd0a9150d-b6a4-4b17-a325-e3a24fed0aa9'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2012 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of the .NET Framework required by this module
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module
FunctionsToExport = '*'

# Cmdlets to export from this module
CmdletsToExport = '*'

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module
AliasesToExport = '*'

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess
# PrivateData = ''

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>Se även

[Skriva ett Windows PowerShell-modul](./writing-a-windows-powershell-module.md)
