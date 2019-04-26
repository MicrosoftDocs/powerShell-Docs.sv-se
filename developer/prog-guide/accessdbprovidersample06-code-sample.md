---
title: AccessDbProviderSample06 kodexempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: baab6a56-c199-48d7-a03e-a904b1bb1baa
caps.latest.revision: 7
ms.openlocfilehash: 6e86318573df92b9ec84056631843e0efa096a3b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081945"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="2de87-102">AccessDbProviderSample06 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="2de87-102">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="2de87-103">Följande kod visar implementeringen av Windows PowerShell innehållsleverantören beskrivs i [skapar en Windows PowerShell-innehållsleverantör](./creating-a-windows-powershell-content-provider.md).</span><span class="sxs-lookup"><span data-stu-id="2de87-103">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span> <span data-ttu-id="2de87-104">Den här providern gör att användaren kan ändra innehållet i objekten i ett datalager.</span><span class="sxs-lookup"><span data-stu-id="2de87-104">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="2de87-105">Du kan ladda ned den C# källfilen (AccessDBSampleProvider06.cs) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3.0-körtidskomponenter.</span><span class="sxs-lookup"><span data-stu-id="2de87-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2de87-106">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="2de87-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="2de87-107">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="2de87-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="2de87-108">Läs mer om andra Windows PowerShell-providern implementeringar [designa din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="2de87-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="2de87-109">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="2de87-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="2de87-110">Se även</span><span class="sxs-lookup"><span data-stu-id="2de87-110">See Also</span></span>

[<span data-ttu-id="2de87-111">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2de87-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="2de87-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2de87-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)