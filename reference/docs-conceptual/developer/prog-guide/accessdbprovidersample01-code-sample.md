---
title: AccessDbProviderSample01 kod exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: b52882c3f38b64347b9e9f2c3dedcc8a7dd02458
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978607"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="26dbc-102">AccessDbProviderSample01 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="26dbc-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="26dbc-103">Följande kod visar implementeringen av Windows PowerShell-providern som beskrivs i [skapa en grundläggande Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="26dbc-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span>
<span data-ttu-id="26dbc-104">Den här implementeringen innehåller metoder för att starta och stoppa providern och även om det inte ger möjlighet att komma åt ett data lager eller hämta eller ange data i data lagret, innehåller den de grundläggande funktioner som krävs av alla leverantörer.</span><span class="sxs-lookup"><span data-stu-id="26dbc-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="26dbc-105">Du kan ladda ned C# käll filen (AccessDBSampleProvider01.CS) för den här providern med hjälp av Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="26dbc-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="26dbc-106">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="26dbc-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="26dbc-107">De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .</span><span class="sxs-lookup"><span data-stu-id="26dbc-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="26dbc-108">Mer information om implementeringar av andra Windows PowerShell-leverantörer finns i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="26dbc-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="26dbc-109">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="26dbc-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a><span data-ttu-id="26dbc-110">Se även</span><span class="sxs-lookup"><span data-stu-id="26dbc-110">See Also</span></span>

[<span data-ttu-id="26dbc-111">Windows PowerShell Programmer ' s guide</span><span class="sxs-lookup"><span data-stu-id="26dbc-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="26dbc-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="26dbc-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
