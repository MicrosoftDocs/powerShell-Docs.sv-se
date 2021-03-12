---
description: Beskriver hur du definierar och använder parameter uppsättningar i avancerade funktioner.
title: about_Parameter_Sets
Locale: en-US
ms.date: 01/05/2021
schema: 2.0.0
ms.openlocfilehash: d9437c8d53a54e766b42e24cd405b1fa2fccc4f8
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195597"
---
# <a name="about-parameter-sets"></a><span data-ttu-id="05266-103">Om parameter uppsättningar</span><span class="sxs-lookup"><span data-stu-id="05266-103">About parameter sets</span></span>

## <a name="short-description"></a><span data-ttu-id="05266-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="05266-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="05266-105">Beskriver hur du definierar och använder parameter uppsättningar i avancerade funktioner.</span><span class="sxs-lookup"><span data-stu-id="05266-105">Describes how to define and use parameter sets in advanced functions.</span></span>

## <a name="long-description"></a><span data-ttu-id="05266-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="05266-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="05266-107">PowerShell använder parameter uppsättningar för att ge dig möjlighet att skriva en enda funktion som kan utföra olika åtgärder för olika scenarier.</span><span class="sxs-lookup"><span data-stu-id="05266-107">PowerShell uses parameter sets to enable you to write a single function that can do different actions for different scenarios.</span></span> <span data-ttu-id="05266-108">Parameter uppsättningar gör att du kan exponera olika parametrar för användaren.</span><span class="sxs-lookup"><span data-stu-id="05266-108">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="05266-109">Och för att returnera annan information baserat på de parametrar som anges av användaren.</span><span class="sxs-lookup"><span data-stu-id="05266-109">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="parameter-set-requirements"></a><span data-ttu-id="05266-110">Krav för parameter uppsättning</span><span class="sxs-lookup"><span data-stu-id="05266-110">Parameter set requirements</span></span>

<span data-ttu-id="05266-111">Följande krav gäller för alla parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="05266-111">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="05266-112">Varje parameter uppsättning måste ha en unik kombination av parametrar.</span><span class="sxs-lookup"><span data-stu-id="05266-112">Each parameter set must have a unique combination of parameters.</span></span> <span data-ttu-id="05266-113">Om möjligt måste minst en av de unika parametrarna vara en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="05266-113">If possible, at least one of the unique parameters should be a mandatory parameter.</span></span>

- <span data-ttu-id="05266-114">En parameter uppsättning som innehåller flera positions parametrar måste definiera unika positioner för varje parameter.</span><span class="sxs-lookup"><span data-stu-id="05266-114">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="05266-115">Det går inte att ange samma position med två positions parametrar.</span><span class="sxs-lookup"><span data-stu-id="05266-115">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="05266-116">Endast en parameter i en mängd kan deklarera `ValueFromPipeline` nyckelordet med värdet `true` .</span><span class="sxs-lookup"><span data-stu-id="05266-116">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span> <span data-ttu-id="05266-117">Flera parametrar kan definiera `ValueFromPipelineByPropertyName` nyckelordet med värdet `true` .</span><span class="sxs-lookup"><span data-stu-id="05266-117">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="05266-118">Om ingen parameter uppsättning anges för en parameter, tillhör parametern alla parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="05266-118">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="05266-119">Det finns en gräns på 32 parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="05266-119">There is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="05266-120">Standard parameter uppsättningar</span><span class="sxs-lookup"><span data-stu-id="05266-120">Default parameter sets</span></span>

