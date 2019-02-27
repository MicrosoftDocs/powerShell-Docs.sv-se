---
title: AccessDbProviderSample01 kodexempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 01b95e18794501c2aff13d1e51b7400ae6fb8730
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849380"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="24371-102">AccessDbProviderSample01 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="24371-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="24371-103">Följande kod visar implementeringen av Windows PowerShell-providern som beskrivs i [skapar en grundläggande Windows PowerShell-providern](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="24371-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="24371-104">Den här implementeringen ger metoder för att starta och stoppa providern, och även om det inte ger ett sätt att få åtkomst till ett datalager eller för att hämta eller ange data i datalagret kan det tillhandahåller grundläggande funktioner som krävs av alla leverantörer.</span><span class="sxs-lookup"><span data-stu-id="24371-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="24371-105">Du kan ladda ned den C# källfilen (AccessDBSampleProvider01.cs) för den här providern med hjälp av Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3.0-körtidskomponenter.</span><span class="sxs-lookup"><span data-stu-id="24371-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="24371-106">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="24371-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="24371-107">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="24371-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="24371-108">Läs mer om andra Windows PowerShell-providern implementeringar [designa din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="24371-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="24371-109">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="24371-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="24371-110">Se även</span><span class="sxs-lookup"><span data-stu-id="24371-110">See Also</span></span>

[<span data-ttu-id="24371-111">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="24371-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="24371-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="24371-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)