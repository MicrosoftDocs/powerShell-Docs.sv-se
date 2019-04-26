---
title: OutputType-attributet deklarationen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067611"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="b29d2-102">Deklaration av attributet OutputType</span><span class="sxs-lookup"><span data-stu-id="b29d2-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="b29d2-103">Den `OutputType` attributet anger .NET Framework-typer som returneras av en cmdlet, en funktion eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="b29d2-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="b29d2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b29d2-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="b29d2-105">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b29d2-105">Parameters</span></span>

<span data-ttu-id="b29d2-106">Typ (`string[]` eller `Type[]`) krävs.</span><span class="sxs-lookup"><span data-stu-id="b29d2-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="b29d2-107">Anger vilka typer som returneras av cmdlet: en funktion eller skript.</span><span class="sxs-lookup"><span data-stu-id="b29d2-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="b29d2-108">ParameterSetName (string[]) valfritt.</span><span class="sxs-lookup"><span data-stu-id="b29d2-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="b29d2-109">Anger parameteruppsättningar som returnerar de angivna typerna i den `type` parametern.</span><span class="sxs-lookup"><span data-stu-id="b29d2-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="b29d2-110">providerCmdlet valfritt.</span><span class="sxs-lookup"><span data-stu-id="b29d2-110">providerCmdlet Optional.</span></span> <span data-ttu-id="b29d2-111">Anger den provider-cmdlet som returnerar de angivna typerna i den `type` parametern.</span><span class="sxs-lookup"><span data-stu-id="b29d2-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="b29d2-112">Se även</span><span class="sxs-lookup"><span data-stu-id="b29d2-112">See Also</span></span>

[<span data-ttu-id="b29d2-113">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b29d2-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
