---
description: Gör att du kan ange vilka namn områden som används i sessionen.
Locale: en-US
ms.date: 01/19/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_using?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Using
ms.openlocfilehash: 2ada269fd0ce6b34a5f7faccfddf47a799301eb9
ms.sourcegitcommit: 94d597c4fb38793bc49ca7610e2c9973b1e577c2
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/21/2021
ms.locfileid: "98619949"
---
# <a name="about-using"></a><span data-ttu-id="67e68-103">Om att använda</span><span class="sxs-lookup"><span data-stu-id="67e68-103">About Using</span></span>

## <a name="short-description"></a><span data-ttu-id="67e68-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="67e68-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="67e68-105">Gör att du kan ange vilka namn områden som används i sessionen.</span><span class="sxs-lookup"><span data-stu-id="67e68-105">Allows you to indicate which namespaces are used in the session.</span></span>

## <a name="long-description"></a><span data-ttu-id="67e68-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="67e68-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="67e68-107">Med `using` instruktionen kan du ange vilka namn områden som används i sessionen.</span><span class="sxs-lookup"><span data-stu-id="67e68-107">The `using` statement allows you to specify which namespaces are used in the session.</span></span> <span data-ttu-id="67e68-108">Genom att lägga till namn områden blir det enklare att använda .NET-klasser och-medlemmar och du kan importera klasser från skriptfiler och sammansättningar.</span><span class="sxs-lookup"><span data-stu-id="67e68-108">Adding namespaces simplifies usage of .NET classes and member and allows you to import classes from script modules and assemblies.</span></span>

<span data-ttu-id="67e68-109">`using`Instruktionerna måste komma före andra instruktioner i ett skript eller en modul.</span><span class="sxs-lookup"><span data-stu-id="67e68-109">The `using` statements must come before any other statements in a script or module.</span></span> <span data-ttu-id="67e68-110">Ingen kommentars instruktion kan föregås, inklusive parametrar.</span><span class="sxs-lookup"><span data-stu-id="67e68-110">No uncommented statement can precede it, including parameters.</span></span>

<span data-ttu-id="67e68-111">`using`Instruktionen får inte innehålla några variabler.</span><span class="sxs-lookup"><span data-stu-id="67e68-111">The `using` statement must not contain any variables.</span></span>

