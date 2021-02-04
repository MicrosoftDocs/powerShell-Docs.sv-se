---
description: Beskriver hur du definierar och använder parameter uppsättningar i avancerade funktioner.
ms.date: 02/11/2020
title: about_Parameter_Sets
ms.openlocfilehash: 405ef1c70b49f703f17a9e76f899a9643cc065bc
ms.sourcegitcommit: eb7ad1850550032880f5529b4e4281514cba1673
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/06/2021
ms.locfileid: "97917872"
---
# <a name="about-parameter-sets"></a><span data-ttu-id="9f9b8-103">Om parameter uppsättningar</span><span class="sxs-lookup"><span data-stu-id="9f9b8-103">About parameter sets</span></span>

## <a name="short-description"></a><span data-ttu-id="9f9b8-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9f9b8-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="9f9b8-105">Beskriver hur du definierar och använder parameter uppsättningar i avancerade funktioner.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-105">Describes how to define and use parameter sets in advanced functions.</span></span>

## <a name="long-description"></a><span data-ttu-id="9f9b8-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9f9b8-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="9f9b8-107">PowerShell använder parameter uppsättningar för att ge dig möjlighet att skriva en enda funktion som kan utföra olika åtgärder för olika scenarier.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-107">PowerShell uses parameter sets to enable you to write a single function that can do different actions for different scenarios.</span></span> <span data-ttu-id="9f9b8-108">Parameter uppsättningar gör att du kan exponera olika parametrar för användaren.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-108">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="9f9b8-109">Och för att returnera annan information baserat på de parametrar som anges av användaren.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-109">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="parameter-set-requirements"></a><span data-ttu-id="9f9b8-110">Krav för parameter uppsättning</span><span class="sxs-lookup"><span data-stu-id="9f9b8-110">Parameter set requirements</span></span>

<span data-ttu-id="9f9b8-111">Följande krav gäller för alla parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-111">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="9f9b8-112">Varje parameter uppsättning måste ha en unik kombination av parametrar.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-112">Each parameter set must have a unique combination of parameters.</span></span> <span data-ttu-id="9f9b8-113">Om möjligt måste minst en av de unika parametrarna vara en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-113">If possible, at least one of the unique parameters should be a mandatory parameter.</span></span>

- <span data-ttu-id="9f9b8-114">En parameter uppsättning som innehåller flera positions parametrar måste definiera unika positioner för varje parameter.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-114">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="9f9b8-115">Det går inte att ange samma position med två positions parametrar.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-115">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="9f9b8-116">Endast en parameter i en mängd kan deklarera `ValueFromPipeline` nyckelordet med värdet `true` .</span><span class="sxs-lookup"><span data-stu-id="9f9b8-116">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span> <span data-ttu-id="9f9b8-117">Flera parametrar kan definiera `ValueFromPipelineByPropertyName` nyckelordet med värdet `true` .</span><span class="sxs-lookup"><span data-stu-id="9f9b8-117">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="9f9b8-118">Om ingen parameter uppsättning anges för en parameter, tillhör parametern alla parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-118">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="9f9b8-119">Det finns en gräns på 32 parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-119">There is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="9f9b8-120">Standard parameter uppsättningar</span><span class="sxs-lookup"><span data-stu-id="9f9b8-120">Default parameter sets</span></span>

<span data-ttu-id="9f9b8-121">När flera parameter uppsättningar definieras `DefaultParameterSetName` anger nyckelordet för attributet **CmdletBinding** standard parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-121">When multiple parameter sets are defined, the `DefaultParameterSetName` keyword of the **CmdletBinding** attribute specifies the default parameter set.</span></span>
<span data-ttu-id="9f9b8-122">PowerShell använder standard parametern som anges när den inte kan avgöra vilken parameter som ska användas baserat på den information som ges till kommandot.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-122">PowerShell uses the default parameter set when it can't determine the parameter set to use based on the information provided to the command.</span></span> <span data-ttu-id="9f9b8-123">Mer information om attributet **CmdletBinding** finns i [about_functions_cmdletbindingattribute](about_functions_cmdletbindingattribute.md).</span><span class="sxs-lookup"><span data-stu-id="9f9b8-123">For more information about the **CmdletBinding** attribute, see [about_functions_cmdletbindingattribute](about_functions_cmdletbindingattribute.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="9f9b8-124">Deklarera parameter uppsättningar</span><span class="sxs-lookup"><span data-stu-id="9f9b8-124">Declaring parameter sets</span></span>

