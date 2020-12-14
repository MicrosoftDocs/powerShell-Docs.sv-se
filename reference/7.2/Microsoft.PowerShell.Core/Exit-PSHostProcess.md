---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: a1a8c6fcc16bcddc3bfcdade56cd75aadd179b74
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709229"
---
# <span data-ttu-id="b8b68-102">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="b8b68-102">Exit-PSHostProcess</span></span>

## <span data-ttu-id="b8b68-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b8b68-103">SYNOPSIS</span></span>
<span data-ttu-id="b8b68-104">Stänger en interaktiv session med en lokal process.</span><span class="sxs-lookup"><span data-stu-id="b8b68-104">Closes an interactive session with a local process.</span></span>

## <span data-ttu-id="b8b68-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b8b68-105">SYNTAX</span></span>

```
Exit-PSHostProcess [<CommonParameters>]
```

## <span data-ttu-id="b8b68-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b8b68-106">DESCRIPTION</span></span>

<span data-ttu-id="b8b68-107">`Exit-PSHostProcess`Cmdleten stänger en interaktiv session med en lokal process som du har öppnat genom att köra `Enter-PSHostProcess` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b8b68-107">The `Exit-PSHostProcess` cmdlet closes an interactive session with a local process that you have opened by running the `Enter-PSHostProcess` cmdlet.</span></span> <span data-ttu-id="b8b68-108">Du kör `Exit-PSHostProcess` cmdleten inifrån processen när du är färdig med fel sökningen eller fel sökning av ett skript som körs i en process.</span><span class="sxs-lookup"><span data-stu-id="b8b68-108">You run the `Exit-PSHostProcess` cmdlet from within the process, when you are finished debugging or troubleshooting a script that is running within a process.</span></span> <span data-ttu-id="b8b68-109">Från och med PowerShell 6,2 stöds denna cmdlet på plattformar som inte är Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="b8b68-109">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

## <span data-ttu-id="b8b68-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b8b68-110">EXAMPLES</span></span>

### <span data-ttu-id="b8b68-111">Exempel 1: avsluta en process</span><span class="sxs-lookup"><span data-stu-id="b8b68-111">Example 1: Exit a process</span></span>

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

<span data-ttu-id="b8b68-112">I det här exemplet har du arbetat i en aktiv process för att felsöka ett skript som körs i en körnings utrymme i processen, enligt beskrivningen i `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="b8b68-112">In this example, you have been working in an active process to debug a script running in a runspace in the process, as described in `Enter-PSHostProcess`.</span></span> <span data-ttu-id="b8b68-113">När du har angett `exit` kommandot för att avsluta fel söknings programmet, kör du `Exit-PSHostProcess` cmdleten för att stänga den interaktiva sessionen med processen.</span><span class="sxs-lookup"><span data-stu-id="b8b68-113">After you type the `exit` command to exit the debugger, run the `Exit-PSHostProcess` cmdlet to close your interactive session with the process.</span></span>
<span data-ttu-id="b8b68-114">Cmdleten stänger sessionen i processen och återgår till `PS C:\>` prompten.</span><span class="sxs-lookup"><span data-stu-id="b8b68-114">The cmdlet closes your session in the process, and returns you to the `PS C:\>` prompt.</span></span>

## <span data-ttu-id="b8b68-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b8b68-115">PARAMETERS</span></span>

### <span data-ttu-id="b8b68-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b8b68-116">CommonParameters</span></span>

<span data-ttu-id="b8b68-117">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b8b68-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b8b68-118">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b8b68-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b8b68-119">INDATA</span><span class="sxs-lookup"><span data-stu-id="b8b68-119">INPUTS</span></span>

## <span data-ttu-id="b8b68-120">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b8b68-120">OUTPUTS</span></span>

## <span data-ttu-id="b8b68-121">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b8b68-121">NOTES</span></span>

## <span data-ttu-id="b8b68-122">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b8b68-122">RELATED LINKS</span></span>

[<span data-ttu-id="b8b68-123">Retur-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="b8b68-123">Enter-PSHostProcess</span></span>](Enter-PSHostProcess.md)

