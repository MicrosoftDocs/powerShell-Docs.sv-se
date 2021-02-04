---
ms.date: 01/04/2021
ms.topic: reference
title: Skriva ett PowerShell-modulmanifest
description: Skriva ett PowerShell-modulmanifest
ms.openlocfilehash: 8c644391008cb97c1206f985f0f5eca9d7dfcc9e
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97879379"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>Så här skriver du ett manifest för PowerShell-modul

När du har skrivit din PowerShell-modul kan du lägga till ett valfritt modul manifest som innehåller information om modulen. Du kan till exempel beskriva författaren, ange filer i modulen (t. ex. kapslade moduler), köra skript för att anpassa användarens miljö, läsa in typ av format och formatera filer, definiera system krav och begränsa de medlemmar som modulen exporterar.

## <a name="creating-a-module-manifest"></a>Skapa ett modul manifest

Ett **modul manifest** är en PowerShell-datafil ( `.psd1` ) som beskriver innehållet i en modul och bestämmer hur en modul bearbetas. Manifest filen är en textfil som innehåller en hash-tabell med nycklar och värden. Du länkar en manifest fil till en modul genom att namnge manifestet på samma sätt som modulen och lagra manifestet i modulens rot Katalog.

För enkla moduler som bara innehåller en enda `.psm1` eller binär sammansättning, är ett modul-manifest valfritt. Men rekommendationen är att använda ett modul manifest närhelst det är möjligt, eftersom de är användbara för att hjälpa dig att organisera din kod och underhålla versions information. Dessutom krävs ett modul manifest för att exportera en sammansättning som är installerad i den [globala sammansättningscachen](/dotnet/framework/app-domains/gac). Ett modul manifest krävs också för moduler som stöder den uppdaterbara hjälp funktionen. Uppdaterings bara hjälp använder **HelpInfoUri** -nyckeln i modulen manifest för att hitta hjälp information (HelpInfo XML) som innehåller platsen för de uppdaterade hjälpfilerna för modulen. Mer information om uppdaterings bar hjälp finns i [support uppdaterings bara hjälp](./supporting-updatable-help.md).

### <a name="to-create-and-use-a-module-manifest"></a>Skapa och använda ett modul manifest

