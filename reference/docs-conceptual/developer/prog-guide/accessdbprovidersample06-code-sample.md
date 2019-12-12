---
title: AccessDbProviderSample06 kod exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: baab6a56-c199-48d7-a03e-a904b1bb1baa
caps.latest.revision: 7
ms.openlocfilehash: 7f75a3a3d2ab89696bb34ec2fdf7ba7a5ce0f9b1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416231"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="90b0e-102">AccessDbProviderSample06 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="90b0e-102">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="90b0e-103">Följande kod visar implementeringen av Windows PowerShell-innehålls leverantören som beskrivs i [skapa en Windows PowerShell-innehålls leverantör](./creating-a-windows-powershell-content-provider.md).</span><span class="sxs-lookup"><span data-stu-id="90b0e-103">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span> <span data-ttu-id="90b0e-104">Den här providern gör det möjligt för användaren att ändra innehållet i objekt i ett data lager.</span><span class="sxs-lookup"><span data-stu-id="90b0e-104">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="90b0e-105">Du kan ladda ned C# käll filen (AccessDBSampleProvider06.CS) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="90b0e-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="90b0e-106">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="90b0e-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="90b0e-107">De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .</span><span class="sxs-lookup"><span data-stu-id="90b0e-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="90b0e-108">Mer information om implementeringar av andra Windows PowerShell-leverantörer finns i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="90b0e-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="90b0e-109">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="90b0e-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="90b0e-110">Se även</span><span class="sxs-lookup"><span data-stu-id="90b0e-110">See Also</span></span>

[<span data-ttu-id="90b0e-111">Windows PowerShell Programmer ' s guide</span><span class="sxs-lookup"><span data-stu-id="90b0e-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="90b0e-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="90b0e-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
