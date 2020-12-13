---
title: Skriptmoduler
description: Skript moduler är ett enkelt sätt att paketera skript och funktioner i ett återanvändbart verktyg.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 661ba725764e1f31df628f6c5f2d58d760656e37
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "84436514"
---
# <a name="chapter-10---script-modules"></a>Kapitel 10 – skript moduler

Att aktivera en-liners och skript i PowerShell till återanvändbara verktyg blir ännu viktigare om det är något som du kommer att använda ofta. Genom att paketera dina funktioner i en-skript-modul kan de se ut och känna sig tryggare och gör dem lättare att dela.

## <a name="dot-sourcing-functions"></a>Dot-Sourcing funktioner

Något som vi inte pratar om i det förra kapitlet är funktioner för punkt-ursprung. När en funktion i ett skript inte är en del av en modul, är det enda sättet att läsa in den i minnet att vara i punkt källa `.PS1` filen som den sparats i.

Följande funktion har sparats som `Get-MrPSVersion.ps1` .

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}
```

När du kör skriptet händer ingenting.

```powershell
.\Get-MrPSVersion.ps1
```

Om du försöker anropa funktionen genererar det ett fel meddelande.

```powershell
Get-MrPSVersion
```

```Output
Get-MrPSVersion : The term 'Get-MrPSVersion' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [], CommandNotFou
   ndException
    + FullyQualifiedErrorId : CommandNotFoundException

```

Du kan kontrol lera om funktioner läses in i minnet genom att kontrol lera om de finns i **funktionen** PSDrive.

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
Get-ChildItem : Cannot find path 'Get-MrPSVersion' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path Function:\Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [Get-ChildItem],
   ItemNotFoundException
    + FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
```

Problemet med att anropa skriptet som innehåller funktionen är att funktionerna läses in i _skript_ omfånget. När skriptet har slutförts tas omfattningen bort och funktionen tas bort med den.

Funktionen måste läsas in i det _globala_ omfånget. Detta kan utföras av punkt-käll skriptet som innehåller funktionen. Du kan använda den relativa sökvägen.

```powershell
. .\Get-MrPSVersion.ps1
```

Den fullständigt kvalificerade sökvägen kan också användas.

```powershell
. C:\Demo\Get-MrPSVersion.ps1
```

Om en del av sökvägen lagras i en variabel, kan den kombineras med resten av sökvägen.
Det finns ingen anledning att använda sträng sammanfogning för att kombinera variabeln tillsammans med resten av sökvägen.

```powershell
$Path = 'C:\'
. $Path\Get-MrPSVersion.ps1
```

Nu när jag kontrollerar **funktionen** PSDrive `Get-MrPSVersion` finns funktionen.

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-MrPSVersion
```

## <a name="script-modules"></a>Skript moduler

En skript-modul i PowerShell är bara en fil som innehåller en eller flera funktioner som sparas som en `.PSM1` fil i stället för en `.PS1` fil.

Hur skapar du en-skript-modul? Du är förmodligen nöjd med ett kommando med namnet någonting `New-Module` . Ditt antagande skulle vara fel. Även om det finns ett kommando i PowerShell med namnet `New-Module` skapar det kommandot en dynamisk modul, inte en-skript-modul. Se alltid till att läsa hjälpen för ett kommando även när du tror att du har hittat det kommando du behöver.

```powershell
help New-Module
```

```Output
NAME
    New-Module

SYNOPSIS
    Creates a new dynamic module that exists only in memory.

SYNTAX
    New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-ArgumentList <Object[]>]
    [-AsCustomObject] [-Cmdlet <String[]>] [-Function <String[]>] [-ReturnResult]
    [<CommonParameters>]

DESCRIPTION
    The New-Module cmdlet creates a dynamic module from a script block. The members of
    the dynamic module, such as functions and variables, are immediately available in
    the session and remain available until you close the session.

    Like static modules, by default, the cmdlets and functions in a dynamic module are
    exported and the variables and aliases are not. However, you can use the
    Export-ModuleMember cmdlet and the parameters of New-Module to override the defaults.

    You can also use the AsCustomObject parameter of New-Module to return the dynamic
    module as a custom object. The members of the modules, such as functions, are
    implemented as script methods of the custom object instead of being imported into
    the session.

    Dynamic modules exist only in memory, not on disk. Like all modules, the members of
    dynamic modules run in a private module scope that is a child of the global scope.
    Get-Module cannot get a dynamic module, but Get-Command can get the exported members.

    To make a dynamic module available to Get-Module , pipe a New-Module command to
    Import-Module, or pipe the module object that New-Module returns to Import-Module .
    This action adds the dynamic module to the Get-Module list, but it does not save the
    module to disk or make it persistent.

RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821495
    Export-ModuleMember
    Get-Module
    Import-Module
    Remove-Module

REMARKS
    To see the examples, type: "get-help New-Module -examples".
    For more information, type: "get-help New-Module -detailed".
    For technical information, type: "get-help New-Module -full".
    For online help, type: "get-help New-Module -online"
```

I föregående kapitel nämnde jag att funktioner ska använda godkända verb, annars genererar de ett varnings meddelande när modulen importeras. Följande kod använder `New-Module` cmdleten för att skapa en dynamisk modul i minnet. Den här modulen visar varningen för ej godkända verb.

```powershell
New-Module -Name MyModule -ScriptBlock {

    function Return-MrOsVersion {
        Get-CimInstance -ClassName Win32_OperatingSystem |
        Select-Object -Property @{label='OperatingSystem';expression={$_.Caption}}
    }

    Export-ModuleMember -Function Return-MrOsVersion

} | Import-Module
```

```Output
WARNING: The names of some imported commands from the module 'MyModule' include
unapproved verbs that might make them less discoverable. To find the commands with
unapproved verbs, run the Import-Module command again with the Verbose parameter. For a
list of approved verbs, type Get-Verb.
```

Bara att upprepa, även om `New-Module` cmdleten användes i föregående exempel, är det inte kommandot för att skapa skript moduler i PowerShell.

Spara följande två funktioner i en fil med namnet `MyScriptModule.psm1` .

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}
```

Försök att anropa en av funktionerna.

```powershell
Get-MrComputerName
```