<span data-ttu-id="9f9b8-125">Om du vill skapa en parameter uppsättning måste du ange `ParameterSetName` nyckelordet för attributet **parameter** för varje parameter i parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-125">To create a parameter set, you must specify the `ParameterSetName` keyword of the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="9f9b8-126">För parametrar som tillhör flera parameter uppsättningar lägger du till ett **parameter** -attribut för varje parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-126">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span>

<span data-ttu-id="9f9b8-127">Med attributet **parameter** kan du definiera parametern på olika sätt för varje parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-127">The **Parameter** attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="9f9b8-128">Du kan till exempel definiera en parameter som obligatorisk i en uppsättning och valfri i en annan.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-128">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="9f9b8-129">Varje parameter uppsättning måste dock innehålla minst en unik parameter.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-129">However, each parameter set must contain at least one unique parameter.</span></span>

<span data-ttu-id="9f9b8-130">Parametrar som inte har en tilldelad parameter uppsättnings namn tillhör alla parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-130">Parameters that don't have an assigned parameter set name belong to all parameter sets.</span></span>

### <a name="example"></a><span data-ttu-id="9f9b8-131">Exempel</span><span class="sxs-lookup"><span data-stu-id="9f9b8-131">Example</span></span>

<span data-ttu-id="9f9b8-132">Följande exempel funktion räknar antalet rader, tecken och ord i en textfil.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-132">The following example function counts the number lines, characters, and words in a text file.</span></span> <span data-ttu-id="9f9b8-133">Med parametrar kan du ange vilka värden som du vill ska returneras och vilka filer du vill mäta.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-133">Using parameters, you can specify which values you want returned and which files you want to measure.</span></span> <span data-ttu-id="9f9b8-134">Det finns fyra parameter uppsättningar definierade:</span><span class="sxs-lookup"><span data-stu-id="9f9b8-134">There are four parameter sets defined:</span></span>

- <span data-ttu-id="9f9b8-135">Sökväg</span><span class="sxs-lookup"><span data-stu-id="9f9b8-135">Path</span></span>
- <span data-ttu-id="9f9b8-136">PathAll</span><span class="sxs-lookup"><span data-stu-id="9f9b8-136">PathAll</span></span>
- <span data-ttu-id="9f9b8-137">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9f9b8-137">LiteralPath</span></span>
- <span data-ttu-id="9f9b8-138">LiteralPathAll</span><span class="sxs-lookup"><span data-stu-id="9f9b8-138">LiteralPathAll</span></span>

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

<span data-ttu-id="9f9b8-139">Varje parameter uppsättning måste ha en unik parameter eller en unik kombination av parametrar.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-139">Each parameter set must have a unique parameter or a unique combination of parameters.</span></span> <span data-ttu-id="9f9b8-140">Parameter uppsättningarna `Path` och är `PathAll` mycket likartade men parametern **all** är unik för `PathAll` parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-140">The `Path` and `PathAll` parameter sets are very similar but the **All** parameter is unique to the `PathAll` parameter set.</span></span> <span data-ttu-id="9f9b8-141">Samma sak gäller för `LiteralPath` `LiteralPathAll` parameter uppsättningarna och.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-141">The same is true with the `LiteralPath` and `LiteralPathAll` parameter sets.</span></span> <span data-ttu-id="9f9b8-142">Även om `PathAll` parametern och `LiteralPathAll` anger båda har parametern **all** , särskiljer **sökvägen** och **LiteralPath** -parametrarna.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-142">Even though the `PathAll` and `LiteralPathAll` parameter sets both have the **All** parameter, the **Path** and **LiteralPath** parameters differentiate them.</span></span>

<span data-ttu-id="9f9b8-143">Använd `Get-Command -Syntax` visar syntaxen för varje parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-143">Use `Get-Command -Syntax` shows you the syntax of each parameter set.</span></span> <span data-ttu-id="9f9b8-144">Men det visar inte namnet på parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-144">However it does not show the name of the parameter set.</span></span> <span data-ttu-id="9f9b8-145">I följande exempel visas vilka parametrar som kan användas i varje parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-145">The following example shows which parameters can be used in each parameter set.</span></span>

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

### <a name="parameter-sets-in-action"></a><span data-ttu-id="9f9b8-146">Parameter uppsättningar i åtgärd</span><span class="sxs-lookup"><span data-stu-id="9f9b8-146">Parameter sets in action</span></span>

<span data-ttu-id="9f9b8-147">I det här exemplet använder vi `PathAll` parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="9f9b8-147">In this example, we are using the `PathAll` parameter set.</span></span>

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

