---
description: Gör att du kan ange vilka namn områden som används i sessionen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/29/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_using?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Using
ms.openlocfilehash: 6001f2f4495490c9f2b9dbfbeac2e1f4298febd8
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273255"
---
# <a name="about-using"></a><span data-ttu-id="e92ad-104">Om att använda</span><span class="sxs-lookup"><span data-stu-id="e92ad-104">About Using</span></span>

## <a name="short-description"></a><span data-ttu-id="e92ad-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e92ad-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="e92ad-106">Gör att du kan ange vilka namn områden som används i sessionen.</span><span class="sxs-lookup"><span data-stu-id="e92ad-106">Allows you to indicate which namespaces are used in the session.</span></span>

## <a name="long-description"></a><span data-ttu-id="e92ad-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e92ad-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="e92ad-108">Med `using` instruktionen kan du ange vilka namn områden som används i sessionen.</span><span class="sxs-lookup"><span data-stu-id="e92ad-108">The `using` statement allows you to specify which namespaces are used in the session.</span></span> <span data-ttu-id="e92ad-109">Genom att lägga till namn områden blir det enklare att använda .NET-klasser och-medlemmar och du kan importera klasser från skriptfiler och sammansättningar.</span><span class="sxs-lookup"><span data-stu-id="e92ad-109">Adding namespaces simplifies usage of .NET classes and member and allows you to import classes from script modules and assemblies.</span></span>

<span data-ttu-id="e92ad-110">`using`Instruktionerna måste komma före alla andra instruktioner i ett skript.</span><span class="sxs-lookup"><span data-stu-id="e92ad-110">The `using` statements must come before any other statements in a script.</span></span>

