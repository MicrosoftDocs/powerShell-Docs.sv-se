---
title: AccessDbProviderSample06 kod exempel | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f650648320a0a31324af1bd1a112f01bdfc6c599
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787248"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="0e895-102">AccessDbProviderSample06 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="0e895-102">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="0e895-103">Följande kod visar implementeringen av Windows PowerShell-innehålls leverantören som beskrivs i [skapa en Windows PowerShell-innehålls leverantör](./creating-a-windows-powershell-content-provider.md).</span><span class="sxs-lookup"><span data-stu-id="0e895-103">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span>
<span data-ttu-id="0e895-104">Den här providern gör det möjligt för användaren att ändra innehållet i objekt i ett data lager.</span><span class="sxs-lookup"><span data-stu-id="0e895-104">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="0e895-105">Du kan ladda ned C#-käll filen (AccessDBSampleProvider06.cs) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="0e895-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="0e895-106">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="0e895-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="0e895-107">De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.</span><span class="sxs-lookup"><span data-stu-id="0e895-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="0e895-108">Mer information om implementeringar av andra Windows PowerShell-leverantörer finns i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="0e895-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="0e895-109">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="0e895-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="11-2399":::

## <a name="see-also"></a><span data-ttu-id="0e895-110">Se även</span><span class="sxs-lookup"><span data-stu-id="0e895-110">See Also</span></span>

[<span data-ttu-id="0e895-111">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e895-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="0e895-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0e895-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