<span data-ttu-id="05266-121">När flera parameter uppsättningar definieras `DefaultParameterSetName` anger nyckelordet för attributet **CmdletBinding** standard parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="05266-121">When multiple parameter sets are defined, the `DefaultParameterSetName` keyword of the **CmdletBinding** attribute specifies the default parameter set.</span></span>
<span data-ttu-id="05266-122">PowerShell använder standard parametern som anges när den inte kan avgöra vilken parameter som ska användas baserat på den information som ges till kommandot.</span><span class="sxs-lookup"><span data-stu-id="05266-122">PowerShell uses the default parameter set when it can't determine the parameter set to use based on the information provided to the command.</span></span> <span data-ttu-id="05266-123">Mer information om attributet **CmdletBinding** finns i [about_functions_cmdletbindingattribute](about_functions_cmdletbindingattribute.md).</span><span class="sxs-lookup"><span data-stu-id="05266-123">For more information about the **CmdletBinding** attribute, see [about_functions_cmdletbindingattribute](about_functions_cmdletbindingattribute.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="05266-124">Deklarera parameter uppsättningar</span><span class="sxs-lookup"><span data-stu-id="05266-124">Declaring parameter sets</span></span>

<span data-ttu-id="05266-125">Om du vill skapa en parameter uppsättning måste du ange `ParameterSetName` nyckelordet för attributet **parameter** för varje parameter i parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="05266-125">To create a parameter set, you must specify the `ParameterSetName` keyword of the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="05266-126">För parametrar som tillhör flera parameter uppsättningar lägger du till ett **parameter** -attribut för varje parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="05266-126">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span>

<span data-ttu-id="05266-127">Med attributet **parameter** kan du definiera parametern på olika sätt för varje parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="05266-127">The **Parameter** attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="05266-128">Du kan till exempel definiera en parameter som obligatorisk i en uppsättning och valfri i en annan.</span><span class="sxs-lookup"><span data-stu-id="05266-128">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="05266-129">Varje parameter uppsättning måste dock innehålla minst en unik parameter.</span><span class="sxs-lookup"><span data-stu-id="05266-129">However, each parameter set must contain at least one unique parameter.</span></span>

<span data-ttu-id="05266-130">Parametrar som inte har en tilldelad parameter uppsättnings namn tillhör alla parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="05266-130">Parameters that don't have an assigned parameter set name belong to all parameter sets.</span></span>

### <a name="example"></a><span data-ttu-id="05266-131">Exempel</span><span class="sxs-lookup"><span data-stu-id="05266-131">Example</span></span>

<span data-ttu-id="05266-132">Följande exempel funktion räknar antalet rader, tecken och ord i en textfil.</span><span class="sxs-lookup"><span data-stu-id="05266-132">The following example function counts the number lines, characters, and words in a text file.</span></span> <span data-ttu-id="05266-133">Med parametrar kan du ange vilka värden som du vill ska returneras och vilka filer du vill mäta.</span><span class="sxs-lookup"><span data-stu-id="05266-133">Using parameters, you can specify which values you want returned and which files you want to measure.</span></span> <span data-ttu-id="05266-134">Det finns fyra parameter uppsättningar definierade:</span><span class="sxs-lookup"><span data-stu-id="05266-134">There are four parameter sets defined:</span></span>

- <span data-ttu-id="05266-135">Sökväg</span><span class="sxs-lookup"><span data-stu-id="05266-135">Path</span></span>
- <span data-ttu-id="05266-136">PathAll</span><span class="sxs-lookup"><span data-stu-id="05266-136">PathAll</span></span>
- <span data-ttu-id="05266-137">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="05266-137">LiteralPath</span></span>
- <span data-ttu-id="05266-138">LiteralPathAll</span><span class="sxs-lookup"><span data-stu-id="05266-138">LiteralPathAll</span></span>

