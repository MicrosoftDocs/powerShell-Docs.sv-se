---
title: Deklaration av OutputType-attribut | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a4cc874031bba092cfef6041bef0e19e6af3f09c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786551"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="4c109-102">Deklaration av attributet OutputType</span><span class="sxs-lookup"><span data-stu-id="4c109-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="4c109-103">`OutputType`Attributet identifierar de .NET Framework typer som returneras av en cmdlet, funktion eller skript.</span><span class="sxs-lookup"><span data-stu-id="4c109-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="4c109-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4c109-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="4c109-105">Parametrar</span><span class="sxs-lookup"><span data-stu-id="4c109-105">Parameters</span></span>

<span data-ttu-id="4c109-106">Typ ( `string[]` eller `Type[]` ) krävs.</span><span class="sxs-lookup"><span data-stu-id="4c109-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="4c109-107">Anger de typer som returneras av cmdlet-funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="4c109-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="4c109-108">ParameterSetName (String []) är valfritt.</span><span class="sxs-lookup"><span data-stu-id="4c109-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="4c109-109">Anger parameter uppsättningar som returnerar de typer som anges i `type` parametern.</span><span class="sxs-lookup"><span data-stu-id="4c109-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="4c109-110">providerCmdlet valfritt.</span><span class="sxs-lookup"><span data-stu-id="4c109-110">providerCmdlet Optional.</span></span> <span data-ttu-id="4c109-111">Anger Provider-cmdleten som returnerar de typer som anges i `type` parametern.</span><span class="sxs-lookup"><span data-stu-id="4c109-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c109-112">Se även</span><span class="sxs-lookup"><span data-stu-id="4c109-112">See Also</span></span>

[<span data-ttu-id="4c109-113">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="4c109-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
