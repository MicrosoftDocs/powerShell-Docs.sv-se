---
ms.date: 09/13/2016
ms.topic: reference
title: Deklarera egenskaper som parametrar
description: Deklarera egenskaper som parametrar
ms.openlocfilehash: ade7928e2ca277da8bbd1a5e04997bd1d05f1e5d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653153"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="27794-103">Deklarera egenskaper som parametrar</span><span class="sxs-lookup"><span data-stu-id="27794-103">Declaring Properties as Parameters</span></span>

<span data-ttu-id="27794-104">Det här avsnittet innehåller grundläggande information som du måste förstå innan du deklarerar parametrarna för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="27794-104">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="27794-105">Om du vill deklarera parametrarna för en cmdlet i cmdlet-klassen definierar du de offentliga egenskaper som representerar varje parameter och lägger sedan till ett eller flera parametriserade till varje egenskap.</span><span class="sxs-lookup"><span data-stu-id="27794-105">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="27794-106">Windows PowerShell-körningsmiljön använder parameter-attribut för att identifiera egenskapen som en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="27794-106">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="27794-107">Den grundläggande syntaxen för att deklarera parameter-attributet är `[Parameter()]` .</span><span class="sxs-lookup"><span data-stu-id="27794-107">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="27794-108">Här är ett exempel på en egenskap som definierats som en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="27794-108">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="27794-109">Här är några saker att komma ihåg om parametrar.</span><span class="sxs-lookup"><span data-stu-id="27794-109">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="27794-110">En parameter måste markeras som offentlig.</span><span class="sxs-lookup"><span data-stu-id="27794-110">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="27794-111">Parametrar som inte har marker ATS som offentliga som offentliga som standard till interna och som inte hittas av Windows PowerShell-körningsmiljön.</span><span class="sxs-lookup"><span data-stu-id="27794-111">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="27794-112">Parametrar ska definieras som Microsoft .NET Framework-typer för att ge bättre parameter verifiering.</span><span class="sxs-lookup"><span data-stu-id="27794-112">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="27794-113">Till exempel ska parametrar som är begränsade till ett värde av en uppsättning värden definieras som en uppräknings typ.</span><span class="sxs-lookup"><span data-stu-id="27794-113">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="27794-114">Parametrar som tar ett Uniform Resource Identifier (URI)-värde måste vara av typen [system. URI](/dotnet/api/System.Uri).</span><span class="sxs-lookup"><span data-stu-id="27794-114">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="27794-115">Undvik grundläggande sträng parametrar för alla fält med fri Forms egenskaper.</span><span class="sxs-lookup"><span data-stu-id="27794-115">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="27794-116">Du kan lägga till en parameter till valfritt antal parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="27794-116">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="27794-117">Mer information om parameter uppsättningar finns i [cmdlet parameter Sets](./cmdlet-parameter-sets.md).</span><span class="sxs-lookup"><span data-stu-id="27794-117">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="27794-118">Windows PowerShell tillhandahåller också en uppsättning vanliga parametrar som automatiskt är tillgängliga för varje cmdlet.</span><span class="sxs-lookup"><span data-stu-id="27794-118">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="27794-119">Mer information om dessa parametrar och deras alias finns i parametrar för [cmdlets common](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="27794-119">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="27794-120">Se även</span><span class="sxs-lookup"><span data-stu-id="27794-120">See Also</span></span>

[<span data-ttu-id="27794-121">Vanliga parametrar för cmdlet</span><span class="sxs-lookup"><span data-stu-id="27794-121">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="27794-122">Typer av cmdlet-parameter</span><span class="sxs-lookup"><span data-stu-id="27794-122">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

[<span data-ttu-id="27794-123">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="27794-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
