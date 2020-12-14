---
description: Gör att du kan ange vilka namn områden som används i sessionen.
Locale: en-US
ms.date: 11/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_using?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Using
ms.openlocfilehash: bbea815f93ba503fcce550dec28736630fec5a51
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890771"
---
# <a name="about-using"></a>Om att använda

## <a name="short-description"></a>KORT BESKRIVNING
Gör att du kan ange vilka namn områden som används i sessionen.

## <a name="long-description"></a>LÅNG BESKRIVNING

Med `using` instruktionen kan du ange vilka namn områden som används i sessionen. Genom att lägga till namn områden blir det enklare att använda .NET-klasser och-medlemmar och du kan importera klasser från skriptfiler och sammansättningar.

`using`Instruktionerna måste komma före alla andra instruktioner i ett skript.

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

## <a name="assembly-syntax"></a>Syntax för sammansättning

För preload-typer från en .NET-sammansättning:

```
using assembly <.NET-assembly-path>
```

Inläsning av en sammansättnings-och inläsnings-.NET-typer från den sammansättningen till ett skript vid parse-tiden. På så sätt kan du skapa nya PowerShell-klasser som använder typer från den förinstallerade sammansättningen.

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
