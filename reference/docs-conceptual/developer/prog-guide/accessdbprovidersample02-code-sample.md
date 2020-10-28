---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDbProviderSample02 – kodexempel
description: AccessDbProviderSample02 – kodexempel
ms.openlocfilehash: f467ee59b36027e80852ae1f7b2f1af5c9aa8569
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659400"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="2bd92-103">AccessDbProviderSample02 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="2bd92-103">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="2bd92-104">Följande kod visar implementeringen av Windows PowerShell-providern som beskrivs i [skapa en provider för Windows PowerShell-enheter](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="2bd92-104">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>
<span data-ttu-id="2bd92-105">Den här implementeringen skapar en sökväg, skapar en anslutning till en Access-databas och tar sedan bort enheten.</span><span class="sxs-lookup"><span data-stu-id="2bd92-105">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="2bd92-106">Du kan hämta C#-källfilen (AccessDBSampleProvider02.cs) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="2bd92-106">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2bd92-107">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="2bd92-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="2bd92-108">De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.</span><span class="sxs-lookup"><span data-stu-id="2bd92-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="2bd92-109">Mer information om implementeringar av andra Windows PowerShell-leverantörer finns i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="2bd92-109">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="2bd92-110">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="2bd92-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a><span data-ttu-id="2bd92-111">Se även</span><span class="sxs-lookup"><span data-stu-id="2bd92-111">See Also</span></span>

[<span data-ttu-id="2bd92-112">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2bd92-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="2bd92-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2bd92-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
