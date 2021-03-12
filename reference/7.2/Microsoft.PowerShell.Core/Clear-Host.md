---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Host
ms.openlocfilehash: 6b7541fba77c4160cf8d5c2dd36a4bad0bf99c5f
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195174"
---
# <span data-ttu-id="cc2fc-102">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="cc2fc-102">Clear-Host</span></span>

## <span data-ttu-id="cc2fc-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="cc2fc-103">SYNOPSIS</span></span>

<span data-ttu-id="cc2fc-104">Tar bort visningen i värd programmet.</span><span class="sxs-lookup"><span data-stu-id="cc2fc-104">Clears the display in the host program.</span></span>

## <span data-ttu-id="cc2fc-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cc2fc-105">SYNTAX</span></span>

```
Clear-Host [<CommonParameters>]
```

## <span data-ttu-id="cc2fc-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="cc2fc-106">DESCRIPTION</span></span>

<span data-ttu-id="cc2fc-107">`Clear-Host`Funktionen tar bort all text från den aktuella visningen, inklusive kommandon och utdata som kan ha samlats.</span><span class="sxs-lookup"><span data-stu-id="cc2fc-107">The `Clear-Host` function removes all text from the current display, including commands and output that might have accumulated.</span></span> <span data-ttu-id="cc2fc-108">När du är klar visas kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="cc2fc-108">When complete, it displays the command prompt.</span></span> <span data-ttu-id="cc2fc-109">Du kan använda funktions namnet eller dess alias `cls` .</span><span class="sxs-lookup"><span data-stu-id="cc2fc-109">You can use the function name or its alias, `cls`.</span></span>

<span data-ttu-id="cc2fc-110">`Clear-Host` påverkar endast den aktuella visningen.</span><span class="sxs-lookup"><span data-stu-id="cc2fc-110">`Clear-Host` affects only the current display.</span></span> <span data-ttu-id="cc2fc-111">Det tar inte bort sparade resultat eller tar bort objekt från sessionen.</span><span class="sxs-lookup"><span data-stu-id="cc2fc-111">It does not delete saved results or remove any items from the session.</span></span> <span data-ttu-id="cc2fc-112">Sessionsbaserade objekt, till exempel variabler och funktioner, påverkas inte av den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="cc2fc-112">Session-specific items, such as variables and functions, are not affected by this function.</span></span>

<span data-ttu-id="cc2fc-113">Eftersom `Clear-Host` funktionens funktion bestäms av värd programmet `Clear-Host` kan fungera annorlunda i olika värd program.</span><span class="sxs-lookup"><span data-stu-id="cc2fc-113">Because the behavior of the `Clear-Host` function is determined by the host program, `Clear-Host` might work differently in different host programs.</span></span>

## <span data-ttu-id="cc2fc-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="cc2fc-114">EXAMPLES</span></span>

### <span data-ttu-id="cc2fc-115">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="cc2fc-115">Example 1</span></span>

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

<span data-ttu-id="cc2fc-116">Det här kommandot använder `cls` aliaset för `Clear-Host` för att ta bort den aktuella visningen.</span><span class="sxs-lookup"><span data-stu-id="cc2fc-116">This command uses the `cls` alias of `Clear-Host` to clear the current display.</span></span>

## <span data-ttu-id="cc2fc-117">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="cc2fc-117">PARAMETERS</span></span>

### <span data-ttu-id="cc2fc-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cc2fc-118">CommonParameters</span></span>
<span data-ttu-id="cc2fc-119">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cc2fc-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cc2fc-120">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cc2fc-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cc2fc-121">INDATA</span><span class="sxs-lookup"><span data-stu-id="cc2fc-121">INPUTS</span></span>

### <span data-ttu-id="cc2fc-122">Inget</span><span class="sxs-lookup"><span data-stu-id="cc2fc-122">None</span></span>

<span data-ttu-id="cc2fc-123">Du kan inte skicka pipe-ininformation till `Clear-Host` .</span><span class="sxs-lookup"><span data-stu-id="cc2fc-123">You cannot pipe input to `Clear-Host`.</span></span>

## <span data-ttu-id="cc2fc-124">UTDATA</span><span class="sxs-lookup"><span data-stu-id="cc2fc-124">OUTPUTS</span></span>

### <span data-ttu-id="cc2fc-125">Inget</span><span class="sxs-lookup"><span data-stu-id="cc2fc-125">None</span></span>

<span data-ttu-id="cc2fc-126">`Clear-Host` genererar inga utdata</span><span class="sxs-lookup"><span data-stu-id="cc2fc-126">`Clear-Host` does not generate any output</span></span>

## <span data-ttu-id="cc2fc-127">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="cc2fc-127">NOTES</span></span>

<span data-ttu-id="cc2fc-128">`Clear-Host` är en enkel funktion, inte en avancerad funktion.</span><span class="sxs-lookup"><span data-stu-id="cc2fc-128">`Clear-Host` is a simple function, not an advanced function.</span></span> <span data-ttu-id="cc2fc-129">Därför kan du inte använda vanliga parametrar, t. ex. **fel sökning**, i ett `Clear-Host` kommando.</span><span class="sxs-lookup"><span data-stu-id="cc2fc-129">As such, you cannot use common parameters, such as **Debug**, in a `Clear-Host` command.</span></span>

## <span data-ttu-id="cc2fc-130">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="cc2fc-130">RELATED LINKS</span></span>

[<span data-ttu-id="cc2fc-131">Hämta värd</span><span class="sxs-lookup"><span data-stu-id="cc2fc-131">Get-Host</span></span>](../Microsoft.PowerShell.Utility/Get-Host.md)

[<span data-ttu-id="cc2fc-132">Ut-värd</span><span class="sxs-lookup"><span data-stu-id="cc2fc-132">Out-Host</span></span>](Out-Host.md)

[<span data-ttu-id="cc2fc-133">Read-Host</span><span class="sxs-lookup"><span data-stu-id="cc2fc-133">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)

[<span data-ttu-id="cc2fc-134">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="cc2fc-134">Write-Host</span></span>](../Microsoft.PowerShell.Utility/Write-Host.md)

