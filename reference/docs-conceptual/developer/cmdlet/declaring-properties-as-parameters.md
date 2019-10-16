---
title: Deklarera egenskaper som parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356450"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="f0c55-102">Deklarera egenskaper som parametrar</span><span class="sxs-lookup"><span data-stu-id="f0c55-102">Declaring Properties as Parameters</span></span>

<span data-ttu-id="f0c55-103">Det här avsnittet innehåller grundläggande information som du måste förstå innan du deklarerar parametrarna för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f0c55-103">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="f0c55-104">Om du vill deklarera parametrarna för en cmdlet i cmdlet-klassen definierar du de offentliga egenskaper som representerar varje parameter och lägger sedan till ett eller flera parametriserade till varje egenskap.</span><span class="sxs-lookup"><span data-stu-id="f0c55-104">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="f0c55-105">Windows PowerShell-körningsmiljön använder parameter-attribut för att identifiera egenskapen som en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="f0c55-105">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="f0c55-106">Den grundläggande syntaxen för att deklarera parameter-attributet är `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="f0c55-106">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="f0c55-107">Här är ett exempel på en egenskap som definierats som en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="f0c55-107">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="f0c55-108">Här är några saker att komma ihåg om parametrar.</span><span class="sxs-lookup"><span data-stu-id="f0c55-108">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="f0c55-109">En parameter måste markeras som offentlig.</span><span class="sxs-lookup"><span data-stu-id="f0c55-109">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="f0c55-110">Parametrar som inte har marker ATS som offentliga som offentliga som standard till interna och som inte hittas av Windows PowerShell-körningsmiljön.</span><span class="sxs-lookup"><span data-stu-id="f0c55-110">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="f0c55-111">Parametrar ska definieras som Microsoft .NET Framework-typer för att ge bättre parameter verifiering.</span><span class="sxs-lookup"><span data-stu-id="f0c55-111">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="f0c55-112">Till exempel ska parametrar som är begränsade till ett värde av en uppsättning värden definieras som en uppräknings typ.</span><span class="sxs-lookup"><span data-stu-id="f0c55-112">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="f0c55-113">Parametrar som tar ett Uniform Resource Identifier (URI)-värde måste vara av typen [system. URI](/dotnet/api/System.Uri).</span><span class="sxs-lookup"><span data-stu-id="f0c55-113">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="f0c55-114">Undvik grundläggande sträng parametrar för alla fält med fri Forms egenskaper.</span><span class="sxs-lookup"><span data-stu-id="f0c55-114">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="f0c55-115">Du kan lägga till en parameter till valfritt antal parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="f0c55-115">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="f0c55-116">Mer information om parameter uppsättningar finns i [cmdlet parameter Sets](./cmdlet-parameter-sets.md).</span><span class="sxs-lookup"><span data-stu-id="f0c55-116">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="f0c55-117">Windows PowerShell tillhandahåller också en uppsättning vanliga parametrar som automatiskt är tillgängliga för varje cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f0c55-117">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="f0c55-118">Mer information om dessa parametrar och deras alias finns i parametrar för [cmdlets common](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="f0c55-118">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f0c55-119">Se även</span><span class="sxs-lookup"><span data-stu-id="f0c55-119">See Also</span></span>

[<span data-ttu-id="f0c55-120">Vanliga parametrar för cmdlet</span><span class="sxs-lookup"><span data-stu-id="f0c55-120">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="f0c55-121">Typer av cmdlet-parameter</span><span class="sxs-lookup"><span data-stu-id="f0c55-121">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

[<span data-ttu-id="f0c55-122">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="f0c55-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
