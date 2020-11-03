---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-modulemanifest?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ModuleManifest
ms.openlocfilehash: 03f32d798a9e7ec1e58cdeb4ddf5d30edccd2490
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267411"
---
# Test-ModuleManifest

## SAMMANFATTNING
Verifierar att en modul manifest fil beskriver innehållet i en modul korrekt.

## SYNTAX

```
Test-ModuleManifest [-Path] <String> [<CommonParameters>]
```

## BESKRIVNING

Cmdleten **test-ModuleManifest** verifierar att filerna som listas i modul manifest filen (. psd1) verkligen finns i de angivna Sök vägarna.

Denna cmdlet är utformad för att hjälpa utvecklare att testa sina MANIFEST filer.
Module användare kan också använda denna cmdlet i skript och kommandon för att identifiera fel innan de kör skript som är beroende av modulen.

**Test-ModuleManifest** returnerar ett objekt som representerar modulen.
Det här är samma typ av objekt som Get-Module returnerar.
Om några filer inte finns på de platser som anges i manifestet genererar cmdleten också ett fel för varje fil som saknas.

## EXEMPEL

### Exempel 1: testa ett manifest

```powershell
test-ModuleManifest -Path "$pshome\Modules\TestModule.psd1"
```

Det här kommandot testar manifestet för TestModule.psd1-modulen.

### Exempel 2: testa ett manifest med hjälp av pipelinen

```powershell
"$pshome\Modules\TestModule.psd1" | test-modulemanifest
```

```Output
Test-ModuleManifest : The specified type data file 'C:\Windows\System32\Wi
ndowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml' could not be processed because the file was not found. Please correct the path and try again.
At line:1 char:34
+ "$pshome\Modules\TestModule.psd1" | test-modulemanifest <<<<
+ CategoryInfo          : ResourceUnavailable: (C:\Windows\System32\WindowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml:String) [Test-ModuleManifest], FileNotFoundException
+ FullyQualifiedErrorId : Modules_TypeDataFileNotFound,Microsoft.PowerShell.Commands.TestModuleManifestCommandName

Name              : TestModule
Path              : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule\TestModule.psd1
Description       :
Guid              : 6f0f1387-cd25-4902-b7b4-22cff6aefa7b
Version           : 1.0
ModuleBase        : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule
ModuleType        : Manifest
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {}
ExportedVariables : {}
NestedModules     : {}
```

Det här kommandot använder en pipeline-operator (|) för att skicka en Sök vägs sträng till **test-ModuleManifest**.

Kommandots utdata visar att testet misslyckades eftersom TestTypes.ps1XML-filen, som fanns i listan i manifestet, inte hittades.

### Exempel 3: Skriv en funktion för att testa ett modul manifest

```powershell
function Test-ManifestBool ($path)
```

```Output
{$a = dir $path | Test-ModuleManifest -ErrorAction SilentlyContinue; $?}
```

Den här funktionen liknar **test-ModuleManifest** , men returnerar ett booleskt värde.
Funktionen returnerar $True om manifestet godkände testet och $False annars.

Funktionen använder Get-ChildItem-cmdlet, alias = dir, för att hämta det modul manifest som anges av $path variabeln.
Kommandot använder en pipeline-operator (|) för att skicka filobjektet till **test-ModuleManifest**.

**Test-ModuleManifest** använder den gemensamma parametern *ErrorAction* med värdet SilentlyContinue för att förhindra visning av eventuella fel som genereras av kommandot.
Det sparar också **PSModuleInfo** -objektet som **test-ModuleManifest** returnerar i variabeln $a.
Därför visas inte objektet.

I ett separat kommando visar funktionen värdet $?
automatisk variabel.
Om föregående kommando inte genererar något fel, visar kommandot $True och $False annars.

Du kan använda den här funktionen i villkorliga uttryck, till exempel sådana som kan komma före ett **import-module-** kommando eller ett kommando som använder modulen.

## PARAMETRAR

### -Path

Anger en sökväg och ett fil namn för manifest filen.
Ange en valfri sökväg och ett namn för modulens manifest fil som har fil namns tillägget. psd1.
Standard platsen är den aktuella katalogen.
Jokertecken stöds, men måste matchas till en enda moduls manifest fil.
Den här parametern är obligatorisk.
Du kan också skicka en sökväg till **test-ModuleManifest**.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare sökvägen till ett modul manifest till denna cmdlet.

## UTDATA

### System. Management. Automation. PSModuleInfo

Denna cmdlet returnerar ett **PSModuleInfo** -objekt som representerar modulen.
Det returnerar objektet även om manifestet innehåller fel.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Exportera – ModuleMember](Export-ModuleMember.md)

[Hämta modul](Get-Module.md)

[Importera-modul](Import-Module.md)

[Ny modul](New-Module.md)

[New-ModuleManifest](New-ModuleManifest.md)

[Ta bort modul](Remove-Module.md)

[about_Modules](About/about_Modules.md)
