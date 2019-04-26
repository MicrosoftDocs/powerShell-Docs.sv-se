---
title: AccessDbProviderSample04 kodexempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: 43f01b9cd6af3ab6c26f88ee0c1e9269499b2bc3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081962"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="9da56-102">AccessDbProviderSample04 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="9da56-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="9da56-103">Följande kod visar implementeringen av Windows PowerShell-providern som beskrivs i [skapar en Windows PowerShell-providern för behållaren](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="9da56-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span> <span data-ttu-id="9da56-104">Den här providern fungerar på flera lager datalager.</span><span class="sxs-lookup"><span data-stu-id="9da56-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="9da56-105">Den översta nivån i arkivet innehåller rot-objekt för den här typen av datalager och varje efterföljande nivå kallas för en nod i underordnade objekt.</span><span class="sxs-lookup"><span data-stu-id="9da56-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="9da56-106">Genom att tillåta användare att arbeta på dessa underordnade noder, kan en användare interagera hierarkiskt via datalagret.</span><span class="sxs-lookup"><span data-stu-id="9da56-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="9da56-107">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="9da56-107">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="9da56-108">Se även</span><span class="sxs-lookup"><span data-stu-id="9da56-108">See Also</span></span>

[<span data-ttu-id="9da56-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9da56-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)