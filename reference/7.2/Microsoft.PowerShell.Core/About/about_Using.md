---
description: Gör att du kan ange vilka namn områden som används i sessionen.
Locale: en-US
ms.date: 11/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_using?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Using
ms.openlocfilehash: d08ada489ebe04ae51e3927486f354a8371de03f
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892543"
---
# <a name="about-using"></a><span data-ttu-id="8dc2f-103">Om att använda</span><span class="sxs-lookup"><span data-stu-id="8dc2f-103">About Using</span></span>

## <a name="short-description"></a><span data-ttu-id="8dc2f-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8dc2f-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="8dc2f-105">Gör att du kan ange vilka namn områden som används i sessionen.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-105">Allows you to indicate which namespaces are used in the session.</span></span>

## <a name="long-description"></a><span data-ttu-id="8dc2f-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8dc2f-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="8dc2f-107">Med `using` instruktionen kan du ange vilka namn områden som används i sessionen.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-107">The `using` statement allows you to specify which namespaces are used in the session.</span></span> <span data-ttu-id="8dc2f-108">Genom att lägga till namn områden blir det enklare att använda .NET-klasser och-medlemmar och du kan importera klasser från skriptfiler och sammansättningar.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-108">Adding namespaces simplifies usage of .NET classes and member and allows you to import classes from script modules and assemblies.</span></span>

<span data-ttu-id="8dc2f-109">`using`Instruktionerna måste komma före alla andra instruktioner i ett skript.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-109">The `using` statements must come before any other statements in a script.</span></span>

<span data-ttu-id="8dc2f-110">`using`Instruktionen ska inte förväxlas med `using:` omfångs modifieraren för variabler.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-110">The `using` statement should not be confused with the `using:` scope modifier for variables.</span></span> <span data-ttu-id="8dc2f-111">Mer information finns i [about_Remote_Variables](about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="8dc2f-111">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

## <a name="namespace-syntax"></a><span data-ttu-id="8dc2f-112">Syntax för namnrymd</span><span class="sxs-lookup"><span data-stu-id="8dc2f-112">Namespace syntax</span></span>

<span data-ttu-id="8dc2f-113">Så här anger du .NET-namnrum som ska matcha typer:</span><span class="sxs-lookup"><span data-stu-id="8dc2f-113">To specify .NET namespaces from which to resolve types:</span></span>

```
using namespace <.NET-namespace>
```

<span data-ttu-id="8dc2f-114">Genom att ange ett namn område blir det enklare att referera till typer med deras korta namn.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-114">Specifying a namespace makes it easier to reference types by their short names.</span></span>

## <a name="module-syntax"></a><span data-ttu-id="8dc2f-115">Modulens syntax</span><span class="sxs-lookup"><span data-stu-id="8dc2f-115">Module syntax</span></span>

<span data-ttu-id="8dc2f-116">Läsa in klasser från en PowerShell-modul:</span><span class="sxs-lookup"><span data-stu-id="8dc2f-116">To load classes from a PowerShell module:</span></span>

```
using module <module-name>
```

<span data-ttu-id="8dc2f-117">Värdet för `<module-name>` kan vara ett modulnamn, en fullständig modul eller en sökväg till en modul.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-117">The value of `<module-name>` can be a module name, a full module specification, or a path to a module file.</span></span>

<span data-ttu-id="8dc2f-118">När `<module-name>` är en sökväg kan sökvägen vara fullständigt kvalificerad eller relativ.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-118">When `<module-name>` is a path, the path can be fully qualified or relative.</span></span> <span data-ttu-id="8dc2f-119">En relativ sökväg matchas i förhållande till skriptet som innehåller using-instruktionen.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-119">A relative path is resolved relative to the script that contains the using statement.</span></span>

<span data-ttu-id="8dc2f-120">När `<module-name>` är ett namn eller en modul-specifikation söker PowerShell i **PSModulePath** efter den angivna modulen.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-120">When `<module-name>` is a name or module specification, PowerShell searches the **PSModulePath** for the specified module.</span></span>

<span data-ttu-id="8dc2f-121">En modul specifikation är en hash-tabell som har följande nycklar.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-121">A module specification is a hash table that has the following keys.</span></span>

- <span data-ttu-id="8dc2f-122">`ModuleName` - **Krävs** Anger namnet på modulen.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-122">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="8dc2f-123">`GUID` - **Valfritt** Anger modulens GUID.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-123">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="8dc2f-124">Du **måste** också ange en av de tre nycklarna nedan.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-124">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="8dc2f-125">Nycklarna kan inte användas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-125">These keys can't be used together.</span></span>
  - <span data-ttu-id="8dc2f-126">`ModuleVersion` -Anger en minsta godtagbar version av modulen.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-126">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="8dc2f-127">`RequiredVersion` -Anger en exakt, obligatorisk version av modulen.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-127">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="8dc2f-128">`MaximumVersion` -Anger den högsta godkända versionen av modulen.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-128">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

## <a name="assembly-syntax"></a><span data-ttu-id="8dc2f-129">Syntax för sammansättning</span><span class="sxs-lookup"><span data-stu-id="8dc2f-129">Assembly syntax</span></span>

