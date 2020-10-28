---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDbProviderSample01 – kodexempel
description: AccessDbProviderSample01 – kodexempel
ms.openlocfilehash: 5be593b9e86347b2f55de156fe4d9b44cfab5b78
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659412"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="9c013-103">AccessDbProviderSample01 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="9c013-103">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="9c013-104">Följande kod visar implementeringen av Windows PowerShell-providern som beskrivs i [skapa en grundläggande Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="9c013-104">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span>
<span data-ttu-id="9c013-105">Den här implementeringen innehåller metoder för att starta och stoppa providern och även om det inte ger möjlighet att komma åt ett data lager eller hämta eller ange data i data lagret, innehåller den de grundläggande funktioner som krävs av alla leverantörer.</span><span class="sxs-lookup"><span data-stu-id="9c013-105">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="9c013-106">Du kan hämta C#-källfilen (AccessDBSampleProvider01.cs) för den här providern med hjälp av Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="9c013-106">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="9c013-107">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="9c013-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="9c013-108">De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.</span><span class="sxs-lookup"><span data-stu-id="9c013-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="9c013-109">Mer information om implementeringar av andra Windows PowerShell-leverantörer finns i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="9c013-109">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="9c013-110">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="9c013-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a><span data-ttu-id="9c013-111">Se även</span><span class="sxs-lookup"><span data-stu-id="9c013-111">See Also</span></span>

[<span data-ttu-id="9c013-112">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9c013-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="9c013-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9c013-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
