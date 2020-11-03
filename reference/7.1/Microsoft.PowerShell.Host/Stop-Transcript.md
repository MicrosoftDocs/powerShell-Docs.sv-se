---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: 86903ca648ff3ee58ec939143b7881741827f453
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261687"
---
# <span data-ttu-id="f4fff-103">Stop-Transcript</span><span class="sxs-lookup"><span data-stu-id="f4fff-103">Stop-Transcript</span></span>

## <span data-ttu-id="f4fff-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f4fff-104">SYNOPSIS</span></span>
<span data-ttu-id="f4fff-105">Stoppar en avskrift.</span><span class="sxs-lookup"><span data-stu-id="f4fff-105">Stops a transcript.</span></span>

## <span data-ttu-id="f4fff-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f4fff-106">SYNTAX</span></span>

```
Stop-Transcript [<CommonParameters>]
```

## <span data-ttu-id="f4fff-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f4fff-107">DESCRIPTION</span></span>

<span data-ttu-id="f4fff-108">`Stop-Transcript`Cmdleten stoppar en avskrift som startades av `Start-Transcript` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f4fff-108">The `Stop-Transcript` cmdlet stops a transcript that was started by the `Start-Transcript` cmdlet.</span></span>
<span data-ttu-id="f4fff-109">Du kan också avsluta en session för att stoppa avskriften.</span><span class="sxs-lookup"><span data-stu-id="f4fff-109">Alternatively, you can end a session to stop a transcript.</span></span>

## <span data-ttu-id="f4fff-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f4fff-110">EXAMPLES</span></span>

### <span data-ttu-id="f4fff-111">Exempel 1: stoppa alla avskrifter</span><span class="sxs-lookup"><span data-stu-id="f4fff-111">Example 1: Stop all transcripts</span></span>

```powershell
Stop-Transcript
```

<span data-ttu-id="f4fff-112">Det här kommandot stoppar alla avskrifter.</span><span class="sxs-lookup"><span data-stu-id="f4fff-112">This command stops all transcripts.</span></span>

## <span data-ttu-id="f4fff-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f4fff-113">PARAMETERS</span></span>

### <span data-ttu-id="f4fff-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f4fff-114">CommonParameters</span></span>

<span data-ttu-id="f4fff-115">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f4fff-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f4fff-116">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f4fff-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f4fff-117">INDATA</span><span class="sxs-lookup"><span data-stu-id="f4fff-117">INPUTS</span></span>

### <span data-ttu-id="f4fff-118">Inget</span><span class="sxs-lookup"><span data-stu-id="f4fff-118">None</span></span>

<span data-ttu-id="f4fff-119">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f4fff-119">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="f4fff-120">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f4fff-120">OUTPUTS</span></span>

### <span data-ttu-id="f4fff-121">System. String</span><span class="sxs-lookup"><span data-stu-id="f4fff-121">System.String</span></span>

<span data-ttu-id="f4fff-122">Denna cmdlet returnerar en sträng som innehåller ett status meddelande och sökvägen till utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="f4fff-122">This cmdlet returns a string that contains a status message and the path to the output file.</span></span>

## <span data-ttu-id="f4fff-123">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f4fff-123">NOTES</span></span>

* <span data-ttu-id="f4fff-124">Om en avskrift inte har startats Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="f4fff-124">If a transcript has not been started, the command fails.</span></span>

*

## <span data-ttu-id="f4fff-125">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f4fff-125">RELATED LINKS</span></span>

[<span data-ttu-id="f4fff-126">Start-avskrift</span><span class="sxs-lookup"><span data-stu-id="f4fff-126">Start-Transcript</span></span>](Start-Transcript.md)

