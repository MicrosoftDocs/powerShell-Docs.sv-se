---
description: Förklarar hur du skapar objekt i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_object_creation?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Object_Creation
ms.openlocfilehash: 57cc45640879aa80142c27c27a7810dcc5f31a9c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272601"
---
# <a name="about-object-creation"></a>Om att skapa objekt

## <a name="short-description"></a>Kort beskrivning

Förklarar hur du skapar objekt i PowerShell.

## <a name="long-description"></a>Lång beskrivning

Du kan skapa objekt i PowerShell och använda de objekt som du skapar i kommandon och skript.

Det finns många sätt att skapa objekt, den här listan är inte slutgiltig:

- [New-Object](xref:Microsoft.PowerShell.Utility.New-Object): skapar en instans av ett .NET Framework-objekt eller com-objekt.
- [Importera – CSV](xref:Microsoft.PowerShell.Utility.Import-Csv) /
   [ConvertFrom-CSV](xref:Microsoft.PowerShell.Utility.ConvertFrom-Csv): skapar anpassade objekt ( **PSCustomObject** ) från objekt som definieras som kommaavgränsade värden.
- [ConvertFrom-JSON](xref:Microsoft.PowerShell.Utility.ConvertFrom-Json): skapar anpassade objekt som definieras i JavaScript Object Notation (JSON).
- [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData): skapar anpassade objekt som definieras som nyckel värdes par.
- [Tilläggs typ](xref:Microsoft.PowerShell.Utility.Add-Type): gör att du kan definiera en klass i din PowerShell-session som du kan instansiera med `New-Object` .
- [Ny modul](xref:Microsoft.PowerShell.Core.New-Module): parametern **AsCustomObject** skapar ett anpassat objekt som du definierar med hjälp av skript block.
- [Lägg till medlem](xref:Microsoft.PowerShell.Utility.Add-Member): lägger till egenskaper i befintliga objekt. Du kan använda `Add-Member` för att skapa ett anpassat objekt av en enkel typ, t `[System.Int32]` . ex..
- [Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object): väljer Egenskaper för ett objekt. Du kan använda `Select-Object` för att skapa anpassade och beräknade egenskaper för ett redan instansierat objekt.

Följande ytterligare metoder beskrivs i den här artikeln:

- Genom att anropa en bastyps konstruktor med en statisk `new()` metod
- Av Typecasting hash-tabeller för egenskaps namn och egenskaps värden

## <a name="static-new-method"></a>Statisk ny ()-metod

Alla .NET-typer har en `new()` metod som gör att du enkelt kan skapa instanser. Du kan också se alla tillgängliga konstruktorer för en specifik typ.

Om du vill se konstruktörer för en typ anger du `new` metod namnet efter typ namnet och trycker på `<ENTER>` .

```powershell
[System.Uri]::new
```

```Output
OverloadDefinitions
-------------------
uri new(string uriString)
uri new(string uriString, bool dontEscape)
uri new(uri baseUri, string relativeUri, bool dontEscape)
uri new(string uriString, System.UriKind uriKind)
uri new(uri baseUri, string relativeUri)
uri new(uri baseUri, uri relativeUri)
```

Nu kan du skapa en **system. URI** genom att ange lämplig konstruktor.

```powershell
[System.Uri]::new("https://www.bing.com")
```

```Output
AbsolutePath   : /
AbsoluteUri    : https://www.bing.com/
LocalPath      : /
Authority      : www.bing.com
...
```

Du kan använda följande exempel för att avgöra vilka .NET-typer som för närvarande läses in för att skapa en instans.

```powershell
[AppDomain]::CurrentDomain.GetAssemblies() |
  ForEach-Object {
    $_.GetExportedTypes() |
      ForEach-Object { $_.FullName }
  }
```

Objekt som har skapats med `new()` metoden kanske inte har samma egenskaper som objekt av samma typ som skapas av PowerShell-cmdletar. PowerShell-cmdletar, providers och utökat typ system kan lägga till extra egenskaper till instansen.

Till exempel lägger fil Systems leverantören i PowerShell sex **NoteProperty** -värden till **DirectoryInfo** -objektet som returnerades av `Get-Item` .

```powershell
$PSDirInfo = Get-Item /
$PSDirInfo | Get-Member | Group-Object MemberType | Select-Object Count, Name
```

```Output
Count Name
----- ----
    4 CodeProperty
   13 Property
    6 NoteProperty
    1 ScriptProperty
   18 Method
```

När du skapar ett **DirectoryInfo** -objekt direkt har det inte dessa sex **NoteProperty** -värden.

```powershell
$NewDirInfo = [System.IO.DirectoryInfo]::new('/')
$NewDirInfo | Get-Member | Group-Object MemberType | Select-Object Count, Name
```

```Output
Count Name
----- ----
    4 CodeProperty
   13 Property
    1 ScriptProperty
   18 Method
```

Mer information om det utökade typ systemet finns i [about_Types.ps1XML](about_Types.ps1xml.md).

Den här funktionen lades till i PowerShell 5,0

## <a name="create-objects-from-hash-tables"></a>Skapa objekt från hash-tabeller