1. Det bästa sättet att skapa ett modul manifest är att använda cmdleten [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) . Du kan använda parametrar för att ange ett eller flera av Manifestets standard nycklar och värden. Det enda kravet är att ge filen ett namn. `New-ModuleManifest` skapar ett modul manifest med dina angivna värden och innehåller återstående nycklar och standardvärden. Om du behöver skapa flera moduler använder `New-ModuleManifest` du för att skapa en modul manifest-mall som kan ändras för dina olika moduler. Ett exempel på ett manifest för en standardmodul finns i [exemplet på modulen manifest](#sample-module-manifest).

   `New-ModuleManifest -Path C:\myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   Ett alternativ är att manuellt skapa modul Manifestets hash-tabell med minsta möjliga information som krävs, **ModuleVersion**. Du sparar filen med samma namn som modulen och använder `.psd1` fil namns tillägget. Du kan sedan redigera filen och lägga till lämpliga nycklar och värden.

1. Lägg till ytterligare element som du vill ha i manifest filen.

   Redigera manifest filen med valfri text redigerare som du föredrar. Men manifest filen är en skript fil som innehåller kod, så du kanske vill redigera den i en skript-eller utvecklings miljö, t. ex. Visual Studio Code. Alla element i en manifest fil är valfria, förutom **ModuleVersion** -numret.

   Beskrivningar av nycklar och värden som du kan inkludera i ett modul manifest finns i tabellen [modul manifest element](#module-manifest-elements) . Mer information finns i parameter beskrivningar i cmdleten [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) .

1. Om du vill åtgärda scenarier som kanske inte omfattas av manifest elementen för Bask module har du möjlighet att lägga till ytterligare kod i manifestet för modulen.

   Av säkerhets skäl kör PowerShell bara en liten delmängd av de tillgängliga åtgärderna i en modul manifest fil. I allmänhet kan du använda `if` instruktionen satser, aritmetiska och jämförelse operatorer och Basic PowerShell-datatyper.

1. När du har skapat modulen manifest kan du testa den för att bekräfta att alla sökvägar som beskrivs i manifestet är korrekta. Om du vill testa manifestet för modulen använder du [test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest).

   `Test-ModuleManifest myModuleName.psd1`

1. Se till att modul manifestet finns på den översta nivån i katalogen som innehåller modulen.

   När du kopierar modulen till ett system och importerar den, använder PowerShell modulen manifest för att importera modulen.

1. Alternativt kan du direkt testa modul manifestet med ett anrop till [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) med punkt-källa själva manifestet.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Modul manifest element

I följande tabell beskrivs de element som du kan inkludera i ett modul manifest.

|Element|Standardvärde|Description|
|-------------|-------------|-----------------|
|**RootModule**<br /> Bastyp `String`|`<empty string>`|Skriptbaserad modul eller binär modul som är associerad med det här manifestet. Tidigare versioner av PowerShell anropade det här elementet som **ModuleToProcess**.<br /> Möjliga typer för rotnoden kan vara tomma, vilket skapar en **manifest** -modul, namnet på en skript-modul ( `.psm1` ) eller namnet på en binär modul ( `.exe` eller `.dll` ). Att placera namnet på ett modul manifest ( `.psd1` ) eller en skript fil ( `.ps1` ) i det här elementet orsakar ett fel. <br /> Exempel: `RootModule = 'ScriptModule.psm1'`|
|**ModuleVersion**<br /> Bastyp `Version`|`'0.0.1'`|Versions nummer för den här modulen. Om ett värde inte anges används standardvärdet `New-ModuleManifest`   . Strängen måste kunna konvertera till typen till `Version` exempel `#.#.#.#.#` . `Import-Module` läser in den första modul som den hittar på den **$PSModulePath** som matchar namnet och har minst lika hög som en **ModuleVersion**, som **MinimumVersion** -parameter. Om du vill importera en version använder du `Import-Module` cmdlet: en **RequiredVersion** -parameter.<br /> Exempel: `ModuleVersion = '1.0'`|
|**LED**<br /> Bastyp `GUID`|`'<GUID>'`|ID som används för att identifiera den här modulen unikt. Om ett värde inte anges `New-ModuleManifest` genererar automatiskt värdet. Du kan för närvarande inte importera en modul efter **GUID**. <br /> Exempel: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|**Författare**<br /> Bastyp `String`|`'<Current user>'`|Författare för den här modulen. Om ett värde inte anges `New-ModuleManifest` använder den aktuella användaren. <br /> Exempel: `Author = 'AuthorNameHere'`|
|**CompanyName**<br /> Bastyp `String`|`'Unknown'`|Företaget eller leverantören för den här modulen. Om ett värde inte anges används standardvärdet `New-ModuleManifest` .<br /> Exempel: `CompanyName = 'Fabrikam'`|
|**Material**<br /> Bastyp `String`|`'(c) <Author>. All rights reserved.'`| Copyright-instruktion för den här modulen. Om ett värde inte anges används standardvärdet för `New-ModuleManifest` den aktuella användaren som `<Author>` . Om du vill ange en författare använder du parametern **Author** . <br /> Exempel: `Copyright = '2019 AuthorName. All rights reserved.'`|
|**Beskrivning**<br /> Bastyp `String`|`<empty string>`|Beskrivning av de funktioner som tillhandahålls av den här modulen.<br /> Exempel: `Description = 'This is the module's description.'`|
|**PowerShellVersion**<br /> Bastyp `Version`|`<empty string>`|Lägsta version av PowerShell-motorn som krävs av den här modulen. Giltiga värden är 1,0, 2,0, 3,0, 4,0, 5,0, 5,1, 6,0, 6,1, 6,2, 7,0 och 7,1.<br /> Exempel: `PowerShellVersion = '5.0'`|
|**PowerShellHostName**<br /> Bastyp `String`|`<empty string>`|Namnet på PowerShell-värden som krävs av den här modulen. Det här namnet tillhandahålls av PowerShell. Om du vill hitta namnet på ett värd program skriver du följande i programmet: `$host.name` .<br /> Exempel: `PowerShellHostName = 'ConsoleHost'`|
|**PowerShellHostVersion**<br /> Bastyp `Version`|`<empty string>`|Lägsta version av PowerShell-värden som krävs av den här modulen.<br /> Exempel: `PowerShellHostVersion = '2.0'`|
|**DotNetFrameworkVersion**<br /> Bastyp `Version`|`<empty string>`|Lägsta version av Microsoft .NET Framework som krävs av den här modulen. Den här förutsättningen gäller endast för PowerShell Desktop Edition, till exempel PowerShell 5,1.<br /> Exempel: `DotNetFrameworkVersion = '3.5'`|
|**CLRVersion**<br /> Bastyp `Version`|`<empty string>`|Lägsta version av Common Language Runtime (CLR) som krävs för den här modulen. Den här förutsättningen gäller endast för PowerShell Desktop Edition, till exempel PowerShell 5,1.<br /> Exempel: `CLRVersion = '3.5'`|
|**ProcessorArchitecture**<br /> Bastyp `ProcessorArchitecture`|`<empty string>`|Processor arkitektur (ingen, x86, amd64) som krävs av den här modulen. Giltiga värden är x86, AMD64, arm, IA64, MSIL och None (okänd eller ospecificerad).<br /> Exempel: `ProcessorArchitecture = 'x86'`|
|**RequiredModules**<br /> Bastyp `Object[]`|`@()`|Moduler som måste importeras till den globala miljön innan den här modulen importeras. Detta laddar alla moduler som anges om de inte redan har lästs in. Till exempel kanske vissa moduler redan har lästs in av en annan modul. Det är möjligt att ange en angiven version som ska läsas in med `RequiredVersion` i stället för `ModuleVersion` . När `ModuleVersion` används läser det in den senaste versionen som är tillgänglig med minst den angivna versionen. Du kan kombinera strängar och hash-tabeller i parametervärdet.<br /> Exempel: `RequiredModules = @("MyModule", @{ModuleName="MyDependentModule"; ModuleVersion="2.0"; GUID="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /> Exempel: `RequiredModules = @("MyModule", @{ModuleName="MyDependentModule"; RequiredVersion="1.5"; GUID="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|**RequiredAssemblies**<br /> Bastyp `String[]`|`@()`|Sammansättningar som måste läsas in innan den här modulen importeras. Anger de sammansättnings `.dll` fil namn () som modulen kräver.<br /> PowerShell läser in de angivna sammansättningarna innan du uppdaterar typer eller format, importerar kapslade moduler eller importerar filen som anges i värdet för nyckeln RootModule. Använd den här parametern för att visa en lista över alla sammansättningar som modulen kräver.<br /> Exempel: `RequiredAssemblies = @("assembly1.dll", "assembly2.dll", "assembly3.dll")`|
|**ScriptsToProcess**<br /> Bastyp `String[]`|`@()`|Skript ( `.ps1` ) filer som körs i anroparens sessionstillstånd när modulen importeras. Detta kan vara det globala sessionstillståndet eller, för kapslade moduler, sessionens tillstånd för en annan modul. Du kan använda dessa skript för att förbereda en miljö på samma sätt som du kan använda ett inloggnings skript.<br /> Dessa skript körs innan någon av modulerna som anges i manifestet läses in. <br /> Exempel: `ScriptsToProcess = @("script1.ps1", "script2.ps1", "script3.ps1")`|
|**TypesToProcess**<br /> Bastyp `String[]`|`@()`|Skriv filer ( `.ps1xml` ) som ska läsas in när du importerar den här modulen. <br /> Exempel: `TypesToProcess = @("type1.ps1xml", "type2.ps1xml", "type3.ps1xml")`|
|**FormatsToProcess**<br /> Bastyp `String[]`|`@()`|Formatera filer ( `.ps1xml` ) som ska läsas in när modulen importeras. <br /> Exempel: `FormatsToProcess = @("format1.ps1xml", "format2.ps1xml", "format3.ps1xml")`|
|**NestedModules**<br /> Bastyp `Object[]`|`@()`|Moduler som ska importeras som kapslade moduler i modulen som anges i **RootModule** (alias:**ModuleToProcess**).<br /> Att lägga till ett modulnamn i det här elementet liknar att anropa inifrån `Import-Module` ditt skript eller din sammansättnings kod. Den största skillnaden genom att använda en manifest fil är att det är enklare att se vad du läser in. Och om en modul inte kan läsas in så har du inte läst in den faktiska modulen ännu.<br /> Förutom andra moduler kan du även läsa in skript ()- `.ps1` filer här. De här filerna körs i kontexten för modulen root. Detta motsvarar punkt källa i skriptet i modulen root. <br /> Exempel: `NestedModules = @("script.ps1", @{ModuleName="MyModule"; ModuleVersion="1.0.0.0"; GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"})`|
|**FunctionsToExport**<br /> Bastyp `String[]`|`@()`|Anger vilka funktioner som ska exporteras från den här modulen, för bästa prestanda, Använd inte jokertecken och ta inte bort posten, Använd en tom matris om det inte finns några funktioner att exportera. Som standard exporteras inga funktioner. Du kan använda den här nyckeln för att visa en lista över de funktioner som exporteras av modulen.<br /> Modulen exporterar funktionerna till anroparens sessionstillstånd. Anroparens sessionstillstånd kan vara det globala sessionstillståndet eller, för kapslade moduler, sessionens tillstånd för en annan modul. Vid länkning av kapslade moduler exporteras alla funktioner som exporteras av en kapslad modul till det globala sessionstillståndet om inte en modul i kedjan begränsar funktionen med hjälp av **FunctionsToExport** -nyckeln.<br /> Om manifestet exporterar alias för funktionerna kan den här nyckeln ta bort funktioner vars alias visas i **AliasesToExport** -nyckeln, men den här nyckeln kan inte lägga till funktions Ali Aset i listan. <br /> Exempel: `FunctionsToExport = @("function1", "function2", "function3")`|
|**CmdletsToExport**<br /> Bastyp `String[]`|`@()`|Anger vilka cmdlet: ar som ska exporteras från den här modulen för bästa prestanda, Använd inte jokertecken och ta inte bort posten, Använd en tom matris om det inte finns några cmdlets att exportera. Som standard exporteras inga cmdletar. Du kan använda den här nyckeln för att visa en lista över de cmdletar som exporteras av modulen.<br /> Anroparens sessionstillstånd kan vara det globala sessionstillståndet eller, för kapslade moduler, sessionens tillstånd för en annan modul. När du kedjar kapslade moduler exporteras alla cmdletar som exporteras av en kapslad modul till det globala sessionstillståndet om inte en modul i kedjan begränsar cmdleten med hjälp av **CmdletsToExport** -nyckeln.<br /> Om manifestet exporterar alias för cmdletarna, kan den här nyckeln ta bort cmdletar vars alias visas i **AliasesToExport** -nyckeln, men den här nyckeln kan inte lägga till cmdlet-alias i listan. <br /> Exempel: `CmdletsToExport = @("Get-MyCmdlet", "Set-MyCmdlet", "Test-MyCmdlet")`|
|**VariablesToExport**<br /> Bastyp `String[]`|`'*'`|Anger de variabler som modulen exporterar till anroparens sessionstillstånd. Jokertecken är tillåtna. Som standard exporteras alla variabler ( `'*'` ). Du kan använda den här nyckeln för att begränsa de variabler som exporteras av modulen.<br /> Anroparens sessionstillstånd kan vara det globala sessionstillståndet eller, för kapslade moduler, sessionens tillstånd för en annan modul. När du kopplar kapslade moduler exporteras alla variabler som exporteras av en kapslad modul till det globala sessionstillståndet om inte en modul i kedjan begränsar variabeln med hjälp av **VariablesToExport** -nyckeln.<br /> Om manifestet även exporterar alias för variablerna, kan den här nyckeln ta bort variabler vars alias visas i **AliasesToExport** -nyckeln, men den här nyckeln kan inte lägga till variabel Ali Aset i listan. <br /> Exempel: `VariablesToExport = @('$MyVariable1', '$MyVariable2', '$MyVariable3')`|
|**AliasesToExport**<br /> Bastyp `String[]`|`@()`|Anger de alias som ska exporteras från den här modulen, för bästa prestanda, Använd inte jokertecken och ta inte bort posten, Använd en tom matris om det inte finns några alias att exportera. Som standard exporteras inga alias. Du kan använda den här nyckeln för att visa en lista över de alias som exporteras av modulen.<br /> Modulen exporterar alias till anroparens sessionstillstånd. Anroparens sessionstillstånd kan vara det globala sessionstillståndet eller, för kapslade moduler, sessionens tillstånd för en annan modul. När du kedjar kapslade moduler exporteras alla alias som exporteras av en kapslad modul till det globala sessionstillståndet, om inte en modul i kedjan begränsar aliaset med hjälp av **AliasesToExport** -nyckeln. <br /> Exempel: `AliasesToExport = @("MyAlias1", "MyAlias2", "MyAlias3")`|
|**DscResourcesToExport**<br /> Bastyp `String[]`|`@()`|Anger DSC-resurser som ska exporteras från den här modulen. Jokertecken är tillåtna. <br /> Exempel: `DscResourcesToExport = @("DscResource1", "DscResource2", "DscResource3")`|
|**ModuleList**<br /> Bastyp `Object[]`|`@()`|Anger alla moduler som paketeras med den här modulen. Dessa moduler kan anges med namn, med hjälp av en kommaavgränsad sträng eller som en hash-tabell med **Modulnamn** och **GUID** -nycklar. Hash-tabellen kan också ha en valfri **ModuleVersion** -nyckel. **ModuleList** -nyckeln är utformad för att fungera som en modul för inventering. De här modulerna bearbetas inte automatiskt. <br /> Exempel: `ModuleList = @("SampleModule", "MyModule", @{ModuleName="MyModule"; ModuleVersion="1.0.0.0"; GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"})`|
|**FileList**<br /> Bastyp `String[]`|`@()`|Lista över alla filer som paketeras med den här modulen. Precis som med **ModuleList** är **filelist** en inventerings lista och bearbetas inte på annat sätt. <br /> Exempel: `FileList = @("File1", "File2", "File3")`|
|**PrivateData**<br /> Bastyp `Object`|`@{...}`|Anger eventuella privata data som måste skickas till den rotdomän som anges av nyckeln **RootModule** (alias: **ModuleToProcess**). **PrivateData** är en hash-tabell som består av flera element: **taggar**, **LicenseUri**, **ProjectURI**, **IconUri**, **releasenotes**, för **hands version**, **RequireLicenseAcceptance** och **ExternalModuleDependencies**. |
|**Taggar** <br /> Bastyp `String[]` |`@()`| Taggar hjälp med modul identifiering i online-gallerier. <br /> Exempel: `Tags = "PackageManagement", "PowerShell", "Manifest"`|
|**LicenseUri**<br /> Bastyp `Uri` |`<empty string>`| En URL till licensen för den här modulen. <br /> Exempel: `LicenseUri = 'https://www.contoso.com/license'`|
|**ProjectUri**<br /> Bastyp `Uri` |`<empty string>`| En URL till den huvudsakliga webbplatsen för projektet. <br /> Exempel: `ProjectUri = 'https://www.contoso.com/project'`|
|**IconUri**<br /> Bastyp `Uri` |`<empty string>`| En URL till en ikon som representerar den här modulen. <br /> Exempel: `IconUri = 'https://www.contoso.com/icons/icon.png'`|
|**ReleaseNotes**<br /> Bastyp `String` |`<empty string>`| Anger modulens versions information. <br /> Exempel: `ReleaseNotes = 'The release notes provide information about the module.`|
|**Hands**<br /> Bastyp `String` |`<empty string>`| Den här parametern har lagts till i PowerShellGet 1.6.6. En för **hands** versions sträng som identifierar modulen som en för hands version i online-gallerier. <br /> Exempel: `PreRelease = 'This module is a prerelease version.`|
|**RequireLicenseAcceptance**<br /> Bastyp `Boolean`|`$true`| Den här parametern har lagts till i PowerShellGet 1,5. Flagga för att ange om modulen kräver explicit användar godkännande för installation, uppdatering eller Spara. <br /> Exempel: `RequireLicenseAcceptance = $false`|
|**ExternalModuleDependencies**<br /> Bastyp `String[]` |`@()`| Den här parametern har lagts till i PowerShellGet v2. En lista över externa moduler som den här modulen är beroende av. <br /> Exempel: `ExternalModuleDependencies =  @("ExtModule1", "ExtModule2", "ExtModule3")`|
|**HelpInfoURI**<br /> Bastyp `String`|`<empty string>`|HelpInfo-URI för den här modulen. <br /> Exempel: `HelpInfoURI = 'https://www.contoso.com/help'`|
|**DefaultCommandPrefix**<br /> Bastyp `String`|`<empty string>`|Standardprefix för kommandon som exporteras från den här modulen. Åsidosätt standardprefixet med `Import-Module -Prefix` . <br /> Exempel: `DefaultCommandPrefix = 'My'`|

## <a name="sample-module-manifest"></a>Manifest för exempel modul

Följande exempel manifest har skapats med `New-ModuleManifest` i PowerShell 7 och innehåller standard nycklar och-värden.

```powershell
#
# Module manifest for module 'SampleModuleManifest'
#
# Generated by: User01
#
# Generated on: 10/15/2019
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '0.0.1'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'b632e90c-df3d-4340-9f6c-3b832646bf87'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) User01. All rights reserved.'

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
        RequireLicenseAcceptance = $true

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

## <a name="see-also"></a>Se även

[about_Comparison_Operators](/powershell/module/microsoft.powershell.core/about/about_comparison_operators)

[about_If](/powershell/module/microsoft.powershell.core/about/about_if)

[Global Assembly Cache](/dotnet/framework/app-domains/gac)

[Importera-modul](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[New-ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest)

[Test-ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest)

[Uppdatera – ModuleManifest](/powershell/module/powershellget/update-modulemanifest)

[Skriva en Windows PowerShell-modul](./writing-a-windows-powershell-module.md)
