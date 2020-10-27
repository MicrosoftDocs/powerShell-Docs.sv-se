---
ms.date: 09/13/2016
ms.topic: reference
title: Deklaration av attributet OutputType
description: Deklaration av attributet OutputType
ms.openlocfilehash: b5e33346e9ac29c13323781d62daffab892573a4
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646454"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="2dbb7-103">Deklaration av attributet OutputType</span><span class="sxs-lookup"><span data-stu-id="2dbb7-103">OutputType Attribute Declaration</span></span>

<span data-ttu-id="2dbb7-104">`OutputType`Attributet identifierar de .NET Framework typer som returneras av en cmdlet, funktion eller skript.</span><span class="sxs-lookup"><span data-stu-id="2dbb7-104">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="2dbb7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2dbb7-105">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="2dbb7-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="2dbb7-106">Parameters</span></span>

<span data-ttu-id="2dbb7-107">Typ ( `string[]` eller `Type[]` ) krävs.</span><span class="sxs-lookup"><span data-stu-id="2dbb7-107">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="2dbb7-108">Anger de typer som returneras av cmdlet-funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="2dbb7-108">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="2dbb7-109">ParameterSetName (String []) är valfritt.</span><span class="sxs-lookup"><span data-stu-id="2dbb7-109">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="2dbb7-110">Anger parameter uppsättningar som returnerar de typer som anges i `type` parametern.</span><span class="sxs-lookup"><span data-stu-id="2dbb7-110">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="2dbb7-111">providerCmdlet valfritt.</span><span class="sxs-lookup"><span data-stu-id="2dbb7-111">providerCmdlet Optional.</span></span> <span data-ttu-id="2dbb7-112">Anger Provider-cmdleten som returnerar de typer som anges i `type` parametern.</span><span class="sxs-lookup"><span data-stu-id="2dbb7-112">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="2dbb7-113">Se även</span><span class="sxs-lookup"><span data-stu-id="2dbb7-113">See Also</span></span>

[<span data-ttu-id="2dbb7-114">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="2dbb7-114">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
