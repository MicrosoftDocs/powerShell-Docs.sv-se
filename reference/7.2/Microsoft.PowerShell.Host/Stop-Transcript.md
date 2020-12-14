---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: 16b41711e98276fee37d56f77f57e7372daa4cf3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709558"
---
# <span data-ttu-id="b8b68-102">Stop-Transcript</span><span class="sxs-lookup"><span data-stu-id="b8b68-102">Stop-Transcript</span></span>

## <span data-ttu-id="b8b68-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b8b68-103">SYNOPSIS</span></span>
<span data-ttu-id="b8b68-104">Stoppar en avskrift.</span><span class="sxs-lookup"><span data-stu-id="b8b68-104">Stops a transcript.</span></span>

## <span data-ttu-id="b8b68-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b8b68-105">SYNTAX</span></span>

```
Stop-Transcript [<CommonParameters>]
```

## <span data-ttu-id="b8b68-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b8b68-106">DESCRIPTION</span></span>

<span data-ttu-id="b8b68-107">`Stop-Transcript`Cmdleten stoppar en avskrift som startades av `Start-Transcript` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b8b68-107">The `Stop-Transcript` cmdlet stops a transcript that was started by the `Start-Transcript` cmdlet.</span></span>
<span data-ttu-id="b8b68-108">Du kan också avsluta en session för att stoppa avskriften.</span><span class="sxs-lookup"><span data-stu-id="b8b68-108">Alternatively, you can end a session to stop a transcript.</span></span>

## <span data-ttu-id="b8b68-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b8b68-109">EXAMPLES</span></span>

### <span data-ttu-id="b8b68-110">Exempel 1: stoppa alla avskrifter</span><span class="sxs-lookup"><span data-stu-id="b8b68-110">Example 1: Stop all transcripts</span></span>

```powershell
Stop-Transcript
```

<span data-ttu-id="b8b68-111">Det här kommandot stoppar alla avskrifter.</span><span class="sxs-lookup"><span data-stu-id="b8b68-111">This command stops all transcripts.</span></span>

## <span data-ttu-id="b8b68-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b8b68-112">PARAMETERS</span></span>

### <span data-ttu-id="b8b68-113">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b8b68-113">CommonParameters</span></span>

<span data-ttu-id="b8b68-114">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b8b68-114">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b8b68-115">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b8b68-115">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b8b68-116">INDATA</span><span class="sxs-lookup"><span data-stu-id="b8b68-116">INPUTS</span></span>

### <span data-ttu-id="b8b68-117">Inga</span><span class="sxs-lookup"><span data-stu-id="b8b68-117">None</span></span>

<span data-ttu-id="b8b68-118">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b8b68-118">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="b8b68-119">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b8b68-119">OUTPUTS</span></span>

### <span data-ttu-id="b8b68-120">System. String</span><span class="sxs-lookup"><span data-stu-id="b8b68-120">System.String</span></span>

<span data-ttu-id="b8b68-121">Denna cmdlet returnerar en sträng som innehåller ett status meddelande och sökvägen till utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="b8b68-121">This cmdlet returns a string that contains a status message and the path to the output file.</span></span>

## <span data-ttu-id="b8b68-122">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b8b68-122">NOTES</span></span>

* <span data-ttu-id="b8b68-123">Om en avskrift inte har startats Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="b8b68-123">If a transcript has not been started, the command fails.</span></span>

*

## <span data-ttu-id="b8b68-124">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b8b68-124">RELATED LINKS</span></span>

[<span data-ttu-id="b8b68-125">Start-avskrift</span><span class="sxs-lookup"><span data-stu-id="b8b68-125">Start-Transcript</span></span>](Start-Transcript.md)

