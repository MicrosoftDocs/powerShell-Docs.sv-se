---
title: AccessDbProviderSample02 kod exempel | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ca7674ba5cff601394af4df20f0dda8794c14d22
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784817"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="5eb4c-102">AccessDbProviderSample02 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="5eb4c-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="5eb4c-103">Följande kod visar implementeringen av Windows PowerShell-providern som beskrivs i [skapa en provider för Windows PowerShell-enheter](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="5eb4c-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>
<span data-ttu-id="5eb4c-104">Den här implementeringen skapar en sökväg, skapar en anslutning till en Access-databas och tar sedan bort enheten.</span><span class="sxs-lookup"><span data-stu-id="5eb4c-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="5eb4c-105">Du kan hämta C#-källfilen (AccessDBSampleProvider02.cs) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="5eb4c-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="5eb4c-106">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="5eb4c-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="5eb4c-107">De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.</span><span class="sxs-lookup"><span data-stu-id="5eb4c-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="5eb4c-108">Mer information om implementeringar av andra Windows PowerShell-leverantörer finns i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="5eb4c-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="5eb4c-109">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="5eb4c-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a><span data-ttu-id="5eb4c-110">Se även</span><span class="sxs-lookup"><span data-stu-id="5eb4c-110">See Also</span></span>

[<span data-ttu-id="5eb4c-111">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5eb4c-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="5eb4c-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5eb4c-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
