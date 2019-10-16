---
title: AccessDbProviderSample04 kod exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: ff43286bc90c1a4d2270be0ee03ca5910867cec2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357304"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="cb91f-102">AccessDbProviderSample04 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="cb91f-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="cb91f-103">Följande kod visar implementeringen av Windows PowerShell-providern som beskrivs i [skapa en Windows PowerShell container-Provider](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="cb91f-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span> <span data-ttu-id="cb91f-104">Den här providern fungerar på data lager i flera lager.</span><span class="sxs-lookup"><span data-stu-id="cb91f-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="cb91f-105">För den här typen av data lager innehåller lagrings platsen på den högsta nivån rot objekten och varje efterföljande nivå kallas nod för underordnade objekt.</span><span class="sxs-lookup"><span data-stu-id="cb91f-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="cb91f-106">Genom att tillåta att användaren arbetar på dessa underordnade noder kan en användare interagera hierarkiskt via data lagret.</span><span class="sxs-lookup"><span data-stu-id="cb91f-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="cb91f-107">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="cb91f-107">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="cb91f-108">Se även</span><span class="sxs-lookup"><span data-stu-id="cb91f-108">See Also</span></span>

[<span data-ttu-id="cb91f-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="cb91f-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
