---
description: Beskriver ett språk kommando som du kan använda för att bläddra igenom alla objekt i en objekt samling.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 2/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_foreach?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Foreach
ms.openlocfilehash: b5f09785fbf1fa8c3c14d287efc7cf5fed2d18eb
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270746"
---
# <a name="about-foreach"></a><span data-ttu-id="cbbd7-104">Om</span><span class="sxs-lookup"><span data-stu-id="cbbd7-104">About ForEach</span></span>

## <a name="short-description"></a><span data-ttu-id="cbbd7-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="cbbd7-105">Short description</span></span>
<span data-ttu-id="cbbd7-106">Beskriver ett språk kommando som du kan använda för att bläddra igenom alla objekt i en objekt samling.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-106">Describes a language command you can use to traverse all the items in a collection of items.</span></span>

## <a name="long-description"></a><span data-ttu-id="cbbd7-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="cbbd7-107">Long description</span></span>

<span data-ttu-id="cbbd7-108">`Foreach`Instruktionen (kallas även en `Foreach` loop) är en språk konstruktion för stega igenom (iterera) en serie med värden i en samling objekt.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-108">The `Foreach` statement (also known as a `Foreach` loop) is a language construct for stepping through (iterating) a series of values in a collection of items.</span></span>

<span data-ttu-id="cbbd7-109">Den enklaste och mest typiska typen av samling att passera är en matris.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-109">The simplest and most typical type of collection to traverse is an array.</span></span>
<span data-ttu-id="cbbd7-110">I en `Foreach` slinga är det vanligt att köra ett eller flera kommandon mot varje objekt i en matris.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-110">Within a `Foreach` loop, it is common to run one or more commands against each item in an array.</span></span>

## <a name="syntax"></a><span data-ttu-id="cbbd7-111">Syntax</span><span class="sxs-lookup"><span data-stu-id="cbbd7-111">Syntax</span></span>

<span data-ttu-id="cbbd7-112">Följande visar `ForEach` syntaxen:</span><span class="sxs-lookup"><span data-stu-id="cbbd7-112">The following shows the `ForEach` syntax:</span></span>

```
foreach ($<item> in $<collection>){<statement list>}
```

<span data-ttu-id="cbbd7-113">Den del av `ForEach` instruktionen som omges av parentes representerar en variabel och en samling att iterera.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-113">The part of the `ForEach` statement enclosed in parenthesis represents a variable and a collection to iterate.</span></span> <span data-ttu-id="cbbd7-114">PowerShell skapar variabeln `$<item>` automatiskt när `Foreach` loopen körs.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-114">PowerShell creates the variable `$<item>` automatically when the `Foreach` loop runs.</span></span> <span data-ttu-id="cbbd7-115">Före varje iteration genom loopen anges variabeln till ett värde i samlingen.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-115">Prior to each iteration through the loop, the variable is set to a value in the collection.</span></span>
<span data-ttu-id="cbbd7-116">Blocket som följer efter en `Foreach` instruktion `{<statement list>}` innehåller en uppsättning kommandon som ska köras mot varje objekt i en samling.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-116">The block following a `Foreach` statement `{<statement list>}` contains a set of commands to execute against each item in a collection.</span></span>

### <a name="examples"></a><span data-ttu-id="cbbd7-117">Exempel</span><span class="sxs-lookup"><span data-stu-id="cbbd7-117">Examples</span></span>

<span data-ttu-id="cbbd7-118">`Foreach`Slingan i följande exempel visar till exempel värdena i `$letterArray` matrisen.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-118">For example, the `Foreach` loop in the following example displays the values in the `$letterArray` array.</span></span>

```powershell
$letterArray = "a","b","c","d"
foreach ($letter in $letterArray)
{
  Write-Host $letter
}
```

<span data-ttu-id="cbbd7-119">I det här exemplet `$letterArray` skapas och initieras matrisen med sträng värden `"a"` , `"b"` , `"c"` och `"d"` .</span><span class="sxs-lookup"><span data-stu-id="cbbd7-119">In this example, the `$letterArray` array is created and initialized with the string values `"a"`, `"b"`, `"c"`, and `"d"`.</span></span> <span data-ttu-id="cbbd7-120">Första gången som `Foreach` instruktionen körs anger den `$letter` variabeln som är lika med det första objektet i `$letterArray` ( `"a"` ).</span><span class="sxs-lookup"><span data-stu-id="cbbd7-120">The first time the `Foreach` statement runs, it sets the `$letter` variable equal to the first item in `$letterArray` (`"a"`).</span></span> <span data-ttu-id="cbbd7-121">Sedan använder den `Write-Host` cmdleten för att visa bokstaven a.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-121">Then, it uses the `Write-Host` cmdlet to display the letter a.</span></span> <span data-ttu-id="cbbd7-122">Nästa gången genom loopen `$letter` ställs in på `"b"` och så vidare.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-122">The next time through the loop, `$letter` is set to `"b"`, and so on.</span></span> <span data-ttu-id="cbbd7-123">När `Foreach` loopen visar bokstaven d avslutar PowerShell slingan.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-123">After the `Foreach` loop displays the letter d, PowerShell exits the loop.</span></span>

