---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDbProviderSample04 – kodexempel
description: AccessDbProviderSample04 – kodexempel
ms.openlocfilehash: bb70ce9f1b1c94349c354a8771fedf7fcb1bb320
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647563"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="12efa-103">AccessDbProviderSample04 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="12efa-103">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="12efa-104">Följande kod visar implementeringen av Windows PowerShell-providern som beskrivs i [skapa en Windows PowerShell container-Provider](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="12efa-104">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>
<span data-ttu-id="12efa-105">Den här providern fungerar på data lager i flera lager.</span><span class="sxs-lookup"><span data-stu-id="12efa-105">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="12efa-106">För den här typen av data lager innehåller lagrings platsen på den högsta nivån rot objekten och varje efterföljande nivå kallas nod för underordnade objekt.</span><span class="sxs-lookup"><span data-stu-id="12efa-106">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="12efa-107">Genom att tillåta att användaren arbetar på dessa underordnade noder kan en användare interagera hierarkiskt via data lagret.</span><span class="sxs-lookup"><span data-stu-id="12efa-107">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="12efa-108">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="12efa-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a><span data-ttu-id="12efa-109">Se även</span><span class="sxs-lookup"><span data-stu-id="12efa-109">See Also</span></span>

[<span data-ttu-id="12efa-110">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="12efa-110">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