<span data-ttu-id="e92ad-111">`using`Instruktionen ska inte förväxlas med `using:` omfångs modifieraren för variabler.</span><span class="sxs-lookup"><span data-stu-id="e92ad-111">The `using` statement should not be confused with the `using:` scope modifier for variables.</span></span> <span data-ttu-id="e92ad-112">Mer information finns i [about_Remote_Variables](about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="e92ad-112">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="e92ad-113">Syntax</span><span class="sxs-lookup"><span data-stu-id="e92ad-113">Syntax</span></span>

<span data-ttu-id="e92ad-114">Så här anger du .NET-namnrum som ska matcha typer:</span><span class="sxs-lookup"><span data-stu-id="e92ad-114">To specify .NET namespaces from which to resolve types:</span></span>

```
using namespace <.NET-namespace>
```

<span data-ttu-id="e92ad-115">Läsa in klasser från en PowerShell-modul:</span><span class="sxs-lookup"><span data-stu-id="e92ad-115">To load classes from a PowerShell module:</span></span>

```
using module <module-name>
```

<span data-ttu-id="e92ad-116">För preload-typer från en .NET-sammansättning:</span><span class="sxs-lookup"><span data-stu-id="e92ad-116">To preload types from a .NET assembly:</span></span>

```
using assembly <.NET-assembly-path>
```

<span data-ttu-id="e92ad-117">Genom att ange ett namn område blir det enklare att referera till typer med deras korta namn.</span><span class="sxs-lookup"><span data-stu-id="e92ad-117">Specifying a namespace makes it easier to reference types by their short names.</span></span>

<span data-ttu-id="e92ad-118">Inläsning av en sammansättnings-och inläsnings-.NET-typer från den sammansättningen till ett skript vid parse-tiden.</span><span class="sxs-lookup"><span data-stu-id="e92ad-118">Loading an assembly preloads .NET types from that assembly into a script at parse time.</span></span> <span data-ttu-id="e92ad-119">På så sätt kan du skapa nya PowerShell-klasser som använder typer från den förinstallerade sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="e92ad-119">This allows you to create new PowerShell classes that use types from the preloaded assembly.</span></span>

<span data-ttu-id="e92ad-120">Om du inte skapar nya PowerShell-klasser använder du `Add-Type` cmdleten i stället.</span><span class="sxs-lookup"><span data-stu-id="e92ad-120">If you are not creating new PowerShell classes, use the `Add-Type` cmdlet instead.</span></span> <span data-ttu-id="e92ad-121">Mer information finns i [Add-Type](xref:Microsoft.PowerShell.Utility.Add-Type).</span><span class="sxs-lookup"><span data-stu-id="e92ad-121">For more information, see [Add-Type](xref:Microsoft.PowerShell.Utility.Add-Type).</span></span>

## <a name="examples"></a><span data-ttu-id="e92ad-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="e92ad-122">Examples</span></span>

### <a name="example-1---add-namespaces-for-typename-resolution"></a><span data-ttu-id="e92ad-123">Exempel 1 – Lägg till namn områden för matchning av TypeName</span><span class="sxs-lookup"><span data-stu-id="e92ad-123">Example 1 - Add namespaces for typename resolution</span></span>

<span data-ttu-id="e92ad-124">Följande skript hämtar krypterings-hashen för strängen "Hello World".</span><span class="sxs-lookup"><span data-stu-id="e92ad-124">The following script gets the cryptographic hash for the "Hello World" string.</span></span>

<span data-ttu-id="e92ad-125">Observera hur `using namespace System.Text` och `using namespace System.IO` förenkla referenser till `[UnicodeEncoding]` i `System.Text` och `[Stream]` och till `[MemoryStream]` i `System.IO` .</span><span class="sxs-lookup"><span data-stu-id="e92ad-125">Note how the `using namespace System.Text` and `using namespace System.IO` simplify the references to `[UnicodeEncoding]` in `System.Text` and `[Stream]` and to `[MemoryStream]` in `System.IO`.</span></span>

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

### <a name="example-2---load-classes-from-a-script-module"></a><span data-ttu-id="e92ad-126">Exempel 2 – läsa in klasser från en skriptbaserad modul</span><span class="sxs-lookup"><span data-stu-id="e92ad-126">Example 2 - Load classes from a script module</span></span>

<span data-ttu-id="e92ad-127">I det här exemplet har vi en PowerShell-skriptfil med namnet **CardGames** som definierar följande klasser:</span><span class="sxs-lookup"><span data-stu-id="e92ad-127">In this example, we have a PowerShell script module named **CardGames** that defines the following classes:</span></span>

- <span data-ttu-id="e92ad-128">**CardGames. kortlek**</span><span class="sxs-lookup"><span data-stu-id="e92ad-128">**CardGames.Deck**</span></span>
- <span data-ttu-id="e92ad-129">**CardGames. Card**</span><span class="sxs-lookup"><span data-stu-id="e92ad-129">**CardGames.Card**</span></span>

<span data-ttu-id="e92ad-130">`Import-Module` och `#requires` instruktionen importerar bara modulens funktioner, alias och variabler, som definieras av modulen.</span><span class="sxs-lookup"><span data-stu-id="e92ad-130">`Import-Module` and the `#requires` statement only import the module functions, aliases, and variables, as defined by the module.</span></span> <span data-ttu-id="e92ad-131">Klasser importeras inte.</span><span class="sxs-lookup"><span data-stu-id="e92ad-131">Classes are not imported.</span></span> <span data-ttu-id="e92ad-132">`using module`Kommandot importerar modulen och läser även in klass definitionerna.</span><span class="sxs-lookup"><span data-stu-id="e92ad-132">The `using module` command imports the module and also loads the class definitions.</span></span>

```powershell
using module CardGames
using namespace CardGames

[Deck]$deck = [Deck]::new()
$deck.Shuffle()
[Card[]]$hand1 = $deck.Deal(5)
[Card[]]$hand2 = $deck.Deal(5)
[Card[]]$hand3 = $deck.Deal(5)
```

### <a name="example-3---load-classes-from-an-assembly"></a><span data-ttu-id="e92ad-133">Exempel 3 – Läs in klasser från en sammansättning</span><span class="sxs-lookup"><span data-stu-id="e92ad-133">Example 3 - Load classes from an assembly</span></span>

<span data-ttu-id="e92ad-134">I det här exemplet läses en sammansättning in så att dess klasser kan användas för att skapa nya PowerShell-klasser.</span><span class="sxs-lookup"><span data-stu-id="e92ad-134">This example loads an assembly so that its classes can be used to create new PowerShell classes.</span></span> <span data-ttu-id="e92ad-135">Följande skript skapar en ny PowerShell-klass som härleds från **DirectoryContext** -klassen.</span><span class="sxs-lookup"><span data-stu-id="e92ad-135">The following script creates a new PowerShell class that is derived from **DirectoryContext** class.</span></span>

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
