---
description: Gör att du kan ange vilka namn områden som används i sessionen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/29/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_using?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Using
ms.openlocfilehash: bfd1208516193adf470a25dbdf3d58563847a26a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271328"
---
# <a name="about-using"></a>Om att använda

## <a name="short-description"></a>KORT BESKRIVNING
Gör att du kan ange vilka namn områden som används i sessionen.

## <a name="long-description"></a>LÅNG BESKRIVNING

Med `using` instruktionen kan du ange vilka namn områden som används i sessionen. Genom att lägga till namn områden blir det enklare att använda .NET-klasser och-medlemmar och du kan importera klasser från skriptfiler och sammansättningar.

`using`Instruktionerna måste komma före alla andra instruktioner i ett skript.

`using`Instruktionen ska inte förväxlas med `using:` omfångs modifieraren för variabler. Mer information finns i [about_Remote_Variables](about_Remote_Variables.md).

## <a name="syntax"></a>Syntax

Så här anger du .NET-namnrum som ska matcha typer:

```
using namespace <.NET-namespace>
```

Läsa in klasser från en PowerShell-modul:

```
using module <module-name>
```

För preload-typer från en .NET-sammansättning:

```
using assembly <.NET-assembly-path>
```

Genom att ange ett namn område blir det enklare att referera till typer med deras korta namn.

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