<span data-ttu-id="8dc2f-130">För preload-typer från en .NET-sammansättning:</span><span class="sxs-lookup"><span data-stu-id="8dc2f-130">To preload types from a .NET assembly:</span></span>

```
using assembly <.NET-assembly-path>
```

<span data-ttu-id="8dc2f-131">Inläsning av en sammansättnings-och inläsnings-.NET-typer från den sammansättningen till ett skript vid parse-tiden.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-131">Loading an assembly preloads .NET types from that assembly into a script at parse time.</span></span> <span data-ttu-id="8dc2f-132">På så sätt kan du skapa nya PowerShell-klasser som använder typer från den förinstallerade sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-132">This allows you to create new PowerShell classes that use types from the preloaded assembly.</span></span>

<span data-ttu-id="8dc2f-133">Om du inte skapar nya PowerShell-klasser använder du `Add-Type` cmdleten i stället.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-133">If you are not creating new PowerShell classes, use the `Add-Type` cmdlet instead.</span></span> <span data-ttu-id="8dc2f-134">Mer information finns i [Add-Type](xref:Microsoft.PowerShell.Utility.Add-Type).</span><span class="sxs-lookup"><span data-stu-id="8dc2f-134">For more information, see [Add-Type](xref:Microsoft.PowerShell.Utility.Add-Type).</span></span>

## <a name="examples"></a><span data-ttu-id="8dc2f-135">Exempel</span><span class="sxs-lookup"><span data-stu-id="8dc2f-135">Examples</span></span>

### <a name="example-1---add-namespaces-for-typename-resolution"></a><span data-ttu-id="8dc2f-136">Exempel 1 – Lägg till namn områden för matchning av TypeName</span><span class="sxs-lookup"><span data-stu-id="8dc2f-136">Example 1 - Add namespaces for typename resolution</span></span>

<span data-ttu-id="8dc2f-137">Följande skript hämtar krypterings-hashen för strängen "Hello World".</span><span class="sxs-lookup"><span data-stu-id="8dc2f-137">The following script gets the cryptographic hash for the "Hello World" string.</span></span>

<span data-ttu-id="8dc2f-138">Observera hur `using namespace System.Text` och `using namespace System.IO` förenkla referenser till `[UnicodeEncoding]` i `System.Text` och `[Stream]` och till `[MemoryStream]` i `System.IO` .</span><span class="sxs-lookup"><span data-stu-id="8dc2f-138">Note how the `using namespace System.Text` and `using namespace System.IO` simplify the references to `[UnicodeEncoding]` in `System.Text` and `[Stream]` and to `[MemoryStream]` in `System.IO`.</span></span>

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

### <a name="example-2---load-classes-from-a-script-module"></a><span data-ttu-id="8dc2f-139">Exempel 2 – läsa in klasser från en skriptbaserad modul</span><span class="sxs-lookup"><span data-stu-id="8dc2f-139">Example 2 - Load classes from a script module</span></span>

<span data-ttu-id="8dc2f-140">I det här exemplet har vi en PowerShell-skriptfil med namnet **CardGames** som definierar följande klasser:</span><span class="sxs-lookup"><span data-stu-id="8dc2f-140">In this example, we have a PowerShell script module named **CardGames** that defines the following classes:</span></span>

- <span data-ttu-id="8dc2f-141">**CardGames. kortlek**</span><span class="sxs-lookup"><span data-stu-id="8dc2f-141">**CardGames.Deck**</span></span>
- <span data-ttu-id="8dc2f-142">**CardGames. Card**</span><span class="sxs-lookup"><span data-stu-id="8dc2f-142">**CardGames.Card**</span></span>

<span data-ttu-id="8dc2f-143">`Import-Module` och `#requires` instruktionen importerar bara modulens funktioner, alias och variabler, som definieras av modulen.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-143">`Import-Module` and the `#requires` statement only import the module functions, aliases, and variables, as defined by the module.</span></span> <span data-ttu-id="8dc2f-144">Klasser importeras inte.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-144">Classes are not imported.</span></span> <span data-ttu-id="8dc2f-145">`using module`Kommandot importerar modulen och läser även in klass definitionerna.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-145">The `using module` command imports the module and also loads the class definitions.</span></span>

```powershell
using module CardGames
using namespace CardGames

[Deck]$deck = [Deck]::new()
$deck.Shuffle()
[Card[]]$hand1 = $deck.Deal(5)
[Card[]]$hand2 = $deck.Deal(5)
[Card[]]$hand3 = $deck.Deal(5)
```

### <a name="example-3---load-classes-from-an-assembly"></a><span data-ttu-id="8dc2f-146">Exempel 3 – Läs in klasser från en sammansättning</span><span class="sxs-lookup"><span data-stu-id="8dc2f-146">Example 3 - Load classes from an assembly</span></span>

<span data-ttu-id="8dc2f-147">I det här exemplet läses en sammansättning in så att dess klasser kan användas för att skapa nya PowerShell-klasser.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-147">This example loads an assembly so that its classes can be used to create new PowerShell classes.</span></span> <span data-ttu-id="8dc2f-148">Följande skript skapar en ny PowerShell-klass som härleds från **DirectoryContext** -klassen.</span><span class="sxs-lookup"><span data-stu-id="8dc2f-148">The following script creates a new PowerShell class that is derived from **DirectoryContext** class.</span></span>

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