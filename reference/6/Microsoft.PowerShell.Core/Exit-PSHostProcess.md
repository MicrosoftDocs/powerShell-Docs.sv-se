---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: 0f076d21ce590b4f1d3eb5b06e891d753dbea638
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261566"
---
# <span data-ttu-id="9a81d-103">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="9a81d-103">Exit-PSHostProcess</span></span>

## <span data-ttu-id="9a81d-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9a81d-104">SYNOPSIS</span></span>
<span data-ttu-id="9a81d-105">Stänger en interaktiv session med en lokal process.</span><span class="sxs-lookup"><span data-stu-id="9a81d-105">Closes an interactive session with a local process.</span></span>

## <span data-ttu-id="9a81d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9a81d-106">SYNTAX</span></span>

```
Exit-PSHostProcess [<CommonParameters>]
```

## <span data-ttu-id="9a81d-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9a81d-107">DESCRIPTION</span></span>

<span data-ttu-id="9a81d-108">Cmdleten **exit-PSHostProcess** stänger en interaktiv session med en lokal process som du har öppnat genom att köra cmdleten Enter-PSHostProcess.</span><span class="sxs-lookup"><span data-stu-id="9a81d-108">The **Exit-PSHostProcess** cmdlet closes an interactive session with a local process that you have opened by running the Enter-PSHostProcess cmdlet.</span></span> <span data-ttu-id="9a81d-109">Du kör cmdleten **exit-PSHostProcess** inifrån processen när du är färdig med fel sökning eller fel sökning av skript som körs i en process.</span><span class="sxs-lookup"><span data-stu-id="9a81d-109">You run the **Exit-PSHostProcess** cmdlet from within the process, when you are finished debugging or troubleshooting a script that is running within a process.</span></span>

## <span data-ttu-id="9a81d-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9a81d-110">EXAMPLES</span></span>

### <span data-ttu-id="9a81d-111">Exempel 1: avsluta en process</span><span class="sxs-lookup"><span data-stu-id="9a81d-111">Example 1: Exit a process</span></span>

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

<span data-ttu-id="9a81d-112">I det här exemplet har du arbetat i en aktiv process för att felsöka ett skript som körs i en körnings utrymme i processen, enligt beskrivningen i Ange-PSHostProcess.</span><span class="sxs-lookup"><span data-stu-id="9a81d-112">In this example, you have been working in an active process to debug a script running in a runspace in the process, as described in Enter-PSHostProcess.</span></span> <span data-ttu-id="9a81d-113">När du har angett kommandot **Avsluta** för att avsluta fel söknings programmet, kör cmdleten **exit-PSHostProcess** för att stänga den interaktiva sessionen med processen.</span><span class="sxs-lookup"><span data-stu-id="9a81d-113">After you type the **exit** command to exit the debugger, run the **Exit-PSHostProcess** cmdlet to close your interactive session with the process.</span></span>
<span data-ttu-id="9a81d-114">Cmdleten stänger sessionen i processen och återgår till PS C: \\ \> prompten.</span><span class="sxs-lookup"><span data-stu-id="9a81d-114">The cmdlet closes your session in the process, and returns you to the PS C:\\\> prompt.</span></span>

## <span data-ttu-id="9a81d-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9a81d-115">PARAMETERS</span></span>

### <span data-ttu-id="9a81d-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9a81d-116">CommonParameters</span></span>

<span data-ttu-id="9a81d-117">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9a81d-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9a81d-118">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9a81d-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9a81d-119">INDATA</span><span class="sxs-lookup"><span data-stu-id="9a81d-119">INPUTS</span></span>

## <span data-ttu-id="9a81d-120">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9a81d-120">OUTPUTS</span></span>

## <span data-ttu-id="9a81d-121">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9a81d-121">NOTES</span></span>

## <span data-ttu-id="9a81d-122">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9a81d-122">RELATED LINKS</span></span>

[<span data-ttu-id="9a81d-123">Retur-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="9a81d-123">Enter-PSHostProcess</span></span>](Enter-PSHostProcess.md)
