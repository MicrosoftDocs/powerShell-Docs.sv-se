---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-host?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Host
ms.openlocfilehash: 592ae387737981c5b6510399d732b9037437257f
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194825"
---
# <span data-ttu-id="e7153-103">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="e7153-103">Clear-Host</span></span>

## <span data-ttu-id="e7153-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e7153-104">SYNOPSIS</span></span>

<span data-ttu-id="e7153-105">Tar bort visningen i värd programmet.</span><span class="sxs-lookup"><span data-stu-id="e7153-105">Clears the display in the host program.</span></span>

## <span data-ttu-id="e7153-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e7153-106">SYNTAX</span></span>

```
Clear-Host [<CommonParameters>]
```

## <span data-ttu-id="e7153-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e7153-107">DESCRIPTION</span></span>

<span data-ttu-id="e7153-108">`Clear-Host`Funktionen tar bort all text från den aktuella visningen, inklusive kommandon och utdata som kan ha samlats.</span><span class="sxs-lookup"><span data-stu-id="e7153-108">The `Clear-Host` function removes all text from the current display, including commands and output that might have accumulated.</span></span> <span data-ttu-id="e7153-109">När du är klar visas kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="e7153-109">When complete, it displays the command prompt.</span></span> <span data-ttu-id="e7153-110">Du kan använda funktions namnet eller dess alias `cls` .</span><span class="sxs-lookup"><span data-stu-id="e7153-110">You can use the function name or its alias, `cls`.</span></span>

<span data-ttu-id="e7153-111">`Clear-Host` påverkar endast den aktuella visningen.</span><span class="sxs-lookup"><span data-stu-id="e7153-111">`Clear-Host` affects only the current display.</span></span> <span data-ttu-id="e7153-112">Det tar inte bort sparade resultat eller tar bort objekt från sessionen.</span><span class="sxs-lookup"><span data-stu-id="e7153-112">It does not delete saved results or remove any items from the session.</span></span> <span data-ttu-id="e7153-113">Sessionsbaserade objekt, till exempel variabler och funktioner, påverkas inte av den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="e7153-113">Session-specific items, such as variables and functions, are not affected by this function.</span></span>

<span data-ttu-id="e7153-114">Eftersom `Clear-Host` funktionens funktion bestäms av värd programmet `Clear-Host` kan fungera annorlunda i olika värd program.</span><span class="sxs-lookup"><span data-stu-id="e7153-114">Because the behavior of the `Clear-Host` function is determined by the host program, `Clear-Host` might work differently in different host programs.</span></span>

## <span data-ttu-id="e7153-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e7153-115">EXAMPLES</span></span>

### <span data-ttu-id="e7153-116">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="e7153-116">Example 1</span></span>

```
# Before

PS C:\> Get-Process

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    843      33    14428      22556    99    17.41   1688 CcmExec
     44       6     2196       4964    52     0.23    692 conhost
    646      12     2332       4896    49     1.12    388 csrss
    189      11     2860       7084   114     0.66   2896 csrss
     78      11     1876       4008    42     0.22   4000 csrss
     76       7     1848       5064    54     0.08   1028 dwm
    610      41    23952      44048   208     4.40   2080 explorer
      0       0        0         24     0               0 Idle
    182      32     7692      15980    91     0.23   3056 LogonUI
    186      25     7832      16068    91     0.27   3996 LogonUI
   1272      32    11512      20432    58    25.07    548 lsass
    267      10     3536       6736    34     0.80    556 lsm
    137      17     3520       7472    61     0.05   1220 msdtc
    447      31    70316      84476   201 1,429.67    836 MsMpEng
    265      18     7136      15628   134     2.20   3544 msseces
    248      16     6476       4076    76     0.22   1592 NisSrv
    368      25    61312      65508   614     1.78    848 powershell
    101       8     2304       6624    70     0.64   3648 rdpclip
    258      15     6804      12156    50     2.65    536 services
...

PS C:\> cls
#After

PS C:>
```

<span data-ttu-id="e7153-117">Det här kommandot använder `cls` aliaset för `Clear-Host` för att ta bort den aktuella visningen.</span><span class="sxs-lookup"><span data-stu-id="e7153-117">This command uses the `cls` alias of `Clear-Host` to clear the current display.</span></span>

## <span data-ttu-id="e7153-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e7153-118">PARAMETERS</span></span>

### <span data-ttu-id="e7153-119">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e7153-119">CommonParameters</span></span>
<span data-ttu-id="e7153-120">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e7153-120">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e7153-121">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e7153-121">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e7153-122">INDATA</span><span class="sxs-lookup"><span data-stu-id="e7153-122">INPUTS</span></span>

### <span data-ttu-id="e7153-123">Inget</span><span class="sxs-lookup"><span data-stu-id="e7153-123">None</span></span>

<span data-ttu-id="e7153-124">Du kan inte skicka pipe-ininformation till `Clear-Host` .</span><span class="sxs-lookup"><span data-stu-id="e7153-124">You cannot pipe input to `Clear-Host`.</span></span>

## <span data-ttu-id="e7153-125">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e7153-125">OUTPUTS</span></span>

### <span data-ttu-id="e7153-126">Inget</span><span class="sxs-lookup"><span data-stu-id="e7153-126">None</span></span>

<span data-ttu-id="e7153-127">`Clear-Host` genererar inga utdata</span><span class="sxs-lookup"><span data-stu-id="e7153-127">`Clear-Host` does not generate any output</span></span>

## <span data-ttu-id="e7153-128">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e7153-128">NOTES</span></span>

<span data-ttu-id="e7153-129">`Clear-Host` är en enkel funktion, inte en avancerad funktion.</span><span class="sxs-lookup"><span data-stu-id="e7153-129">`Clear-Host` is a simple function, not an advanced function.</span></span> <span data-ttu-id="e7153-130">Därför kan du inte använda vanliga parametrar, t. ex. **fel sökning**, i ett `Clear-Host` kommando.</span><span class="sxs-lookup"><span data-stu-id="e7153-130">As such, you cannot use common parameters, such as **Debug**, in a `Clear-Host` command.</span></span>

## <span data-ttu-id="e7153-131">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e7153-131">RELATED LINKS</span></span>

[<span data-ttu-id="e7153-132">Hämta värd</span><span class="sxs-lookup"><span data-stu-id="e7153-132">Get-Host</span></span>](../Microsoft.PowerShell.Utility/Get-Host.md)

[<span data-ttu-id="e7153-133">Ut-värd</span><span class="sxs-lookup"><span data-stu-id="e7153-133">Out-Host</span></span>](Out-Host.md)

[<span data-ttu-id="e7153-134">Read-Host</span><span class="sxs-lookup"><span data-stu-id="e7153-134">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)

[<span data-ttu-id="e7153-135">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="e7153-135">Write-Host</span></span>](../Microsoft.PowerShell.Utility/Write-Host.md)