<span data-ttu-id="cbbd7-124">Hela `Foreach` instruktionen måste finnas på en rad för att köra den som ett kommando i PowerShell-Kommandotolken.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-124">The entire `Foreach` statement must appear on a single line to run it as a command at the PowerShell command prompt.</span></span> <span data-ttu-id="cbbd7-125">Hela `Foreach` instruktionen behöver inte visas på en enda rad om du placerar kommandot i en. ps1-skriptfil i stället.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-125">The entire `Foreach` statement does not have to appear on a single line if you place the command in a .ps1 script file instead.</span></span>

<span data-ttu-id="cbbd7-126">`Foreach` -instruktioner kan också användas tillsammans med cmdletar som returnerar en samling objekt.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-126">`Foreach` statements can also be used together with cmdlets that return a collection of items.</span></span> <span data-ttu-id="cbbd7-127">I följande exempel beskrivs de stegvisa anvisningarna i listan över objekt som returneras av `Get-ChildItem` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-127">In the following example, the Foreach statement steps through the list of items that is returned by the `Get-ChildItem` cmdlet.</span></span>

```powershell
foreach ($file in Get-ChildItem)
{
  Write-Host $file
}
```

<span data-ttu-id="cbbd7-128">Du kan förfina exemplet genom att använda en `If` instruktion för att begränsa resultaten som returneras.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-128">You can refine the example by using an `If` statement to limit the results that are returned.</span></span> <span data-ttu-id="cbbd7-129">I följande exempel `Foreach` Utför instruktionen samma upprepnings åtgärd som i föregående exempel, men lägger till en `If` instruktion som begränsar resultatet till filer som är större än 100 KB:</span><span class="sxs-lookup"><span data-stu-id="cbbd7-129">In the following example, the `Foreach` statement performs the same looping operation as the previous example, but it adds an `If` statement to limit the results to files that are greater than 100 kilobytes (KB):</span></span>

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
  }
}
```

<span data-ttu-id="cbbd7-130">I det här exemplet `Foreach` använder slingan en egenskap i `$file` variabeln för att utföra en jämförelse åtgärd ( `$file.length -gt 100KB` ).</span><span class="sxs-lookup"><span data-stu-id="cbbd7-130">In this example, the `Foreach` loop uses a property of the `$file` variable to perform a comparison operation (`$file.length -gt 100KB`).</span></span> <span data-ttu-id="cbbd7-131">`$file`Variabeln innehåller alla egenskaper i objektet som returneras av `Get-ChildItem` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-131">The `$file` variable contains all the properties in the object that is returned by the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="cbbd7-132">Därför kan du returnera mer än bara ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-132">Therefore, you can return more than just a file name.</span></span>
<span data-ttu-id="cbbd7-133">I nästa exempel returnerar PowerShell längden och den senaste åtkomst tiden i instruktions listan:</span><span class="sxs-lookup"><span data-stu-id="cbbd7-133">In the next example, PowerShell returns the length and the last access time inside the statement list:</span></span>

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
    Write-Host $file.length
    Write-Host $file.lastaccesstime
  }
}
```

<span data-ttu-id="cbbd7-134">I det här exemplet är du inte begränsad till att köra ett enda kommando i en instruktions lista.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-134">In this example, you are not limited to running a single command in a statement list.</span></span>

<span data-ttu-id="cbbd7-135">Du kan också använda en variabel utanför en `Foreach` slinga och öka variabeln i slingan.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-135">You can also use a variable outside a `Foreach` loop and increment the variable inside the loop.</span></span> <span data-ttu-id="cbbd7-136">I följande exempel räknas filer över 100 KB i storlek:</span><span class="sxs-lookup"><span data-stu-id="cbbd7-136">The following example counts files over 100 KB in size:</span></span>

```powershell
$i = 0
foreach ($file in Get-ChildItem) {
  if ($file.length -gt 100KB) {
    Write-Host $file "file size:" ($file.length / 1024).ToString("F0") KB
    $i = $i + 1
  }
}

if ($i -ne 0) {
  Write-Host
  Write-Host $i " file(s) over 100 KB in the current directory."
}
else {
  Write-Host "No files greater than 100 KB in the current directory."
}
```

