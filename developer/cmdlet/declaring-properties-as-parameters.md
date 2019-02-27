---
title: Deklarerar egenskaper som parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850577"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="e8b0a-102">Deklarera egenskaper som parametrar</span><span class="sxs-lookup"><span data-stu-id="e8b0a-102">Declaring Properties as Parameters</span></span>

<span data-ttu-id="e8b0a-103">Det här avsnittet innehåller grundläggande information som du måste förstå innan du deklarera parametrarna för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-103">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="e8b0a-104">Definiera de offentliga egenskaperna som representerar varje parameter för att deklarera parametrarna för en cmdlet i cmdlet-klass och sedan lägga till ett eller flera attribut för parametern i varje egenskap.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-104">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="e8b0a-105">Windows PowerShell-runtime använder parametern-attribut för att identifiera egenskapen som en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-105">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="e8b0a-106">Grundläggande syntaxen för att deklarera parametern-attributet är `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-106">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="e8b0a-107">Här är ett exempel på en egenskap som har definierats som en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-107">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="e8b0a-108">Här följer några saker du bör tänka parametrar.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-108">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="e8b0a-109">En parameter måste uttryckligen markeras som offentliga.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-109">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="e8b0a-110">Parametrar som inte är markerad som offentlig standard till interna och kommer inte att hitta av Windows PowerShell-körningen.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-110">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="e8b0a-111">Parametrar ska definieras som Microsoft .NET Framework-typer för att ge bättre parameterverifieringen.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-111">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="e8b0a-112">Till exempel ska parametrar som är begränsade till ett värde från en uppsättning värden vara definierat som en uppräkningstyp.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-112">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="e8b0a-113">Parametrar som tar ett värde för ID: T URI (Uniform Resource) ska vara av typen [System.Uri](/dotnet/api/System.Uri).</span><span class="sxs-lookup"><span data-stu-id="e8b0a-113">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="e8b0a-114">Undvik grundläggande strängparametrar för allt utom friformsarbetsyta textegenskaper.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-114">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="e8b0a-115">Du kan lägga till en parameter till valfritt antal parameteruppsättningar.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-115">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="e8b0a-116">Läs mer om parameteruppsättningar [cmdlet: en Parameter anger](./cmdlet-parameter-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e8b0a-116">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="e8b0a-117">Windows PowerShell innehåller också en uppsättning gemensamma parametrar som är automatiskt tillgängliga för varje cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-117">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="e8b0a-118">Läs mer om dessa parametrar och deras alias, [gemensamma parametrar för cmdleten](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="e8b0a-118">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e8b0a-119">Se även</span><span class="sxs-lookup"><span data-stu-id="e8b0a-119">See Also</span></span>

[<span data-ttu-id="e8b0a-120">Cmdlet gemensamma parametrar</span><span class="sxs-lookup"><span data-stu-id="e8b0a-120">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="e8b0a-121">Typer av Cmdlet-Parameter</span><span class="sxs-lookup"><span data-stu-id="e8b0a-121">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

[<span data-ttu-id="e8b0a-122">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8b0a-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
