---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: 1734758d34e89020f579fffa217cef58eb222736
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344056"
---
# <span data-ttu-id="07a3b-103">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="07a3b-103">Exit-PSHostProcess</span></span>

## <span data-ttu-id="07a3b-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="07a3b-104">SYNOPSIS</span></span>
<span data-ttu-id="07a3b-105">Stänger en interaktiv session med en lokal process.</span><span class="sxs-lookup"><span data-stu-id="07a3b-105">Closes an interactive session with a local process.</span></span>

## <span data-ttu-id="07a3b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="07a3b-106">SYNTAX</span></span>

```
Exit-PSHostProcess [<CommonParameters>]
```

## <span data-ttu-id="07a3b-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="07a3b-107">DESCRIPTION</span></span>

<span data-ttu-id="07a3b-108">`Exit-PSHostProcess`Cmdleten stänger en interaktiv session med en lokal process som du har öppnat genom att köra `Enter-PSHostProcess` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="07a3b-108">The `Exit-PSHostProcess` cmdlet closes an interactive session with a local process that you have opened by running the `Enter-PSHostProcess` cmdlet.</span></span> <span data-ttu-id="07a3b-109">Du kör `Exit-PSHostProcess` cmdleten inifrån processen när du är färdig med fel sökningen eller fel sökning av ett skript som körs i en process.</span><span class="sxs-lookup"><span data-stu-id="07a3b-109">You run the `Exit-PSHostProcess` cmdlet from within the process, when you are finished debugging or troubleshooting a script that is running within a process.</span></span> <span data-ttu-id="07a3b-110">Från och med PowerShell 6,2 stöds denna cmdlet på plattformar som inte är Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="07a3b-110">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

## <span data-ttu-id="07a3b-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="07a3b-111">EXAMPLES</span></span>

### <span data-ttu-id="07a3b-112">Exempel 1: avsluta en process</span><span class="sxs-lookup"><span data-stu-id="07a3b-112">Example 1: Exit a process</span></span>

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

<span data-ttu-id="07a3b-113">I det här exemplet har du arbetat i en aktiv process för att felsöka ett skript som körs i en körnings utrymme i processen, enligt beskrivningen i `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="07a3b-113">In this example, you have been working in an active process to debug a script running in a runspace in the process, as described in `Enter-PSHostProcess`.</span></span> <span data-ttu-id="07a3b-114">När du har angett `exit` kommandot för att avsluta fel söknings programmet, kör du `Exit-PSHostProcess` cmdleten för att stänga den interaktiva sessionen med processen.</span><span class="sxs-lookup"><span data-stu-id="07a3b-114">After you type the `exit` command to exit the debugger, run the `Exit-PSHostProcess` cmdlet to close your interactive session with the process.</span></span>
<span data-ttu-id="07a3b-115">Cmdleten stänger sessionen i processen och återgår till `PS C:\>` prompten.</span><span class="sxs-lookup"><span data-stu-id="07a3b-115">The cmdlet closes your session in the process, and returns you to the `PS C:\>` prompt.</span></span>

## <span data-ttu-id="07a3b-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="07a3b-116">PARAMETERS</span></span>

### <span data-ttu-id="07a3b-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="07a3b-117">CommonParameters</span></span>

<span data-ttu-id="07a3b-118">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="07a3b-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="07a3b-119">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="07a3b-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="07a3b-120">INDATA</span><span class="sxs-lookup"><span data-stu-id="07a3b-120">INPUTS</span></span>

## <span data-ttu-id="07a3b-121">UTDATA</span><span class="sxs-lookup"><span data-stu-id="07a3b-121">OUTPUTS</span></span>

## <span data-ttu-id="07a3b-122">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="07a3b-122">NOTES</span></span>

## <span data-ttu-id="07a3b-123">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="07a3b-123">RELATED LINKS</span></span>

[<span data-ttu-id="07a3b-124">Retur-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="07a3b-124">Enter-PSHostProcess</span></span>](Enter-PSHostProcess.md)
