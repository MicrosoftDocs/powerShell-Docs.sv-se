---
title: Deklaration av OutputType-attribut | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356163"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="1678b-102">Deklaration av attributet OutputType</span><span class="sxs-lookup"><span data-stu-id="1678b-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="1678b-103">Attributet `OutputType` identifierar de .NET Framework typer som returneras av en cmdlet, funktion eller skript.</span><span class="sxs-lookup"><span data-stu-id="1678b-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="1678b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1678b-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="1678b-105">Parametrar</span><span class="sxs-lookup"><span data-stu-id="1678b-105">Parameters</span></span>

<span data-ttu-id="1678b-106">Typ (`string[]` eller `Type[]`) krävs.</span><span class="sxs-lookup"><span data-stu-id="1678b-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="1678b-107">Anger de typer som returneras av cmdlet-funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="1678b-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="1678b-108">ParameterSetName (String []) är valfritt.</span><span class="sxs-lookup"><span data-stu-id="1678b-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="1678b-109">Anger parameter uppsättningar som returnerar de typer som anges i parametern `type`.</span><span class="sxs-lookup"><span data-stu-id="1678b-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="1678b-110">providerCmdlet valfritt.</span><span class="sxs-lookup"><span data-stu-id="1678b-110">providerCmdlet Optional.</span></span> <span data-ttu-id="1678b-111">Anger Provider-cmdleten som returnerar de typer som anges i parametern `type`.</span><span class="sxs-lookup"><span data-stu-id="1678b-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="1678b-112">Se även</span><span class="sxs-lookup"><span data-stu-id="1678b-112">See Also</span></span>

[<span data-ttu-id="1678b-113">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="1678b-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
