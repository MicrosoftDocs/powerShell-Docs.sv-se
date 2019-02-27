---
title: Datum och tidsparametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 49f6c667b0fd9678586559af39a33f982de0a68c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846713"
---
# <a name="date-and-time-parameters"></a><span data-ttu-id="06ec9-102">Datum- och tidsparametrar</span><span class="sxs-lookup"><span data-stu-id="06ec9-102">Date and Time Parameters</span></span>

<span data-ttu-id="06ec9-103">I följande tabell visas rekommenderade namn och funktioner för parametrar som hanterar datum och tid.</span><span class="sxs-lookup"><span data-stu-id="06ec9-103">The following table lists recommended names and functionality for parameters that handle date and time information.</span></span> <span data-ttu-id="06ec9-104">Datum och tid parametrar används vanligtvis för att registrera när något skapas eller öppnas.</span><span class="sxs-lookup"><span data-stu-id="06ec9-104">Date and time parameters are typically used to record when something is created or accessed.</span></span>

<span data-ttu-id="06ec9-105">Data som används skriver du: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="06ec9-105">Accessed Data type: SwitchParameter</span></span>

<span data-ttu-id="06ec9-106">Implementera den här parametern så att när det anges cmdlet: en ska användas för de resurser som har öppnats baseras på datum och tid som anges av den `Before` och `After` parametrar.</span><span class="sxs-lookup"><span data-stu-id="06ec9-106">Implement this parameter so that when it is specified the cmdlet will operate on the resources that have been accessed based on the date and time specified by the `Before` and `After` parameters.</span></span>

<span data-ttu-id="06ec9-107">Om den här parametern anges den `Created` och `Modified` måste vara inte anges.</span><span class="sxs-lookup"><span data-stu-id="06ec9-107">If this parameter is specified, the `Created` and `Modified` parameters must be not be specified.</span></span>

<span data-ttu-id="06ec9-108">Efter datatyp: Datum/tid</span><span class="sxs-lookup"><span data-stu-id="06ec9-108">After Data type: DateTime</span></span>

<span data-ttu-id="06ec9-109">Implementera den här parametern om du vill ange datum och tid efter vilken cmdleten har använts.</span><span class="sxs-lookup"><span data-stu-id="06ec9-109">Implement this parameter to specify the date and time after which the cmdlet was used.</span></span> <span data-ttu-id="06ec9-110">För den `After` parametern ska fungera, cmdlet: en måste också ha en `Accessed`, `Created`, eller `Modified` parametern.</span><span class="sxs-lookup"><span data-stu-id="06ec9-110">For the `After` parameter to work, the cmdlet must also have an `Accessed`, `Created`, or `Modified` parameter.</span></span> <span data-ttu-id="06ec9-111">Och parametern måste anges till `true` när cmdlet anropas.</span><span class="sxs-lookup"><span data-stu-id="06ec9-111">And, that parameter must be set to `true` when the cmdlet is called.</span></span>

<span data-ttu-id="06ec9-112">Innan du datatyp: Datum/tid</span><span class="sxs-lookup"><span data-stu-id="06ec9-112">Before Data type: DateTime</span></span>

<span data-ttu-id="06ec9-113">Implementera den här parametern om du vill ange datum och tid som användes för cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="06ec9-113">Implement this parameter to specify the date and time before which the cmdlet was used.</span></span> <span data-ttu-id="06ec9-114">För den `Before` parametern ska fungera, cmdlet: en måste också ha en `Accessed`, `Created`, eller `Modified` parametern.</span><span class="sxs-lookup"><span data-stu-id="06ec9-114">For the `Before` parameter to work, the cmdlet must also have an `Accessed`, `Created`, or `Modified` parameter.</span></span> <span data-ttu-id="06ec9-115">Och parametern måste anges till `true` när cmdlet anropas.</span><span class="sxs-lookup"><span data-stu-id="06ec9-115">And, that parameter must be set to `true` when the cmdlet is called.</span></span>

<span data-ttu-id="06ec9-116">Skapad datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="06ec9-116">Created Data type: SwitchParameter</span></span>

<span data-ttu-id="06ec9-117">Implementera den här parametern så att när det anges cmdlet: en ska användas för de resurser som har skapats utifrån datum och tid som anges av den `Before` och `After` parametrar.</span><span class="sxs-lookup"><span data-stu-id="06ec9-117">Implement this parameter so that when it is specified the cmdlet will operate on the resources that have been created based on the date and time specified by the `Before` and `After` parameters.</span></span>

<span data-ttu-id="06ec9-118">Om den här parametern anges den `Accessed` och `Modified` parametrar får inte anges.</span><span class="sxs-lookup"><span data-stu-id="06ec9-118">If this parameter is specified, the `Accessed` and `Modified` parameters must not be specified.</span></span>

<span data-ttu-id="06ec9-119">Exakta datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="06ec9-119">Exact Data type: SwitchParameter</span></span>

<span data-ttu-id="06ec9-120">Implementera den här parametern så att när det anges att resursen termen måste matcha resursnamnet exakt.</span><span class="sxs-lookup"><span data-stu-id="06ec9-120">Implement this parameter so that when it is specified the resource term must match the resource name exactly.</span></span> <span data-ttu-id="06ec9-121">Om parametern inte anges behöver resource termen och namnet inte matcha varandra exakt.</span><span class="sxs-lookup"><span data-stu-id="06ec9-121">When the parameter is not specified the resource term and name do not need to match exactly.</span></span>

<span data-ttu-id="06ec9-122">Ändrade datatyp: Datum/tid</span><span class="sxs-lookup"><span data-stu-id="06ec9-122">Modified Data type: DateTime</span></span>

<span data-ttu-id="06ec9-123">Implementera den här parametern så att när det anges cmdlet kommer att fungera på resurser som har ändrats baseras på datum och tid som anges av den `Before` och `After` parametrar.</span><span class="sxs-lookup"><span data-stu-id="06ec9-123">Implement this parameter so that when it is specified the cmdlet will operate on resources that have been changed based on the date and time specified by the `Before` and `After` parameters.</span></span>

<span data-ttu-id="06ec9-124">Om den här parametern anges den `Accessed` och `Created` parametrar får inte anges.</span><span class="sxs-lookup"><span data-stu-id="06ec9-124">If this parameter is specified, the `Accessed` and `Created` parameters must not be specified.</span></span>

## <a name="see-also"></a><span data-ttu-id="06ec9-125">Se även</span><span class="sxs-lookup"><span data-stu-id="06ec9-125">See Also</span></span>

[<span data-ttu-id="06ec9-126">Cmdlet-parametrarna</span><span class="sxs-lookup"><span data-stu-id="06ec9-126">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="06ec9-127">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="06ec9-127">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="06ec9-128">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="06ec9-128">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