<span data-ttu-id="cbbd7-137">I föregående exempel `$i` är variabeln inställd på `0` utanför loopen och variabeln ökar i slingan för varje fil som finns större än 100 kB.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-137">In the preceding example, the `$i` variable is set to `0` outside the loop, and the variable is incremented inside the loop for each file that is found that is larger than 100 KB.</span></span> <span data-ttu-id="cbbd7-138">När slingan avslutas `If` utvärderar en instruktion värdet för `$i` att visa antalet filer över 100 kB.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-138">When the loop exits, an `If` statement evaluates the value of `$i` to display a count of all the files over 100 KB.</span></span> <span data-ttu-id="cbbd7-139">Eller så visas ett meddelande om att det inte gick att hitta några filer över 100 KB.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-139">Or, it displays a message stating that no files over 100 KB were found.</span></span>

<span data-ttu-id="cbbd7-140">I föregående exempel visas också hur du formaterar filens längd resultat:</span><span class="sxs-lookup"><span data-stu-id="cbbd7-140">The previous example also demonstrates how to format the file length results:</span></span>

```powershell
($file.length / 1024).ToString("F0")
```

<span data-ttu-id="cbbd7-141">Värdet divideras med 1 024 för att visa resultaten i kilobyte i stället för byte, och det resulterande värdet formateras sedan med hjälp av den fasta punktens format för att ta bort alla decimal värden från resultatet.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-141">The value is divided by 1,024 to show the results in kilobytes rather than bytes, and the resulting value is then formatted using the fixed-point format specifier to remove any decimal values from the result.</span></span> <span data-ttu-id="cbbd7-142">0 gör format specifikationen Visa inga decimal platser.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-142">The 0 makes the format specifier show no decimal places.</span></span>

<span data-ttu-id="cbbd7-143">I följande exempel tolkar funktionen PowerShell-skript och-skript moduler och returnerar platsen för de funktioner som finns i.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-143">In the following example, the function defined parses PowerShell scripts and script modules and returns the location of functions contained within.</span></span> <span data-ttu-id="cbbd7-144">Exemplet visar hur du använder `MoveNext` -metoden (som fungerar ungefär som `skip X` i en `For` slinga) och `Current` egenskapen för `$foreach` variabeln i ett förgrunds skript block.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-144">The example demonstrates how to use the `MoveNext` method (which works similarly to `skip X` on a `For` loop) and the `Current` property of the `$foreach` variable inside of a foreach script block.</span></span> <span data-ttu-id="cbbd7-145">Exempel funktionen kan hitta funktioner i ett skript även om det finns ovanligt, eller inkonsekvent funktions definitioner som sträcker sig över flera rader.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-145">The example function can find functions in a script even if there are unusually- or inconsistently-spaced function definitions that span multiple lines.</span></span>

<span data-ttu-id="cbbd7-146">Mer information finns i [använda uppräknare](about_Automatic_Variables.md#using-enumerators).</span><span class="sxs-lookup"><span data-stu-id="cbbd7-146">For more information, see [Using Enumerators](about_Automatic_Variables.md#using-enumerators).</span></span>

```powershell
function Get-FunctionPosition {
  [CmdletBinding()]
  [OutputType('FunctionPosition')]
  param(
    [Parameter(Position = 0, Mandatory,
      ValueFromPipeline, ValueFromPipelineByPropertyName)]
    [ValidateNotNullOrEmpty()]
    [Alias('PSPath')]
    [System.String[]]
    $Path
  )

  process {
    try {
      $filesToProcess = if ($_ -is [System.IO.FileSystemInfo]) {
        $_
      } else {
        $filesToProcess = Get-Item -Path $Path
      }
      $parser = [System.Management.Automation.Language.Parser]
      foreach ($item in $filesToProcess) {
        if ($item.PSIsContainer -or
            $item.Extension -notin @('.ps1', '.psm1')) {
          continue
        }
        $tokens = $errors = $null
        $ast = $parser::ParseFile($item.FullName, ([REF]$tokens),
          ([REF]$errors))
        if ($errors) {
          $msg = "File '{0}' has {1} parser errors." -f $item.FullName,
            $errors.Count
          Write-Warning $msg
        }
        :tokenLoop foreach ($token in $tokens) {
          if ($token.Kind -ne 'Function') {
            continue
          }
          $position = $token.Extent.StartLineNumber
          do {
            if (-not $foreach.MoveNext()) {
              break tokenLoop
            }
            $token = $foreach.Current
          } until ($token.Kind -in @('Generic', 'Identifier'))
          $functionPosition = [pscustomobject]@{
            Name       = $token.Text
            LineNumber = $position
            Path       = $item.FullName
          }
          Add-Member -InputObject $functionPosition `
            -TypeName FunctionPosition -PassThru
        }
      }
    }
    catch {
      throw
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="cbbd7-147">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="cbbd7-147">SEE ALSO</span></span>

[<span data-ttu-id="cbbd7-148">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="cbbd7-148">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="cbbd7-149">about_If</span><span class="sxs-lookup"><span data-stu-id="cbbd7-149">about_If</span></span>](about_If.md)

[<span data-ttu-id="cbbd7-150">-Objekt</span><span class="sxs-lookup"><span data-stu-id="cbbd7-150">ForEach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