```Output
Get-MrComputerName : The term 'Get-MrComputerName' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrComputerName
    + CategoryInfo          : ObjectNotFound: (Get-MrComputerName:String) [], CommandNot
   FoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

Ett fel meddelande skapas som säger att funktionen inte kan hittas. Du kan också kontrol lera att **funktionen** PSDrive precis som tidigare och att det inte finns någon.

Du kan importera filen manuellt med `Import-Module` cmdleten.

```powershell
Import-Module C:\MyScriptModule.psm1
```

Funktionen automatisk inläsning av modulen introducerades i PowerShell version 3. För att kunna dra nytta av automatisk inläsning av modulen måste en modul för skript sparas i en mapp med samma bas namn som `.PSM1` filen och på en plats som anges i `$env:PSModulePath` .

```powershell
$env:PSModulePath
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules;C:\Program Files\WindowsPowerShell\
Modules;C:\Windows\system32\WindowsPowerShell\v1.0\Modules;C:\Program Files (x86)\Microsof
t SQL Server\130\Tools\PowerShell\Modules\
```

Det är svårt att läsa resultatet. Eftersom Sök vägarna skiljs åt med ett semikolon kan du dela resultaten för att returnera varje sökväg på en separat rad. Detta gör dem lättare att läsa.

```powershell
$env:PSModulePath -split ';'
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules
C:\Program Files\WindowsPowerShell\Modules
C:\Windows\system32\WindowsPowerShell\v1.0\Modules
C:\Program Files (x86)\Microsoft SQL Server\130\Tools\PowerShell\Modules\
```

De första tre Sök vägarna i listan är standard. När SQL Server Management Studio installerades lades den senaste sökvägen till. För att automatisk inläsning av modulen ska fungera `MyScriptModule.psm1` måste filen finnas i en mapp som heter `MyScriptModule` direkt inuti någon av dessa sökvägar.

Inte så snabbt. För mig är min nuvarande användar Sök väg inte den första i listan. Jag använder nästan aldrig den sökvägen eftersom jag loggar in i Windows med en annan användare än den som används för att köra PowerShell. Det innebär att den inte finns i min vanliga dokument-mapp.

Den andra sökvägen är **allusers** -sökvägen. Detta är den plats där jag lagrar alla mina moduler.

Den tredje sökvägen är under `C:\Windows\System32` . Endast Microsoft ska lagra moduler på den platsen eftersom det finns i operativ systemets mapp.

När `.PSM1` filen finns på rätt sökväg, kommer modulen att läsas in automatiskt när ett av dess kommandon anropas.

## <a name="module-manifests"></a>Modul manifest

Alla moduler bör ha ett modul manifest. Ett modul manifest innehåller metadata om modulen.
Fil namns tillägget för en modul manifest fil är `.PSD1` . Alla filer med `.PSD1` fil namns tillägget är inte modul manifest. De kan också användas för sådant som att lagra miljö delen av en DSC-konfiguration. `New-ModuleManifest` används för att skapa ett modul manifest. **Sökväg** är det enda värde som krävs. Modulen fungerar dock inte om **RootModule** inte har angetts. Det är en bra idé att ange **författare** och **Beskrivning** om du vill ladda upp modulen till en NuGet-lagringsplats med PowerShellGet eftersom dessa värden krävs i det scenariot.

Versionen av en modul utan manifest är 0,0. Detta är en död Giveaway att modulen inte har något manifest.

```powershell
Get-Module -Name MyScriptModule
```

```Output
ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Script     0.0        myscriptmodule                      {Get-MrComputerName, Get-MrP...
```

Modul manifestet kan skapas med all den rekommenderade informationen.

```powershell
New-ModuleManifest -Path $env:ProgramFiles\WindowsPowerShell\Modules\MyScriptModule\MyScriptModule.psd1 -RootModule MyScriptModule -Author 'Mike F Robbins' -Description 'MyScriptModule' -CompanyName 'mikefrobbins.com'
```

Om någon av dessa uppgifter saknas under den inledande skapandet av modulen manifest, kan den läggas till eller uppdateras senare med `Update-ModuleManifest` . Återskapa inte manifestet med `New-ModuleManifest` när det redan har skapats, eftersom GUID ändras.

## <a name="defining-public-and-private-functions"></a>Definiera offentliga och privata funktioner

Du kan ha hjälp funktioner som du kanske vill vara privata och som endast kan nås av andra funktioner i modulen. De är inte avsedda att vara tillgängliga för användare av modulen. Det finns ett par olika sätt att åstadkomma detta.

Om du inte följer de bästa metoderna och bara har en `.PSM1` fil, är ditt enda alternativ att använda `Export-ModuleMember` cmdleten.

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}

Export-ModuleMember -Function Get-MrPSVersion
```

I föregående exempel `Get-MrPSVersion` är bara funktionen tillgänglig för användare av modulen, men `Get-MrComputerName` funktionen är tillgänglig för andra funktioner i själva modulen.

```powershell
Get-Command -Module MyScriptModule

CommandType     Name                        Version    Source
-----------     ----                        -------    ------
Function        Get-MrPSVersion             1.0        MyScript...
```

Om du har lagt till ett modul-manifest i modulen (och du borde) rekommenderar vi att du anger de enskilda funktioner som du vill exportera i avsnittet **FunctionsToExport** i modulen manifest.

```powershell
FunctionsToExport = 'Get-MrPSVersion'
```

Det är inte nödvändigt att använda båda `Export-ModuleMember` i `.PSM1` filen och **FunctionsToExport** -avsnittet i modulen manifest. En eller flera av dem räcker.

## <a name="summary"></a>Sammanfattning

I det här kapitlet har du lärt dig hur du förvandlar dina funktioner till en-skript-modul i PowerShell. Du har också lagt till några av de bästa metoderna för att skapa skript moduler, till exempel skapa ett modul manifest för din skript-modul.

## <a name="review"></a>Genomgång

1. Hur skapar du en modul för skript i PowerShell?
1. Varför är det viktigt att dina funktioner använder ett godkänt verb?
1. Hur skapar du ett modul-manifest i PowerShell?
1. Vilka är de två alternativen bara för att exportera vissa funktioner från modulen?
1. Vad krävs för att dina moduler ska läsas in automatiskt när ett kommando anropas?

## <a name="recommended-reading"></a>Rekommenderad läsning

- [Så här skapar du PowerShell-skriptfiler och modul manifest][]
- [about_Modules][]
- [New-ModuleManifest][]
- [Exportera – ModuleMember][]

<!-- link references -->
[Så här skapar du PowerShell-skriptfiler och modul manifest]: https://mikefrobbins.com/2013/07/04/how-to-create-powershell-script-modules-and-module-manifests/
[about_Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Exportera – ModuleMember]: /powershell/module/microsoft.powershell.core/export-modulemember