Du kan skapa ett objekt från en hash-tabell med egenskaper och egenskaps värden.

Syntaxen ser ut så här:

```
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

Den här metoden fungerar bara för klasser som har en parameter lös konstruktor. Objekt egenskaperna måste vara offentliga och kan anges.

Den här funktionen har lagts till i PowerShell version 3,0

## <a name="create-custom-objects-from-hash-tables"></a>Skapa anpassade objekt från hash-tabeller

Anpassade objekt är mycket användbara och är enkla att skapa med hjälp av hash-tabell metoden. **PSCustomObject** -klassen har utformats särskilt för detta ändamål.

Anpassade objekt är ett utmärkt sätt att returnera anpassade utdata från en funktion eller ett skript. Detta är mer användbart än att returnera formaterade utdata som inte kan formateras om eller skickas till andra kommandon.

Kommandona i `Test-Object function` anger några variabel värden och använder sedan dessa värden för att skapa ett anpassat objekt. Du kan se att det här objektet används i avsnittet exempel i `Update-Help` Hjälp avsnittet för cmdleten.

```powershell
function Test-Object {
  $ModuleName = "PSScheduledJob"
  $HelpCulture = "en-us"
  $HelpVersion = "3.1.0.0"
  [PSCustomObject]@{
    "ModuleName"=$ModuleName
    "UICulture"=$HelpCulture
    "Version"=$HelpVersion
  }
  $ModuleName = "PSWorkflow"
  $HelpCulture = "en-us"
  $HelpVersion = "3.0.0.0"
  [PSCustomObject]@{
    "ModuleName"=$ModuleName
    "UICulture"=$HelpCulture
    "Version"=$HelpVersion
  }
}
Test-Object
```

Resultatet av den här funktionen är en samling anpassade objekt som är formaterade som en tabell som standard.

```Output
ModuleName        UICulture      Version
---------         ---------      -------
PSScheduledJob    en-us          3.1.0.0
PSWorkflow        en-us          3.0.0.0
```

Användare kan hantera egenskaperna för de anpassade objekten precis som med standard objekt.

```powershell
(Test-Object).ModuleName
```

```Output
 PSScheduledJob
 PSWorkflow
```

## <a name="create-non-custom-objects-from-hash-tables"></a>Skapa icke-anpassade objekt från hash-tabeller

Du kan också använda hash-tabeller för att skapa objekt för klasser som inte är anpassade. När du skapar ett objekt för en icke-anpassad klass, krävs namn områdets kvalificerade typ, men du kan utesluta eventuella initiala **system** namns komponenter.

Till exempel skapar följande kommando ett alternativ för Session-objektet.

```powershell
[System.Management.Automation.Remoting.PSSessionOption]@{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
```

Kraven för hash-tabellens funktion, särskilt parameter lösa krav för konstruktorn, eliminerar många befintliga klasser. De _flesta PowerShell-alternativklasser är_ dock utformade för att fungera med den här funktionen, samt andra mycket användbara klasser, t. ex. klassen **ProcessStartInfo** .

```powershell
[System.Diagnostics.ProcessStartInfo]@{
  CreateNoWindow="$true"
  Verb="run as"
}
```

```Output
Arguments               :
ArgumentList            : {}
CreateNoWindow          : True
EnvironmentVariables    : {OneDriveConsumer, PROCESSOR_ARCHITECTURE,
                           CommonProgramFiles(x86), APPDATA...}
Environment             : {[OneDriveConsumer, C:\Users\user1\OneDrive],
                           [PROCESSOR_ARCHITECTURE, AMD64],
                           [CommonProgramFiles(x86),
                           C:\Program Files (x86)\Common Files],
                           [APPDATA, C:\Users\user1\AppData\Roaming]...}
RedirectStandardInput   : False
RedirectStandardOutput  : False
RedirectStandardError   : False
...
```

Du kan också använda funktionen hash-tabell när du anger parameter värden. Till exempel värdet för parametern **SessionOption** för `New-PSSession` .
cmdleten kan vara en hash-tabell.

```powershell
New-PSSession -ComputerName Server01 -SessionOption @{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
Register-ScheduledJob Name Test -FilePath .\Get-Inventory.ps1 -Trigger @{
  Frequency="Daily"
  At="15:00"
}
```

## <a name="generic-objects"></a>Allmänna objekt

Du kan också skapa generiska objekt i PowerShell. Generiska klasser är klasser, strukturer, gränssnitt och metoder som har plats hållare (typ parametrar) för en eller flera av de typer som de lagrar eller använder.

I följande exempel skapas ett **Dictionary** -objekt.

```powershell
$dict = New-Object 'System.Collections.Generic.Dictionary[String,Int]'
$dict.Add("One", 1)
$dict
```

```Output
Key Value
--- -----
One     1
```

Mer information om generiska finns [i generiska i .net](/dotnet/standard/generics).

## <a name="see-also"></a>Se även

[about_Objects](about_Objects.md)

[about_Methods](about_Methods.md)

[about_Properties](about_Properties.md)

[about_Pipelines](about_Pipelines.md)

[about_Types.ps1XML](about_Types.ps1xml.md)
