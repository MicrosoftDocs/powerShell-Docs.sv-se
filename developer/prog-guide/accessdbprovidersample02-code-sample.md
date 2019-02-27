---
title: AccessDbProviderSample02 kodexempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 22a7bdf43a294d1e28f78ccf3412173892fdd53e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847273"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="db2fc-102">AccessDbProviderSample02 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="db2fc-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="db2fc-103">Följande kod visar implementeringen av Windows PowerShell-providern som beskrivs i [skapar en Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="db2fc-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span> <span data-ttu-id="db2fc-104">Den här implementeringen skapar en sökväg, ansluter till en Access-databas och sedan tar bort enheten.</span><span class="sxs-lookup"><span data-stu-id="db2fc-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="db2fc-105">Du kan ladda ned den C# källfilen (AccessDBSampleProvider02.cs) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3.0-körtidskomponenter.</span><span class="sxs-lookup"><span data-stu-id="db2fc-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="db2fc-106">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="db2fc-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="db2fc-107">Du kan ladda ned den C# källfilen (AccessDBSampleProvider02.cs) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3.0-körtidskomponenter.</span><span class="sxs-lookup"><span data-stu-id="db2fc-107">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="db2fc-108">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="db2fc-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="db2fc-109">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="db2fc-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="db2fc-110">Läs mer om andra Windows PowerShell-providern implementeringar [designa din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="db2fc-110">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="db2fc-111">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="db2fc-111">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a><span data-ttu-id="db2fc-112">Se även</span><span class="sxs-lookup"><span data-stu-id="db2fc-112">See Also</span></span>

[<span data-ttu-id="db2fc-113">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="db2fc-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="db2fc-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="db2fc-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)