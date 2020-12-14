---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-debugger?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Debugger
ms.openlocfilehash: a2ef114a43a63b18f5dc2d28acf7cbc0de8392bd
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709391"
---
# <span data-ttu-id="826bc-102">Wait-Debugger</span><span class="sxs-lookup"><span data-stu-id="826bc-102">Wait-Debugger</span></span>

## <span data-ttu-id="826bc-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="826bc-103">SYNOPSIS</span></span>
<span data-ttu-id="826bc-104">Stoppar ett skript i fel söknings programmet innan du kör nästa instruktion i skriptet.</span><span class="sxs-lookup"><span data-stu-id="826bc-104">Stops a script in the debugger before running the next statement in the script.</span></span>

## <span data-ttu-id="826bc-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="826bc-105">SYNTAX</span></span>

```
Wait-Debugger [<CommonParameters>]
```

## <span data-ttu-id="826bc-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="826bc-106">DESCRIPTION</span></span>

<span data-ttu-id="826bc-107">Stoppar motorn för körning av PowerShell-skript på punkten omedelbart efter `Wait-Debugger` cmdleten och väntar på att en fel sökare ska kopplas.</span><span class="sxs-lookup"><span data-stu-id="826bc-107">Stops the PowerShell script execution engine at the point immediately after the `Wait-Debugger` cmdlet and waits for a debugger to be attached.</span></span> <span data-ttu-id="826bc-108">Detta påminner om att använda `Enable-RunspaceDebug -BreakAll` i en DSC-resurs men slutar vid en viss punkt i skriptet.</span><span class="sxs-lookup"><span data-stu-id="826bc-108">This is similar to using `Enable-RunspaceDebug -BreakAll` in a DSC resource but breaks at a specific point in the script.</span></span>

> [!CAUTION]
> <span data-ttu-id="826bc-109">Se till att du tar bort `Wait-Debugger` raderna när du är färdig.</span><span class="sxs-lookup"><span data-stu-id="826bc-109">Make sure you remove the `Wait-Debugger` lines after you are done.</span></span> <span data-ttu-id="826bc-110">Ett skript som körs verkar vara låst när det stoppas `Wait-Debugger` .</span><span class="sxs-lookup"><span data-stu-id="826bc-110">A running script appears to be hung when it is stopped at a `Wait-Debugger`.</span></span>

## <span data-ttu-id="826bc-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="826bc-111">EXAMPLES</span></span>

### <span data-ttu-id="826bc-112">Exempel 1: Infoga Bryt punkt för fel sökning</span><span class="sxs-lookup"><span data-stu-id="826bc-112">Example 1: Insert breakpoint for debugging</span></span>

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

## <span data-ttu-id="826bc-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="826bc-113">PARAMETERS</span></span>

### <span data-ttu-id="826bc-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="826bc-114">CommonParameters</span></span>

<span data-ttu-id="826bc-115">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="826bc-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="826bc-116">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="826bc-116">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="826bc-117">INDATA</span><span class="sxs-lookup"><span data-stu-id="826bc-117">INPUTS</span></span>

### <span data-ttu-id="826bc-118">Inga</span><span class="sxs-lookup"><span data-stu-id="826bc-118">None</span></span>

## <span data-ttu-id="826bc-119">UTDATA</span><span class="sxs-lookup"><span data-stu-id="826bc-119">OUTPUTS</span></span>

### <span data-ttu-id="826bc-120">Inga</span><span class="sxs-lookup"><span data-stu-id="826bc-120">None</span></span>

## <span data-ttu-id="826bc-121">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="826bc-121">NOTES</span></span>

## <span data-ttu-id="826bc-122">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="826bc-122">RELATED LINKS</span></span>

[<span data-ttu-id="826bc-123">Aktivera – DscDebug</span><span class="sxs-lookup"><span data-stu-id="826bc-123">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)

