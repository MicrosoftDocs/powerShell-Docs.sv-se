---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: 22298a898bd45a9be5eaf98d4963b98ab1bf063b
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261511"
---
# <span data-ttu-id="b7fb9-103">Stop-Transcript</span><span class="sxs-lookup"><span data-stu-id="b7fb9-103">Stop-Transcript</span></span>

## <span data-ttu-id="b7fb9-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b7fb9-104">SYNOPSIS</span></span>
<span data-ttu-id="b7fb9-105">Stoppar en avskrift.</span><span class="sxs-lookup"><span data-stu-id="b7fb9-105">Stops a transcript.</span></span>

## <span data-ttu-id="b7fb9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b7fb9-106">SYNTAX</span></span>

```
Stop-Transcript [<CommonParameters>]
```

## <span data-ttu-id="b7fb9-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b7fb9-107">DESCRIPTION</span></span>
<span data-ttu-id="b7fb9-108">`Stop-Transcript`Cmdleten stoppar en avskrift som startades av `Start-Transcript` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b7fb9-108">The `Stop-Transcript` cmdlet stops a transcript that was started by the `Start-Transcript` cmdlet.</span></span>
<span data-ttu-id="b7fb9-109">Du kan också avsluta en session för att stoppa avskriften.</span><span class="sxs-lookup"><span data-stu-id="b7fb9-109">Alternatively, you can end a session to stop a transcript.</span></span>

## <span data-ttu-id="b7fb9-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b7fb9-110">EXAMPLES</span></span>

### <span data-ttu-id="b7fb9-111">Exempel 1: stoppa alla avskrifter</span><span class="sxs-lookup"><span data-stu-id="b7fb9-111">Example 1: Stop all transcripts</span></span>

```powershell
Stop-Transcript
```

<span data-ttu-id="b7fb9-112">Det här kommandot stoppar alla avskrifter.</span><span class="sxs-lookup"><span data-stu-id="b7fb9-112">This command stops all transcripts.</span></span>

## <span data-ttu-id="b7fb9-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b7fb9-113">PARAMETERS</span></span>

### <span data-ttu-id="b7fb9-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b7fb9-114">CommonParameters</span></span>
<span data-ttu-id="b7fb9-115">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b7fb9-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b7fb9-116">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b7fb9-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b7fb9-117">INDATA</span><span class="sxs-lookup"><span data-stu-id="b7fb9-117">INPUTS</span></span>

### <span data-ttu-id="b7fb9-118">Inget</span><span class="sxs-lookup"><span data-stu-id="b7fb9-118">None</span></span>
<span data-ttu-id="b7fb9-119">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b7fb9-119">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="b7fb9-120">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b7fb9-120">OUTPUTS</span></span>

### <span data-ttu-id="b7fb9-121">System. String</span><span class="sxs-lookup"><span data-stu-id="b7fb9-121">System.String</span></span>
<span data-ttu-id="b7fb9-122">Denna cmdlet returnerar en sträng som innehåller ett status meddelande och sökvägen till utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="b7fb9-122">This cmdlet returns a string that contains a status message and the path to the output file.</span></span>

## <span data-ttu-id="b7fb9-123">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b7fb9-123">NOTES</span></span>

* <span data-ttu-id="b7fb9-124">Om en avskrift inte har startats Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="b7fb9-124">If a transcript has not been started, the command fails.</span></span>

*

## <span data-ttu-id="b7fb9-125">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b7fb9-125">RELATED LINKS</span></span>

[<span data-ttu-id="b7fb9-126">Start-avskrift</span><span class="sxs-lookup"><span data-stu-id="b7fb9-126">Start-Transcript</span></span>](Start-Transcript.md)
