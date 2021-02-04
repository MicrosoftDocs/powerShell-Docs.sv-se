---
description: Gör att du kan ange vilka namn områden som används i sessionen.
Locale: en-US
ms.date: 01/19/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_using?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Using
ms.openlocfilehash: 2a02ff32b110d369c080dde695a8fc2369b1a5e2
ms.sourcegitcommit: 94d597c4fb38793bc49ca7610e2c9973b1e577c2
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/21/2021
ms.locfileid: "98619898"
---
# <a name="about-using"></a>Om att använda

## <a name="short-description"></a>KORT BESKRIVNING
Gör att du kan ange vilka namn områden som används i sessionen.

## <a name="long-description"></a>LÅNG BESKRIVNING

Med `using` instruktionen kan du ange vilka namn områden som används i sessionen. Genom att lägga till namn områden blir det enklare att använda .NET-klasser och-medlemmar och du kan importera klasser från skriptfiler och sammansättningar.

`using`Instruktionerna måste komma före andra instruktioner i ett skript eller en modul. Ingen kommentars instruktion kan föregås, inklusive parametrar.

`using`Instruktionen får inte innehålla några variabler.

`using`Instruktionen ska inte förväxlas med `using:` omfångs modifieraren för variabler. Mer information finns i [about_Remote_Variables](about_Remote_Variables.md).

## <a name="namespace-syntax"></a>Syntax för namnrymd

Så här anger du .NET-namnrum som ska matcha typer:

```
using namespace <.NET-namespace>
```

Genom att ange ett namn område blir det enklare att referera till typer med deras korta namn.

## <a name="module-syntax"></a>Modulens syntax

Läsa in klasser från en PowerShell-modul:

```
using module <module-name>
```

Värdet för `<module-name>` kan vara ett modulnamn, en fullständig modul eller en sökväg till en modul.

När `<module-name>` är en sökväg kan sökvägen vara fullständigt kvalificerad eller relativ. En relativ sökväg matchas i förhållande till skriptet som innehåller using-instruktionen.

När `<module-name>` är ett namn eller en modul-specifikation söker PowerShell i **PSModulePath** efter den angivna modulen.

En modul specifikation är en hash-tabell som har följande nycklar.

- `ModuleName` - **Krävs** Anger namnet på modulen.
- `GUID` - **Valfritt** Anger modulens GUID.
- Du **måste** också ange en av de tre nycklarna nedan. Nycklarna kan inte användas tillsammans.
  - `ModuleVersion` -Anger en minsta godtagbar version av modulen.
  - `RequiredVersion` -Anger en exakt, obligatorisk version av modulen.
  - `MaximumVersion` -Anger den högsta godkända versionen av modulen.

`using module`Instruktionen importerar klasser från rotnoden ( `ModuleToProcess` ) i en skript-modul eller en binär modul. Det går inte alltid att importera klasser som definierats i kapslade moduler eller klasser som definierats i skript som är punkt-källor i modulen. Klasser som du vill ska vara tillgängliga för användare utanför modulen bör definieras i modulen root.

Under utvecklingen av en-skript-modul är det vanligt att göra ändringar i koden och sedan läsa in den nya versionen av modulen med hjälp av `Import-Module` parametern **Force** . Detta fungerar endast för ändringar i modulen i rot-modulen. `Import-Module` laddar inte om några kapslade moduler. Det finns även inget sätt att läsa in några uppdaterade klasser.

För att säkerställa att du kör den senaste versionen måste du ta bort modulen med `Remove-Module` cmdleten. `Remove-Module` tar bort modulen root, alla kapslade moduler och eventuella klasser som definierats i modulerna. Sedan kan du läsa in modulen igen och klasserna med hjälp av `Import-Module` och `using module` instruktionen.

## <a name="assembly-syntax"></a>Syntax för sammansättning

För preload-typer från en .NET-sammansättning:

```
using assembly <.NET-assembly-path>
using assembly <.NET-namespace>
```

Inläsning av en sammansättnings-och inläsnings-.NET-typer från den sammansättningen till ett skript vid parse-tiden. På så sätt kan du skapa nya PowerShell-klasser som använder typer från den förinstallerade sammansättningen.

I Windows PowerShell 5,1 kan du läsa in sammansättningen efter sökväg eller namn. När du använder namnet söker PowerShell i .NET Global Assembly Cache (GAC) för den associerade sammansättningen.

Om du inte skapar nya PowerShell-klasser använder du `Add-Type` cmdleten i stället. Mer information finns i [Add-Type](xref:Microsoft.PowerShell.Utility.Add-Type).

## <a name="examples"></a>Exempel

### <a name="example-1---add-namespaces-for-typename-resolution"></a>Exempel 1 – Lägg till namn områden för matchning av TypeName

Följande skript hämtar krypterings-hashen för strängen "Hello World".

Observera hur `using namespace System.Text` och `using namespace System.IO` förenkla referenser till `[UnicodeEncoding]` i `System.Text` och `[Stream]` och till `[MemoryStream]` i `System.IO` .

```powershell
using namespace System.Text
using namespace System.IO

[string]$string = "Hello World"
## Valid values are "SHA1", "SHA256", "SHA384", "SHA512", "MD5"
[string]$algorithm = "SHA256"

[byte[]]$stringbytes = [UnicodeEncoding]::Unicode.GetBytes($string)

[Stream]$memorystream = [MemoryStream]::new($stringbytes)
$hashfromstream = Get-FileHash -InputStream $memorystream `
  -Algorithm $algorithm
$hashfromstream.Hash.ToString()
```

### <a name="example-2---load-classes-from-a-script-module"></a>Exempel 2 – läsa in klasser från en skriptbaserad modul

I det här exemplet har vi en PowerShell-skriptfil med namnet **CardGames** som definierar följande klasser:

- **CardGames. kortlek**
- **CardGames. Card**

`Import-Module` och `#requires` instruktionen importerar bara modulens funktioner, alias och variabler, som definieras av modulen. Klasser importeras inte. `using module`Kommandot importerar modulen och läser även in klass definitionerna.

```powershell
using module CardGames
using namespace CardGames

[Deck]$deck = [Deck]::new()
$deck.Shuffle()
[Card[]]$hand1 = $deck.Deal(5)
[Card[]]$hand2 = $deck.Deal(5)
[Card[]]$hand3 = $deck.Deal(5)
```

### <a name="example-3---load-classes-from-an-assembly"></a>Exempel 3 – Läs in klasser från en sammansättning

I det här exemplet läses en sammansättning in så att dess klasser kan användas för att skapa nya PowerShell-klasser. Följande skript skapar en ny PowerShell-klass som härleds från **DirectoryContext** -klassen.

```powershell
using assembly 'C:\Program Files\PowerShell\7\System.DirectoryServices.dll'
using namespace System.DirectoryServices.ActiveDirectory

class myDirectoryClass : System.DirectoryServices.ActiveDirectory.DirectoryContext
{

  [DirectoryContext]$domain

  myDirectoryClass([DirectoryContextType]$ctx) : base($ctx)
  {
    $this.domain = [DirectoryContext]::new([DirectoryContextType]$ctx)
  }

}

$myDomain = [myDirectoryClass]::new([DirectoryContextType]::Domain)
$myDomain
```

```Output
domain                                                    Name UserName ContextType
------                                                    ---- -------- -----------
System.DirectoryServices.ActiveDirectory.DirectoryContext                    Domain
```