<span data-ttu-id="67e68-112">`using`Instruktionen ska inte förväxlas med `using:` omfångs modifieraren för variabler.</span><span class="sxs-lookup"><span data-stu-id="67e68-112">The `using` statement should not be confused with the `using:` scope modifier for variables.</span></span> <span data-ttu-id="67e68-113">Mer information finns i [about_Remote_Variables](about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="67e68-113">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

## <a name="namespace-syntax"></a><span data-ttu-id="67e68-114">Syntax för namnrymd</span><span class="sxs-lookup"><span data-stu-id="67e68-114">Namespace syntax</span></span>

<span data-ttu-id="67e68-115">Så här anger du .NET-namnrum som ska matcha typer:</span><span class="sxs-lookup"><span data-stu-id="67e68-115">To specify .NET namespaces from which to resolve types:</span></span>

```
using namespace <.NET-namespace>
```

<span data-ttu-id="67e68-116">Genom att ange ett namn område blir det enklare att referera till typer med deras korta namn.</span><span class="sxs-lookup"><span data-stu-id="67e68-116">Specifying a namespace makes it easier to reference types by their short names.</span></span>

## <a name="module-syntax"></a><span data-ttu-id="67e68-117">Modulens syntax</span><span class="sxs-lookup"><span data-stu-id="67e68-117">Module syntax</span></span>

<span data-ttu-id="67e68-118">Läsa in klasser från en PowerShell-modul:</span><span class="sxs-lookup"><span data-stu-id="67e68-118">To load classes from a PowerShell module:</span></span>

```
using module <module-name>
```

<span data-ttu-id="67e68-119">Värdet för `<module-name>` kan vara ett modulnamn, en fullständig modul eller en sökväg till en modul.</span><span class="sxs-lookup"><span data-stu-id="67e68-119">The value of `<module-name>` can be a module name, a full module specification, or a path to a module file.</span></span>

<span data-ttu-id="67e68-120">När `<module-name>` är en sökväg kan sökvägen vara fullständigt kvalificerad eller relativ.</span><span class="sxs-lookup"><span data-stu-id="67e68-120">When `<module-name>` is a path, the path can be fully qualified or relative.</span></span> <span data-ttu-id="67e68-121">En relativ sökväg matchas i förhållande till skriptet som innehåller using-instruktionen.</span><span class="sxs-lookup"><span data-stu-id="67e68-121">A relative path is resolved relative to the script that contains the using statement.</span></span>

> [!NOTE]
> <span data-ttu-id="67e68-122">När den relativa sökvägen innehåller ett snedstreck ( `/` ) behandlar PowerShell sökvägen som relativ till den aktuella platsen i stället för i förhållande till skript platsen.</span><span class="sxs-lookup"><span data-stu-id="67e68-122">When the relative path contains a forward slash (`/`), PowerShell treats the path as relative to the current location rather than relative to the script location.</span></span> <span data-ttu-id="67e68-123">Den här buggen har åtgärd ATS i PowerShell 7,1.</span><span class="sxs-lookup"><span data-stu-id="67e68-123">This bug is fixed in PowerShell 7.1.</span></span>

<span data-ttu-id="67e68-124">När `<module-name>` är ett namn eller en modul-specifikation söker PowerShell i **PSModulePath** efter den angivna modulen.</span><span class="sxs-lookup"><span data-stu-id="67e68-124">When `<module-name>` is a name or module specification, PowerShell searches the **PSModulePath** for the specified module.</span></span>

<span data-ttu-id="67e68-125">En modul specifikation är en hash-tabell som har följande nycklar.</span><span class="sxs-lookup"><span data-stu-id="67e68-125">A module specification is a hash table that has the following keys.</span></span>

- <span data-ttu-id="67e68-126">`ModuleName` - **Krävs** Anger namnet på modulen.</span><span class="sxs-lookup"><span data-stu-id="67e68-126">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="67e68-127">`GUID` - **Valfritt** Anger modulens GUID.</span><span class="sxs-lookup"><span data-stu-id="67e68-127">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="67e68-128">Du **måste** också ange en av de tre nycklarna nedan.</span><span class="sxs-lookup"><span data-stu-id="67e68-128">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="67e68-129">Nycklarna kan inte användas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="67e68-129">These keys can't be used together.</span></span>
  - <span data-ttu-id="67e68-130">`ModuleVersion` -Anger en minsta godtagbar version av modulen.</span><span class="sxs-lookup"><span data-stu-id="67e68-130">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="67e68-131">`RequiredVersion` -Anger en exakt, obligatorisk version av modulen.</span><span class="sxs-lookup"><span data-stu-id="67e68-131">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="67e68-132">`MaximumVersion` -Anger den högsta godkända versionen av modulen.</span><span class="sxs-lookup"><span data-stu-id="67e68-132">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

<span data-ttu-id="67e68-133">`using module`Instruktionen importerar klasser från rotnoden ( `ModuleToProcess` ) i en skript-modul eller en binär modul.</span><span class="sxs-lookup"><span data-stu-id="67e68-133">The `using module` statement imports classes from the root module (`ModuleToProcess`) of a script module or binary module.</span></span> <span data-ttu-id="67e68-134">Det går inte alltid att importera klasser som definierats i kapslade moduler eller klasser som definierats i skript som är punkt-källor i modulen.</span><span class="sxs-lookup"><span data-stu-id="67e68-134">It does not consistently import classes defined in nested modules or classes defined in scripts that are dot-sourced into the module.</span></span> <span data-ttu-id="67e68-135">Klasser som du vill ska vara tillgängliga för användare utanför modulen bör definieras i modulen root.</span><span class="sxs-lookup"><span data-stu-id="67e68-135">Classes that you want to be available to users outside of the module should be defined in the root module.</span></span>

<span data-ttu-id="67e68-136">Under utvecklingen av en-skript-modul är det vanligt att göra ändringar i koden och sedan läsa in den nya versionen av modulen med hjälp av `Import-Module` parametern **Force** .</span><span class="sxs-lookup"><span data-stu-id="67e68-136">During development of a script module, it is common to make changes to the code then load the new version of the module using `Import-Module` with the **Force** parameter.</span></span> <span data-ttu-id="67e68-137">Detta fungerar endast för ändringar i modulen i rot-modulen.</span><span class="sxs-lookup"><span data-stu-id="67e68-137">This works for changes to functions in the root module only.</span></span> <span data-ttu-id="67e68-138">`Import-Module` laddar inte om några kapslade moduler.</span><span class="sxs-lookup"><span data-stu-id="67e68-138">`Import-Module` does not reload any nested modules.</span></span> <span data-ttu-id="67e68-139">Det finns även inget sätt att läsa in några uppdaterade klasser.</span><span class="sxs-lookup"><span data-stu-id="67e68-139">Also, there is no way to load any updated classes.</span></span>

<span data-ttu-id="67e68-140">För att säkerställa att du kör den senaste versionen måste du ta bort modulen med `Remove-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="67e68-140">To ensure that you are running the latest version, you must unload the module using the `Remove-Module` cmdlet.</span></span> <span data-ttu-id="67e68-141">`Remove-Module` tar bort modulen root, alla kapslade moduler och eventuella klasser som definierats i modulerna.</span><span class="sxs-lookup"><span data-stu-id="67e68-141">`Remove-Module` removes the root module, all nested modules, and any classes defined in the modules.</span></span> <span data-ttu-id="67e68-142">Sedan kan du läsa in modulen igen och klasserna med hjälp av `Import-Module` och `using module` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="67e68-142">Then you can reload the module and the classes using `Import-Module` and the `using module` statement.</span></span>

## <a name="assembly-syntax"></a><span data-ttu-id="67e68-143">Syntax för sammansättning</span><span class="sxs-lookup"><span data-stu-id="67e68-143">Assembly syntax</span></span>

<span data-ttu-id="67e68-144">För preload-typer från en .NET-sammansättning:</span><span class="sxs-lookup"><span data-stu-id="67e68-144">To preload types from a .NET assembly:</span></span>

```
using assembly <.NET-assembly-path>
```

<span data-ttu-id="67e68-145">Inläsning av en sammansättnings-och inläsnings-.NET-typer från den sammansättningen till ett skript vid parse-tiden.</span><span class="sxs-lookup"><span data-stu-id="67e68-145">Loading an assembly preloads .NET types from that assembly into a script at parse time.</span></span> <span data-ttu-id="67e68-146">På så sätt kan du skapa nya PowerShell-klasser som använder typer från den förinstallerade sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="67e68-146">This allows you to create new PowerShell classes that use types from the preloaded assembly.</span></span>

<span data-ttu-id="67e68-147">Om du inte skapar nya PowerShell-klasser använder du `Add-Type` cmdleten i stället.</span><span class="sxs-lookup"><span data-stu-id="67e68-147">If you are not creating new PowerShell classes, use the `Add-Type` cmdlet instead.</span></span> <span data-ttu-id="67e68-148">Mer information finns i [Add-Type](xref:Microsoft.PowerShell.Utility.Add-Type).</span><span class="sxs-lookup"><span data-stu-id="67e68-148">For more information, see [Add-Type](xref:Microsoft.PowerShell.Utility.Add-Type).</span></span>

## <a name="examples"></a><span data-ttu-id="67e68-149">Exempel</span><span class="sxs-lookup"><span data-stu-id="67e68-149">Examples</span></span>

### <a name="example-1---add-namespaces-for-typename-resolution"></a><span data-ttu-id="67e68-150">Exempel 1 – Lägg till namn områden för matchning av TypeName</span><span class="sxs-lookup"><span data-stu-id="67e68-150">Example 1 - Add namespaces for typename resolution</span></span>

<span data-ttu-id="67e68-151">Följande skript hämtar krypterings-hashen för strängen "Hello World".</span><span class="sxs-lookup"><span data-stu-id="67e68-151">The following script gets the cryptographic hash for the "Hello World" string.</span></span>

<span data-ttu-id="67e68-152">Observera hur `using namespace System.Text` och `using namespace System.IO` förenkla referenser till `[UnicodeEncoding]` i `System.Text` och `[Stream]` och till `[MemoryStream]` i `System.IO` .</span><span class="sxs-lookup"><span data-stu-id="67e68-152">Note how the `using namespace System.Text` and `using namespace System.IO` simplify the references to `[UnicodeEncoding]` in `System.Text` and `[Stream]` and to `[MemoryStream]` in `System.IO`.</span></span>

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

### <a name="example-2---load-classes-from-a-script-module"></a><span data-ttu-id="67e68-153">Exempel 2 – läsa in klasser från en skriptbaserad modul</span><span class="sxs-lookup"><span data-stu-id="67e68-153">Example 2 - Load classes from a script module</span></span>

<span data-ttu-id="67e68-154">I det här exemplet har vi en PowerShell-skriptfil med namnet **CardGames** som definierar följande klasser:</span><span class="sxs-lookup"><span data-stu-id="67e68-154">In this example, we have a PowerShell script module named **CardGames** that defines the following classes:</span></span>

- <span data-ttu-id="67e68-155">**CardGames. kortlek**</span><span class="sxs-lookup"><span data-stu-id="67e68-155">**CardGames.Deck**</span></span>
- <span data-ttu-id="67e68-156">**CardGames. Card**</span><span class="sxs-lookup"><span data-stu-id="67e68-156">**CardGames.Card**</span></span>

<span data-ttu-id="67e68-157">`Import-Module` och `#requires` instruktionen importerar bara modulens funktioner, alias och variabler, som definieras av modulen.</span><span class="sxs-lookup"><span data-stu-id="67e68-157">`Import-Module` and the `#requires` statement only import the module functions, aliases, and variables, as defined by the module.</span></span> <span data-ttu-id="67e68-158">Klasser importeras inte.</span><span class="sxs-lookup"><span data-stu-id="67e68-158">Classes are not imported.</span></span> <span data-ttu-id="67e68-159">`using module`Kommandot importerar modulen och läser även in klass definitionerna.</span><span class="sxs-lookup"><span data-stu-id="67e68-159">The `using module` command imports the module and also loads the class definitions.</span></span>

```powershell
using module CardGames
using namespace CardGames

[Deck]$deck = [Deck]::new()
$deck.Shuffle()
[Card[]]$hand1 = $deck.Deal(5)
[Card[]]$hand2 = $deck.Deal(5)
[Card[]]$hand3 = $deck.Deal(5)
```

### <a name="example-3---load-classes-from-an-assembly"></a><span data-ttu-id="67e68-160">Exempel 3 – Läs in klasser från en sammansättning</span><span class="sxs-lookup"><span data-stu-id="67e68-160">Example 3 - Load classes from an assembly</span></span>

<span data-ttu-id="67e68-161">I det här exemplet läses en sammansättning in så att dess klasser kan användas för att skapa nya PowerShell-klasser.</span><span class="sxs-lookup"><span data-stu-id="67e68-161">This example loads an assembly so that its classes can be used to create new PowerShell classes.</span></span> <span data-ttu-id="67e68-162">Följande skript skapar en ny PowerShell-klass som härleds från **DirectoryContext** -klassen.</span><span class="sxs-lookup"><span data-stu-id="67e68-162">The following script creates a new PowerShell class that is derived from **DirectoryContext** class.</span></span>

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
