---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-debugger?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Debugger
ms.openlocfilehash: b0b2205efdef6ddbe1f7e8f552c8422a1f1f558b
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261611"
---
# <span data-ttu-id="7a945-103">Wait-Debugger</span><span class="sxs-lookup"><span data-stu-id="7a945-103">Wait-Debugger</span></span>

## <span data-ttu-id="7a945-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7a945-104">SYNOPSIS</span></span>
<span data-ttu-id="7a945-105">Stoppar ett skript i fel söknings programmet innan du kör nästa instruktion i skriptet.</span><span class="sxs-lookup"><span data-stu-id="7a945-105">Stops a script in the debugger before running the next statement in the script.</span></span>

## <span data-ttu-id="7a945-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7a945-106">SYNTAX</span></span>

```
Wait-Debugger [<CommonParameters>]
```

## <span data-ttu-id="7a945-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7a945-107">DESCRIPTION</span></span>

<span data-ttu-id="7a945-108">Stoppar motorn för körning av PowerShell-skript på punkten omedelbart efter `Wait-Debugger` cmdleten och väntar på att en fel sökare ska kopplas.</span><span class="sxs-lookup"><span data-stu-id="7a945-108">Stops the PowerShell script execution engine at the point immediately after the `Wait-Debugger` cmdlet and waits for a debugger to be attached.</span></span> <span data-ttu-id="7a945-109">Detta påminner om att använda `Enable-RunspaceDebug -BreakAll` i en DSC-resurs men slutar vid en viss punkt i skriptet.</span><span class="sxs-lookup"><span data-stu-id="7a945-109">This is similar to using `Enable-RunspaceDebug -BreakAll` in a DSC resource but breaks at a specific point in the script.</span></span>

> [!CAUTION]
> <span data-ttu-id="7a945-110">Se till att du tar bort `Wait-Debugger` raderna när du är färdig.</span><span class="sxs-lookup"><span data-stu-id="7a945-110">Make sure you remove the `Wait-Debugger` lines after you are done.</span></span> <span data-ttu-id="7a945-111">Ett skript som körs verkar vara låst när det stoppas `Wait-Debugger` .</span><span class="sxs-lookup"><span data-stu-id="7a945-111">A running script appears to be hung when it is stopped at a `Wait-Debugger`.</span></span>

## <span data-ttu-id="7a945-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7a945-112">EXAMPLES</span></span>

### <span data-ttu-id="7a945-113">Exempel 1: Infoga Bryt punkt för fel sökning</span><span class="sxs-lookup"><span data-stu-id="7a945-113">Example 1: Insert breakpoint for debugging</span></span>

```
[DscResource()]
class FileResource
{
    [DscProperty(Key)]
    [string] $Path

    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    [DscProperty(Mandatory)]
    [string] $SourcePath

    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime


    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (! $fileExists)
            {
               $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    [bool] Test()
    {
        $present = Test-Path -LiteralPath $this.Path

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return (! $present)
        }
    }

    [FileResource] Get()
    {
        $present = Test-Path -Path $this.Path

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    [void] CopyFile()
    {
        # Testing only - Remove before deployment!
        Wait-Debugger

        if (! (Test-Path -LiteralPath $this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose "Copying $($this.SourcePath) to $($this.Path)"

        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
}
```

## <span data-ttu-id="7a945-114">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7a945-114">PARAMETERS</span></span>

### <span data-ttu-id="7a945-115">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7a945-115">CommonParameters</span></span>

<span data-ttu-id="7a945-116">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7a945-116">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7a945-117">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="7a945-117">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="7a945-118">INDATA</span><span class="sxs-lookup"><span data-stu-id="7a945-118">INPUTS</span></span>

### <span data-ttu-id="7a945-119">Inget</span><span class="sxs-lookup"><span data-stu-id="7a945-119">None</span></span>

## <span data-ttu-id="7a945-120">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7a945-120">OUTPUTS</span></span>

### <span data-ttu-id="7a945-121">Inget</span><span class="sxs-lookup"><span data-stu-id="7a945-121">None</span></span>

## <span data-ttu-id="7a945-122">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7a945-122">NOTES</span></span>

## <span data-ttu-id="7a945-123">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7a945-123">RELATED LINKS</span></span>

[<span data-ttu-id="7a945-124">Aktivera – DscDebug</span><span class="sxs-lookup"><span data-stu-id="7a945-124">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)