```powershell
function Measure-Lines {
    [CmdletBinding(DefaultParameterSetName = 'Path')]
    param (
        [Parameter(Mandatory = $true,
            ParameterSetName = 'Path',
            HelpMessage = 'Enter one or more filenames',
            Position = 0)]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'PathAll',
            Position = 0)]
        [string[]]$Path,

        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'LiteralPath',
            HelpMessage = 'Enter a single filename',
            ValueFromPipeline = $true)]
        [string]$LiteralPath,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Lines,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Words,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Characters,

        [Parameter(Mandatory = $true, ParameterSetName = 'PathAll')]
        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [switch]$All,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'PathAll')]
        [switch]$Recurse
    )

    begin {
        if ($All) {
            $Lines = $Words = $Characters = $true
        }
        elseif (($Words -eq $false) -and ($Characters -eq $false)) {
            $Lines = $true
        }

        if ($Path) {
            $Files = Get-ChildItem -Path $Path -Recurse:$Recurse
        }
        else {
            $Files = Get-ChildItem -LiteralPath $LiteralPath
        }
    }
    process {
        foreach ($file in $Files) {
            $result = [ordered]@{ }
            $result.Add('File', $file.fullname)

            $content = Get-Content -LiteralPath $file.fullname

            if ($Lines) { $result.Add('Lines', $content.Length) }

            if ($Words) {
                $wc = 0
                foreach ($line in $content) { $wc += $line.split(' ').Length }
                $result.Add('Words', $wc)
            }

            if ($Characters) {
                $cc = 0
                foreach ($line in $content) { $cc += $line.Length }
                $result.Add('Characters', $cc)
            }

            New-Object -TypeName psobject -Property $result
        }
    }
}
```

<span data-ttu-id="05266-139">Varje parameter uppsättning måste ha en unik parameter eller en unik kombination av parametrar.</span><span class="sxs-lookup"><span data-stu-id="05266-139">Each parameter set must have a unique parameter or a unique combination of parameters.</span></span> <span data-ttu-id="05266-140">Parameter uppsättningarna `Path` och är `PathAll` mycket likartade men parametern **all** är unik för `PathAll` parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="05266-140">The `Path` and `PathAll` parameter sets are very similar but the **All** parameter is unique to the `PathAll` parameter set.</span></span> <span data-ttu-id="05266-141">Samma sak gäller för `LiteralPath` `LiteralPathAll` parameter uppsättningarna och.</span><span class="sxs-lookup"><span data-stu-id="05266-141">The same is true with the `LiteralPath` and `LiteralPathAll` parameter sets.</span></span> <span data-ttu-id="05266-142">Även om `PathAll` parametern och `LiteralPathAll` anger båda har parametern **all** , särskiljer **sökvägen** och **LiteralPath** -parametrarna.</span><span class="sxs-lookup"><span data-stu-id="05266-142">Even though the `PathAll` and `LiteralPathAll` parameter sets both have the **All** parameter, the **Path** and **LiteralPath** parameters differentiate them.</span></span>

<span data-ttu-id="05266-143">Använd `Get-Command -Syntax` visar syntaxen för varje parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="05266-143">Use `Get-Command -Syntax` shows you the syntax of each parameter set.</span></span> <span data-ttu-id="05266-144">Men det visar inte namnet på parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="05266-144">However it does not show the name of the parameter set.</span></span> <span data-ttu-id="05266-145">I följande exempel visas vilka parametrar som kan användas i varje parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="05266-145">The following example shows which parameters can be used in each parameter set.</span></span>

```powershell
(Get-Command Measure-Lines).ParameterSets |
  Select-Object -Property @{n='ParameterSetName';e={$_.name}},
    @{n='Parameters';e={$_.ToString()}}
```

```Output
ParameterSetName Parameters
---------------- ----------
Path             [-Path] <string[]> [-Lines] [-Words] [-Characters] [-Recurse] [<CommonParameters>]
PathAll          [-Path] <string[]> -All [-Recurse] [<CommonParameters>]
LiteralPath      -LiteralPath <string> [-Lines] [-Words] [-Characters] [<CommonParameters>]
LiteralPathAll   -LiteralPath <string> -All [<CommonParameters>]
```

### <a name="parameter-sets-in-action"></a><span data-ttu-id="05266-146">Parameter uppsättningar i åtgärd</span><span class="sxs-lookup"><span data-stu-id="05266-146">Parameter sets in action</span></span>

<span data-ttu-id="05266-147">I det här exemplet använder vi `PathAll` parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="05266-147">In this example, we are using the `PathAll` parameter set.</span></span>

```powershell
Measure-Lines test* -All
```

```Output
File                       Lines Words Characters
----                       ----- ----- ----------
C:\temp\test\test.help.txt    31   562       2059
C:\temp\test\test.md          30  1527       3224
C:\temp\test\test.ps1          3     3         79
C:\temp\test\test[1].txt      31   562       2059
```

